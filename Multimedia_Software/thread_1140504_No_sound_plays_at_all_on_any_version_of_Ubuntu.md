---
title: "No sound plays at all on any version of Ubuntu"
date: 2009-04-27
forum: Multimedia Software
---

### Post by herefishyfishy on 2009-04-27
My sound isn't working. I followed the Comprehensive Sound Solutions Guide and the HDA Intel Guide but they haven't helped. I am using an HP Pavilion dv7-1023cl with no hardware changes:

```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 30f4
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at df300000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: oss_hdaudio
	Kernel modules: snd-hda-intel

```

Before I switched from ALSA to OSS and disabled PulseAudio (by running a startup application to kill it) in an attempt to fix the sound, I was only getting system beeps, and PulseAudio detected the sound but it wouldn't play anything - not on speakers, not on the microphone, not on anything but the system beep. (Looking back I probably shouldn't have switched from ALSA... now I don't even get system beeps)

(Also: I have had this problem since I had installed Ubuntu on this computer, which was before 9.04 existed, so that is not the problem.)

I appreciate any help!

---

### Post by herefishyfishy on 2009-07-20
Is there anyone who can help me?

---

### Post by igorzwx on 2009-07-21
aplay -l

man aplay

---

### Post by martinbaselier on 2009-07-21
> 
	Kernel driver in use: oss_hdaudio
	Kernel modules: snd-hda-intel

This suggest you have both an oss and an alsa kernel module. 
That's bound to raise conflicts. 

could you post the output of these commands:
```

lsmod | grep snd
lsmod | grep oss

```

---

### Post by herefishyfishy on 2009-07-21
```
mitchell@ubuntu:~$ aplay -l
aplay: device_list:217: no soundcards found...
mitchell@ubuntu:~$ lsmod | grep snd
mitchell@ubuntu:~$ lsmod | grep oss
oss_usb               133428  2 
oss_hdaudio           160356  6 
osscore               607428  2 oss_usb,oss_hdaudio
usbcore               175760  7 usbhid,oss_usb,uvcvideo,btusb,ehci_hcd,uhci_hcd
```

---

### Post by igorzwx on 2009-07-21
On my old box I have this:
$ lsmod | grep oss
oss_usb               117132  3 
oss_via823x            21232  5 
osscore               561844  6 oss_usb,oss_via823x

It is a big difference.
You have HDA, I have not it.
I got correct setting in the mixer by default,
and you should make this by hands.

Read this:
[7.1 Troubleshooting HDAudio devices]("http://wiki.archlinux.org/index.php/OSS#Troubleshooting_HDAudio_devices")
[http://wiki.archlinux.org/index.php/OSS#Troubleshooting_HDAudio_devices](http://wiki.archlinux.org/index.php/OSS#Troubleshooting_HDAudio_devices)

If it does not help, ask on the OSS4 forum

---

### Post by igorzwx on 2009-07-21
try 

osstest

---

### Post by herefishyfishy on 2009-07-21
I have switched from OSS back to ALSA since I posted this topic. Sorry for not mentioning. However, it still doesn't work.

```
mitchell@ubuntu:~$ osstest
Sound subsystem and version: OSS 4.2 (b 090324/200904261656) (0x00040100)
Platform: Linux/x86_64 2.6.27-11-generic #1 SMP Wed Apr 1 20:53:41 UTC 2009

*** Scanning sound adapter #-1 ***
/dev/oss/oss_hdaudio0/pcm0 (audio engine 0): HD Audio play pcm1
Note! Device is in use (by PID 0/VMIX) but will try anyway
- Performing audio playback test... 
  <left> Device returned error: Input/output error
/dev/oss/oss_hdaudio0/pcm1 (audio engine 1): HD Audio play pcm2
- Performing audio playback test... 
  <left> Device returned error: Input/output error
/dev/oss/oss_hdaudio0/pcm2 (audio engine 2): HD Audio play pcm3
- Performing audio playback test... 
  <left> Device returned error: Input/output error
/dev/oss/oss_hdaudio0/pcm3 (audio engine 3): HD Audio play pcm4
- Performing audio playback test... 
  <left> Device returned error: Input/output error
/dev/oss/oss_hdaudio0/pcm4 (audio engine 4): HD Audio play pcm5
- Performing audio playback test... 
  <left> Device returned error: Input/output error
/dev/oss/oss_hdaudio0/pcm5 (audio engine 5): HD Audio play pcm6
- Performing audio playback test... 
  <left> Device returned error: Input/output error
/dev/oss/oss_hdaudio0/pcm6 (audio engine 6): HD Audio play pcm7
- Performing audio playback test... 
  <left> Device returned error: Input/output error
/dev/oss/oss_hdaudio0/pcm7 (audio engine 7): HD Audio play pcm8
- Performing audio playback test... 
  <left> Device returned error: Input/output error
/dev/oss/oss_hdaudio0/pcmin0 (audio engine 8): HD Audio rec select3
- Skipping input only device
/dev/oss/oss_hdaudio0/pcmin1 (audio engine 9): HD Audio rec select4
- Skipping input only device

*** Some errors were detected during the tests ***

```

---

### Post by igorzwx on 2009-07-21
osstest should not work with ALSA

HDA should be configured by hands in any case.

Whether you have ALSA or OSS4, the problem is the same.

If you have ALSA, then alsamixer.

Perhaps, you should consider a new installation.
Better 2 Ubuntus in dual boot.
One with ALSA, another with OSS4.

Do not mix them together.

---

### Post by martinbaselier on 2009-07-24
Your ke
rnel modules show you are using oss, not alsa. Also osstest does not work without oss installed. 

I have an hdaudio from the ICH6 family and it works fine with ossv4.

Have you checked these pages on oss wiki? 

[http://www.opensound.com/wiki/index.php/Troubleshooting](http://www.opensound.com/wiki/index.php/Troubleshooting)
[http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4](http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4)

[quote]
This suggest you have both an oss and an alsa kernel module.
That's bound to raise conflicts. 
[/qote]
I made a mistake there, because all alsa driver names start with snd, I assumeed this was an alsa driver. Apparently it's shown this way in lscpi -v.

Edit: I just noted that running osstest when there are other applications running, will make my sound stop working until I reboot.

---

