---
title: "How to make the internal speaker beep from a background process"
date: 2007-05-14
forum: Multimedia &amp; Video
---

### Post by vanthai26 on 2007-05-14
Hi

I have a java program that run on the background of my newly installed ubuntu 6.10 server. This java program will reboot the whole system once in a while. Before rebooting the system I like to generate a beep on the system internal speaker. I am using JNI to generate the beep sound and it seems to work fine if I run the program on the foreground with a terminal. However if I run this java program in the background then there is no beep at all.  Is there any one outthere know how I can generate a beep by writing to the /dev/audio directly instead of depending on either C or java api to do it for me. Beside these api seems to require a terminal to hear the beeping sound. Any help is greatly appreciated.....Thanks in advance

T

---

### Post by vanthai26 on 2007-05-17
Does any one outthere nkow how can can manipulate the internal speaker (/dev/audio) on my unbuntu machine  so it make a beep sound.  Please help
Thanks

---

