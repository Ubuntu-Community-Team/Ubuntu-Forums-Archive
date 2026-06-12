---
title: "Ubuntu 10.4 Headphone Jack Not Working"
date: 2010-10-19
forum: Multimedia Software
---

### Post by pinbill on 2010-10-19
Hello All-

This site has helped me a ton setting up a win7 ubuntu dual boot system. I have gotten most of the bugs worked out, but now my headphone jack only works in win7 but not ubuntu. I just got finished downloading medibuntu and all the plugins need to play Mp3s. Please help, I listen to my laptop at work and it is important that we keep up the rock!

Thanks,

Bill

---

### Post by tommcd on 2010-10-19
Have you tried running **alsamixer** in the terminal and making sure that the headphone jack is not muted? If it is muted there will be a "MM" at the bottom of the level for the headphone jack. You can unmute it by toggling the "m" key on the keyboard.

Also, what sound card does the laptop have? If you do not know, post the output of the following command here:
```
/sbin/lspci | grep -i audio
```

---

### Post by pinbill on 2010-10-19
Thanks for responding,

I pulled up alsamixer and didn't see a headphone jack, I have:

Master, speaker, pcm, front mic, mic boost, s/pdif (which has no volume control) and one listed beep,

Both mic settings and beep were turned all the way down. Tried listening to headphones, no luck.

It seems like a setting in ubuntu because the jack works with windows. Here is what I got from the terminal, I think I messed something up.

robertwgrodeska@johnny8:~$ sbin/lspci
bash: sbin/lspci: No such file or directory
robertwgrodeska@johnny8:~$ /sbin/lspci
bash: /sbin/lspci: No such file or directory
robertwgrodeska@johnny8:~$ grep -i audio
/sbin/lspci | grep -i audio
/sbin/lspci | grep -i audio


Thanks again for your help,

Bill

---

### Post by tommcd on 2010-10-20
> **pinbill said:**
> 
Both mic settings and beep were turned all the way down. Tried listening to headphones, no luck.
Try turning everything all the way up in alsamixer, including both mic settings, and make sure everything is unmuted.
Also, go to: system > preferences > sound, and try setting everything to alsa instead of pulseaudio if it gives you alsa as an option.
> **pinbill said:**
> 
 I think I messed something up.
robertwgrodeska@johnny8:~$ sbin/lspci
bash: sbin/lspci: No such file or directory

Sorry, lspci is not in /sbin in Ubuntu, like it is in Slackware. It seems that lspci is in /usr/bin in Ubuntu:
```

tom@Asrock:/data/radio$ which lspci
/usr/bin/lspci

```
So just run:
```
lspci | grep -i audio
```
And this should return what sound card you have, like this:
```

tom@Asrock:/data/radio$ lspci | grep -i audio
00:08.0 Multimedia audio controller: ALi Corporation M5455 PCI AC-Link Controller Audio Device (rev 20)

```
And what laptop is this?

---

### Post by CarpKing on 2010-10-20
I had a similar problem with my laptop, which has a Conexant sound card.  After much sorrow, I solved it in 10.10 by following the directions on [this page.](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

Do tell us the output of that command, though.  The way I solved my problem in 10.04 was very specific to my card so I won't post it here unless you have a similar one.

---

### Post by lateefcs on 2010-10-21
I had the same problem with lenovo z460, thanks for posting the solution.

---

### Post by Gulo gulo on 2010-10-21
Re: Ubuntu 10.4 Headphone Jack Not Working

I have a similar problem with my Headphone Jack in the front panel on my Asus Motherboadr M4A78-E after upgrading to alsa 1.0.23 my front panel audio stoppede working. Anybody out there who has a solution?

---

### Post by pinbill on 2010-10-25
Ran the code from carpking and my jack is working perfectly, thanks to everyone for the input.

Bill

---

### Post by anoop9183 on 2010-10-26
guys thanks for the post..
i have a lenovo z460 with ubundu 10.10 and headphone was not working..
after installing from the link provided above it started working, but still there is alot of disturbance. 
its like playing a damaged audio cd..
audio device is:
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
any ideas..?

---

### Post by pwabrahams on 2010-10-28
In my case the headphone setting of alsamixer is greyed out. The column shows in grey.  Typing m doesn't change it (and of course the headphone is dead).

Before the latest system update (as of today) the headphone worked correctly.  I don't know what alsamixer showed previously, but I assume it did not grey out the headphone.

---

### Post by Gulo gulo on 2010-10-30
> **Gulo gulo said:**
> Re: Ubuntu 10.4 Headphone Jack Not Working

I have a similar problem with my Headphone Jack in the front panel on my Asus Motherboadr M4A78-E after upgrading to alsa 1.0.23 my front panel audio stoppede working. Anybody out there who has a solution?

SOLVED showed up that it was a bios setting that was wrong. Front panel audio was set to HD where it should be AC97

---

### Post by pwabrahams on 2010-10-31
On my Asus k60 laptop, like many other laptops, the bios settings are very limited and, in particular, don't include a front panel audio choice.

---

### Post by bford16 on 2010-10-31
I have an HP dv7-1232NR.  Hardware is:```
barry@barry-laptop:~$ lspci -v | grep Audio
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller

```
My headphones stopped working after upgrade to alsa 1.0.23.  I installed the latest version from the development repository per the instructions at
[https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules]("https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules")
After reboot, the headphones worked again.

---

### Post by Larry_Underwood on 2011-02-16
I am having the same problem on an Asus G60vx. I tried to run the link from carpking but it could not reload ht new package information.

---

### Post by Fisher on 2011-11-30
Same thing here, I have a M2N-SLI Deluxe. No way to make audio front panel to work. The setting in bios is AC97. Tried the repositorie and have no package for my Ubuntu version 10.04.3 LTS, 2.6.32-35-generic-pae.
Any ideas??

---

### Post by pwabrahams on 2011-11-30
I too was suffering the headphone jack woes until I found this link:

[https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS]("https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS")

The method given there solved everything cleanly and easily.  If it works for you too, please spread the word.  There are many different threads on this problem.

---

