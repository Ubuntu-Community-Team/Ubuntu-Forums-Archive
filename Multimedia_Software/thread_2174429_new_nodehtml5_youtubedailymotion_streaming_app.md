---
title: "new node/html5 youtube/dailymotion streaming app"
date: 2013-09-14
forum: Multimedia Software
---

### Post by smo on 2013-09-14
hi 

i present my new project called (for the moment) ht5streamer, based on node-webkit and written in html/javascript/css and node modules

available on linux/windows/osX you ll be able to :

- Watch videos without flash
- Video seeking
- Full screen
- Save videos in local database
- Download videos
- Convert audio from videos to mp3
- Open Youtube or Dailymotion links
- Open youtube or dailymotion page of the current video from the application
- Watch videos on your tv thru airplay (freebox only, in france...)
- upnp server/client
- torrent streaming
- Integrated update system...


and a lot more

installation:
[http://ubukey.fr](http://ubukey.fr)

let me know what you think about this software please :)

screenshot:

[IMG]http://www.ubukey.fr/ht5streamer/ht5streamer.png[/IMG]

++

---

### Post by smo on 2013-10-23
hi

nobody interested :( 

??

++

---

### Post by ymurti2 on 2014-09-01
Dear Smo,

I am getting an error message when I try to launchht5streamer from the  terminal.

yajnamurti@radha:~$ ht5streamer
/opt/ht5streamer/ht5streamer: error while loading shared libraries: libudev.so.1: cannot open shared object file: No such file or directory
yajnamurti@radha:~$ 


Can you please help me?


Ymurti

---

### Post by smo on 2014-09-01
hi

on 64 bits

sudo apt-get install libudev1
cd /lib/x86_64-linux-gnu/
sudo ln -s libudev.so.1 libudev.so.0

on 32 bits

sudo apt-get install libudev1
cd /lib/i386-linux-gnu/
sudo ln -s libudev.so.1 libudev.so.0

i edited the post with noobslab's ppa :p


++

---

### Post by ymurti2 on 2014-09-01
Mine is 32 bits. I did what you said but no result, here it is what I got:

yajnamurti@radha:~$ sudo apt-get install libudev1
[sudo] password for yajnamurti: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libudev1 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'libudev1' has no installation candidate
yajnamurti@radha:~$ cd /lib/i386-linux-gnu/
yajnamurti@radha:/lib/i386-linux-gnu$ 
yajnamurti@radha:/lib/i386-linux-gnu$ sudo ln -s libudev.so.1 libudev.so.0
ln: failed to create symbolic link `libudev.so.0': File exists
yajnamurti@radha:/lib/i386-linux-gnu$

---

### Post by smo on 2014-09-01
so

cd /lib/i386-linux-gnu
sudo ln -s libudev.so.0 libudev.so.1

then retry

---

### Post by ymurti2 on 2014-09-01
Thank You Smo. Now it is working!!!!  :lolflag:

---

### Post by mc4man on 2014-09-01
A few comments
The ppa package for 14.04 has a dep on ffmpeg which is not in the Ubuntu repos
The app prompts to update online everytime it's opened even if if apparently did so. (to 172 from 171
Youtube searched vids cannot be played in app window (or not in any obvious fashion

---

### Post by smo on 2014-09-01
hi

so it s packaging problems, ffmpeg is not needed as dependency (but noobslab page give ppa for ffmpeg)

latest version is 1.7.4

if users have problems with the ppa they must ask to noobslab admin

just download zip file from [http://ubukey.fr](http://ubukey.fr) to get right version

++

---

### Post by ymurti2 on 2014-09-01
Smo, today ht5streamer is not working properly. Very slow. Can you instruct me how to unistall and reinstall the right way?

---

