---
title: "Can I use xorg.conf to &quot;force&quot; HDMI output?"
date: 2009-04-22
forum: Multimedia Software
---

### Post by dannybullit on 2009-04-22
Hi,
 
I have a a Gigabyte GA-73PVM-S2H motherboard. It is has GeForce 7100 / nForce 630i Chipset with HDMI + VGA + DVI output.
 
Ubuntu 8.10 (Intrepid) is installed on a 4BG usb flash drive. It is installed using this [GUIDE]("http://xbmc.org/wiki/?title=HOW-TO:_Install_XBMC_for_Linux_on_Ubuntu_8.10_(Intrepid)_step-by-step")
 
I use this [xorg.conf]("http://217.20.138.65/xbmc/xorg.conf")
 
Nvidia Driver: NVIDIA-Linux-x86-185.19-pkg1.run
 
**Problem**:
 
Can I force X to intialize on the HDMI output, meaning that I want the picture so be sent out using only HDMI.
 
I have a problem with getting picture with HDMI. The only way to get this is to boot the computer with VGA cable, then when the XBMC logo appears - I unplug VGA and plug in HDMI.
 
There has to be a way to get picture over HDMI without swithing cables?
 
It works without switching cables using Windows Vista.
 
Br, Daniel

---

### Post by dannybullit on 2009-04-22
This is my /var/log/Xorg.0.log
[http://www.pastebin.ca/1400166](http://www.pastebin.ca/1400166)
 
I dont know mucg about X but the last part of the log seems interesting:
EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:0:16:0.
(EE) NVIDIA(0):     Please check your system's kernel log for additional error
(EE) NVIDIA(0):     messages and refer to Chapter 8: Common Problems in the
(EE) NVIDIA(0):     README for additional information.
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.
 
Fatal server error:
no screens found
[EMAIL="xbmc@xbmc:~$"]xbmc@xbmc:~$[/EMAIL]
 
 
Can it be problems with EDID detection?
Can EDID be set manually?
 
Br, Daniel

---

### Post by dannybullit on 2009-04-22
> **dannybullit said:**
> This is my /var/log/Xorg.0.log
[http://www.pastebin.ca/1400166](http://www.pastebin.ca/1400166)
 
I dont know mucg about X but the last part of the log seems interesting:
EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:0:16:0.
(EE) NVIDIA(0): Please check your system's kernel log for additional error
(EE) NVIDIA(0): messages and refer to Chapter 8: Common Problems in the
(EE) NVIDIA(0): README for additional information.
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.
 
Fatal server error:
no screens found
xbmc@xbmc:~$
 
 
Can it be problems with EDID detection?
Can EDID be set manually?
 
Br, Daniel
 
 
ok, so this is my log file when I´ve managed to get picture over HDMI, using the VGA to HDMI switch trick (as desribed in my first posting of this thread)
[http://www.pastebin.ca/1400185](http://www.pastebin.ca/1400185)
 
what could be wrong, please help!

---

### Post by kornguy26 on 2009-04-22
quick guestion in the log it says it failed to init the nvidia graphics device does your hardware drivers under the administration showv anything about nvidia and if so is it checked and in use check this

---

### Post by dannybullit on 2009-04-23
> **kornguy26 said:**
> quick guestion in the log it says it failed to init the nvidia graphics device does your hardware drivers under the administration showv anything about nvidia and if so is it checked and in use check this
 
what do you mean with hw drivers under administration?
 
Br, Daniel

---

