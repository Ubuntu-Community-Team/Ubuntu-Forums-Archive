---
title: "Graphics Unknown"
date: 2011-12-04
forum: Multimedia Software
---

### Post by jimbobs on 2011-12-04
Running 11.10 on IBM T42.  Everything is pretty much functional except that some video playback is choppy.  Looked at System Info and got the following:

Memory     1001.5 MiB
Processor  Intel Pentium(R) M processor 1.70GHz
Graphics   Unknown
OS type    32-bit
Disk       58,0GB

While I understand that this is an old machine lacking in horsepower and memory, by comparison with other PC's, I feel that the video performance should be better.

It runs quite poorly with Movie Player and better with VLC (now my default).

Obviously, the graphics card is working but why does the system not recognize it?  And if the system does not recognize it, is it running optimally? The graphics chip is ATI Mobility Radeon 9600 64M.

Any thoughts on how I might improve the performance?

TIA.

---

### Post by MoreOrLess on 2011-12-04
> Obviously, the graphics card is working but why does the system not recognize it? 
This is a bug in sysinfo. Just ignore it.

---

### Post by alzie on 2011-12-06
OK I had the same issue on an HP Desktop

You need to add glxinfo,  you can search for it in the Software Centre or add it from terminal using ```
sudo apt-get install mesa-utils
```

I hope this helps

---

### Post by Mark Phelps on 2011-12-06
If Ubuntu did not recognize your graphics card, there would be no video drivers -- and you would have no video.

Unfortunately, this is a very old ATI chipset, and ATI dropped Linux support for this chipset years ago.

You are now stuck using the default open-source drivers, which are actually quite good these days -- but I'm not aware of any updated ATI drivers that you can install for this chipset.  So, you're pretty much stuck with what you are seeing now.

---

