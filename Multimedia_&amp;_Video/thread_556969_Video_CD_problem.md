---
title: "Video CD problem"
date: 2007-09-22
forum: Multimedia &amp; Video
---

### Post by geeree on 2007-09-22
I know this question has been asked several times on these forums but I could not find any suitable answer. 

I'm using Ubuntu Feisty Fawn and trying to play a video CD. My understanding of multimedia support, codecs, etc. is limited but it would be nice if somebody explains the following: 

[LIST=1]
[*] I have four (!) video players installed on my system (including the default Totem). When asked to play a VCD Totem says "There is no input plugin to handle the location of this movie." Gxine simply hangs. Beep media player cannot play too, although the error is more verbose: it asks me to check if I have enabled the relevant plugins. Realplayer gives a segmentation fault.
[*] Do I need to install a new program that can play a VCD or can I simply install whatever "plugins" these programs need and make them play a VCD? What program or plugin is that?
[*] Is this a problem with the MPEG-1 codec support? Or is there some other  kind of proprietary restriction on playing VCDs? Is it legal to play VCDs on GNU/Linux? 
[/LIST] 

Thanks,
Girish

---

### Post by linuxwizard on 2007-09-22
Check and make sure you have all the codecs you need.

[https://help.ubuntu.com/community/Beginners/Guide/Feisty/Multimedia](https://help.ubuntu.com/community/Beginners/Guide/Feisty/Multimedia)

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Totem will play VCD
[https://help.ubuntu.com/community/MultimediaApplications](https://help.ubuntu.com/community/MultimediaApplications)

---

### Post by geeree on 2007-09-22
Thanks but this doesn't solve my problem.

> **linuxwizard said:**
> Check and make sure you have all the codecs you need.
[https://help.ubuntu.com/community/Beginners/Guide/Feisty/Multimedia](https://help.ubuntu.com/community/Beginners/Guide/Feisty/Multimedia)


All codecs mentioned on this page are already installed on my system. Moreover, there's still no mention of what plugin I need for enabling MPEG-1/VCD support in gstreamer/xine. 

> [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

This page does not have any information on MPEG-1 or VCDs in general. Apparently they are not "restricted formats"? In fact this is one of the questions I asked. It remains unanswered.

> Totem will play VCD
[https://help.ubuntu.com/community/MultimediaApplications](https://help.ubuntu.com/community/MultimediaApplications)


Yeah; that *is* an useful information but doesn't help. My Totem doesn't play VCDs. In fact I found a post on this forum that says VLC will play them and so I installed it (fifth movie player!). VLC does get the sound track but shows no video. Worst, my understanding of all this remains zero. 

Girish

---

