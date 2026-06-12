---
title: "Serious problem with Audacious 2.3"
date: 2010-07-08
forum: Multimedia Software
---

### Post by KutViZ on 2010-07-08
I'm using Lucid Lynx, some day ago I had heavy issues with GNOME so I had to do a reinstall. Since then, Audacious isn't working. It quits every time when I want to play music or just view mp3 tags. I reinstalled it both from Software Center and from Synaptic, same thing.

Here's the terminal's code:
--------------------------------------------------------------------------
gepzsir@gepzsir-desktop:~$ audacious2

** (audacious2:8734): WARNING **: event-device-plugin: unable to load config file evdev-plug.conf , default settings will be used.

0x8cb8720 fopen       : path:file:///usr/share/audacious/Skins/Default/viscolor.txt : mode:r : ret:0x8cb8720
0x8cb8720 fsize       : ret:491
0x8cb8720 fread       : size:1 : nmemb:491 : ret:491
0x8cb8720 fclose      : file:0x8cb8720 : ret:0
0x880b6e0 fopen       : path:file:///home/gepzsir/Zen%C3%A9k/DVD1/Kevin%20Suter%20discography/Kevin%20Suter%20-%20Demo%20songs%202009/Irregularity.mp3 : mode:rb : ret:0x880b6e0
0x880b6e0 fsize       : ret:8845112
0x880b6e0 ftell       : ret:0
0x880b6e0 fseek       : offset:0 : whence:0 : ret:0
0x880b6e0 ftell       : ret:0
0x880b6e0 fseek       : offset:0 : whence:2 : ret:0
0x880b6e0 ftell       : ret:8845112
0x880b6e0 fseek       : offset:8845112 : whence:0 : ret:0
0x880b6e0 fseek       : offset:0 : whence:1 : ret:0
0x880b6e0 fseek       : offset:-32 : whence:1 : ret:0
0x880b6e0 fread       : size:8 : nmemb:1 : ret:1
0x880b6e0 fseek       : offset:8845112 : whence:0 : ret:0
0x880b6e0 fseek       : offset:-128 : whence:1 : ret:0
0x880b6e0 fseek       : offset:-32 : whence:1 : ret:0
0x880b6e0 fread       : size:8 : nmemb:1 : ret:1
0x880b6e0 fseek       : offset:8845112 : whence:0 : ret:0
0x880b6e0 fseek       : offset:-256 : whence:1 : ret:0
0x880b6e0 fseek       : offset:-32 : whence:1 : ret:0
0x880b6e0 fread       : size:8 : nmemb:1 : ret:1
0x880b6e0 fseek       : offset:8845112 : whence:0 : ret:0
0x880b6e0 fseek       : offset:-384 : whence:1 : ret:0
0x880b6e0 fseek       : offset:-32 : whence:1 : ret:0
0x880b6e0 fread       : size:8 : nmemb:1 : ret:1
0x880b6e0 fseek       : offset:8845112 : whence:0 : ret:0
0x880b6e0 fseek       : offset:-512 : whence:1 : ret:0
0x880b6e0 fseek       : offset:-32 : whence:1 : ret:0
0x880b6e0 fread       : size:8 : nmemb:1 : ret:1
0x880b6e0 fseek       : offset:8845112 : whence:0 : ret:0
0x880b6e0 fseek       : offset:-640 : whence:1 : ret:0
0x880b6e0 fseek       : offset:-32 : whence:1 : ret:0
0x880b6e0 fread       : size:8 : nmemb:1 : ret:1
0x880b6e0 fseek       : offset:8845112 : whence:0 : ret:0
0x880b6e0 fseek       : offset:-768 : whence:1 : ret:0
0x880b6e0 fseek       : offset:-32 : whence:1 : ret:0
0x880b6e0 fread       : size:8 : nmemb:1 : ret:1
0x880b6e0 fseek       : offset:8845112 : whence:0 : ret:0
0x880b6e0 fseek       : offset:-896 : whence:1 : ret:0
0x880b6e0 fseek       : offset:-32 : whence:1 : ret:0
0x880b6e0 fread       : size:8 : nmemb:1 : ret:1
0x880b6e0 fseek       : offset:8845112 : whence:0 : ret:0
0x880b6e0 fseek       : offset:-1024 : whence:1 : ret:0
0x880b6e0 fseek       : offset:-32 : whence:1 : ret:0
0x880b6e0 fread       : size:8 : nmemb:1 : ret:1
0x880b6e0 fseek       : offset:8845112 : whence:0 : ret:0
0x880b6e0 fseek       : offset:-1152 : whence:1 : ret:0
0x880b6e0 fseek       : offset:-32 : whence:1 : ret:0
0x880b6e0 fread       : size:8 : nmemb:1 : ret:1
0x880b6e0 fseek       : offset:8845112 : whence:0 : ret:0
0x880b6e0 fseek       : offset:-20000 : whence:1 : ret:0
0x880b6e0 fread       : size:1 : nmemb:20000 : ret:20000
0x880b6e0 fseek       : offset:0 : whence:0 : ret:0
0x880b6e0 fclose      : file:0x880b6e0 : ret:-1
0x880b6e0 fread       : size:1 : nmemb:16384 : ret:16384
0x880b6e0 fread       : size:1 : nmemb:16384 : ret:16384
0x880b6e0 fread       : size:1 : nmemb:16384 : ret:16384
0x880b6e0 fread       : size:1 : nmemb:16384 : ret:16384
0x880b6e0 fread       : size:1 : nmemb:16384 : ret:16384
0x880b6e0 fread       : size:1 : nmemb:16384 : ret:16384
0x880b6e0 fread       : size:1 : nmemb:16384 : ret:16384
0x880b6e0 fread       : size:1 : nmemb:16384 : ret:16384
0x880b6e0 fread       : size:1 : nmemb:16384 : ret:16384
0x880b6e0 fread       : size:1 : nmemb:16384 : ret:16384
0x880b6e0 fread       : size:1 : nmemb:16384 : ret:16384
0x880b6e0 fread       : size:1 : nmemb:16384 : ret:16384
0x880b6e0 fread       : size:1 : nmemb:16384 : ret:16384
0x880b6e0 fread       : size:1 : nmemb:16384 : ret:16384
0x880b6e0 fread       : size:1 : nmemb:16384 : ret:16384
0x880b6e0 fread       : size:1 : nmemb:16384 : ret:16384
0x880b6e0 fread       : size:1 : nmemb:16384 : ret:16384
0x880b6e0 fread       : size:1 : nmemb:16384 : ret:16384
0x880b6e0 fread       : size:1 : nmemb:16384 : ret:16384
0x880b6e0 fread       : size:1 : nmemb:16384 : ret:16384
0x880b6e0 fread       : size:1 : nmemb:16384 : ret:16384
0x880b6e0 fread       : size:1 : nmemb:16384 : ret:16384
0x880b6e0 fread       : size:1 : nmemb:16384 : ret:16384
0x880b6e0 fread       : size:1 : nmemb:16384 : ret:16384
0x880b6e0 fread       : size:1 : nmemb:16384 : ret:16384
0x880b6e0 fread       : size:1 : nmemb:16384 : ret:16384
0x880b6e0 fread       : size:1 : nmemb:16384 : ret:16384
0x880b6e0 fread       : size:1 : nmemb:16384 : ret:16384
0x880b6e0 fread       : size:1 : nmemb:16384 : ret:16384
0x880b6e0 fread       : size:1 : nmemb:16384 : ret:16384
0x880b6e0 fread       : size:1 : nmemb:16384 : ret:16384
0x880b6e0 fread       : size:1 : nmemb:16384 : ret:16384
0x880b6e0 fread       : size:1 : nmemb:16384 : ret:16384
0x880b6e0 fread       : size:1 : nmemb:16384 : ret:16384
0x880b6e0 fread       : size:1 : nmemb:16384 : ret:16384
0x880b6e0 fread       : size:1 : nmemb:16384 : ret:16384
0x880b6e0 fread       : size:1 : nmemb:16384 : ret:16384
0x880b6e0 fread       : size:1 : nmemb:16384 : ret:16384
0x880b6e0 fread       : size:1 : nmemb:15557 : ret:15557
0x880b6e0 fread       : size:1 : nmemb:1045 : ret:1045
0x880b6e0 fread       : size:1 : nmemb:0 : ret:0
0x880b6e0 fseek       : offset:0 : whence:0 : ret:0
0x880b6e0 fread       : size:1 : nmemb:1024 : ret:1024
0x880b6e0 fseek       : offset:611338 : whence:1 : ret:0
0x880b6e0 fread       : size:1 : nmemb:1024 : ret:1024
0x880b6e0 fread       : size:1 : nmemb:3072 : ret:3072
0x880b6e0 fread       : size:1 : nmemb:3133 : ret:3133
0x880b6e0 fread       : size:1 : nmemb:3135 : ret:3135
0x880b6e0 fread       : size:1 : nmemb:3135 : ret:3135
Érvénytelen utasítás
--------------------------------------------------------------------------
Last line means "unknown command". The problem isn't in the output plugin because it does the same on all.

I know it's hard but please help me if you can or recommend another similar music player. I don't like Rhythmbox.

---

### Post by cchhrriiss121212 on 2010-07-08
I'm not sure about this error but xmms2 or quod libet are good alternatives.

---

### Post by KutViZ on 2010-07-08
Hey, I've made it! It's working now! 3rd reinstall in two day but worth it. This time I removed every previous plugins and configuration files (hidden folders in /home). Some plugin always crashed I think. :)

:popcorn: Anyway thanks for the suggestions, maybe I'll try them!

---

