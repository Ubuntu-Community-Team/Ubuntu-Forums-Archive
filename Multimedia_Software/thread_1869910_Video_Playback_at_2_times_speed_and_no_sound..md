---
title: "Video Playback at 2 times speed and no sound."
date: 2011-10-26
forum: Multimedia Software
---

### Post by martinskruze on 2011-10-26
Hi,

I have a problem in Ubuntu 10.10
Since yesterday I cannot watch any video, in any medium, because it is sped-up - the playback speed is around two times normal and there is no sound to it.

It is over any medium - youtube.com (boath - flash and html5), any other flash or html video, any video with Totem Movie Player, but VLC player gets speed OK, but with no sound.

There is no sound in general.

Thanks for every attempt to help.

Martins

---

### Post by t-dome on 2011-11-01
I have the same problem. After upgrading to the new version, Kubuntu 11.10 64 bit doesn't play audio anymore and flash videos play back at twice the speed.


> lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:03.0 Communication controller: Intel Corporation 4 Series Chipset HECI Controller (rev 03)
00:03.2 IDE interface: Intel Corporation 4 Series Chipset PT IDER Controller (rev 03)
00:03.3 Serial controller: Intel Corporation 4 Series Chipset Serial KT Controller (rev 03)
00:19.0 Ethernet controller: Intel Corporation 82567LM-3 Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801JD/DO (ICH10 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801JD/DO (ICH10 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801JD/DO (ICH10 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a2)
00:1f.0 ISA bridge: Intel Corporation 82801JDO (ICH10DO) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801JD/DO (ICH10 Family) 4-port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801JD/DO (ICH10 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801JD/DO (ICH10 Family) 2-port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3600 Series
01:00.1 Audio device: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series]


---

### Post by rockprincess on 2011-11-16
hey guys,

i have exactly the same problem. have you found any fix to this problem yet?
please help, if you can :)

---

### Post by t-dome on 2011-11-16
> **rockprincess said:**
> hey guys,

i have exactly the same problem. have you found any fix to this problem yet?
please help, if you can :)

Yes, I reinstalled Kubuntu from scratch.

Initially I had an installation dating back from 10.10 with upgrading to every new version, and a mix of Gnome and KDE.

---

### Post by rockprincess on 2011-11-16
> **t-dome said:**
> Yes, I reinstalled Kubuntu from scratch.

Initially I had an installation dating back from 10.10 with upgrading to every new version, and a mix of Gnome and KDE.

I was afraid you were gonna say that :(
I really wanna fix this without having to reinstall kubuntu from scratch. In the meantime I fixed my problem with the audio in amarok, and the video playback (with sound) in Dragon player.

But i still cant get flash videos à la youtube to work DAMN :(

please help, anyone who reads this!

thanks x

---

### Post by marinara on 2011-11-17
I've had this problem come up twice,  In the last two days.  

It's probably nothing but I also get errors on this: (which works when I tried it on my VM)> 
sudo apt-get install --reinstall libasound2

Both times I was able to format and reinstall Lubuntu clean to fix it.  

Now having someone delete my bug report out of Launchpad.net... now that's frustrating!

---

### Post by rockprincess on 2011-11-17
the solution for my problem was,

reinstalling the flash driver (latest version)
AND
killall pulseaudio (then audio worked in flash videos again)

thankyou pulseaudio, you cost me several hours of my life grrr!! :(

---

### Post by marinara on 2011-11-17
Please and Thank you post the fix for this.

Please post a link to step-by-step instructions that fixed the problem.

Is there a fix for flash and and a fix for 'everything else'?  Or is there just one fix, that fixes it all?

---

