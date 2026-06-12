---
title: "Flash player settings disabled"
date: 2010-05-24
forum: Multimedia Software
---

### Post by ganeshmallyap on 2010-05-24
Hi,

I use Ubuntu Lucid AMD64 system. I have installed Ubuntu-Restricted-Extras and I believe it has installed 32bit flash player in my computer.  This is working magnificiently, except when I play farmville which is a CPU hog.  

The issue that came to my notice was the flash player cache which gets accumulated beyond 1 GB.  At times it has exceeded 4 GB (my desktop has around 4gb ram).  After 1.4 GB videos tend to crawl.  I tried to change flash settings by right clicking the mouse on the flash video, but I found the settings menu option is greyed out.

Did anybody else facing this issue?  Or does this need me to remove 32 bit player and install 64 bit alpha version of the adobe flash player?  If I install 64 bit adobe flash player, will there be any other issues?

Thanks in advance.

Regards
Ganesh

---

### Post by lovinglinux on 2010-05-24
> **ganeshmallyap said:**
> Or does this need me to remove 32 bit player and install 64 bit alpha version of the adobe flash player?

Yes.

Install [FLASH-AID](http://ubuntuforums.org/showthread.php?t=1491268) extension for Firefox. It will allow you to easily install the 64bit version and go back to the 32bit version if needed.

---

### Post by ganeshmallyap on 2010-05-24
This is really great. Thanks a ton for all your help.

---

### Post by lovinglinux on 2010-05-24
> **ganeshmallyap said:**
> This is really great. Thanks a ton for all your help.

You are welcome. I'm glad you like it.

---

### Post by JamieKitson on 2010-10-09
I found the opposite to be true. I was using the 64 bit version of flash but it was crashing when I tried to fullscreen videos. The solution was to go settings -> display -> disable hardware acceleration, however the version I was using had the settings context menu item disabled. I used flash-aid to reinstall the 64 bit version but to no avail. I then used flash-aid to install the 32 bit version which worked, ie I could click "settings" on the context menu, disable hardware acceleration and fullscreen videos ran.

---

### Post by paul_in_london on 2011-09-10
Just stumbled on a workaround for this.

Switching to full-screen enabled me to access **Settings** after a right-click :)

---

### Post by cdgugler on 2011-12-06
> **paul_in_london said:**
> Just stumbled on a workaround for this.

Switching to full-screen enabled me to access **Settings** after a right-click :)

Awesome! Thanks for posting this.  I had was unable to disable the hardware acceleration in the settings box until I went full screen.

---

