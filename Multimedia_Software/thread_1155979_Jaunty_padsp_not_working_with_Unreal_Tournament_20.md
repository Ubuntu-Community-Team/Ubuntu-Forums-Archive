---
title: "Jaunty: padsp not working with Unreal Tournament 2004 (OSS)"
date: 2009-05-11
forum: Multimedia Software
---

### Post by berot3 on 2009-05-11
big problem: until now - in every previous ubuntu - UT2004 (unreal tournament) worked very nice with padsp/pulseaudio. but in Jaunty... i have no idea whats wrong.
even "killall pulseaudio" didnt help 

so i looked in paman if anythink appears... NOTHING

so i made i test with smplayer:
[INDENT]it doesn't seem to make ANY difference, weather i choose "ALSA" or "pulse"... every time it appearse in paman OR it automatically start pulseaudio itself if i killed pulseaudio... [/INDENT]

soooo wahts going on? why doent pulseaudio STAY DEAD? :confused:

last test with smplayer: i've set "OSS" as output and started smplayer with "padsp smplayer", and indeed paman showed correctly an OSS-stream.
BUT why doesnt it work with UT2004??? all the previous version worked!

and how can i get direct access to my soundcart WITHOUT deinstalling pulseaudio (like in Intrepid with killall pulseaudio)? so i can start UT2004 with "aoss"

P.S.: i searched for a solution here in the forum and of course in google, but couldnt find a problem that like mine...

---

### Post by markbuntu on 2009-05-11
Pulseaudio is set to autostart in /etc/default/pulseaudio. Just comment that line out and then you can kill pulse successfully.

---

### Post by berot3 on 2009-05-13
thx, ill try that, but i wanted to give pa a try; do u have any idea why its not working with "padsp"?

---

### Post by berot3 on 2009-05-17
ok, i want sound, with or without pa, so i removed pulseaudio. but still no sound... i tried aoss and esddsp too...

i also am dualbooting with sabayon, ut2004 causes there no problems at all

whats wrong with alsa? wrong config? can i just copy the config from sabyon over to ubuntu?

lets see...

---

### Post by berot3 on 2009-06-12
seem my openal was messed up, did a fresh reinstall with Kubiuntu this time, works great now :D

---

### Post by PureLoneWolf on 2009-06-12
I realise I am a little late to the party here but Pulseaudio needed to be "apt-get purge"'d from my system to stop interfering with games etc.

This resolved my sound issues for everything, *except* UT2004 interestingly enough.  For that I removed openal.so in the UT2004 system folder and then created a symbolic link in there (called openal.so) that points to /usr/lib/libopenal.so.1

At which point UT2004 sprang into life with sound

I realise you fixed it by moving to Kubuntu, but this should work if you ever go back to Ubuntu :)

---

### Post by berot3 on 2009-06-12
thx PureLoneWolf that is exactly what seems to be the best solution:
```
ln --symbolic /usr/lib64/libopenal.so /path/to/ut2004/System/openal.so
```
but i looked around in the "System"-folder and found another lib: "libSDL-1.2.so.0", so i also made this link:
```
ln --symbolic /usr/lib64/libSDL-1.2.so.0 /path/to/ut2004/System/libSDL-1.2.so.0:
```
,dont know if it is really necessary, but it wont hurt.

p.s.: ill perhaps come back to ubuntu as soon as gnome 3 releases ;)

---

