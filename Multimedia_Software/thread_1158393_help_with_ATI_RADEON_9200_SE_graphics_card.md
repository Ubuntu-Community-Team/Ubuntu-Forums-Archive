---
title: "help with ATI RADEON 9200 SE graphics card"
date: 2009-05-13
forum: Multimedia Software
---

### Post by Bigneil on 2009-05-13
Hi, i have been having a little bit of trouble with my flash player, i think i have exhausted every possibility of codecs drivers and installed flashplayer from different locations after reading other threads.  Youtube videos for example work more or less ok but get very jerky on full screen.  

I read up on the sticky about video too, and made sure everything was up to date and all the restricted repositories were enabled. (whether i have understood and followed the directions properly, I don't know)


So, i mentioned this in an unrelated thread and someone suggested that the problem may actually be due to my graphics card and or my drivers.

I did a little research but i don't really get it#-o

I did find some instructions and work arounds for older ubuntu versions. but i haven't found anything hardy related yet.

I stumbled on this > [https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

My output was the attached file

My worry is that this web page is for an older ubuntu, and won't work for hardy. 


any help advice or comments would be greatly appreciated.

---

### Post by Bigneil on 2009-05-14
Am I just barking up the wrong tree. or should i just admit defeat and buy a better card off Ebay  lol

---

### Post by Megamanic on 2009-05-14
You've got a similar problem to me.

[This page ]("http://wiki.cchtml.com/index.php/Ubuntu") gives you some useful background.

9.04 has XServer 1.7
Older ATI cards are only supported to Catalyst 9.3
Catalyst 9.3 is incompatible with XServer 1.7

So, you are stuck on the Open Source 3D drivers which it may or may not be possible to get working well.  There are reports of people getting good performance but I've not sen anything concrete.

Your options:-

1. Stand pat - the open source drivers will steadily improve.  Although ATI aren't supporting us with their proprietary drivers anymore they have given documentation to the open source community and provide developers to the open source driver project
2.Downgrade to Ubuntu 8.10 (or presumably earlier) and install the catalyst 9.3 driver.  The above link will provide help.

---

### Post by Bigneil on 2009-05-14
thanks megamanic, your advice is very helpful

---

