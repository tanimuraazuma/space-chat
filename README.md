# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...

## usersテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false| index :true|
|email|string|null: false|
|password|string|null: false|
### Association
- has_many :messages
- has_many :groups, through: :group_users
- has_many :group_users

## groupテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
### Association
- has_many :users, through: :group_users
- has_many :messages
- has_many :group_users

## group_userテーブル
|Coulmn|Type|Option|
|------|----|-------|
|user_id|references|null: false, foreign_key: true|
|group_id|references|null: false, foreign_key: true|
### Association
-belongs_to :user
-belongs_to :group

## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|image|string|
|body|text|
|user_id|references|null: false, |foreign_key: true|
|group_id|references|null: false, |foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group