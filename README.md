# DB設計
## groups_usersテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|references|null: false, foreign_key: true|
|group_id|references|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user

## usersテーブル

|Column|Type|Options|
|------|----|-------|
|mail|string|null: false, unique: true|
|password|string|null: false|
|name|string|null: false|

### Association
- has_many :groups,through:groups_users
- has_many :messages

## groupsテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false|

### Association
- has_many :users,through:groups_users
- has_many :messages

## messagesテーブル

|Column|Type|Options|
|------|----|-------|
|body|string||
|image|string||
|user_id|references|null: false, foreign_key: true|
|groups_id|references|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user
