---
title: "Audio over HDMI help. Intel HDA ALC887"
date: 2010-01-31
forum: Multimedia Software
---

### Post by johnnytoxic on 2010-01-31
Hi,

I'm having trouble getting audio working over HDMI.

My motherboard is a G41M-ES2H with an Intel X4500 card.

I've checked in alsamixer and unmuted the IEC958 devices. I've also updated to the latest alsa drivers using the script that was posted on here.

Should I be able to use audio over hdmi with this setup?


card 0: Intel [HDA Intel], device 0: ALC887 Analog [ALC887 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC887 Digital [ALC887 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


default:CARD=Intel
    HDA Intel, ALC887 Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC887 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=Intel,DEV=0
    HDA Intel, INTEL HDMI 0
    HDMI Audio Output

---

### Post by Joe on 2010-04-30
Did you get this issue resolved?  I'm having the same problem on Lucid.  I can get sound over analog but not through HDMI.  I'm not sure this is the cause but my motherboard (Gigabyte GA-H55M-S2H) documentation states that it uses Realtek ALC888B but Kubuntu detects it as ALC887.

---

### Post by themacmeister on 2010-05-06
actually... ALC888B = ALC887 -> talk to Intel and Realtek and you might be able to figure that one out :-)

As for the Digital, I have the same motherboard as the first poster, with HDMI out. I have Intel GMA-X4500 disabled in BIOS and use NVIDIA card.

Could this be an issue with HDMI out (? does it need video too)?

---

### Post by Joe on 2010-05-06
Video was working ok but audio wasn't over HDMI.  I actually figured out the problem, well I didn't figure it out as much as got it resolved by recompiling and reconfiguring alsa.

---

### Post by sanderm on 2010-05-12
> **Joe said:**
> Video was working ok but audio wasn't over HDMI.  I actually figured out the problem, well I didn't figure it out as much as got it resolved by recompiling and reconfiguring alsa.

Which version of alsa are you using?
Wondring if the sound will work with Ubuntu 10.04.

---

### Post by Joe on 2010-05-12
> **sanderm said:**
> Which version of alsa are you using?
Wondring if the sound will work with Ubuntu 10.04.

I'm using the version that comes with 10.04 (1.0.22.1).  You just have to reconfigure the settings.  I followed the directions under Alsa Driver Compilation here:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

