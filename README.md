# chat-space2 DB設計
## usersテーブル
|Column|Type|Options|
|------|----|------|
|email|string|null: falese|
|password|string|null: false|
|name|string|null: false|
### Association
- has_many :messages
- has_many :members
- has_many :groups,throught::group_users

## groupsテーブル
|Column|Type|Options|
|------|----|------|
|name|string|null: faluse|
### Association
- has_many :messages
- has_many :members
- has_many :users,throught::group_users

## group_usersテーブル
|column|Type|Options|
|------|----|-------|
|user_id|references|null: false,foreign_key: true|
|group_id|references|null: false,foreign_key: true|
### Association
- belongs_to :group
- belongs_to :user

## messageテーブル
|Column|Type|Options|
|------|----|-------|
|body|text| |
|image|string| |
|user_id|references|null: false,foreign_key: true|
|group_id|references|null: false,foreign_key: true|
### Association
- belongs_to :group
- belongs_to :user