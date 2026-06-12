---
title: "connecting Video Cassette Recorder and CONVERT VHS VIDEO to DVD VIDEO/MP4... How can"
date: 2020-07-15
forum: Multimedia Software
---

### Post by lsepolis123 on 2020-07-15
I have this system: // rather old System // When had Windows 7 Pro, I ran Adobe Premiere Pro CS6 -- but now with Windows 10 Pro, Adobe Premiere Pro CS6... Do Not open probably due OLD Graphics card... I installed as VM: UBUNTU STUDIO 20.04 --- That I ask what programs work like Adobe Premiere Pro... ? This graphics card has adapters for connecting Video Cassette Recorder and CONVERT VHS VIDEO to DVD VIDEO/MP4... How can do this in Ubuntu Studio...?
Product:
HP Xw6600 Workstation / XEON E5405 / 26GB RAM DDR2
Operating System:
Microsoft Windows 10 (64-Bit) Pro  // WAS WIN 7 PRO // WAS WIN VISTA
NVIDIA GTX 260 Graphics Card

==================================================================
Adobe Premiere Pro CS6 
Compatible with NVIDIA graphics cards for GPU acceleration
GeForce GTX 285 (Windows and Mac OS)
GeForce GTX 470 (Windows)
GeForce GTX 570 (Windows)
GeForce GTX 580 (Windows)
...
...
and up

---

### Post by SeijiSensei on 2020-07-15
OK, first, most VHS players offered output via "composite video" over a single cable with an "RCA plug." Often you'll see a [three-plug cable]("https://www.amazon.com/Audio-Video-Cable-Gold-Plated/dp/B00BDYL93Y/"), one (yellow) for video, and two (red/white) for stereo audio.  Some players also offered "[S-Video]("https://www.amazon.com/feet-Gold-Plated-S-Video-Cable/dp/B0002MQGK4/")"  with a specialized plug, and "[component video]("https://www.amazon.com/BlueRigger-5-RCA-Component-Video-Audio/dp/B008UGEJ94/")," with a three-cable system that handles Red/Green/Blue outputs separately.  Presumably your system will need to accept input via whichever of these you are using.  There are some converters to USB.

