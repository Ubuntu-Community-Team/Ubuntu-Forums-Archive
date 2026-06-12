---
title: "Audiophile 2496 soundcard problem"
date: 2011-01-05
forum: Multimedia Software
---

### Post by orsalmon on 2011-01-05
Hi,
I just installed Ubuntu for the first time in my life. I had never used Linux before and I don't know how to configure my hardware well.
 
My soundcard is M-Audio Audiophile 2496.
I tried to use the Envy24mixer but I still dont hear anything.
I'll be happy if someone will help me and tell me what to do step by step. I really dont know how linux works yet.
 
Thank you

---

### Post by snapback77 on 2011-01-05
click System click Preferences click sound click Hardware to see if your soundcard is listed there.  Click Output click your soundcard.  That should get you going. I am using Music Streamer II. Love the sound of Ubuntu.  GNOME Mplayer is my choice at this time.  Enjoy.

---

### Post by orsalmon on 2011-01-06
I did it, and it's still not working...
:\

---

### Post by b0b138 on 2011-01-06
Create this file; /etc/udev/rules.d/your_ice1712.rules
```
 gksudo gedit /etc/udev/rules.d/your_ice1712.rules
```
and paste into it
```
SUBSYSTEM!="sound", GOTO="ice1712_end"
 ACTION!="change", GOTO="ice1712_end"
 KERNEL!="card*", GOTO="ice1712_end"

SUBSYSTEMS=="pci", ATTRS{vendor}=="0x1412", ATTRS{device}=="0x1712", ATTRS{subsystem_vendor}=="0x1412", ATTRS{subsystem_device}=="0xd634", ENV{PULSE_PROFILE_SET}="via-ice1712.conf"

 LABEL="ice1712_end"
```

Then edit another file
```
gksudo gedit /usr/share/pulseaudio/alsa-mixer/profile-sets/via-ice1712.conf
```
and replace its contents with

# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as
# published by the Free Software Foundation; either version 2.1 of the
# License, or (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software Foundation,
# Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA.

; Via ICE1712 multi-channel audio chipset
;
; This chipset has up to four stereo pairs of input and four stereo pairs of
; output, named channels 1 to 8. Also available are separate S/PDIF stereo
; channels (input and output), and a separate "system-out" stereo jack that
; supports 6-channel hardware mixing.
;
; The S/PDIF stereo channels can be controlled via the mixer for hw:0, and
; additionally, the 8 main outputs can be loop-routed to a separate stereo
; input pair, available as channels 11 and 12.
;
; Many cards available from vendors do not expose all channels from this chip
; to an external port, which effectively reduces the number of channels that
; are useful to the user. However, the ALSA driver still exposes all channels
; even if they are not connected.
;
; We knowingly only define a subset of the theoretically possible
; mapping combinations as profiles here.
;
; See default.conf for an explanation on the directives used here.

[General]
auto-profiles = no

[Mapping analog-mch-in]
description = Analog Multi-Channel Main Input
device-strings = hw:%f,0
#channel-map = front-left,front-right,rear-left,rear-right,front-center,lfe,side-left,side-right,aux0,aux1,aux2,aux3
channel-map = aux0,aux1,front-left,front-right,aux2,aux3,aux4,aux5,aux6,aux7,aux8,aux9
direction = input

[Mapping analog-mch-out]
description = Analog Multi-Channel Main Output
device-strings = hw:%f,0
#channel-map = front-left,front-right,rear-left,rear-right,front-center,lfe,side-left,side-right,aux0,aux1
channel-map = front-left,front-right,aux0,aux1,aux2,aux3,aux4,aux5,aux6,aux7
direction = output

[Mapping digital-stereo]
description = Digital Stereo Input/Output
#device-strings = hw:%f,1
device-strings = iec958:%f
channel-map = left,right
direction = any

[Mapping analog-system-out]
description = Analog Stereo System-Out
device-strings = hw:%f,2
channel-map = left,right
direction = output


[Profile output:mch]
description = Multi-Channel Output Active (Digital Disabled)
output-mappings = analog-mch-out analog-system-out
input-mappings =
priority = 90
skip-probe = yes

[Profile output:mch+input:mch]
description = Multi-Channel Input/Output (Digital Disabled)
output-mappings = analog-mch-out analog-system-out
input-mappings = analog-mch-in
priority = 100
skip-probe = yes

[Profile output:spdif]
description = Digital Output (Multi-Channel Disabled)
output-mappings = digital-stereo analog-system-out
input-mappings =
priority = 80
skip-probe = yes

[Profile output:spdif+input:spdif]
description = Digital Input/Output (Multi-Channel Disabled)
output-mappings = digital-stereo analog-system-out
input-mappings = digital-stereo
priority = 90
skip-probe = yes

[Profile output:system]
description = System Output Only
output-mappings = analog-system-out
input-mappings =
priority = 60
skip-probe = yes


This was taken from here [http://dev.modmancer.com/index.php/2010/05/15/m-audio-audiophile-2496-on-ubuntu-9-10-no-sound/](http://dev.modmancer.com/index.php/2010/05/15/m-audio-audiophile-2496-on-ubuntu-9-10-no-sound/)
and worked for me

---

### Post by orsalmon on 2011-01-09
First of all - thank you very much!

:( it didn't work to me. I did every step.

When I open the Envy24mixer I see no pulse there. Its look like the mixer dont getting sound.

What to do?
:(

---

### Post by cchhrriiss121212 on 2011-01-09
In envy24control you must also raise the volume as it is muted by default. Go to the analogue volume tab and adjust the sliders, ADC is input  and DAC is output.

---

### Post by b0b138 on 2011-01-10
Ah yes, as cchhrriiss121212 said. Play with all the sliders. Remember this card is somewhat complicated, as its for multitrack recording. Basicly, stereo output is going to use 2 channels. 1 channel left and the other right. Plus, you'll want to mute one side of each channel accordingly so the left is only left and right is right.

---

