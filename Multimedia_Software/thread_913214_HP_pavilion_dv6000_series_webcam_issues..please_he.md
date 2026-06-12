---
title: "HP pavilion dv6000 series webcam issues..please help"
date: 2008-09-07
forum: Multimedia Software
---

### Post by gnarLEE on 2008-09-07
So I recently switched to Ubuntu(hardy) and I can't seem to get my webcam to work at all...I've tried searching here for a solution, but can't seem to find anything. lsusb recognizes the camera as "Bus 005 Device 002: ID 05ca:1810 Ricoh Co., Ltd"
Anyone know where I might find the driver for this?
Any help would be muuuch appreciated.
I'm pretty new to Ubuntu, so I've got minimal understanding of most of the more "high-tech" stuff.
Trying to learn.

---

### Post by linuxwizard on 2008-09-08
Look here > [http://wiki.mediati.org/R5u870](http://wiki.mediati.org/R5u870) > it shows your webcam listed as supported but don't know if it will work in Hardy. Good Luck

---

### Post by rrbarbosa on 2008-09-08
For Ubuntu users, the website [http://www.arakhne.org/ricoh/index.html](http://www.arakhne.org/ricoh/index.html) provides the deb package for your webcam which is much easier to install.

However I am having a problem right now. As the website says, the package is a kernel module, thus compiled to a specific kernel version. I checked and now I am using the version 2.6.24-19, but the website only provides the package for versions 2.6.24-20 and 2.6.24-21. Using using any this packages causes my system to freeze sometimes (nothing works and I have to reboot).

Are version -20 and -21 of the kernel available in ubuntu repositories? The "update manager" says that my system is up-to-date.

Any suggestions?

---

### Post by tonyblue on 2008-11-30
hey i got hp pavilion dv9260us, and i got a problem with my camera, it never works. i used chesee and amsn but it wont work,
can anybody help find the drivers
thnx in adv

---

### Post by rrbarbosa on 2008-11-30
Which version of Ubuntu are you using?

Supposing you have the same camera as gnarLEE (check with lsusb), the driver is currently broken for kernel 2.6.24-26 or superior, meaning it still doesn't in Intrepid.

I guess the driver mentioned by linuxwizard still works on Hardy though.

---

### Post by roberto971 on 2009-11-17
This will solve your problems:
[http://linux.softpedia.com/progDownload/ricoh-webcam-r5u870-Download-30296.html](http://linux.softpedia.com/progDownload/ricoh-webcam-r5u870-Download-30296.html)

Cheers

R.

---

### Post by chersen on 2009-11-18
> **roberto971 said:**
> This will solve your problems:
[http://linux.softpedia.com/progDownload/ricoh-webcam-r5u870-Download-30296.html](http://linux.softpedia.com/progDownload/ricoh-webcam-r5u870-Download-30296.html)

Cheers

R.

Roberto,
Thank you so much! I've been trying to find a solution to this problem for so long! Can't believe it was as simple as installing the firmware and drivers. You rock!
-M

---

### Post by galland on 2009-11-19
Dear all,

Arakhne.org ([http://www.arakhne.org/ricoh/](http://www.arakhne.org/ricoh/)) does not support kernel prior to 2.6.24.20. You must find the sources and compile by hand the ricoh webcam module. Unfortunately, the sources of this version seems to be removed from Internet.

For kernels 2.6.24.20, 2.6.24.21 and 2.6.24.22 specific packages are provided because they provide a pre-compiled module for the webcam.

For newer kernels, I recommend to use the generic package ricoh-webcam-r5u870 at version 0.11.4. It use the DKMS system which permits to automatically compile the ricoh webcam module just at the end of the installation. According to this it may be usable on all the kernels (if the sources in the packages could be compiled against your kernel).

I'm only the packager of the Ricoh webcam but you are welcome to give me feed back.

Stéphane.

---

### Post by ChristianConservative.ca on 2009-11-25
> **roberto971 said:**
> This will solve your problems:
[http://linux.softpedia.com/progDownload/ricoh-webcam-r5u870-Download-30296.html](http://linux.softpedia.com/progDownload/ricoh-webcam-r5u870-Download-30296.html)

Cheers

R.WOO HOO!  Works for the Ricoh webcams on the HP dv9000 series.  Thanks a bunch!  (man... why did it take forever to find someone who knew what they were talking about on this one?)

---

### Post by Karimbo on 2011-07-31
Hello,

I am having the same problem you did with my HP Pavilion dv9000 webcam. I can't make it work. 

Your link...

[http://linux.softpedia.com/progDownload/ricoh-webcam-r5u870-Download-30296.html](http://linux.softpedia.com/progDownload/ricoh-webcam-r5u870-Download-30296.html)

doesn't work, it's dead. Can you tell me where I could find something similar?

Do you still use the same dv9000 computer? Which kernel are you using? I  am using Lucid Lynx 10.04 and it doesn't "see" my webcam. Any  suggestions? 

God bless you!

---

