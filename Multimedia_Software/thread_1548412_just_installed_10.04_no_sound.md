---
title: "just installed 10.04 no sound"
date: 2010-08-08
forum: Multimedia Software
---

### Post by kmrs75 on 2010-08-08
i have been looking and trying different things for about 2 days now and i cant get anything to work. 

here is what i have 

Dell studio xps 435mt but i am only running 32 bit ubuntu right now 

tina@tina-desktop:~$ sudo cat /proc/asound/card0/codec#* | grep Codec
Codec: ATI R6xx HDMI




tina@tina-desktop:~$ sudo lshw -class sound
  *-multimedia            
       description: Audio device
       product: HD48x0 audio
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:04:00.1
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: driver=HDA Intel latency=0tina@tina-desktop:~$ sudo lshw -class sound
  *-multimedia            
       description: Audio device
       product: HD48x0 audio
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:04:00.1
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:31 memory:fbefc000-fbefffff
  *-multimedia UNCLAIMED
       description: Audio device
       product: 82801JI (ICH10 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:fbcf8000-fbcfbfff

       resources: irq:31 memory:fbefc000-fbefffff
  *-multimedia UNCLAIMED
       description: Audio device
       product: 82801JI (ICH10 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 00tina@tina-desktop:~$ sudo lshw -class sound
  *-multimedia            
       description: Audio device
       product: HD48x0 audio
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:04:00.1
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:31 memory:fbefc000-fbefffff
  *-multimedia UNCLAIMED
       description: Audio device
       product: 82801JI (ICH10 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:fbcf8000-fbcfbfff

       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:fbcf8000-fbcfbfff

---

### Post by simosx on 2010-08-08
Obtain the full soundcard details with

[FONT="Courier New"]wget [www.alsa-project.org/alsa-info.sh](www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh
[/FONT]

When prompted, say Yes to send the data to alsa-project.org (Alsa website) and post here the URL you will be given. In this way we can see what hardware you have and if there are any problems.

---

### Post by kmrs75 on 2010-08-08
This is the message that I got when I did that.

tina@tina-desktop:~$ wget [www.alsa-project.org/also-info.sh](www.alsa-project.org/also-info.sh) -O alsa-info.sh && bash alsa-info.sh
--2010-08-08 11:23:36--  [http://www.alsa-project.org/also-info.sh](http://www.alsa-project.org/also-info.sh)
Resolving [www.alsa-project.org](www.alsa-project.org)... 212.20.107.51
Connecting to [www.alsa-project.org|212.20.107.51|:80](www.alsa-project.org|212.20.107.51|:80)... connected.
HTTP request sent, awaiting response... 404 Not Found
2010-08-08 11:23:36 ERROR 404: Not Found.

---

### Post by Yellow Pasque on 2010-08-08
You can get the alsa-info script here: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

Since the driver isn't even loading, it may be helpful to look for relevant info in dmesg as well.

---

### Post by kmrs75 on 2010-08-08
Thanks for the help.  I will try that and see what happens.  Will keep you posted!

---

### Post by simosx on 2010-08-09
> **kmrs75 said:**
> This is the message that I got when I did that.

tina@tina-desktop:~$ wget [www.alsa-project.org/also-info.sh](www.alsa-project.org/also-info.sh) -O alsa-info.sh && bash alsa-info.sh
--2010-08-08 11:23:36--  [http://www.alsa-project.org/also-info.sh](http://www.alsa-project.org/also-info.sh)
Resolving [www.alsa-project.org](www.alsa-project.org)... 212.20.107.51
Connecting to [www.alsa-project.org|212.20.107.51|:80](www.alsa-project.org|212.20.107.51|:80)... connected.
HTTP request sent, awaiting response... 404 Not Found
2010-08-08 11:23:36 ERROR 404: Not Found.

You wrote by accident 'also-info.sh' in 'www.alsa-project.org/also-info.sh'. It should be 'alsa-info.sh'. 
Typically you can copy-paste the original command and paste them on your terminal.

---

