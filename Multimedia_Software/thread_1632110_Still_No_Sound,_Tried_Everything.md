---
title: "Still No Sound, Tried Everything"
date: 2010-11-27
forum: Multimedia Software
---

### Post by xcalx29 on 2010-11-27
I could really use some help.  I am pretty new to linux, and have setup my HP Pavilion DV7 1245-dx to dual boot into either Windows 7 or Ubuntu 10.10.  I am pretty tech savy, and can get around windows with no problem.

Everything was working great in Ubuntu, until i messed around a little to much in the terminal, entering in numerous command prompts in order to fix a microphone issue with skype. Now my sound does not work at all in Ubuntu, but works fine when i boot into windows 7.  I have attempted numerous fixes found  on this forum, as well as here:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

I have used the alsa-project debugging script to generate the following report on my current setup:

[http://www.alsa-project.org/db/?f=9bfb79eb9e903c698e5bb28448d012efd35fae67](http://www.alsa-project.org/db/?f=9bfb79eb9e903c698e5bb28448d012efd35fae67) 

Could someone please assist? Ill be checking this post frequently, and will provide feedback to any help offered immediately.

-rookie

---

### Post by xcalx29 on 2010-11-27
Well i fixed it on my own. 
Deleted the files in /lib/modules/kernel/sound and then reinstalled. 

Thanks for all the replies....not

---

