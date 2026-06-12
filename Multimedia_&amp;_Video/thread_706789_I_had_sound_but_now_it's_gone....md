---
title: "I had sound but now it's gone..."
date: 2008-02-24
forum: Multimedia &amp; Video
---

### Post by zeiz on 2008-02-24
I used to enjoy sound but it's gone after I tried to record with a mic. First record was good second was corrupted and then "whistle" sound appeared, kind of one if mic and speakers are too close... I finally unplugged the mic - no changes, I rebooted and  then I noticed red cross next to volume control on taskbar. There is no sound at all now. I tried to play with sound service. I read <Sticky:Comprehensive..." but I only could get rid of the red cross and no sound anyway :(
Does anybody know what could happen?
PS. My card is supported: SBLive.

---

### Post by superprash2003 on 2008-02-25
try this [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by zeiz on 2008-02-25
> **superprash2003 said:**
> try this [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

Thanks a lot for your answer:) I found the place very useful. However my case is really strange: #more /dev/sndstat => no such file or directory. I navigated to /dev and found there broken link to /proc/asound/oss/sndstat. Filemanager failed to open /proc even as real root but in terminal ls /proc gave me a list of files and folders EXCLUDING asound! It's just gone. I tried to copy asound from LiveCD configuration but it wasn't possible to copy anything to that (probably corrupted)  /proc on my disk (with both terminal or nautilus) and finally I reinstalled the OS. So I still don't know what happened. 
I just noticed that Ubuntu recognized my webcam as "usb-audio", it has entries in sndstat and even has it's own mixer:confused: 
Now I'm trying to enable also my onboard sound chip to use it with Ekiga/Skype. So I'd rather go back to your place. Thanks again:)

---

