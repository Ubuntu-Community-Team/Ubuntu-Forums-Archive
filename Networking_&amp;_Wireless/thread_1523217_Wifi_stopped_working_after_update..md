---
title: "Wifi stopped working after update."
date: 2010-07-03
forum: Networking &amp; Wireless
---

### Post by Strandvasker on 2010-07-03
Hey..

I've been running ubuntu on my Asus 1001ha netbook for half a year or so. I ran Karmic for at while, wifi working and all, accepted the recommended updates when Update Manager popped up and everything was fine until one day I let Update Manager do it's thing and my wifi stopped working.. Lycid had just come out that same week, so I thought "screw it" and installed 10.04 instead..

So I've been running 10.04 for a couple of months now, everything working fine, including the wifi - until today.. Update Manager suggested some upgrades, I accepted and *pouf* my wifi is gone again.. 

That's the second time Update Manager knocks out my wifi, any way to roll back todays update or any suggenstions on how to the the wifi working again?

I use the rt3090sta driver, been working fine until half an hour ago..

---

### Post by Halifaxlad on 2010-07-03
I use an EeePC 901 and have been experiencing nothing but wireless problems for the last 3 weeks or so, it keeps dropping out and reconnecting or just dropping out and failing to reconnect.

It all worked fine when I had Win XP on this system

---

### Post by Strandvasker on 2010-07-03
Not sure just what made the difference, but I got it working again..

First I googled around and found someone recommending doing:

sudo modprobe rt3090sta
iwconfig
dmesg | grep -e-rt2 -e rt3

..that didn't work and just left me with some errors about me having no wlan..

Then I started Ubuntu Software Center, typed rt3090 in the search box and found rt3090-dkms. Just for the hell of it I clicked Remove and it uninstalled. 

Next I found out the Ubuntu Software Center didn't feel like letting me install it again, so I googled some more and found this link:

[https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.3.1.3-0ubuntu0~ppa1_all.deb](https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.3.1.3-0ubuntu0~ppa1_all.deb)

I clicked the link, rt3090-dkms was installed again and my wifi didn't work..

After staring at the screen for a while I swapped back to my terminal and did 'sudo modprobe rt3090sta' and 'iwconfig' again and then my wifi turned on.. 

I'm pretty much clueless as to why, I'm just happy it's working again..

Oh, I connected my netbook wired while doing the above, now the wired connection is unplugged again and I'm writing this over the wifi connection.

---

### Post by Strandvasker on 2010-09-30
Today Update Manager killed my wifi for the third time, luckily the procedure in #3 still works so it was a 5 minute fix.. Any idea how to make it work on a more permanent basis or am I destined to repeat the process every 3-4 months?

---

### Post by mikeleach on 2010-09-30
> **Strandvasker said:**
> Today Update Manager killed my wifi for the third time, luckily the procedure in #3 still works so it was a 5 minute fix.. Any idea how to make it work on a more permanent basis or am I destined to repeat the process every 3-4 months?

Thank you so much Strandvasker!  It took me a week or two to get the wireless working to begin with on my Revo earlier this summer and the update this morning killed my wifi too.  I found your post and two minutes later I was back in business!

Thanks again!

Mike

---

### Post by Donalt2010 on 2010-10-01
Thanks I had the same problem.. Worked a treat.

---

### Post by Strandvasker on 2010-10-03
Glad to be of assistance. I've now downloaded the file from the link and a copy of the instructions to have a permanent home on my laptop, just in case the link or this forum some day goes belly up..

---

### Post by Donalt2010 on 2010-11-24
Yet again I had to refer to this post as my wireless dropped again after the recent update.

---

### Post by Strandvasker on 2010-12-01
> **Donalt2010 said:**
> Yet again I had to refer to this post as my wireless dropped again after the recent update.

Same here. It seems to be related to kernal updates. Maybe some dependencies gets lost when the kernal is recompiled or something?

---

### Post by desnaike on 2010-12-01
I use the same driver for my desktop wifi card and kernel updates always knocks out wifi on my Kubuntu 10.04 drive but not my Ubuntu 10.04 drive I keep the 3090 deb package on an external drive I simply reinstall it after the updates that break it.

---

### Post by Strandvasker on 2011-06-12
Still does the trick!

---

### Post by Strandvasker on 2012-08-21
Needed it again today and it still work, so a shameless bump in case someone else needs to spot this post.

---

