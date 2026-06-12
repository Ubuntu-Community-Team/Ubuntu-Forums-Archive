---
title: "NVidia HDMI audio device not listed"
date: 2013-01-07
forum: Multimedia Software
---

### Post by StuartPM on 2013-01-07
Hi all,

I'm trying to build an Ubuntu XBMC machine and I'm having problems with HDMI audio. I've installed a spanking new version of 12.04 and done a full update. I've also installed the current recommended NVidia drivers which seem to work fine. However I don't get audio over HDMI. In fact I get a constant static style hiss from the speakers. After a bit of research I found I should use aplay -l to determine my device. The problem is my device isn't listed!!! When I do aplay -l I only see one device which looks something like this:

**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0

I can find many many thread on how to solve HDMI audio problems but they mostly seem to start with the assumption that the HDMI device is recognised by alsa. I've read a few threads that suggest that the kernel may need updating with a patch, but those threads seem to be out of date and newer ones suggest that NVidia HDMI audio should just work with 12.04.

How would I go about determining why aplay doesn't list my card? What logs should I look at and what should I be searching for in them to find the problem? I've not had much experience in debugging issues like this so don't know where to start.

I'm using a PCI-E NVidia GForce 8600GT

Any help would be much appreciated,
Stu

---

### Post by BicyclerBoy on 2013-01-07
The older discrete cards do not have HDA HDMI audio.
The 8600GT is 8 yrs old..?

Real HDA HDMI audio started with IGP 8200 nforce chipset & ION/ION2 & on GT210/220 discrete cards. Altho' ION & GT210 are incomplete/odd.  

Pre-azalia HDMI S/PDIF audio is possible with some 8000/9000 cards but only if they have S/PDIF (input) header.
This is an input from mobo soundcard S/PDIF output.
"aplay" will never list this as an HDMI device.

I would suggest GT640 as a very good HTPC choice with lots of spare shader performance.
The older VDPAU devices (9400 ION etc) are only just okay c.f. later cards.

---

### Post by StuartPM on 2013-01-08
Ah! I'll save my efforts and stop trying to get it to work then!

Thanks for the advice. I'll go find a cheap compatible card.

Thanks,
Stu

---

### Post by BicyclerBoy on 2013-01-08
Not cheap...buy the card that does the job required.
Video decoding is only one part of the equation.
Video post-processing requires certain shader performance.
Gaming performance is diff again.

The GT640 looks to be the best option because it is:-
- kepler
- 4K? stereo decode vdpau (2K stereo for sure)
- power efficient
- excess shader performance for scaling, deinterlace, denoise etc.
- adequate gaming power

Don't reward nVidia for designing GT210.
Don't reward them for GT520..(only okay if **no** interlaced video & no scaling/sharpening).
The GT520/GT610 are just VDPAU decoders.

---

