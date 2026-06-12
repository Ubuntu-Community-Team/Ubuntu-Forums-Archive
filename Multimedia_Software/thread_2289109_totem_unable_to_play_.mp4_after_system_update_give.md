---
title: "totem unable to play .mp4 after system update give (segmentation fault) Ubuntu 14.04"
date: 2015-08-01
forum: Multimedia Software
---

### Post by cloube on 2015-08-01
Description
----------------

I have problem playing mp4 file after updating my system  on totem . Totem crash at startup and gives Segmentation fault (core dumped) error .
I am able to play the file using vlc player . below is media info snapshot of the faulty file .

[ATTACH=CONFIG]263549[/ATTACH]
                                                                FAULTY File


when i choose different mp4 file, totem able to play the file. please refer below details.

[ATTACH=CONFIG]263548[/ATTACH]
                                                                OK FILE

I have tested both file on video editing software such as kdenlive and openshot 

On testing using the faulty file, non of  the video editing software able to import the file and crash at startup.

On testing using the ok file , openshot and kdenlive video is kind of choppy,delay and jumping frame at times . I can't do much editing job with this file.


totem information
----------------------------
dpkg -l | grep totem
ii  gir1.2-totem-1.0                                      3.10.1-1ubuntu4                                     amd64        GObject introspection data for Totem media player
ii  gir1.2-totem-plparser-1.0                             3.10.2-0ubuntu1                                     amd64        GObject introspection data for the Totem Playlist Parser library
ii  libtotem-plparser18                                   3.10.2-0ubuntu1                                     amd64        Totem Playlist Parser library - runtime files
ii  libtotem0                                             3.10.1-1ubuntu4                                     amd64        Main library for the Totem media player
ii  totem                                                 3.10.1-1ubuntu4                                     amd64        Simple media player for the GNOME desktop based on GStreamer
ii  totem-common                                          3.10.1-1ubuntu4                                     all          Data files for the Totem media player
ii  totem-mozilla                                         3.10.1-1ubuntu4                                     amd64        Totem Mozilla plugin
ii  totem-plugins                                         3.10.1-1ubuntu4                                     amd64  

kernel video properties
-----------------------------------
 lsmod | grep video
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
video                  19476  2 i915,asus_wmi


My system information
--------------------------------------


[ATTACH=CONFIG]263552[/ATTACH]

[ATTACH=CONFIG]263553[/ATTACH]



I've tried some materials online to solve this problem but to no success . Is anyone out there can give me direction on how to solve this problem?.
I ran out of idea and need some helping hand. HELP!!

---

