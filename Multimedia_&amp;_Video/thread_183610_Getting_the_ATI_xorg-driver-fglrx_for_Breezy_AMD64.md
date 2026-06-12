---
title: "Getting the ATI xorg-driver-fglrx for Breezy AMD64"
date: 2006-05-28
forum: Multimedia &amp; Video
---

### Post by Frank-Hamersley on 2006-05-28
Apols for the n00b question, but I am struggling to get down the Breezy xorg-driver-fglrx driver for my ATI Xpress 200 controller.

I know it is restricted but my "apt-get install xorg-driver-fglrx" simply says it can't find the package.

I have had a look in /etc/apt/sources.list but can't pick out where I have to enable access to the restricted packages.

Can someone point me in the right direction?

Cheers, Frank.

---

### Post by Lokken on 2006-05-28
[QUOTE=Frank-Hamersley]Apols for the n00b question, but I am struggling to get down the Breezy xorg-driver-fglrx driver for my ATI Xpress 200 controller.

I know it is restricted but my "apt-get install xorg-driver-fglrx" simply says it can't find the package.

I have had a look in /etc/apt/sources.list but can't pick out where I have to enable access to the restricted packages.

Can someone point me in the right direction?

Cheers, Frank.[/QUOTE]


Frank,

It might be simpler to just use Synaptic, and search for 'fglrx' (why couldn't they pick a better name?).

Just a thought,
                        Lokken.

---

### Post by Frank-Hamersley on 2006-05-28
Thanks for the tip - I haven't got a working X environment yet so expect I will have to persevere with the apt-get cli approach for now.

I can see the pkg on several of the ubuntu mirrors but can't convince apt-get to find it.  I know the "restricted" packages were out of bounds (from the installer) but am wondering what change is required in the apt config to put them back on the supply list?

Cheers, Frank.

---

### Post by Frank-Hamersley on 2006-05-29
OK - cracked it - simple really.  First those following ...

1) Update /etc/apt/sources.list to show (for an au mirror)...

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) breezy main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) breezy main restricted

(ie. add the restricted if not already present).

2) then run "apt-get update"

3) finally you can run "apt-get install xorg-driver-fglrx" as described in

[http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide)

Step 2) was the key bit I was missing!  Cheers, Frank.

---

