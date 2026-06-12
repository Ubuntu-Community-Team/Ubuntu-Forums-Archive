---
title: "Audio Devices Disappear, Reboot fixes a for while"
date: 2014-03-02
forum: Multimedia Software
---

### Post by TheFu on 2014-03-02
I'm seeing this in the last week or so.  In the prior 18 months, never had this issue on the SAME hardware with 12.04. Current kernel is 3.11.0-17-generic. Radeon HD 6310 onboard.

```
$ aplay -l
aplay: device_list:252: no soundcards found...
```
But only after a little time when the monitor (actually a projector) is off.  A reboot brings the audio devices back, provided the HDMI connection is active, but not if the projector is off.  I'm using analog audio out. After a reboot, the audio devices are back!
```
~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC887-VD Digital [ALC887-VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
Then it will disappear after a period of inactivity. A reboot with the HDMI active gets the devices back, but not without the monitor powered. It has an ATI video chip and fglrx is loaded. Related?

Compared the lsmod output between working/non-working times. All the video/audio drivers are loaded. Only diff seen is the order of the pcm and seq in the snd_timer:
```
snd_timer              29989  2 snd_pcm,snd_seq
```

I'm stumped.

---

### Post by tgalati4 on 2014-03-02
HDMI is digital sound and often it will shut down the analog sound channel when in use (part of HDCP I believe).  So when your projector times out or the order of powering up the devices--remember HDCP devices must perform a handshake to work causes the HDMI connection to go dark, you lose that connection.  Yours in an edge use case.  It's possible that the newer video driver or power management in 3.11 kernel is causing this.

Try disconnecting the HDMI cable.  If it is not being used, then try isolating that part of the problem.  The HDMI must be disconnected from the PC side, because the port has a cable-detect circuitry that is used as part of HDCP.  Since you are using a proprietary driver, you can try filing a bug with ATI/AMD, but good luck getting any response.  Make sure your fglrx is up to date.

The curse of HDCP:  [http://en.wikipedia.org/wiki/High-bandwidth_Digital_Content_Protection#Problems](http://en.wikipedia.org/wiki/High-bandwidth_Digital_Content_Protection#Problems)

---

### Post by TheFu on 2014-03-02
Thanks for the ideas!
I'll try the unplug/replug step. Not really a solution, but for troubleshooting ... 

Other things attempted:
* increased the screensaver timeout for XBMC to 60 minutes, hoping that will help by avoiding the issue.
* removed a 4x1 HDMI switch and an HDMI-audio to optical out device to troubleshoot. Didn't help. The receiver involved doesn't do HDMI (it is THX however).
* always force an ATI driver re-install after a new kernel is installed, but only use the driver from Canonical's repo.

The real problem is that we like to listen to audio all day controlled by an Android app (XBMC or DLNA) through the stereo, but without the projector on.
Don't see why HDCP would be involved at all - if true it is the overly-greedy media companies - none of the media has any DRM, plus over the last 18 months, this has never been an issue.  Could switch to VGA for video, but those cables are larger and would mean nasty redrilling inside the walls and ceiling to get a cable through plus the length is an issue for signals.

---

### Post by tgalati4 on 2014-03-02
It's also possible that a kernel update has caused a regression with the ATI driver.  How many kernel upgrades have you gone through in the last 18 months?  Is there a newer driver from AMD's website that you could try?  Or try the open ATI driver and see if that fixes the sound problem.  

HDCP is a hardware DRM solution that can cause these types of issues, regardless of what content you are putting through the HDMI.  Using quality RGB cables, you can run through VGA and avoid this problem.  I find little difference between a quality RGB signal and HDMI for short runs (less than 40').  But if this setup was working and now it is not, then a regression has occured.  But exactly where to point the finger.  You can't really file a bug until you narrow down the issue, otherwise it will get kicked around the bug tracker.  

If you had a dedicated RaspberryPi with a Wolfson codec sound board driving your stereo, then this would not be an issue.  I was impressed at a demo showing a RaspberryPi running XBMC running 1080i 3D video at SCaLE12x.  So that little board can handle high definition quite well.

---

### Post by TheFu on 2014-03-05
> **tgalati4 said:**
> It's also possible that a kernel update has caused a regression with the ATI driver.  How many kernel upgrades have you gone through in the last 18 months?  Is there a newer driver from AMD's website that you could try?  Or try the open ATI driver and see if that fixes the sound problem.  

HDCP is a hardware DRM solution that can cause these types of issues, regardless of what content you are putting through the HDMI.  Using quality RGB cables, you can run through VGA and avoid this problem.  I find little difference between a quality RGB signal and HDMI for short runs (less than 40').  But if this setup was working and now it is not, then a regression has occured.  But exactly where to point the finger.  You can't really file a bug until you narrow down the issue, otherwise it will get kicked around the bug tracker.  

If you had a dedicated RaspberryPi with a Wolfson codec sound board driving your stereo, then this would not be an issue.  I was impressed at a demo showing a RaspberryPi running XBMC running 1080i 3D video at SCaLE12x.  So that little board can handle high definition quite well.

The XBMC box gets limited patching due to the fragile nature of the video/audio drivers.  Perhaps once every 2 -3 months. 
However, about 2 months ago, I was forced with a fresh reinstall due to a new 4TB HDD being swapped into the box.  MBR-->GPT thing.

The rPi is impressive for extremely specific content. It sucks for 95% of my stuff. If everything was h.264/aac - fine. That just isn't the case here.  It does make for an impressive demo - BTW, I have a chromecast with the same issue.

Tried the physical pull HDMI cable, reinsert today. Didn't help with the audio at all. Good thought.

Forced booting an old kernel this morning. .15 - same issue. Can't easily go back any farther. I cleanup old kernels and my other 12.04.4 systems are running the 3.2.x line still.  Both the audio devices disappear AND xbmc crashes when the project is turned off.

---

