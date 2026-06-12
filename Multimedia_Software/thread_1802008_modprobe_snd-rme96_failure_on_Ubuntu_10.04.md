---
title: "modprobe snd-rme96 failure on Ubuntu 10.04"
date: 2011-07-11
forum: Multimedia Software
---

### Post by mk7 on 2011-07-11
Hi Guys,

I'm trying to get my RME Digi 96 sound card working and having some trouble, I have been reading through the forums and I'm not sure what I should try.  Here is what I have been trying:

$lspci -v

07:02.0 Multimedia audio controller: Xilinx Corporation RME Digi96/8 Pad (rev 04)
    Flags: slow devsel, IRQ 18
    Kernel modules: snd-rme96

$sudo modprobe snd-rme96
$dmesg > message.txt

I have attached the message.txt, looking at this you can see that the driver is failing:

[   45.213296] unable to remap memory region 0x0-0x5ffff
[   45.213349] RME Digi96 0000:07:02.0: PCI INT A disabled
[   45.213353] RME Digi96: probe of 0000:07:02.0 failed with error -12

I'm not sure what I should try next.

Thanks for helping,
Michael

---

### Post by mk7 on 2011-07-11
Apparently .txt files can only be 19.5  KB:

Your file of 66.6 KB bytes exceeds the forum's limit of 19.5 KB for this filetype.

---

### Post by Pro_Sylvain on 2012-05-30
Hi MK7 !

Just have the same problem, after changing my motherboard (it worked before).

I opened a bug report, if you want to subscribe to see the solution (and that the bug affects you too).

See here :

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1005661](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1005661)

---

### Post by Pro_Sylvain on 2012-06-09
Solution here :

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/541991](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/541991)

=> Changing the PCI slot.

Strange, but works !
If this bug affects you, please register launchpad and click to show that the bug affects you.

---

