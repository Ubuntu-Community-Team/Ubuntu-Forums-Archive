---
title: "8800 crash... help!"
date: 2007-10-14
forum: Multimedia &amp; Video
---

### Post by zeroxwolfx on 2007-10-14
Ok, so i just put Ubuntu, 32-bit edition on my computer, and of course I've been playing with linux for all of two days now, and it all seemed to work out pretty good, until i enabled the drivers for my xfx 8800 320 mb extreme edition gpu.  When i restarted my computer and booted to linux, I got some weird *** colors and an error basically saying that my drivers sucked.  I am completely Linux retarded and have no idea how to fix it, please please give me some assistance.

---

### Post by overdrank on 2007-10-16
> **zeroxwolfx said:**
> Ok, so i just put Ubuntu, 32-bit edition on my computer, and of course I've been playing with linux for all of two days now, and it all seemed to work out pretty good, until i enabled the drivers for my xfx 8800 320 mb extreme edition gpu.  When i restarted my computer and booted to linux, I got some weird *** colors and an error basically saying that my drivers sucked.  I am completely Linux retarded and have no idea how to fix it, please please give me some assistance.

Hi and welcome, when you reach the login screen use the keys ctrl, alt, F1 all at the same time and this will bring you to the command line. Login with user name and password and then enter this command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and answer a few questions ( if you don't know the answers then leave as default answer given) and when complete use the command to reboot ```
sudo reboot
```  When you reach the desktop, I would recommend using Envy to install the drivers for you graphics card.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
Hope this helps and good luck!

---

### Post by zeroxwolfx on 2007-10-21
well, I think i just might have gotten it to work... then I updated to 7.10... now I have no idea what to do again.  This time however I get a screen that says it needs to be configured manually, so when I configure it to the exact specifications, the screen goes black and nothing happens.

---

### Post by Sockerdrickan on 2007-10-21
Ubuntu 7.10 sucks for us 8800 users

---

### Post by zeroxwolfx on 2007-10-21
ok... well the good news is I got my video drivers to work 100% with desktops effects and everything.  The bad news?  Since my 7.10 upgrade, my sound decided to break.  One thing works another goes wrong...  I get some weird error that says "No GSstreamer plug-ins and/or devices found"  Anyway, thats a different problem and I'll bring in up in a different thread.

---

