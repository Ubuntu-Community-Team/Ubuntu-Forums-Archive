---
title: "vlc crashes instantly"
date: 2007-09-13
forum: Multimedia &amp; Video
---

### Post by perfect_circle on 2007-09-13
i cant open a file without it crashing.  i tried it in terminal.  heres what it said. whats it mean? what do i do?


@lappy486:~$ vlc V.For.Vendetta[2005]DvDrip[Eng]-aXXo.avi
VLC media player 0.8.6 Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Can't stat V.For.Vendetta[2005]DvDrip[Eng]-aXXo.avi
No such file or directory
libdvdnav: vm: faild to open/read the DVD
[00000296] main input error: no suitable access module for `V.For.Vendetta[2005]DvDrip[Eng]-aXXo.avi'
[00000287] main playlist: nothing to play
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Can't stat V.For.Vendetta[2005]DvDrip[Eng]-aXXo.avi
No such file or directory
libdvdnav: vm: faild to open/read the DVD
[00000310] main input error: no suitable access module for `V.For.Vendetta[2005]DvDrip[Eng]-aXXo.avi'
[00000287] main playlist: nothing to play
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Can't stat V.For.Vendetta[2005]DvDrip[Eng]-aXXo.avi
No such file or directory
libdvdnav: vm: faild to open/read the DVD
[00000314] main input error: no suitable access module for `V.For.Vendetta[2005]DvDrip[Eng]-aXXo.avi'
[00000287] main playlist: nothing to play
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  82
  Current serial number in output stream:  83

---

### Post by PaulFr on 2007-09-13
Have you installed w32codecs ? See
> 1. **[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Multimedia_Codecs_.26_Browser_Plug-ins](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Multimedia_Codecs_.26_Browser_Plug-ins)**
2. **[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)**, and
3. **[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)**for details.

---

### Post by perfect_circle on 2007-09-13
yea, i tried them all, and the program still crashes everytime i open any file type.

---

### Post by rsambuca on 2007-09-13
Have you tried right-clicking the file that you illegally downloaded and selected open with vlc media player?

---

### Post by perfect_circle on 2007-09-13
yes, i did. thats when it was crashing. however, i completely removed it and re-installed it, now all is well.  thanks anyway!

---

### Post by perfect_circle on 2007-09-17
ok, it worked fine for a while then started crashing again. so i completely removed it, and reinstalled it again. and its still crashing, so im at a loss. i even rebooted! i tried it in totem, and it did the same thing.

---

### Post by rsambuca on 2007-09-17
This is strange.  Is it crashing with a file that previously worked?

---

### Post by perfect_circle on 2007-09-17
correct, but its not just that, its every file, even .ogg files. not just .avi's

---

### Post by rsambuca on 2007-09-17
Have you tried running the memory test from the main grub menu?  The reason I am suggesting this is the "insufficient resources BadAlloc)" error.  I would suggest running it overnight, or at least for a few hours and see if that turns up anything.

---

### Post by perfect_circle on 2007-09-17
ok, ill do that tonight, if there is anything else that i could try today, ill do that first.

---

### Post by perfect_circle on 2007-09-20
so ive descoved that it crashes when i have beryl running.  any ideas?

---

### Post by perfect_circle on 2007-09-21
bump?

---

### Post by rsambuca on 2007-09-21
Disable beryl?

---

### Post by perfect_circle on 2007-09-21
well yea i do when i want to watch movies. but is there any way i can run both?

---

### Post by raiwo on 2007-09-21
do you have intel video card? if so there was an update for this that fixed similar problem for me.

edit: i just realised this fix was for gutsy, you didn't mention your version of ubuntu.

---

### Post by perfect_circle on 2007-09-22
7.04 i believe fiesty?  i could be wrong how do i find it out for sure.

---

### Post by perfect_circle on 2007-09-24
bumpizzle?

---

### Post by raiwo on 2007-10-01
system ->about ubuntu

---

