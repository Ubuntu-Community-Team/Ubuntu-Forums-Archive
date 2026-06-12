---
title: "no digital out (SPDIF) through &quot;Via VT1708S&quot; on Asus-M4N78-Pro - PLease Help"
date: 2009-07-10
forum: Multimedia Software
---

### Post by old-pioneer on 2009-07-10
Hello dear ubuntu community,

since 2 days i setup my new htpc based on Asus- M4N78-Pro (Geforce8300-Chipset) Mainboard and engergy efficient AMD-Athlon X2 5050e CPU.. I can already watch HDTV Contents over DVB-S2 "TechniSat SkyStar HD2" and all other things works well....execpt Digital Audio Out (SPDIF)

The Operating-System is an ubuntu/mythbuntu 9.04 (jaunty), fully upgraded and patched.
The kernel Version is "2.6.28-13-generic"

...short story ahead....
two weeks ago, i have already installed a prototype based on ga-73pvm-s2h mainboard and intel core2duo cpu fine.
the disadvantages of the prototype-system are HDTV-Support only up to 720P (Nvidia 7100), only two pci-slots and heavy power-comsumption.
Spdif-Out works fine at this system, i could switch between two Digital Device-Outputs SPDIF & HDMI...!

Now @ my brand-new engergy-efficent system based on asus-m4n78-pro with via- VT1708S- audio chipset only one Digital Output Device shows in alsa-mixer.And thats only "HDMI Out..."

Are there any possibility to switch it to my SPDIF-Out?
so i can connect  my Sourround-Receiver over SPDIF and enjoy full DTS/Ac3 etc...

Thanks a lot...
have a nice weekend...

Marc

---

### Post by old-pioneer on 2009-07-10
Hey guys......i'm very happy...i get it working =D

Shell# AlsaUpgrade-1.0.x-rev-1.17 -d
Shell# reboot
Shell# AlsaUpgrade-1.0.x-rev-1.17 -snap
Shell# reboot
Shell# alsamixer

> Now in alsamixer shows up another IEC (Digital Device) -> As default it's muted,
so you've to go to the regulator and press "M".

No it should work!

UBUNTU-SERVER:~$ aplay -l
**** Liste von PLAYBACK Geräten ****
Karte 0: NVidia [HDA NVidia], Gerät 0: VT1708S Analog [VT1708S Analog]
  Untergeordnete Geräte: 2/2
  Untergeordnetes Gerät '0: subdevice #0
  Untergeordnetes Gerät '1: subdevice #1
Karte 0: NVidia [HDA NVidia], Gerät 1: VT1708S Digital [VT1708S Digital]
  Untergeordnete Geräte: 0/1
  Untergeordnetes Gerät '0: subdevice #0
Karte 0: NVidia [HDA NVidia], Gerät 3: NVIDIA HDMI [NVIDIA HDMI]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0


cya

---

