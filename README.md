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

* ## usersテーブル
|Column|Type|Options|
|------|----|-------|
|username|string|null: false|
|email|string|null: false|

### Association
- has_many :group, through: :groups_users
- has_many :message

## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|groupname|string|null: false|

### Association
- has_many :user, through: :groups_users
- has_many :message

## groups_usersテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user

## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|message|string|null: false|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
|photo_id|integer|

|
### Association
- belongs_to :group
- has_many :user
- has_many :photo

## photosテーブル
|Column|Type|Options|
|------|----|-------|
|photo|string|null: false|
|user_id|integer|null: false, foreign_key: true|

### Association
- has_many :message
