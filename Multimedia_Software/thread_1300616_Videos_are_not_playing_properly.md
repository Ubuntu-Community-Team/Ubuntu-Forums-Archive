---
title: "Videos are not playing properly"
date: 2009-10-25
forum: Multimedia Software
---

### Post by samuel.faith on 2009-10-25
Hi folks,

I have been using Ubuntu for quite a long time already and never had this problem before.

Right now I am on my new laptop, Dell Inspiron 1440. The graphic card is ATI Radeon. The resolution is 1366 x 768 (16:9) as the LCD screen of the laptop is an HD (16:9) one.

What happen is, whenever I play movies or any videos, using the default media player or VLC, the videos won't play properly. It won't show entirely on the screen, and I can't move the slider to skip forward or backward, and whenever I did, it will either slow down, and will take some time to move to the point I want to.

If I try full screen, either the X Windows crash and I got a command line screen, or the player would just crash.

I have restricted extras plugins installed and believe me, I've tried like everything I know. Nothing works right now.

I have XP installed on VirtualBox. And when I play the movies on VLC player on my guest OS XP, it just works. No errors.

Help me out with this please, guys. :(

-- Samuel Faith

---

### Post by vinutux on 2009-10-25
In vlc tools > preferences > Video > Output options change to x11    if it is not worked Try one after one form that menu.........

---

### Post by shnurui on 2009-10-25
libdvdread3 refuses to install,
Video player insists that libdvdread3 must be installed
libdvdread4 is "locked by another application"
Gxine doesn't appear anywhere but the app menu, so can't open dvd with it....

Nvidia 512 agp ubuntu 9.04

---

### Post by samuel.faith on 2009-10-27
> **vinutux said:**
> In vlc tools > preferences > Video > Output options change to x11    if it is not worked Try one after one form that menu.........

Thanks a lot! It works like charm :)

---

### Post by vinutux on 2009-10-27
OK...plz....Mark thread SOLVED under **[COLOR="Red"]thread tools[/COLOR]** right top

---