Second, if you're running Studio in a VM, be aware that it does not have direct access to the system's hardware. The VM software provides an emulated system on which the guest can be installed.  It may not be possible to pipe the video input through to the VM.  If you're using a converter to USB, then you may or may not be able to see the device from the VM if you've set up the proper filters.  Here, for instance, is how it works on VirtualBox: [https://www.virtualbox.org/manual/ch03.html#usb-support](https://www.virtualbox.org/manual/ch03.html#usb-support)

---

### Post by TheFu on 2020-07-15
Don't expect any Adobe products to actually work under Ubuntu or any Linux.  They don't officially support any Linux.

But if all you want to do is to convert a VHS video into a DVD, then you don't need any of those proprietary tools.  Use any analog video capture device you like - most GPUs do NOT support that effort.  Don't confuse svideo OUTPUT with an svideo input. They are NOT the same. A GTX 260 does not support recording (input). It only supports outputs.

A $35 USB TV Tuner will usually have an analog input capability and can be seen as a V4L2 device with the correct driver. In Linux, any recording software that supports v4l2 can record from any supported devices.  [https://linuxtv.org/wiki/index.php/V4L_capturing](https://linuxtv.org/wiki/index.php/V4L_capturing) has some more background. Don't worry about all the "tuner" stuff, you'll just use the analog inputs for video and audio.  I have a few of these USB2 devices - a Haupauge 950Q and a Pinnacle thing.  They came with all sorts of drivers and software for Windows XP at the time. None of that is needed.  What's more important is to get a device that is plug-n-play with Linux, so start with the list of supported devices/chips on the V4L website, do some high-level local shopping for things in your price range from that list, then check that the chips inside are still the same and supported.  I know the 950Q and the 955 USB devices use different chips internally.

As for recording, you can use almost any program you like, just use the v4l device name and it will work; ffmpeg, obs, and a few others all will work.  For VHS, resolutions over 500 are useless, so generally, recording to mpeg2 video is fine. Higher just makes for a fuzzy image.  Then use any of the modern tools for editing, adding overlays, etc.  Kdenlive, openshot, opencut, there are probably 10 other choices. Most of those should be able to "record" input from a v4l2 device. Google found this list:
[https://itsfoss.com/best-video-editing-software-linux/](https://itsfoss.com/best-video-editing-software-linux/)

They aren't all Premiere or even try to be much like it, but most have very similar capabilities for non-experts used to Premiere.

I haven't a clue about UbuntuStudio - if it is like all the other Ubuntu-based distros, they simply preinstall and configure tools for audio and video creation needs by default.  Those tools are available on all Ubuntu flavors, though I suspect some of the audio stuff is difficult to get working, so Studio pre-installing it makes life easier.  For something like converting a VHS tape to a digital video file, I've used Ubuntu Server without any GUI many, many, times.

---

### Post by lsepolis123 on 2020-07-15
Thanks for replying

If supposed all OK with Hardware/VirtualBox-VM/UbuntuStudio/20.04

What software(s) I have to try in Ubuntu Studio 20.04, that do this job... ? In other words the Premiere Pro job - but in my case

---

### Post by lsepolis123 on 2020-07-15
[COLOR=#000000]Thanks for replying

[recording software] OBS for Windows 10 supported for my PC... ? can use it easy

 
[/COLOR]

---

### Post by TheFu on 2020-07-15
I use OBS on Linux.  Whether it is "easy" or not depends on your idea, knowledge, skill, and flexibility.  But without a recording device, you won't record anything.  As I said above, that GPU doesn't record anything.

---

### Post by lsepolis123 on 2020-07-15
> **TheFu said:**
> Don't expect any Adobe products to actually work under Ubuntu or any Linux.  They don't officially support any Linux.

But if all you want to do is to convert a VHS video into a DVD, then you don't need any of those proprietary tools.  Use any analog video capture device you like - most GPUs do NOT support that effort.  Don't confuse svideo OUTPUT with an svideo input. They are NOT the same. A GTX 260 does not support recording (input). It only supports outputs.

A $35 USB TV Tuner will usually have an analog input capability and can be seen as a V4L2 device with the correct driver. In Linux, any recording software that supports v4l2 can record from any supported devices.  [https://linuxtv.org/wiki/index.php/V4L_capturing](https://linuxtv.org/wiki/index.php/V4L_capturing) has some more background. Don't worry about all the "tuner" stuff, you'll just use the analog inputs for video and audio.  I have a few of these USB2 devices - a Haupauge 950Q and a Pinnacle thing.  They came with all sorts of drivers and software for Windows XP at the time. None of that is needed.  What's more important is to get a device that is plug-n-play with Linux, so start with the list of supported devices/chips on the V4L website, do some high-level local shopping for things in your price range from that list, then check that the chips inside are still the same and supported.  I know the 950Q and the 955 USB devices use different chips internally.

As for recording, you can use almost any program you like, just use the v4l device name and it will work; ffmpeg, obs, and a few others all will work.  For VHS, resolutions over 500 are useless, so generally, recording to mpeg2 video is fine. Higher just makes for a fuzzy image.  Then use any of the modern tools for editing, adding overlays, etc.  Kdenlive, openshot, opencut, there are probably 10 other choices. Most of those should be able to "record" input from a v4l2 device. Google found this list:
[https://itsfoss.com/best-video-editing-software-linux/](https://itsfoss.com/best-video-editing-software-linux/)

They aren't all Premiere or even try to be much like it, but most have very similar capabilities for non-experts used to Premiere.

I haven't a clue about UbuntuStudio - if it is like all the other Ubuntu-based distros, they simply preinstall and configure tools for audio and video creation needs by default.  Those tools are available on all Ubuntu flavors, though I suspect some of the audio stuff is difficult to get working, so Studio pre-installing it makes life easier.  For something like converting a VHS tape to a digital video file, I've used Ubuntu Server without any GUI many, many, times.

====
====

Can you provide links for USB 2 HARDWARE:
A $35 USB TV Tuner will usually have an analog input capability an... etc

in Amazon.co.uk...? or USA

Is this region specific...? My Region is Europe - Cyprus.

---

### Post by SeijiSensei on 2020-07-15
[https://www.amazon.com/s?k=usb+av+converter](https://www.amazon.com/s?k=usb+av+converter)

As I said, though, getting these to run in a VM by passing through the USB connection might be complicated.

---

### Post by lsepolis123 on 2020-07-15
what if dual boot - Win 10 Pro + Ubuntu Studio OS 20.04 
rather run in VM... 

May this work better?

---

### Post by TheFu on 2020-07-15
Dude. It might work, but it might not.  BTW, there's no mention in this thread of using a VM.

I use VMs for all sorts of stuff .... my main desktop runs inside a VM for flexibility and convenience, but I don't do video capture nor video editing inside a VM.  I tried. It didn't work well and there were all sorts of issues.  Before you ask - no, I don't remember all of them.

Similarly, I'm not in the market for the HW you need, so I'm not going to do your shopping research either.  I've owned many video capture devices over the decades.  Used one for about 4 hrs today, but it only accepts HDMI input and doesn't need any computer to work. That isn't what you need.  The files it creates are less than ideal, so they need some processing.  I need to go and do that now.

But you should try everything yourself. Perhaps you are smarter than us and can get it working flawlessly. That would be great!  When you do, please post a how-to guide.

---

### Post by KJKJKJ on 2020-07-15
Inexpensive consumer grade hardware might not be able to sync up to a VHS signal as well as it does to a TV signal. Be careful.

---

### Post by SeijiSensei on 2020-07-16
> **TheFu said:**
> Dude. It might work, but it might not.  BTW, there's no mention in this thread of using a VM.
From the original post:  I installed as VM: UBUNTU STUDIO 20.04

---

### Post by lsepolis123 on 2020-07-29
[h=1]Golden Videos VHS to DVD Converter[/h][h=2]Convert VHS tapes to your PC, DVD, AVI or MPEG files[/h][URL="https://www.nchsoftware.com/goldenvideos/index.html"]
https://www.nchsoftware.com/goldenvideos/index.html[/URL]

====

---

### Post by shantiq on 2020-07-29
==

---

