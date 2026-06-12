---
title: "(another) mesa problem with ATI video card"
date: 2006-09-04
forum: Multimedia &amp; Video
---

### Post by rodrigo666 on 2006-09-04
Okay, I finally give up and ask for help.

I tried it all without successed.

The thing is: I have a ATI Radeon 9600 pro 256 mb and followed a lot of how's-to in this forum to get it working, but "fglrxinfo" command always get me a "mesa3d" drive.

I'm posting my "dmesg | grep fglrx":

> [17179756.180000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologie s, Starnberg, GERMANY' taints kernel.
[17179756.184000] [fglrx] Maximum main memory to use for locked dma buffers: 430  MBytes.
[17179756.184000] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0
[17179757.188000] [fglrx] Internal AGP is not supported in 2.6 kernel.
[17179757.188000] [fglrx:firegl_unlock] *ERROR* Process 7026 using kernel contex t 0

I am also attaching my "/var/log/Xorg.0.log" file. Maybe that can help someone.

I already formated this machine a lot of times and have no problem in doing that again, if that is necessary. 

All I want is get my ATI video card working properly.

Thanks everyone!

---

