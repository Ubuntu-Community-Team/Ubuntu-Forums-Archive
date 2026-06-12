---
title: "what linux tools are needed to down load You Tube videos?"
date: 2009-05-14
forum: Multimedia Software
---

### Post by edhawk2 on 2009-05-14
Pretty straight forward...
What do I need to copy you tube videos onto my hard drive.  I have a Dell PIII laptop runing Jaunty.

---

### Post by themusicalduck on 2009-05-14
There are a fair few websites around that do that for you, but if you want a software program then I think there is one written for adobe AIR. (I got it but didn't actually test it). If you do a search around you can probably find adobe air and the program pretty easily.

---

### Post by Vaphell on 2009-05-14
you have something like dozen of different firefox addons to do that

or you can just create bookmark with this address:

javascript:if(document.location.href.match(/http:\/\/[a-zA-Z\.]*youtube\.com\/watch/)){document.location.href='http://www.youtube.com/get_video?fmt='+(isHDAvailable?'22':'18')+'&video_id='+swfArgs['video_id']+'&t='+swfArgs['t']}

and click it when you have page of youtube video opened

---

### Post by sgosnell on 2009-05-14
You don't need anything special.  Open the video, start playing it and immediately pause it.  When it has fully downloaded, as seen by the progress bar going all the way to the end, open Nautilus and go to /tmp.  The temp file will be there, probably named FLASH*, where * is a series of letters/numbers, and you can copy and paste it to anywhere you like, renaming it to whatever you want.  If you give it a .flv extension, you can open it by double-clicking on it.

---

