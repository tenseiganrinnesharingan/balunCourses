# Структура БД для социальной сети ВКонтакте
## Postgres (т.к. сущности со связями) и Blob storage (храним медиа файлы)

### user (профиль пользователя):
- id
- name
- surname
- date_birth
- description
- city
- interests

### user_relation:
- id
- user_id
- post_id_list
- friend_id_list
- subscriber_id_list (подписчики)
- group_list (группы на которе подписан пользователь)
- photo_id_list
- video_id_list
- audio_id_list

### media:
- id
- type (фото/аудио/видео)
- name
- adding_time
- path (сам медиа файл хранится в Blob Storage, в path хранится путь до файла в Blob Storage)

### post:
- id
- description
- media_id
- hashtags
- like_count
- view_count
- comment_id_list

### comment:
- id
- user_id
- username
- adding_time
- likeCount
- parent_comment_id (пусть у нас могут быть вложенные комментарии, т.е. коммент под комментом)

### group:
- id
- name
- subscriber_id_list
- user_count
- post_id_list
- owner_id (тоже что и user_id)

### message:
- id
- chat_id
- user_id
- add_time
- status (pending, sent, read, failed)

### channel:
- id
- user_id_list
- message_id_list
