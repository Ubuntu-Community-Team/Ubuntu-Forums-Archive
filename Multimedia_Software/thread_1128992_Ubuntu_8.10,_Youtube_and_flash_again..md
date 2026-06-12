---
title: "Ubuntu 8.10, Youtube and flash again."
date: 2009-04-18
forum: Multimedia Software
---

### Post by Jimmmac1 on 2009-04-18
Hi all

Well, I am back again.  I was having problems with Youtube video's playing on my computer.  I installed FlashPlayer-Nonfree and that didn't help.  Then I ran a script from this site which someone suggested on the forum

[http://www.myscienceisbetter.info/64bit/](http://www.myscienceisbetter.info/64bit/)

And it worked the first time, but then when I started up Firefox again, it wouldn't play ANY flash websites at all.  This is getting frustrating.  Has anyone solved this problem yet?  Thanks for your help.

Jim

---

### Post by radovav on 2009-04-18
Not sure that this is gonna help, but try to have a look here
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by gandaran on 2009-04-18
> **Jimmmac1 said:**
> Hi all

Well, I am back again.  I was having problems with Youtube video's playing on my computer.  I installed FlashPlayer-Nonfree and that didn't help.  Then I ran a script from this site which someone suggested on the forum

[http://www.myscienceisbetter.info/64bit/](http://www.myscienceisbetter.info/64bit/)

And it worked the first time, but then when I started up Firefox again, it wouldn't play ANY flash websites at all.  This is getting frustrating.  Has anyone solved this problem yet?  Thanks for your help.

Jim
are you running 64-bits ubuntu? you followed that link for installing 64-bits flash, did you remove the flasplugin-nonfree first.
note: I wouldn't recommend using that link unless you know what you are doing, this is an easier  link for installing [64-bits flash]("http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml")

---

### Post by Jimmmac1 on 2009-04-18
Hi all

Thanks for your responses.  I think I am running 32 bit Ubuntu.  But somehow on my first post for this problem, someone moved the discussion to 64 bit.  I didn't see any information about installing 32 bit.  Now I am not sure even how to uninstall the 64  bit if I had to.  But I was getting to the point where I would try anything to get things working.  If there is a post somewhere on how to do 32 bit, I would be more than happy to try that.  Thanks again.

Jim

---

### Post by gandaran on 2009-04-18
> **Jimmmac1 said:**
> Hi all

Thanks for your responses.  I think I am running 32 bit Ubuntu.  But somehow on my first post for this problem, someone moved the discussion to 64 bit.  I didn't see any information about installing 32 bit.  Now I am not sure even how to uninstall the 64  bit if I had to.  But I was getting to the point where I would try anything to get things working.  If there is a post somewhere on how to do 32 bit, I would be more than happy to try that.  Thanks again.

Jim
for 32-bits the flashplugin-nonfree from the repository or the adobe-flashplugin you can download from [adobe]("http://get.adobe.com/flashplayer/") should work if the system is fully updated first.
your big problem now is removing the 64-bits flash, don't install anything if you don't understand the process, look at that script again, find the folder and links where it installed the libflashplayer.so file, delete the libflashplayer.so file and libflashplayer.so links.
to find out if 32-bits or 64-bits type in terminal **uname -a** post the output here.

---

### Post by Jimmmac1 on 2009-04-19
Hi all

Thanks for your responses.  I think I finally got it fixed.  Or at least it is working for now.  I just uninstalled the Adobe flash plugin and kept the non-free and all is working.  Thanks again.

Jim

---

### Post by hyperdude111 on 2009-04-19
If you want to have all codecs = Java, flash, divx, mp3 etc. go to terminal and type.

```
sudo apt-get install ubuntu-restricted-extras
```

---

