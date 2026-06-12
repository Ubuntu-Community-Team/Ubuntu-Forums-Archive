---
title: "Is this possible? Record, add to mythweb, stream? or download/"
date: 2010-11-06
forum: Mythbuntu
---

### Post by geekyhawkes on 2010-11-06
Pretty much as the title really?  I spend a fair amount of time away from home and it would be really cool if i could get myth install after it has recorded a show to add it to mythweb (or similar i guess) in an android friendly fashion so i can download (or preferably stream) to my HTC HD2 / galaxcy tab (if santa is kind!).

I dont want to compromise the original recording on the myth machine so was thinking along the lines of post recording, copy to a new folder, transcode to android friendly fashion, make available on mythweb or similar for stream/download.

Nice idea, but fairly short of ideas where to start with this!

Thanks for any help you can provide;

Andy

---

### Post by ian dobson on 2010-11-06
Hi,

Just install Mythweb on your backend, and just use it to plan your recordings/stream them (asx format) or download them in the recorded format (mpg).

Just make sure you have enough uplink bandwidth. I mainly use Mythweb to plan my recordings, it's much easier to search in it than with the frontend.

Regards
Ian Dobson

---

### Post by geekyhawkes on 2010-11-06
Thanks, i do have mythweb on and have been using it for a while to schedule recordings.  

I clearly should have had a look around mythweb more, obvious within the recorded programs menu.  

Thanks for your help, seems my question is one of lack of familiarity with mythweb!


EDIT:  Works fine from firefox but when i use my android browser apache reports my browser has sent a message it doesnt understand for either the .asx or the mpg download options.  Any thoughts?

---

### Post by ian dobson on 2010-11-06
> **geekyhawkes said:**
> Thanks, i do have mythweb on and have been using it for a while to schedule recordings.  

I clearly should have had a look around mythweb more, obvious within the recorded programs menu.  

Thanks for your help, seems my question is one of lack of familiarity with mythweb!


EDIT:  Works fine from firefox but when i use my android browser apache reports my browser has sent a message it doesnt understand for either the .asx or the mpg download options.  Any thoughts?

Without knowning exactly what the error message is, I can only guess that your andriod browest is not able to handle asx/mpg streams. Maybe have a look in the apache error log file.

Regards
Ian Dobson

---

### Post by tgm4883 on 2010-11-06
You could try installing flash on froyo and activating expermental flash support in mythweb

---

### Post by nickrout on 2010-11-07
There are several apps about which will transcode to iphone friendly fashion and pop the result in a RSS feed, which the iphone then accesses like any other vidcast.

I assume it would work for android too, although some of the transcoding may be different, I too have an android device and would love to play with this. However at the moment I have just been overjoyed with having a combined remote for xbmc (their official android remote is the bees knees!), mythtv (mythmote) and squeezebox.

---

