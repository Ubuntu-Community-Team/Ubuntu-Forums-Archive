---
title: "How to use DLNA with Ubuntu"
date: 2012-05-09
forum: Multimedia Software
---

### Post by susja on 2012-05-09
Hello,
I just bought HDTV (with WiFi) which supports DLNA. I'm thinking how could I use my Ubuntu 11.10 to connect to TV using DLNA.
Could someone please explain me what should I do on my PC side to enable it ... like install some app? or just enable existing one or etc?
I'm hoping that using DLNA I should be able to stream video from my PC to TV box.
Thanks in advance.

---

### Post by shz1 on 2012-05-09
There are several server software choices. I use minidlna + the webmin interface for minidlna.  Another choice is Serviio.

---

### Post by susja on 2012-05-09
shz1 - thanks for reply ..
does it work well for you? would you recommend me to play with it?
Thanks

---

### Post by susja on 2012-05-09
I also found that my TV supports Plex Media.
Does anyone has opinion which one would be preferable: DLNA or Plex Media?
thanks

---

### Post by ryazkhan on 2012-05-09
> **susja said:**
> I also found that my TV supports Plex Media.
Does anyone has opinion which one would be preferable: DLNA or Plex Media?
thanks

Hi,
I am using minidlna and it is worth trying, for me its working pretty good

---

### Post by shz1 on 2012-05-09
> **susja said:**
> shz1 - thanks for reply ..
does it work well for you? would you recommend me to play with it?
Thanks

It works "well enough".  I have some problems refreshing my library every now and then. I do recommend that you play around with it.

---

### Post by susja on 2012-05-10
- shz1 , ryazkhan
Thanks for your reply. I decided to try it and have some questions if you could help me.
1. I installed minidlna and the webmin.
2. minidlna starts automatically after reboot and I also could access webmin .
Two issues I have:
1. when I login to webmin ... I don't know what to do next  :)
2. when I try to access dlna server from my smartphone it get connected to my server i.e. Ubuntu but it shows only 2 folders and it can't see any folders were actually my pictures and video were stored. FYI: I have samba installed and my home directory is shared so I'd expect to see all folders but I don't. Actually when I try to open e.g. Video folder it states: 'No files to display'. Maybe I should configure some files? BTW I could access my Linux home directory from iPad.
Could you pls answer my question and explain how you practically are using it? I mean currently I'm playing with my smart-phone but the goal is to use dlna client on my TV

Thanks

---

### Post by susja on 2012-05-11
hi,
Eventually I figured out how install and setup minidlna and webmin.
I configured /etc/minidlna.conf file and pointed media_dir to my folders.
Then I rescan/restarted minidlna but for some reason I don't see my folders. I see only 4 defaults empty folders from my client: Music, Video, Pictures and 'Browse Folders'.
Do you have any idea why I can't see my folders?
Thanks

---

