---
title: "no sound over hdmi"
date: 2019-02-15
forum: Multimedia Software
---

### Post by buill on 2019-02-15
hi im building a media server but one BIG stumbling bloc is i cat get sound over hdmi have been googleing and tried alot of different solutions but still no sound on my tv. i have picture on both latitude e630 and my tv but only pictur on the tv alsa mixer doesnot show hdmi output and 
aplay -l outputs
```

**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: 92HD93BXX Analog [92HD93BXX Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```
if anyone had any idea it would be great my kid needs cartoons thanks

---

### Post by Autodave on 2019-02-15
We need some info on your machine first.  And do you know what video card is in it?  Did you install and driver for the video card?  If so, what one and where did you get it from?

What version of Buntu are you running?

---

### Post by buill on 2019-02-15
thanks for reply
> @ubuntu:~$  glxinfo | grep OpenGL
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Ivybridge Mobile 
OpenGL core profile version string: 4.2 (Core Profile) Mesa 18.2.2
OpenGL core profile shading language version string: 4.20
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 3.0 Mesa 18.2.2
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.0 Mesa 18.2.2
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.00
OpenGL ES profile extensions:

---

### Post by Autodave on 2019-02-15
We still need you to answer what I asked before please.  Need make and model of machine, graphics card (if it has one besides what is not on the mother board), and graphics driver you installed.

---

### Post by SeijiSensei on 2019-02-15
Use "lspci" to identify the graphics card. Like most modern laptops, my machine has two adapters. 

```
$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Whistler [Radeon HD 6730M/6770M/7690M XT]

```

Finding the driver can be a bit tricky.  Use "lsmod | grep vid" like this
```

$ lsmod | grep vid
uvcvideo              102400  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_common       45056  2 videobuf2_v4l2,uvcvideo
videodev              188416  3 videobuf2_v4l2,uvcvideo,videobuf2_common
media                  36864  2 videodev,uvcvideo
video                  45056  1 i915

```
These are "kernel modules" that are running as part of the operating system.  That's how drivers are represented in Linux.  Listing the modules with "lsmod" shows that the "video" module at the bottom uses the i915 driver.  That's the standard driver for the Intel adapter listed above.

---

### Post by ssreddy555 on 2019-02-16
Set sound output to digital.

---

### Post by buill on 2019-02-16
thanks for replys im using a dell latitude e6430

```
@ubuntu:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108GLM [NVS 5200M] (rev a1)

```
and
```

@ubuntu:~$ lsmod | grep vid
video                  45056  4 dell_wmi,dell_laptop,i915,nouveau

```

---

### Post by buill on 2019-02-16
Set sound output to digital.? 
how? there is no option in pulse audio control

---

### Post by Autodave on 2019-02-16
Check the Nvidia panel in Settings. Also, in Alsa Mixer -> Output Devices: look for HDMI or Nvidia.

---

### Post by ssreddy555 on 2019-02-17
Go to settings & set digital output.

---

### Post by tea for one on 2019-02-17
> **buill said:**
> Set sound output to digital.? 
how? there is no option in pulse audio control

PulseAudio > Configuration

Also notice the drop-down arrow at the end of the Profile line.

---

### Post by buill on 2019-02-19
yeah i dont have that option all i have is
1.analouge sterio ouput
2.aanaloug sterio duplex
3.analouge sterio input
4.off

the hdmi doesint show up at all but i do have image on tv so? any ideas would be great thanks

---

### Post by vidtek on 2019-02-19
> **buill said:**
> yeah i dont have that option all i have is
1.analouge sterio ouput
2.aanaloug sterio duplex
3.analouge sterio input
4.off

the hdmi doesint show up at all but i do have image on tv so? any ideas would be great thanks

You are getting no HDMI sound digital signals to your tv.  Start with hardware first then move on to your software.  Once you have digital sound signals appearing at your monitor then you can get into checking asla, drivers, pci  stuff  etc.

What kind of cable are you using?  Some cheapo far East cables will give erratic results.  Swap your cables around even swapping ends can make a difference.

Try another monitor/tv, if you don't have one, borrow one (and some cables too) from someone else for a test.

Start with basics then move forward in logical steps.

Once you have signals then start with the software approach always logic first when troubleshooting, step by step.

Tony.

---

### Post by tea for one on 2019-02-19
Another suggestion:-

Turn off laptop and TV (i.e. no **power** to either device).
Connect HDMI cable to both devices.
Power on TV and select the appropriate HDMI input.
Power on laptop and you should see the image on your laptop and TV (probably no sound yet because your laptop is using the default output).
Open PulseAudio and navigate to the **Configuration** tab.

Do you have any HDMI choices?

I just double checked by connecting my netbook to my TV and successfully played an MP3 audio file through the TV speakers.

Both my devices fall into the "cheap n' cheerful" price bracket - a 11.6" HP Stream and a Linsar DVB-T2 Terrestrial TV (no cable or satellite).

Good luck

---

### Post by koshamo on 2019-02-20
As vidtek suggested I would try some different cables and another monitor or tele if you've got one handy. In my experience the solution has 80% of the time been something of that nature.

---

### Post by Yellow Pasque on 2019-02-21
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

