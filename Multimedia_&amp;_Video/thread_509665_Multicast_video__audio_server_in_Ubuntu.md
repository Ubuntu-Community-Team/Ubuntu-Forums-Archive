---
title: "Multicast video / audio server in Ubuntu?"
date: 2007-07-25
forum: Multimedia &amp; Video
---

### Post by gwolfman on 2007-07-25
I'm new to Ubuntu and I was wondering if Ubuntu can help me with the following:

[LIST]I'd like to setup a video and/or audio multicast server to stream video/audio to users in a corporate LAN.[/LIST]
Does Ubuntu have a program that can do this or is there a free Linux program out there that will run on Ubuntu that can do this for me?  Any help and/or ideas would be greatly appreciated.

-GWolfman

---

### Post by gwolfman on 2007-07-27
Anyone?

---

### Post by gwolfman on 2007-08-06
*bump*  sorry, looking for an answer of some sort

---

### Post by MMoudry on 2007-08-07
Well yes there are programs to do this. However it ia s acollection of programs working together rather than one program alone. You certanily coul use Video Lan Client that would stream video and audio to one or several multicast adresses.

---

### Post by gwolfman on 2007-08-07
Ok, I know that program.  I'm assuming you mean the VLS (the server version of VLC)?  Does this feature work only on linux or does it run off Windows as well?

Thanks for the reply!

---

### Post by MMoudry on 2007-08-08
no, the VLS is old and unmaintained and they migrated all the features from VLS to VLC so I definetely mean VLC.

Here is a chart how it works :
[http://www.videolan.org/vlc/streaming.html](http://www.videolan.org/vlc/streaming.html)

Here is a list of what works and what doesnt under different systems :
[http://www.videolan.org/vlc/features.html](http://www.videolan.org/vlc/features.html)

MM

---

### Post by gwolfman on 2007-08-08
Thanks a lot!  Especially since you're the only one that replied.  Do you have any experience with this in case I run into issues and need to ask a few questions?  If not, I'll try the VLC forums.

---

### Post by MMoudry on 2007-08-09
Hi, yes I have some experience with this however the hardest part is to setup the multicasting, after it's just one command to stream rtp packets to that address. Feel free to post any question and I'll do my best to answer you.

MM

---

### Post by phpGuyLV on 2008-02-09
> **MMoudry said:**
> Hi, yes I have some experience with this however the hardest part is to setup the multicasting, after it's just one command to stream rtp packets to that address. Feel free to post any question and I'll do my best to answer you.

MM

MM, I am most interested to learn where to start to setup a multicast group. thank you for any info.

---

