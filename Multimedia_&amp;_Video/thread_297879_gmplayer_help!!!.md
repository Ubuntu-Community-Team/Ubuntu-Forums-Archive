---
title: "gmplayer help!!!"
date: 2006-11-11
forum: Multimedia &amp; Video
---

### Post by Double-Helix on 2006-11-11
[skin] file ( /usr/local/share/mplayer/skins/default/skin ) not readable.
Skin not found (default).


how do I setup a  default skin?

---

### Post by Double-Helix on 2006-11-11
I downloaded a skin and extracted it and I have put a folder in the skins area:

/usr/local/share/mplayer/skins/default/Blue

I still get an error.  Any help?

---

### Post by taurus on 2006-11-11
Why won't you install it in ~/.mplayer/Skin???

---

### Post by Double-Helix on 2006-11-12
I have tried installing it everywhere.

I did install it there also.

/home/jordan/.mplayer/skin/default

/home/jordan/.mplayer/Skin

it is mplayer version from [http://www.mplayerhq.hu/design6/dload.html](http://www.mplayerhq.hu/design6/dload.html)

i have tried the synaptic install and man i am just really struggling to get gmplayer working.  I always get the error:

[skin] file ( /usr/local/share/mplayer/skins/default/skin ) not readable.
Skin not found (default).

---

### Post by taurus on 2006-11-12
It should be ~/.mplayer/Skin/Blue...

How did you install mplayer anyway?

---

### Post by Double-Helix on 2006-11-12
I figured it out:

you have to edit the gui.conf file with the name of the skin

what a pain, anyone know how to resize the video?  I go fullscreen and the window the file is still small, how to expand?

---

### Post by taurus on 2006-11-12
Are you using xv or x11 in ~/.mplayer/gui.conf?

---

### Post by Double-Helix on 2006-11-12
I installed it by unzipping the tar file and then compiling using ./configure and reading through all the errors and getting the dependencies resolved and finally was able to 

then make install

ok now for the hard part

I changed the gui.conf to vo_driver = "xv"

but I get a new error now when I open the movie file

error opening/initializing the selected video_out (-vo) device

---

### Post by taurus on 2006-11-12
In ~/.mplayer/config, add this line in...

```
zoom=yes
```

---

### Post by Double-Helix on 2006-11-12
awesome that worked!!!

now - how to stream all of my movies on the network? 

I have mounted a drive through smb, but streaming wont work for mp3s or for movies

---

