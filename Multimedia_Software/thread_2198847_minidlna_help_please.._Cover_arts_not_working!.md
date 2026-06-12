---
title: "minidlna help please.. Cover arts not working!"
date: 2014-01-10
forum: Multimedia Software
---

### Post by jondecker76-gmail on 2014-01-10
Hello

I'm pulling my hair out over getting minidlna to work with cover arts.
I'm using a standard minidlna.conf:
```

# port for HTTP (descriptions, SOAP, media transfer) traffic
port=8200


# network interfaces to serve, comma delimited
#network_interface=eth0


# set this to the directory you want scanned.
# * if have multiple directories, you can have multiple media_dir= lines
# * if you want to restrict a media_dir to a specific content type, you
#   can prepend the type, followed by a comma, to the directory:
#   + "A" for audio  (eg. media_dir=A,/home/jmaggard/Music)
#   + "V" for video  (eg. media_dir=V,/home/jmaggard/Videos)
#   + "P" for images (eg. media_dir=P,/home/jmaggard/Pictures)
media_dir=V,/media/sde/dlna/video
media_dir=A,/media/sde/dlna/audio
media_dir=P,/media/sde/dlna/pictures
friendly_name=Workout Stuff


# set this if you would like to specify the directory where you want MiniDLNA t$
db_dir=/var/cache/minidlna


# set this if you would like to specify the directory where you want MiniDLNA t$
log_dir=/var/log


# this should be a list of file names to check for when searching for album art
# note: names should be delimited with a forward slash ("/")
album_art_names=Cover.jpg/cover.jpg/AlbumArtSmall.jpg/albumartsmall.jpg/AlbumAr$


# set this to no to disable inotify monitoring to automatically discover new fi$
# note: the default is yes
inotify=yes


# set this to yes to enable support for streaming .jpg and .mp3 files to a TiVo$
enable_tivo=no
# * This will allow server-side downscaling of very large JPEG images,
#   which may hurt JPEG serving performance on (at least) Sony DLNA products.
strict_dlna=no


# default presentation url is http address on port 80
#presentation_url=http://www.mylan/index.php


# notify interval in seconds. default is 895 seconds.
notify_interval=900


# serial and model number the daemon will report to clients
# in its XML description
serial=12345678
model_number=1


# use different container as root of the tree
# possible values:
#   + "." - use standard container (this is the default)
#   + "B" - "Browse Directory"
#   + "M" - "Music"
#   + "V" - "Video"
#   + "P" - "Pictures"
# if you specify "B" and client device is audio-only then "Music/Folders" will $
#root_container=.





```

Everything works fine EXCEPT for cover arts!
If I put a "cover.jpg" in a folder containing "Movie.mp4", then "Movie.mp4" disappears completely from all of my dlna clients.
I'va also tried Movie.jpg, Movie.cover.jpg, etc.  None of them will work.

How do you get cover arts to work with minidlna?  I've searched all day (8+ hours) just to try to get covers to work with absolutely no success.

Thanks

---

