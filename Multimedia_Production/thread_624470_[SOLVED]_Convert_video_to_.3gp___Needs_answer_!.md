---
title: "[SOLVED] Convert video to .3gp   Needs answer !"
date: 2007-11-27
forum: Multimedia Production
---

### Post by CameronCalver on 2007-11-27
OK i no there have been hundreds of identical post for this but i have yet to find a result.
 I have tryed all these commands in the terminal using programs like convertit - BUT  i can convert a video off youtube to avi perfectly but if i try and conver it to .3gp it just say file is converted but NO there i no file created WEIRD. The main reason i need this is because my friend sent me alot of videos from his phone that are in .mp4 and i need them to be converted to .3gp for my phone and the same thing happens with every converter. Can someone help me with this because none of the threads iv seen worked

---

### Post by Creative2 on 2007-11-27
well all depends by your telephone ..... what kind of codec it supports and what kind resolution it supports ... 

give me these things and i will write your solution...

---

### Post by CameronCalver on 2007-11-27
well its a motorola v3x massive screen specs >


Colors 	 
Camera 	2 MP, 1600x1200 pixels, video, flash; secondary video call VGA camera
 	- Java MIDP 2.0
- MP3/AAC/MPEG4 player
Display 	Type 	TFT, 256K colors
Size 	240 x 320 pixels, 33 x 45 mm

according to that it says it can play mpeg4 but it wont play mp4 so i dunno all i can get it to play in videos it .3gp so what do u think?

---

### Post by Creative2 on 2007-11-27
in few seconds i have found this... from my topic

it could not work but in few time is what i found out  (this was for motorola v3i)

```
ffmpeg -i INPUT -s qcif -vcodec mpeg4 -acodec aac -ac 2 -ar 16000 -r 25 -ab 32 -y OUTPUT
```

you can try this too(for your max resolution)

```
ffmpeg -i INPUT -s 240x320  -vcodec mpeg4 -acodec aac -ac 2 -ar 16000 -r 25 -ab 32 -y OUTPUT
```

what i think...mmm i think your mp4 files maybe have particular settings which your phone is not be able  to recognize

---

### Post by CameronCalver on 2007-11-27
```
cameron@ubuntu:~$ ffmpeg -i '/home/cameron/Videos/phone_vidz/bag_hits_fan.mp4'  -s 240x320  -vcodec mpeg4 -acodec aac -ac 2 -ar 16000 -r 25 -ab 32 -y /home/cameron/bag_hits.3gp
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Nov 17 2007 21:23:57, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Input #0, avi, from '/home/cameron/Videos/phone_vidz/bag_hits_fan.mp4':
  Duration: 00:16:24.6, start: 0.000000, bitrate: 3 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 240x320, 13.25 fps(r)
  Stream #0.1: Audio: 0x00ff, 48000 Hz, stereo, 128 kb/s
Unknown codec 'aac'


```


where do i get the aac plugin from?

---

### Post by Creative2 on 2007-11-27
let me know if it works so i can add this commandline..

---

### Post by Creative2 on 2007-11-27
replace aac with mp3 and if doesn t work 
replace aac with libfaac

---

### Post by CameronCalver on 2007-11-27
yeah will do but i need aac plugin

edit oh your to fast for me

---

### Post by Creative2 on 2007-11-27
mm i have seen your mp4 file have frame for second 13, and stuff
mm this is a bit strange....so try to change -r 25 with something  like -r 13 or -r 15

---

### Post by CameronCalver on 2007-11-27
```
Unknown codec 'libfaac'
cameron@ubuntu:~$
```

and 

```
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Unsupported codec for output stream #0.1
cameron@ubuntu:~$ 

```

ideas?

---

### Post by CameronCalver on 2007-11-27
ok i dunno what u mean with that -r 13 thing say that whole command again please

---

### Post by Creative2 on 2007-11-27
mmm try to encode before into avi  with this 

