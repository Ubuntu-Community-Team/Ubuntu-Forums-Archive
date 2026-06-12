---
title: "Audio issue on 12.04"
date: 2012-10-01
forum: Multimedia Software
---

### Post by BigD77 on 2012-10-01
Hello,

   I just upgraded to Ubuntu 12.04 from a disc from Linux Format magazine.  It was an LXF Remix, with Unity and XFCE on it.  It loaded fine, and I have access to either Unity or XFCE.

   My problem is that when I put audio into the microphone jack, it starts coming out of the speakers!  This never happened with previous versions of Ubuntu (9.10 or 10.10).  I dual boot with Windows XP, and I don't have that problem with XP.  I also run ham radio software via Ubuntu/Xubuntu which this plays havoc with, and I can't shut off the speakers or headphones when running this software, since they are needed.  

   This is a 2003 vintage Dell Inspiron 1100 with an Intel 82801 DB-ICH4 sound card (Sigmatel audio).

---

### Post by BigD77 on 2012-10-02
Bump.

---

### Post by BigD77 on 2012-10-06
Don't know if it solved the problem or not, but I re-installed 12.04 from a downloaded USB stick. and the problem cleared up.  Then I added XFCE so I can have either desktop.

---

### Post by Rinre on 2012-10-12
Not sure if it's the same problem but this might be worth a try

I had a similar problem with 12.04, or at least the two seem to be connected (according to another thread on sound issues in 12.04):
On my girlfriend's brand new ASUS 1225C, with Ubuntu 12.04 preinstalled,  the speakers worked fine at first. The second time she started it up  (this time with the battery plugged in, don't know if that makes a  difference), the sound only worked in headphones/external speakers. 

After looking around a bit, I found this ingenious solution:
[https://bugs.launchpad.net/ubuntu/+s...r/+bug/1037763]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1037763")

That is, I upgraded the ALSA dkms package through the link given in the bug report ([https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems))

After I rebooted the computer, the sound works perfectly (also the  switch between speakers and headphones., i.e. the speakers are silent  when headphones are plugged in).

---

