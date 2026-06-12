---
title: "Dual Monitors Not Working- Radeon R7 graphics"
date: 2016-06-12
forum: Multimedia Software
---

### Post by titan53 on 2016-06-12
Hello!

I am a brand new Linux user and recently built a desktop with an AMD a10 7870, dual booted with windows 10 and ubuntu 16.04 64 bit. Only one of my monitors shows any video, even though ubuntu detects and recognizes both in the system settings. The monitor that isn't working is old, a Samsung SyncMaster 175v, connected with a VGA. I haven't downloaded any drivers, just am using whatever was downloaded when I installed Ubuntu. Hoping to figure out whats wrong. Thanks!

---

### Post by gordintoronto on 2016-06-13
It might be helpful to install an "additional driver" for the video. I use Synaptic Package Manager, which makes it very easy to install additional drivers.

Also, AMD has made significant changes in its Linux support, very recently.

---

### Post by QIII on 2016-06-13
Canonical removed fglrx from their repo because it will not work with X Server in 16.04.

When you install Ubuntu, either of these two open source drivers are installed depending on hardware:  Radeon or AMDGPU.  I suspect that with your APU Radeon was installed.

Do not try to install fglrx from AMD's website.  It will not work with 16.04.

---

### Post by titan53 on 2016-06-13
In synaptic it appears as I have xserver-xorg-video-amdgpu, xserver-xorg-video-ati, and xserver-xorg-video-radeon installed. They all are up to date. Do you have any idea what driver I would need, would it be AMD specific or related to the monitor brand? Thanks!

---

### Post by titan53 on 2016-06-13
Additionally, in Software and Updates under additional drivers, it says 
Unknown: Unknown 
This device is not working.

Currently the radio button is selected as do not use this device, but there is another option: "Using processor microcode firmware for AMD CPUs from amd64-mircocode (proprietary)

Should I try checking this?

---

### Post by QIII on 2016-06-13
If you would post back the results of 

```
lsmod | grep amdgpu
```

we can see if you are using AMDGPU or Radeon.  If there are not sever lines containing "amdgpu", you are using the Radeon driver.

One of those will be the driver in use.

---

### Post by titan53 on 2016-06-13
Got it to work somehow :) I switched the resolution of the samsung monitor and found it worked on lower resolutions, and after restarting my computer I was able to select 1280x1024 and it is working perfectly now.

---

### Post by yoshii on 2016-06-15
Be aware that due to the v16 graphics issues with AMD/ATI/Radeon your AMD monitor probably won't have hardware acceleration for games.  But playing back videos should be just fine.

---

### Post by huguesyanis-amanieu on 2016-11-13
I have the same problem than above


[LIST]
[*]Output from 'lsmod | grep amdgpu' 
[/LIST]
 ```
amdgpu               1949696  4
i2c_algo_bit           16384  1 amdgpu
ttm                    94208  1 amdgpu
drm_kms_helper        155648  1 amdgpu
drm                   364544  7 ttm,drm_kms_helper,amdgpu
```
so I am using AMDGPU.

[LIST]
[*]lspci -nn | grep VGA:
```
Output from VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Tonga PRO [Radeon R9 285/380] [1002:6939] (rev f1)

``` 
[*]Output from xrandr --listmonitors
```

Monitors: 2
 0: +*HDMI-A-0 1920/521x1080/293+0+0  HDMI-A-0
 1: +DVI-D-1 800/477x600/268+1920+480  DVI-D-1


``` 
[*]My xenial packages are updated. 
[*]I have tried to reduce screen resolution and restart, but it didn't fix the problem. You can see it under xrandr: I used even the minimum 800*600 resolution. 
[/LIST]

One important thing: when I start the computer, the GRUB menu appears on both monitor. Then ubuntu starts and my main monitor (HDMI) works as usual but my second monitor (DVI VGA) prompts "VGA NO SIGNAL" then goes to rest.

Under monitor parameters, both monitors appear. Even the names are detected. If I move my mouse to the right border, it disappears into the black monitor.

My conclusions: the computer detects the second monitor and thinks it is working and certainly sends image information. But for some reason the VGA monitor doesn't detects it. I don't think it is a problem from the monitor as before 16.4 both monitor would work. I rarely need dual monitor at home, this is why this issue comes up only now.
It seems the monitor is expecting some signal from the GPU that it isn't receiving.

Any thoughts on how to fix this issue?

Thank you.

---

