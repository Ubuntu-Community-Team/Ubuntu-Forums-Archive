---
title: "Error installing XMMS via .deb file...!"
date: 2007-07-08
forum: Multimedia &amp; Video
---

### Post by bimaljr on 2007-07-08
Hi,
I don't have internet connection on my pc on which I have installed Ubuntu 7.04.

Everything is working fine, but I cannot play my MP3 songs.

I know MP3 codecs are propritory so ubuntu is not supporting it official.

so I downloaded "xmms_1.2.10+20070601-1_i386.deb" file from my friend's PC and run the file on my pc. But it gives me this error : "**Error : Dependency is not satisfiable: libc6**" and cannot install it.

I don't now what is this.. Please help me on installing XMMS with MP3 support.

**PC config :**
Intel original Motherboard
P4 3.06GHz processor with HT technology
256MB RAM


Thanks

---

### Post by bimaljr on 2007-07-09
Ohh..
 I see XMMS in "add/remove program" section and install it via it. The XMMS is installed perfectly but cannot play MP3 songs.

I know it is the patent problem, but how do I play MP3 file on XMMS?

---

### Post by dioporco on 2007-07-09
maybe you get into synaptic and look for some plugins?
or better, remove it with apt-get, and after that do

```
sudo apt-get autoremove
```

then

```
sudo apt-get install xmms
```

you should get xmms only, apt-get will resolve dependencies and you should play mp3.

---

### Post by bimaljr on 2007-07-10
Thanks for your reply..
As I say.. I don't have internet connection. so I cannot use **apt-get** command.

Any other offline way?

---

### Post by dioporco on 2007-09-09
i don't know. try to get "-dev" version of librearies then try to install xmms only via .deb.

---

### Post by bimaljr on 2007-09-11
Hey, I have solved this. I have downloaded some .deb files and the XMMS is now working with MP3 files.. Thanks

---

### Post by neodare on 2008-04-18
ca u specify the particular url from where u get that xmms player

---

