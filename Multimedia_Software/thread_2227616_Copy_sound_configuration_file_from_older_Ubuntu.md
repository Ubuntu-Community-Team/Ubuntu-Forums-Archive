---
title: "Copy sound configuration file from older Ubuntu?"
date: 2014-06-03
forum: Multimedia Software
---

### Post by miroslav6 on 2014-06-03
Hi,  I recently switched from Windows to Linux. Currently I have installed Xubuntu 14.04 (I also tried Linux Mint 16 and 17 with the same result). Everything is working on my old laptop, except sound.  I will not go through all I tried and my settings (for now). All I want to know, if I can copy some configuration file from older Linux system to newer one?  What I found is that sound is working perfectly on Ubuntu 10.4.  I don't know, what is that big difference between Ubuntu 10.4. and 14.4 in terms of application managing sound?  

Thanks for any help.
Miroslav

---

### Post by TheFu on 2014-06-03
The sound subsystem has changed and drivers have definitely changed in 4 yrs. Copying over settings is unlikely to help, sorry.  They are in ~/.asound* and /etc/default/alsa, and /etc/init/alsa*   .  The change to upstart can also impact audio - especially after suspend/hibernation.

I can only recommend that you google "ubuntu sound troubleshooter" and follow those instructions. Should be from an ubuntu.com website.

The first step is to verify that mute isn't enabled. Usually it is a checkbox inside the mixer app.  I use alsamixer, but any of them should be fine.

