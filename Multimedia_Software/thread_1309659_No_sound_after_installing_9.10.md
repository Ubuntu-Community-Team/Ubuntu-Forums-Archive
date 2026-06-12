---
title: "No sound after installing 9.10"
date: 2009-11-01
forum: Multimedia Software
---

### Post by Arthur_D on 2009-11-01
Hello, I've been using several versions of Ubuntu before, and just used the upgrade option each new release, with no issues. When 9.10 came out, I decided to start fresh because I wanted ext4 and 64-bit. Everything worked fine, except for sound.

Here's some technical information:
```

sudo lspci -v | less:
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: Inventec Corporation Device 0040
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at f0500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
        Capabilities: [100] Virtual Channel <?>
        Capabilities: [130] Root Complex Link <?>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

```

I've tried using both PulseAudio (which I run now) and ALSA, and both seems to recognize my sound card, but they don't give me any sound.

---

### Post by Seaniesean on 2009-11-02
Same problem here.  And LOTS of other problems after upgrading to version 9.10.

Here's some info

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: ASRock Incorporation Device 0888
	Flags: bus master, slow devsel, latency 32, IRQ 16
	Memory at fe9f4000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 

Enable-
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

What does "enable" mean, anyone?

After "upgrading" several versions of ubuntu, I have hit on a new, better method for distribution upgrade.  Simply use your current version of ubuntu to download an iso of the new version, then burn it to cd, wipe the ubuntu partition from your hard drive, then install again from the new version of ubuntu on the disc you just made.  This results in a 700% speed increase and a lot less screaming and shouting.

---

### Post by gypsumwolf on 2009-11-02
I have a Dell Mini 10. I had no sound after upgrade (of 9.10). Now the sound is working perfectly. I used this to fix the problem (Its very simple to do). Maybe the solution for your card is somewhat similar.

[http://georgeblog.nyarangi.com/2009/10/no-sound-on-dell-mini-10-running-ubuntu.html]("http://georgeblog.nyarangi.com/2009/10/no-sound-on-dell-mini-10-running-ubuntu.html")

Quoted from the website:"

Follow these steps:
1.First you must find which model of sound card you use, so run this command:


```
cat /proc/asound/card0/codec#* | grep Codec
```


Note: You should obtain this:


```
Codec: Realtek ALC269
Codec: Silicon Image SiI1392 HDMI
```


This means that your soundcard is ALC269. If it is not ALC269, follow the instructions here. Otherwise, continue to step 2.

2.Open /etc/modprobe.d/alsa-base with the following command:

```
sudo nano /etc/modprobe.d/alsa-base.conf
```


3.Paste the following line at the end of the file:

```
options snd-hda-intel model=basic
```


Save the file and close it.

4.Go to System>Preferences>Sound>Hardware.
On the Profile drop down menu, select "Analog Stereo Output".
Make sure the Output Volume is set to 100% and close.

5.Reboot and now you can enjoy Karmic with sound:) "

---

### Post by Seaniesean on 2009-11-02
@gypsumwolf

Curses!  Well, the reinstall WAS quicker, I did it in the time it took for the reply (which was quick) and now its all back to normal.  Good advice for future reference, though.

:-(

---

### Post by epek on 2009-11-02
all others and keep in mind, that the existance of a dummy audio device might be the result of an activated smartlink modem driver. That too disables sound on many laptops

---

### Post by Faz1 on 2009-11-02
> **gypsumwolf said:**
> I have a Dell Mini 10. I had no sound after upgrade (of 9.10). Now the sound is working perfectly. I used this to fix the problem (Its very simple to do). Maybe the solution for your card is somewhat similar.

[http://georgeblog.nyarangi.com/2009/10/no-sound-on-dell-mini-10-running-ubuntu.html]("http://georgeblog.nyarangi.com/2009/10/no-sound-on-dell-mini-10-running-ubuntu.html")

Quoted from the website:"

Follow these steps:
1.First you must find which model of sound card you use, so run this command:


```
cat /proc/asound/card0/codec#* | grep Codec
```


Note: You should obtain this:


```
Codec: Realtek ALC269
Codec: Silicon Image SiI1392 HDMI
```


This means that your soundcard is ALC269. If it is not ALC269, follow the instructions here. Otherwise, continue to step 2.

2.Open /etc/modprobe.d/alsa-base with the following command:

```
sudo nano /etc/modprobe.d/alsa-base.conf
```


3.Paste the following line at the end of the file:

```
options snd-hda-intel model=basic
```


Save the file and close it.

4.Go to System>Preferences>Sound>Hardware.
On the Profile drop down menu, select "Analog Stereo Output".
Make sure the Output Volume is set to 100% and close.

5.Reboot and now you can enjoy Karmic with sound:) "


I lost sound upgrading my Acer Aspire 9500 series from 9.04 to 9.10. Added that one line to my alsa-base.conf and it's back!!

Much appreciated *gypsumwolf*!!! :)

---

### Post by xenon-master on 2009-11-04
It works perfectly on asus 1101HA with Ubuntu 9.10 Karmic.

Thanks ;)

---

### Post by stankopp on 2009-11-04
I have tried everything in this and a myriad other threads after upgrading from 9.04 to 9.10.  Nothing has worked.  I have returned to 9.04.  I did not expect sound problems.  Whoever is in charge of pulseaudio has really screwwed up this one.  I will not upgrade again.  Why are there always problems with these upgrades?

---

