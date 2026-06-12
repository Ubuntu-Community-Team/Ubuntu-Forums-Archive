---
title: "[SOLVED] Atheros wireless confusion"
date: 2008-12-05
forum: Networking &amp; Wireless
---

### Post by slammed87d21 on 2008-12-05
Well, I'm trying to put Hardy on my Aspire 4720Z. I tried doing what I thought I should do to compile Madwifi (still a noob compiling) but no wireless. My Acer is a 4720Z, Core 2 Duo, 1G ram, 160G HD, Intel audio and video, Atheros AR242x wireless and Broadcom ethernet. If anyone can link me to a walk through or give me a walk through, that would be great. Thanks in advance.

---

### Post by slammed87d21 on 2008-12-05
Should I install Intrepid instead of Hardy?

---

### Post by IQRules on 2008-12-05
Check this thread, [http://ubuntuforums.org/showthread.php?p=6302409](http://ubuntuforums.org/showthread.php?p=6302409)

---

### Post by slammed87d21 on 2008-12-05
The link in the link you posted doesn't work. Trying to get the backports module for Intrepid doesn't work.

---

### Post by |{urse on 2008-12-05
follow these instructions.

> 
jzerbini
September 22nd, 2008, 09:22 AM
Caveira, I didn`t use any parameters to boot, and I didn`t try the 64-bit version of Intrepid. My notebook is also the one with the Athlon X2 processor, and the exact version that worked is the Intrepid Ibex (8.10) alpha 4 32-bits. I didn`t try alpha 5 or anything else since my last post on this thread, because my notebook is still being repaired. I wonder if the alpha 5 will make the 4530 work out of the box? I suspect the 32-bit version will work, not sure about the 64-bit one.

It will [almost] work. Wireless won't work with the native ath5k drivers.
You'll have to compile and load this specific module to get wireless working:
[http://madwifi.org/ticket/1192](http://madwifi.org/ticket/1192)


It's very easy.. Just make && make install, blacklist ath5k and voilá ! Everything's working !


Can you teach me how to blacklist the ath5 before install?

Absolutelly, Sir !

Just open /etc/modprobe.d/blacklist and add the ath5k at the last line of the file.
Or if you're lazy (like me ;]) just run this command:

sudo echo "blacklist ath5k" >> /etc/modprobe.d/blacklist

:popcorn:


> do the steps listed here also as im not sure whether Ibex's modprobe.d is dissimilar from hardy.

[http://ubuntuforums.org/showpost.php?p=6089169&postcount=3]("http://ubuntuforums.org/showpost.php?p=6089169&postcount=3")

---

