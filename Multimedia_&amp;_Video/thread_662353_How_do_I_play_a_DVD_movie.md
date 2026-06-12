---
title: "How do I play a DVD movie?"
date: 2008-01-08
forum: Multimedia &amp; Video
---

### Post by Eoghanalbar on 2008-01-08
I've followed the instructions [in the Ubuntu gutsy guide]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_To_Add_DVD_Playback_Capability"), but it still tells me that "there is no plugin to handle this movie", using the default Totem movie player that starts when I put the disk in.

This is what I got in the terminal. Is the problem with how it just says "ldconfig deferred processing now taking place" and ends?

```
sudo apt-get install libdvdread3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdread3 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

```
sudo /usr/share/doc/libdvdread3/install-css.sh
--18:36:10--  http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb
           => `/tmp/dvdcss-pN6279/libdvdcss.deb'
Resolving www.dtek.chalmers.se... 129.16.30.198
Connecting to www.dtek.chalmers.se|129.16.30.198|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 25,178 (25K) [text/plain]

100%[====================================>] 25,178        26.67K/s             

18:36:11 (26.61 KB/s) - `/tmp/dvdcss-pN6279/libdvdcss.deb' saved [25178/25178]

(Reading database ... 104024 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.5-1 (using .../dvdcss-pN6279/libdvdcss.deb) ...
Unpacking replacement libdvdcss2 ...
Setting up libdvdcss2 (1.2.5-1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

```

---

### Post by defenestratos on 2008-01-09
I had this problem as well. I could never fix it. With me it worked fine with the Gxine program. It was on both my 64 bit and 32 bit setups as well. Mysteriously, Totem started to work later. 
Also it could be the disc. Have you tried a couple? Are they the right region and format (NTSC or PAL). I hit problems trying to play a NTSC on my PAL system.

---

### Post by barisurum on 2008-01-09
The problem may be related to your regions setting.
     First install regionset:
     ```
sudo apt-get install regionset
```
     insert a dvd with your regionset (ex: 1 for US, 2 for EU)
     ```
regionset
```
     set your drive to the correct region
     see if it helps.

---

