---
title: "MSI A6500 Laptop / Oneiric = Please Help"
date: 2011-11-04
forum: Multimedia Software
---

### Post by crjackson on 2011-11-04
Hi,

I just bought a new laptop for my daughter and installed 11.10.

The problem is this, sometimes (rarely) when it boots it has sound but most of the time it detects the HDMI sound output only which seems to produce nothing on the internal speakers.

When it does detect both sound devices (HDMI / Analog) the HDMI is the default and I have to change the sound device to Analog in the sound preferences.

I've looked at and tried some things in the guide (remove / reinstall ALSA) but none of that has worked so far.

Can someone please help me track this down and possibly make this work? I need a little hand holding here so I'm begging for assistance please!

Thanks

Here's some more information. This is my terminal output when sound is working:

```
ericka@ericka-MS-16GN:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Okay It seems that if I power all the way off after losing sound, it will return on next boot, but I still have to change the output device.

If I plug in headphones, they work fine, but when I unplug them I've lost the speakers again.

If I select reboot, then it will lose the analog device and I have no sound.

---

### Post by crjackson on 2011-11-08
Bump

---

### Post by MoreOrLess on 2011-11-08
What kind of laptop is this, and are you going to use the HDMI audio?

---

### Post by crjackson on 2011-11-10
It's an MSI A6500 laptop and HDIM won't be used.

---

### Post by crjackson on 2011-11-27
bump

---

### Post by MoreOrLess on 2011-11-28
You can try blacklisting the hdmi module by creating a file in /etc/modprobe.d
```
gksu gedit /etc/modprobe.d/blacklist-hdmi.conf
```
copy/past
```
blacklist snd_hda_codec_hdmi
```
Save and quit.
```
sudo depmod -a
sudo update-initramfs -u -k all
```
Reboot, and hopefully, you'll only have one sound device.

---

### Post by crjackson on 2011-11-28
Cool, I'll try that...

---

### Post by crjackson on 2011-11-30
> **MoreOrLess said:**
> You can try blacklisting the hdmi module by creating a file in /etc/modprobe.d
```
gksu gedit /etc/modprobe.d/blacklist-hdmi.conf
```
copy/past
```
blacklist snd_hda_codec_hdmi
```
Save and quit.
```
sudo depmod -a
sudo update-initramfs -u -k all
```
Reboot, and hopefully, you'll only have one sound device.

Thanks MoreOrLess,

That did the trick as far as default device. I don't have any headsets laying around right here at the moment to test, but speakers are working correctly.

---

