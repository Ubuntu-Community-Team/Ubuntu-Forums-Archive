---
title: "Mythtv will not be nice() to me!"
date: 2011-09-01
forum: Mythbuntu
---

### Post by televimsen on 2011-09-01
Problem: 
Playback of recordings (DVB-T) works fine without subtitles. But once subtitles is on, 2-4 frames are usually dropped subsequent to painting lines of subtitles - causing highly visible stuttering. 

I am running Mythbuntu 11.04 on an Asus AT3IONT board 1.6 GHz, 4 cores, 4096 MB RAM with VDPAU graphics. The latest Nvidia driver. 

 MythTV Version : v0.24.1-78-g8b9e5ce 
 MythTV Branch : fixes/0.24 
 Network Protocol : 63 
 Library API : 0.24.20110505-1 
 QT Version : 4.7.2 

Realtime threads are enabled in mythfrontend, VDAPU high quality is selected. "top" reports less than 20% CPU load and no threads of the mythtvfrontend have higher priority. I have edited /etc/security/limits.conf and inserted the following: 
 * - rtprio 0 
 * - nice 0 
 @audio - rtprio 50 
 @audio - nice 20 

And grep audio /etc/group returns: 
audio:x:29:mythtv,perf,pulse 

"top" reports perf as the owner of the process. In the mythfrontend code, nice() is called with -19 as parameter, but nothing happens to the values reported by "ps" or "top". All processes have equal priority (20) and zero NICE value. 

Apparently, I do not understand how to configure Linux to raise the priority (actually drop) the niceness of a user process! 

Please help!

---

