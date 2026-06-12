---
title: "Help with sound problem"
date: 2007-11-14
forum: Multimedia &amp; Video
---

### Post by ConundrumPious on 2007-11-14
I have Recently installed Ubuntu and have noticed that my computer offers me no sound whatsoever... I have an Hp Pavilion dv6568se notebook and have already checked the alsamixer...I would really appreciate any help you could offer!

Regards

-Conundrum

P.S 

I have indeed tried quite a few of the quick fixes...

---

### Post by Yellow Pasque on 2007-11-14
What sound card do you have? (run lspci if you're not sure)
Have you tried removing ALSA and using OSS? (see my sig)

---

### Post by ConundrumPious on 2007-11-14
Is it this

06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Expres

or this 

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

also, i have tried doing the oss thing

---

### Post by delusion77 on 2007-11-14
I had this problem and still do. 

I tried following some guys instructions i saw on a similar thread. and my my ubuntu dosnt get past GRUB.   the sceen just says black.  And right now im running of of the live cd. and STILL the sound dont work

---

### Post by erginemr on 2007-11-14
Hello to All,

I am using a Sound Blaster PCI 128 card, but have seen this problem in many threads under Ubuntu forums. And in almost all, the key to the solution was to edit a config file:
/etc/modprobe.d/alsa-base 

and adding the following line:
options snd-hda-intel model=auto

or in some other sites:
options snd-hda-intel model=laptop

Could you please try this and reboot to see if your sound works?

Also please have a look at the following wiki page, It describes ways to make parts of a Dell laptop, which has an Intel HD Audio Controller as the sound card, work. See the audio section:

[https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1330](https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1330)

---