mencoder INPUT -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=192 -srate 48000 -xvidencopts fixed_quant=4 -o OUTPUT

then use ffmpeg

---

### Post by Creative2 on 2007-11-27
i have just converted my avi file to 3gp with 

ffmpeg -i INPUT -s qcif -vcodec mpeg4 -acodec aac -ac 2 -ar 16000 -r 25 -ab 32 -y OUTPUT

and you have the right ffmpeg i think you have installated after you have turned on medibuntu repo right?

---

### Post by Creative2 on 2007-11-27
changing frame for second 

-r 13 or -r 15
to understand see these

ffmpeg -i INPUT -s qcif -vcodec mpeg4 -acodec aac -ac 2 -ar 16000 -r 13 -ab 32 -y OUTPUT

ffmpeg -i INPUT -s qcif -vcodec mpeg4 -acodec aac -ac 2 -ar 16000 -r 15 -ab 32 -y OUTPUT

---

### Post by Creative2 on 2007-11-27
ok here is not easy talk about your problem  i am in irc


#irc.freenode.net

channell 

#ConvertIT

---

### Post by CameronCalver on 2007-11-27
Well i sucessfully converted a video from mp4 to avi but!  when i go to convert to 3gp it says 
```
Unknown codec 'aac'
cameron@ubuntu:~$ 


```
i dunno where i got ffmpeg from i think synaptic

---

### Post by CameronCalver on 2007-11-28
YES it worked i used ffmpeg from media ubuntu THANKS HEAPS one last thing how do i convert flv to avi again?

---

### Post by CameronCalver on 2007-11-28
Works THANKS

---

### Post by Creative2 on 2007-11-28
plz write what have worked...so i will add your command-line :)
yesterday i have talked about some stuff with ffmpeg guys developer and user and with ffmpeg , from medibuntu, we must use aac and not libfaac....this only for ffmpeg...

this means the command-line is right but there is someproblem with your mp4...or with your ffmpeg ....i would like know if you can upload one of yours mp4 so i can see better where is the problem

---

### Post by CameronCalver on 2007-11-28
um all i did was add the mediaubuntu repo and sudo apt get ffmpeg it ??  but another problem the sound quality is real echoy and bad quality why? 

( i uploaded a mp4 for you )

---

### Post by CameronCalver on 2007-11-28
join 
#irc.freenode.net 

#calver

---

### Post by Creative2 on 2007-11-28
ffmpeg -i bag_and_fan_unedit.mp4 -s YOURRESOLUTION -vcodec mpeg4 -acodec aac -ac 2 -ar 16000 -r 25 -ab 192 -y trial.3gp

EX: for 240x320 resolution 

ffmpeg -i bag_and_fan_unedit.mp4 -s 240x320  -vcodec mpeg4 -acodec aac -ac 2 -ar 16000 -r 25 -ab 192 -y trial.3gp


ps next  time read better documentation because in converIT page it said 
[B]
install these packages after you have turned on MEDIBUNTU REPO....[/B]

---

### Post by CameronCalver on 2007-11-28
mkay thanks heaps

---

### Post by Creative2 on 2007-11-29
:P
cheers

---

### Post by Creative2 on 2007-11-30
write solved plz

---

### Post by CameronCalver on 2007-11-30
what  u mean?

---

### Post by CameronCalver on 2007-11-30
do u mean post the command?

---

### Post by CameronCalver on 2007-11-30
another thing if i have this command do convert 
```
ffmpeg -i INPUT -s 240x320  -vcodec mpeg4 -acodec aac -ac 2 -ar 16000 -r 25 -ab 32 -y OUTPUT

```

how would i put that in a script so i right click on the file and run the scrip and it converts?

---

### Post by Creative2 on 2007-11-30
xD if you want put it in a bash script i think you must learn bash....

you have solved your problem... you have found out the command line for your motorola v3x  so plz go in the first page of the this topic and select 

Thread Tools====>Mark this theand as Solved

---

