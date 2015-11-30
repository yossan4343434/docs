#Rails Docs

#Model

## User

**property**
 - id: integer
 - name: string
 - email: string
 - password_digest: string
 - remember_token: string

## Video

model for managing videos
*do not call them movie!*

**property**
 - id: integer
 - title: string
 - url: string (stroed place)
 - category: integer
 - author: string
 - description: text
 - duration: float (length in seconds)
 - source_type: integer (0:user upload, 1:youtube)

**relation**
has_many :sounds, through: :video_sounds
has_many :video_sounds
has_many :thumbnails

## Sound
model for managing jingles and voices
**property**
 - id:integer
 - name:string
 - url:string (stroed place)
 - type:integer (1: sound_stamp or 2: voice)
 - duration:float (in seconds)
 - size:float (in kb)
 - format:string

**relation**
has_many :video_sounds
has_many :videos, through: :video_sounds

## VideoSound
timerecord of sounds in videos
**property**
 - id:integer
 - video_id:integer
 - sound_id:integer
 - time:float (in seconds)

**relation**
belongs_to :video
belongs_to :sound

## Thumbnail
extracted images of video
**property**
 - id:integer
 - video_id:integer
 - name:string
 - size:float (in kb)
 - format:string

**relation**
belongs_to :video


