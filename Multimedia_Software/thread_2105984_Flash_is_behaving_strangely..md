---
title: "Flash is behaving strangely."
date: 2013-01-17
forum: Multimedia Software
---

### Post by ManamiVixen on 2013-01-17
I'm running Ubuntu 12.10 64bit and flash for me is acting in a bizarre manner that I can not make heads or tales of. 

Essentially what is happening is that flash video refuses play in any browser. Including Firefox, Midori, Epiphany, even Chrome which has it's own plugin. I can play .flv (flash video) in Totem, and can even run local .swf flash files by opening them in a browser; As well as open a Flash game over the internet too, BUT can not play Flash Video in a browser. 

I tried every conceivable fix including the installation of the browsers listed here, reinstalling flashplugin-installer, flash-aid, disabling hardware acceleration on flash, but nothing works.

Also to note, SOMETIMES the video(s) would start, but then would vanish to a black box or with Youtube give me the Error with the static background.   

Does anyone think it could be with the Xorg-Edgers PPA? I have it enabled for the new 313.09 Nvidia Driver and 3.7 Kernel. My internet is also slow, but not so slow as to crash flash. Please help.

UPDATE-------------
Turns out IT WAS my internet connection... Youtube and other video sites apparently and suddenly declared people with slow connections to be of no value and instead display error messages if you cannot load a video in a set time. So I have been Timing-Out the entire time. Found out after using a friend's wifi hotspot which has high speed internet. Loaded a youtube video while connected to my friend and it played fine. Great..... No I have to get COMCAST the only high speed provider in my area who can give me internet service.

---

### Post by ManamiVixen on 2013-01-17
Anybody? Please?

---

### Post by binaryCrusader00 on 2013-01-17
im having the same problem on 12.04 except that instead of your problem im 404ing on the ubuntu security page or whatever

actually it appears to be doing it on everything

```
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/nspr/libnspr4_4.8.9-1ubuntu2.3_i386.deb 404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/n/nss/libnss3_3.13.1.with.ckbi.1.88-1ubuntu6.1_i386.deb 404  Not Found [IP: 91.189.92.190 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/nspr/libnspr4-0d_4.8.9-1ubuntu2.3_i386.deb 404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/n/nss/libnss3-1d_3.13.1.with.ckbi.1.88-1ubuntu6.1_i386.deb 404  Not Found [IP: 91.189.92.190 80]
```

---

### Post by Kiori on 2013-01-17
This is very strange, try loading the liveCD install flash there and see what happens.
I have 64-bit at home and its working fine. It may be the Xorg-edgers ppa but...

I assume the partners repository is activated. Its not with the browsers its not flash per se. I guess you could check your network for issues. Try the livecd first though.

---

### Post by ManamiVixen on 2013-01-17
Alright, I'll try these options. I'll report back tomorrow. Thanks.

---

