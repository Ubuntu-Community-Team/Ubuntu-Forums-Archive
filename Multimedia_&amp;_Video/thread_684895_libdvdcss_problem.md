---
title: "libdvdcss problem"
date: 2008-02-01
forum: Multimedia &amp; Video
---

### Post by Lloydus on 2008-02-01
Hi Everyone,

I followed this tutorial to get dvd playback on totem.

[http://geekybits.blogspot.com/2007/10/playing-encrypted-dvds-in-ubuntu-710.html](http://geekybits.blogspot.com/2007/10/playing-encrypted-dvds-in-ubuntu-710.html)

I still cant get playback in totem I get the error "The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?"

I would appreciate any advise or suggestions, as libdvdcss appeared to have installed when i was in the terminal, though i still get the same error.

I tried the tutorial for vlc player and m player with similar results, the logs said the same thing.

The log from the terminal is below

Thanks in advance - Lloydus

lloyd@lloyd-laptop:~$ sudo apt-get install libdvdread3 totem-xine libxine1-ffmpeg 
[sudo] password for lloyd: 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
libdvdread3 is already the newest version. 
totem-xine is already the newest version. 
libxine1-ffmpeg is already the newest version. 
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded. 
lloyd@lloyd-laptop:~$ sudo /usr/share/doc/libdvdread3/install-css.sh 
--17:30:32--  [http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb](http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb) 
           => `/tmp/dvdcss-Ax7798/libdvdcss.deb' 
Resolving [www.dtek.chalmers.se](www.dtek.chalmers.se)... 129.16.30.198 
Connecting to www.dtek.chalmers.se|129.16.30.198|:80... connected. 
HTTP request sent, awaiting response... 200 OK 
Length: 25,178 (25K) [text/plain] 

100%[====================================>] 25,178        53.36K/s             

17:30:33 (53.35 KB/s) - `/tmp/dvdcss-Ax7798/libdvdcss.deb' saved [25178/25178] 

(Reading database ... 94174 files and directories currently installed.) 
Preparing to replace libdvdcss2 1.2.5-1 (using .../dvdcss-Ax7798/libdvdcss.deb) ... 
Unpacking replacement libdvdcss2 ... 
Setting up libdvdcss2 (1.2.5-1) ... 

Processing triggers for libc6 ... 
ldconfig deferred processing now taking place 
lloyd@lloyd-laptop:~$

---

