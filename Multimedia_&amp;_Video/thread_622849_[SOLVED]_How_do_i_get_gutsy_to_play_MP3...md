---
title: "[SOLVED] How do i get gutsy to play MP3..?"
date: 2007-11-25
forum: Multimedia &amp; Video
---

### Post by hunter_te on 2007-11-25
The real problem is that i dont have internet on the new gutsy computer. So is there a way to download the mp3 codec on windows and then transfer it to other computer and get it installed...
Is this possible? If yes, how?
Now, not just mp3, can i also download ubuntu updates and other ubuntu stuff in windows system and transfer and install???? :confused:

---

### Post by Keith Hedger on 2007-11-25
Why not just share your internet conection from windows?

---

### Post by hunter_te on 2007-11-25
^^Because we r yet to setup phone lines to the other secluded room and its gonna take a few days. And ubuntu comp. cant even play songs......so i want to do that.....
But will it be possible to do what i asked in first post?

---

### Post by overdrank on 2007-11-25
> **hunter_te said:**
> ^^Because we r yet to setup phone lines to the other secluded room and its gonna take a few days. And ubuntu comp. cant even play songs......so i want to do that.....
But will it be possible to do what i asked in first post?

Hi and you may have a look here
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by hunter_te on 2007-11-25
Yipppeeeeeee :D

---

### Post by Martje_001 on 2007-11-25
Select ubuntu-restricted-extras in synaptic and click 'make script' and execute in on another linux system. It will automaticly download the packages for you. Copy them to a USB-disk, and on the computer without internet do:
```
cd /path/to/usb
sudo dpkg -i *
```

---

### Post by hunter_te on 2007-11-25
@overdrank.
Sorry for that yippeee, i got too excited without giving it a neat look. :lolflag:
APTonCD definitely is a great app. and thanks for it, but it doesnt really solve my problem. It works on linux...

Lemme write very clearly...

I have 2 desktops, one with WinXP and other new one with Gutsy. I dont want to install gutsy in my old computer which also has internet. This new comp. with gutsy is placed in a secluded room and no phone lines have been setup yet, so no internet. Phone lines are going to be setup after sometime. So my ubuntu PC seems lifeless....

Now,_ i want to download codec(s) and update(s) from ubuntu repositories for gutsy on WinXP and transfer them to the secluded PC with gutsy._

---

### Post by Yellow Pasque on 2007-11-25
The packages are all available for download: [http://packages.ubuntu.com/gutsy/](http://packages.ubuntu.com/gutsy/)

---

### Post by Martje_001 on 2007-11-25
> **Martje_001 said:**
> Select ubuntu-restricted-extras in synaptic and click 'make script' and execute in on another linux system. It will automaticly download the packages for you. Copy them to a USB-disk, and on the computer without internet do:
```
cd /path/to/usb
sudo dpkg -i *
```
If you open the script in WinXP you will see a list of URL's with 'wget' before it. Download the URL's one by one, and install them on the ubuntu PC.

---

