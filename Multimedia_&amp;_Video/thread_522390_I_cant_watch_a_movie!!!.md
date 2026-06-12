---
title: "I cant watch a movie!!!"
date: 2007-08-10
forum: Multimedia &amp; Video
---

### Post by ItsAmazazazing on 2007-08-10
My laptop has a DVD drive, and it picks up that I have a movie in, however Totem wont play either the disc, or the Image file that I have made. How do I add codecs, or how can I solve this problem. I dont want to have to listen to crappy music on the way to work, a movie would be so much better....

---

### Post by kast on 2007-08-10
Not sure the name of all the codec, but what i did was install Automatix2 use that to install the necessary stuff ,flash, non-free codecs etc...  then remove Automatix2. 

I guess Automatix2 can cause some issues when upgrading or something so i lean to the safe side and removed it.

---

### Post by sep1318 on 2007-08-10
Try this page, and see if it helps. [https://help.ubuntu.com/7.04/musicvideophotos/C/video.html]("https://help.ubuntu.com/7.04/musicvideophotos/C/video.html")

---

### Post by ItsAmazazazing on 2007-08-24
I tried to follow the instructions but when it came to installing libdvdcss2, all i could get was  an error that read: 

libdvdcss2:
Depends: libc6 (>=2.4-1) but 2.3.6-Obuntu20.5 is to be installed

---

### Post by nasov on 2007-08-24
howdy there...
i got a similar-ish problem.
My DVD's Play in Totem but only that bit just before the menu and i can not select play not the next chapter buttons work.
i have followed instructiions from [https://help.ubuntu.com/7.04/musicvideophotos/C/video.html](https://help.ubuntu.com/7.04/musicvideophotos/C/video.html)
on how to make DVD's play in ubuntu from the ubuntu website. Got gxine and so on.... listed on the website.
 gxine launches but says its missing a demuxer so it can't play.
any help would be appriciated.

tom

---

### Post by rebolyte on 2007-08-30
> **ItsAmazazazing said:**
> I tried to follow the instructions but when it came to installing libdvdcss2, all i could get was  an error that read: 

libdvdcss2:
Depends: libc6 (>=2.4-1) but 2.3.6-Obuntu20.5 is to be installed

I am having exactly the same problem. I enter "sudo apt-get install libdvdcss2" and this comes up:

[FONT="Courier New"]The following packages have unmet dependencies:
  libdvdcss2: Depends: libc6 (>= 2.4-1) but 2.3.6-0ubuntu20.5 is to be installed
E: Broken packages
[/FONT]
So I try to update libc6, but it says I  already have the latest version.

Any help would be much appreciated.

---

### Post by Gremlinzzz on 2007-08-30
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[https://help.ubuntu.com/community/RestrictedFormats?action=fullsearch&context=180&value=codecs&titlesearch=Titles](https://help.ubuntu.com/community/RestrictedFormats?action=fullsearch&context=180&value=codecs&titlesearch=Titles)
:guitar:

---

