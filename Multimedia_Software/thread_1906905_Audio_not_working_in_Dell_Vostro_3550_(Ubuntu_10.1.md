---
title: "Audio not working in Dell Vostro 3550 (Ubuntu 10.10 Maverick)"
date: 2012-01-10
forum: Multimedia Software
---

### Post by yundi on 2012-01-10
Hi,

I'm trying to install audio drivers for my Dell Vostro 3550 in my Ubuntu 10.10, but I'm not able to do it.

I've tried installing Alsa drivers but they don't work either, so I am kind of desperated.

Here is the $lspci result:


00:00.0 Host bridge: Intel Corporation Sandy Bridge DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Sandy Bridge Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 4 (rev b5)
00:1c.4 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 5 (rev b5)
00:1c.7 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 8 (rev b5)
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation Cougar Point LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 05)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
09:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
0b:00.0 USB Controller: Texas Instruments Device 8241 (rev 02)


Thank you very much,

---

### Post by mörgæs on 2012-01-10
Hi, welcome to the fora.

Do you get sound in a 11.10 live boot?

---

### Post by yundi on 2012-01-10
Hello, and thanks for the welcome.

I have not tried with a live CD, is it needed?. I did manage to get sound just via headphones, but the speakers didn't work. Unfortunately, I changed that config while trying to fix it, and now I don't have sound at all.

Thanks a lot,

---

### Post by juanortiz on 2012-01-10
I have a Vostro 1700 running U 11.10. You may have a problem with the audio jack. When you have a headset jacked in, you interrupt the path to the speaker. The contacts may not be closing when you remove the headset to allow a path to the speakers. Play with it in and out to see if you and restore the speaker.

---

### Post by yundi on 2012-01-11
Hi Juan, and thanks for replying.

The problem is not with the jack nor the hardware, because it works ok with windows 7, that's why I think that it's because of the audio driver.

---

### Post by mörgæs on 2012-01-11
10.10 only has a few month of support left, so you will have to find another release soon. 

I wouldn't spend time fixing 10.10 - better to try a fresh install of 11.10 and troubleshoot this one (if needed).

---

### Post by yundi on 2012-01-11
Upgrading to 11.04 from 10.10 would solve this problem? or should I format and reinstall the whole OS? (this option would be very annoying, I don't want to reinstall all my software again)

Thx

---

### Post by mörgæs on 2012-01-11
I can not tell what works and what does not, only what will give you the best chances for solving the problem. 

Have moved the thread to the multimedia forum. Maybe someone here has other ideas.

---

### Post by MoreOrLess on 2012-01-11
Add this line to /etc/modprobe.d/alsa-base.conf

```
options snd-hda-intel model=dell-vostro-3500
```
Then, restart alsa:
```
sudo alsa force-reload
```

Reference: [http://git.alsa-project.org/?p=alsa-kernel.git;a=blob_plain;f=Documentation/sound/alsa/HD-Audio-Models.txt;hb=HEAD](http://git.alsa-project.org/?p=alsa-kernel.git;a=blob_plain;f=Documentation/sound/alsa/HD-Audio-Models.txt;hb=HEAD)

---