Then verify that the driver is loaded. If so,  try internal speakers, external speakers, headphones. You get the idea.
If the driver is NOT loaded, then you need to find it and get one loaded.  Knowing your hardware will be key. [http://blog.jdpfu.com/2013/04/27/linux-troubleshooting-101-knowing-your-hardware](http://blog.jdpfu.com/2013/04/27/linux-troubleshooting-101-knowing-your-hardware)

Good luck. If you get stuck - post your exact sound card (google "ubuntu {sound-card}" first) here for more help. Without that, nobody can really help.

---

### Post by Yellow Pasque on 2014-06-03
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by tgalati4 on 2014-06-04
On my Acer laptop, I have a sound safety setting in BIOS that was tripping me up.  It sets the speakers to mute if the headphones get pulled out, kind of a safety feature if you are watching a loud music video on the bus and your headphones get pulled out.  That feature can also mess up your sound in linux, so try turning it off in BIOS and see if that helps.

---

### Post by miroslav6 on 2014-06-04
Thank you all for answers. I own 10 Years old laptop Acer Aspire 9502WSMi with very primitive BIOS. There is no influencing option whatsoever.

I just installed freshly Linux Mint 17 and here is my Alsa info: [http://www.alsa-project.org/db/?f=a7d3102d0719da946a4e5654295d47374e21c2de](http://www.alsa-project.org/db/?f=a7d3102d0719da946a4e5654295d47374e21c2de)

I tried several Sound troublehootings including those posted as Sticky in the Multimedia/video thread.

It did not help, it just made me to reinstall Linux 3 times in last 3 days - it totally ruined installation.

I am not saying they are wrong, most probably it is me as I am beginner in Linux.

If you can see any problems, I will be happy, if you guide me through correct procedure.

Some additional info:

owner@owner-Aspire-9500 ~ $ dmesg | grep hda

[   16.445794] snd_hda_intel 0000:00:1b.0: irq 44 for MSI/MSI-X

owner@owner-Aspire-9500 ~ $ dmesg | grep HDA

[   16.673246] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15

owner@owner-Aspire-9500 ~ $ cat /proc/asound/card0/codec*|grep Codec

Codec: Realtek ALC260
Codec: Conexant ID 2bfa

---

### Post by Yellow Pasque on 2014-06-04
You may want to wait until kernel 3.15 is released this week and try that. This fix might be relevant: [https://github.com/torvalds/linux/commit/192a98e280e560510a62aca8cfa83b4ae7c095bb](https://github.com/torvalds/linux/commit/192a98e280e560510a62aca8cfa83b4ae7c095bb)

[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)

Also, your libasound is missing/incorrect (it may have been something you did...):
> !!ALSA Version
!!------------

Driver version:     k3.13.0-24-generic
**Library version:**    
Utilities version:  1.0.27.2

```
sudo apt-get install --reinstall libasound2
```

---

### Post by miroslav6 on 2014-06-04
I swear I did not touch the fresh installation. Now I reinstalled libasound: [http://www.alsa-project.org/db/?f=c00e0dfe4d405602759a5ed4a0767832cd0c2c12](http://www.alsa-project.org/db/?f=c00e0dfe4d405602759a5ed4a0767832cd0c2c12) , but it seems nothing changed, even installation ran OK.

I do not understand, what should be done in the first part of your answer (fix).

I have also found on other websites 2 different answers (older ones), how to solve problem with Acer 9500, but I decided not to go through it, unless you confirm it is save and worth trying:

1st
> To solve my problem I did this: {really I do this every time the kernel is updated by update manager :( }

 cd Downloads
wget [http://alsa.mirror.fr/driver/alsa-driver-1.0.25.tar.bz2](http://alsa.mirror.fr/driver/alsa-driver-1.0.25.tar.bz2)
tar xvjf alsa-driver-1.0.25.tar.bz2
cd alsa-driver-1.0.25
./configure --with-cards=hda-intel
make
sudo make install
 <reboot>




2nd
> in */etc/modprobe.d/alsa-base.conf* add:

 options snd-hda-intel model=will probe_mask=1

To second one: in my previous tryouts I added this similar line, which did not work: options snd-hda-intel model=acer

---

### Post by Yellow Pasque on 2014-06-05
> **miroslav6 said:**
> I do not understand, what should be done in the first part of your answer (fix).
"wait until kernel 3.15 is released this week and try that"
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)

> I have also found on other websites 2 different answers (older ones), how to solve problem.

I wouldn't try the 1st one, as that is an old version of ALSA which may not build at all.

The 2nd one puzzles me as I don't know of any model=will for ALC260, but you can try it if you'd like (it's easy to undo if it does not work).

---

### Post by miroslav6 on 2014-06-05
today i tried live CD's of Puppy and Ubuntu 10.4., where my sound works properly.

Just out of curiosity, could you please check it, if you could find some major differencies?

What I noted right away is different IRQ - maybe possible reason?

Puppy: [www.alsa-project.org/db/?f=52571fc9c1eba6482e5ae93635ce19e37c0524f0]("http://www.alsa-project.org/db/?f=52571fc9c1eba6482e5ae93635ce19e37c0524f0")
Ubuntu 10.4.: [http://www.alsa-project.org/db/?f=2d241712f2725925984075d313759b67ab40b1dd](http://www.alsa-project.org/db/?f=2d241712f2725925984075d313759b67ab40b1dd)

---

### Post by Yellow Pasque on 2014-06-05
ALSA had major code changes since 10.04 (they moved to an auto-parser), but you can't just copy some configuration file and expect it to magically work...

Try this (it conatains the patch I linked to): [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

---

### Post by miroslav6 on 2014-06-06
I applied this patch: > oem-audio-hda-daily-dkms_0.201406051811~ubuntu14.04.1_all.deb but nothing changed after reboot.

I will wait for newer kernel, but I do not have much faith in it. I tried kernel 3.14.5, also without any change.

I will also keep testing older versions of Ubuntu as it seems so far the only option for me.

What I have found is that Alsa driver 1.0.21 works for me (Ubuntu 10.4.) and since 1.0.25. it does not.

I assume there is no possibility to apply older alsa driver into newer kernel, right?

---

### Post by Yellow Pasque on 2014-06-06
Can you give updated alsa info now that you've upgraded ALSA?
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by miroslav6 on 2014-06-09
Hi, I have been doing a lot of testing with following result: Sound worked until Ubuntu 12.04.1. From Ubuntu 12.04.2 something changed for integrated Intel sound with Realtek ALC260 and my sound stopped working.

Therefore I am not sure, if upgrading kernel to 3.15 will change anything, but I will give it try, possibly today. Then I will post AlsaInfo.

Then there will be only 1 option for me, which is return to older version: Ubuntu 12.04.1 or Linux Mint 13.

---

### Post by Yellow Pasque on 2014-06-09
Yes, as I've tried to explain, this changed in kernel 3.4.x: [https://github.com/torvalds/linux/commit/20f7d928fa6e](https://github.com/torvalds/linux/commit/20f7d928fa6e)
Kernel 3.4.x came between 12.04.1 (which used 3.2.x kernel) and 12.04.2 (which used 3.5.x).

Recently, there was a fix to that commit (the one I linked to for kernel 3.15.x). If that fix does not work, you should file a bug, because that's the only way it is going to be fixed.

---

### Post by miroslav6 on 2014-06-09
I can confirm it works perfectly!!! :guitar:

After upgrading kernel to 3.15 I can hear sound, very loud actually (even volume is just about 15 %), but it is better than no sound at all.

I recommend it to everyone with Realtek ALC260 sound issue.

Thanks a lot [COLOR=#000000]Temüjin[/COLOR] !!! \\:D/

Final Alsainfo: > [[COLOR=#000000]http://www.alsa-project.org/db/?f=c84aa98ecac49324bab1e8f3fff8f60367a6b9d8[/COLOR]]("http://www.alsa-project.org/db/?f=c84aa98ecac49324bab1e8f3fff8f60367a6b9d8")

---

