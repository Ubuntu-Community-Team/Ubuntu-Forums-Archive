---
title: "[SOLVED] no sound on sony laptop with Ubuntu 7.10"
date: 2007-12-31
forum: Multimedia &amp; Video
---

### Post by mic_la on 2007-12-31
Hello,
I installed Ubuntu 7.10 on a sony vaio laptop. I am not getting any sound - neither from the system sounds nor while playing CDs.
I have tried in the last days to follow some existing troubleshooting instructions but no progress... I also look at some previous ubuntu sony laptop posts but no clue... If anyone has some pointers on how to  solve this issue, it would be much appreciated (see below for technical details)
cheers,
m
Here is some  technical information (based on what I read at [https://help.ubuntu.com/community/DebuggingSoundProblems):](https://help.ubuntu.com/community/DebuggingSoundProblems):)
PCM is at the maximum
alsamixer is also all at maximum
When going into the GUI volume control, I am given the choice to configure two devices:  HDA Intel (ALSA mixer) and Realtek ALC 262 (OSS mixer). According to Sony, the laptop has a Realtek sound card.
----------------------
uname-a
Linux michel-laptop 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 G
NU/Linux
---------------------------------------------
aplay --list-devices
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
---------------------------------------------------
lspci -vvnn (Audio part)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
        Subsystem: Sony Corporation Unknown device [104d:9015]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Step
ping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- 
<MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 23
        Region 0: Memory at fc500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
----------------------------------------------------------------
tail -2 /proc/asound/oss/sndstat 
Mixers:
0: Realtek ALC262

---

### Post by jualin on 2007-12-31
I think that the sound card driver is not installed correctly. Try going to Hardware information under Administration or Preferences to check if the driver is installed.

---

### Post by mic_la on 2008-01-01
thanks for your reply. I found the folllowing under Hardware information. Unfortunately, I was not sure how to check a driver is installed from there. Can you say from the following which device I should install if any? I might be able to google on it...
82801H (ICH8 family) HD Audio Controller
  ALC262 Analog ALSA Capture Device
  ALC262 Analog ALSA Capture Device (it shows twice but with different device_file)
  HDA Intel  ALSA Playback  Device
  ALC262 Analog OSS Control Device
  ALC262 Analog OSS PCM  Device
  ALC262 Analog OSS PCM Device    (yes, it shows twice also, one with /dev/dsp other with /dev/audio  for device)
  For the Playback device, I looked at the content of the linux.sysfs_path:
$>cat /sys/class/sound/pcmC0D0p/power/state
$>0
I am confused to mention of both OSS and ALSA but it might not be a problem.
cheers,
Michel

---

### Post by mic_la on 2008-01-01
This is now solved thanks to a post in this other thread [http://ubuntuforums.org/showthread.php?t=650790](http://ubuntuforums.org/showthread.php?t=650790)  :)
Thanks all
mic_la

---

