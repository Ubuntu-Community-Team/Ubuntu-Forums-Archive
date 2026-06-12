---
title: "HDMI 7.1/5.1 channel reorder"
date: 2013-01-22
forum: Mythbuntu
---

### Post by PhonicLynx on 2013-01-22
Hello everyone... Hoping someone can help me here... I've been searching for ages and not come up with anything useful. 

Have a nVidia GPU that serves out HDMI to a AV Receiver that can support 7.1 and the full list of codecs. All the respective cards work as intended in stereo but when you put them in 5.1 or 7.1 the sound is outputted.. but to the wrong channels. 

If I put it on 7.1 channels the front speakers are assigned correctly, but the rear left is connected to the center speaker, rear right is the LFE and the middle right and left are a mixture of the two front speakers.

Is there any way to tel the ALSA drivers (or what ever it uses) to reorder the speaker configuration?

I found this too: [http://http.download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html#](http://http.download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html#)

---

### Post by muktupavels on 2013-01-22
I had same problem. Do you have file /usr/share/pulseaudio/alsa-mixer/profile-sets/extra-hdmi.conf?

You need change  'channel-map' line.  For 5.1 i changed lines from 'channel-map = front-left,front-right,rear-left,rear-right,front-center,lfe' to 'channel-map = front-left,front-right,front-center,lfe,rear-left,rear-right' and now sound is outputted to correct channels.

My extra-hdmi.conf file content:```
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

; This is a profile for Nvidia and Intel cards - some cards have four HDMI codecs,
; and which ones are working seems to vary a lot between GPU boards. In addition,
; Nvidia and Intel make southbridges as well, so we need to keep the existing
; analog profiles.
; (And by not adding all these extra profiles to default.conf, we make sure
; there is no performance hit for non-Nvidia/Intel cards.)

[General]
auto-profiles = yes

[Mapping analog-mono]
device-strings = hw:%f
channel-map = mono
paths-output = analog-output analog-output-speaker analog-output-desktop-speaker analog-output-headphones analog-output-headphones-2 analog-output-mono
paths-input = analog-input-front-mic analog-input-rear-mic analog-input-internal-mic analog-input-dock-mic analog-input analog-input-mic analog-input-linein analog-input-aux analog-input-video analog-input-tvtuner analog-input-fm analog-input-mic-line
priority = 1

[Mapping analog-stereo]
device-strings = front:%f hw:%f
channel-map = left,right
paths-output = analog-output analog-output-speaker analog-output-desktop-speaker analog-output-headphones analog-output-headphones-2 analog-output-mono
paths-input = analog-input-front-mic analog-input-rear-mic analog-input-internal-mic analog-input-dock-mic analog-input analog-input-mic analog-input-linein analog-input-aux analog-input-video analog-input-tvtuner analog-input-fm analog-input-mic-line
priority = 10

[Mapping analog-surround-40]
device-strings = surround40:%f
channel-map = front-left,front-right,rear-left,rear-right
paths-output = analog-output analog-output-speaker analog-output-desktop-speaker
priority = 7
direction = output

[Mapping analog-surround-41]
device-strings = surround41:%f
channel-map = front-left,front-right,rear-left,rear-right,lfe
paths-output = analog-output analog-output-speaker analog-output-desktop-speaker
priority = 8
direction = output

[Mapping analog-surround-50]
device-strings = surround50:%f
channel-map = front-left,front-right,rear-left,rear-right,front-center
paths-output = analog-output analog-output-speaker analog-output-desktop-speaker
priority = 7
direction = output

[Mapping analog-surround-51]
device-strings = surround51:%f
channel-map = front-left,front-right,rear-left,rear-right,front-center,lfe
paths-output = analog-output analog-output-speaker analog-output-desktop-speaker
priority = 8
direction = output

[Mapping analog-surround-71]
device-strings = surround71:%f
channel-map = front-left,front-right,rear-left,rear-right,front-center,lfe,side-left,side-right
description = Analog Surround 7.1
paths-output = analog-output analog-output-speaker analog-output-desktop-speaker
priority = 7
direction = output

[Mapping iec958-stereo]
device-strings = iec958:%f
channel-map = left,right
paths-input = iec958-stereo-input
paths-output = iec958-stereo-output
priority = 5

[Mapping iec958-ac3-surround-40]
device-strings = a52:%f
channel-map = front-left,front-right,rear-left,rear-right
priority = 2
direction = output

[Mapping iec958-ac3-surround-51]
device-strings = a52:%f
channel-map = front-left,front-right,rear-left,rear-right,front-center,lfe
priority = 3
direction = output

[Mapping iec958-dts-surround-51]
device-strings = dca:%f
channel-map = front-left,front-right,rear-left,rear-right,front-center,lfe
priority = 3
direction = output

[Mapping hdmi-stereo]
device-strings = hdmi:%f
description = Digital Stereo (HDMI)
paths-output = hdmi-output-0
channel-map = left,right
priority = 4
direction = output

[Mapping hdmi-surround]
description = Digital Surround 5.1 (HDMI)
device-strings = hdmi:%f
paths-output = hdmi-output-0
;channel-map = front-left,front-right,rear-left,rear-right,front-center,lfe
channel-map = front-left,front-right,front-center,lfe,rear-left,rear-right
priority = 3
direction = output

[Mapping hdmi-stereo-extra1]
description = Digital Stereo (HDMI)
device-strings = hdmi:%f,1
paths-output = hdmi-output-1
channel-map = left,right
priority = 2
direction = output

[Mapping hdmi-surround-extra1]
description = Digital Surround 5.1 (HDMI)
device-strings = hdmi:%f,1
paths-output = hdmi-output-1
;channel-map = front-left,front-right,rear-left,rear-right,front-center,lfe
channel-map = front-left,front-right,front-center,lfe,rear-left,rear-right
priority = 1
direction = output

[Mapping hdmi-stereo-extra2]
description = Digital Stereo (HDMI)
device-strings = hdmi:%f,2
paths-output = hdmi-output-2
channel-map = left,right
priority = 2
direction = output

[Mapping hdmi-surround-extra2]
description = Digital Surround 5.1 (HDMI)
device-strings = hdmi:%f,2
paths-output = hdmi-output-2
;channel-map = front-left,front-right,rear-left,rear-right,front-center,lfe
channel-map = front-left,front-right,front-center,lfe,rear-left,rear-right
priority = 1
direction = output

[Mapping hdmi-stereo-extra3]
description = Digital Stereo (HDMI)
device-strings = hdmi:%f,3
paths-output = hdmi-output-3
channel-map = left,right
priority = 2
direction = output

[Mapping hdmi-surround-extra3]
description = Digital Surround 5.1 (HDMI)
device-strings = hdmi:%f,3
paths-output = hdmi-output-3
;channel-map = front-left,front-right,rear-left,rear-right,front-center,lfe
channel-map = front-left,front-right,front-center,lfe,rear-left,rear-right
priority = 1
direction = output
```

---

### Post by PhonicLynx on 2013-01-22
/usr/share/pulseaudio/ doesn't seem to exist.

---

### Post by jksj on 2013-01-23
You can    	 	 	 	get round the problem by setting 		in Advanced Audio Settings - Stereo PCM only. This moves the responsibility of decoding the signal to 5:1 to the surround sound receiver rather than within mythtv. I used this when I had an ion 1 nvidia card and it worked fine without any quality degradation.

---

### Post by PhonicLynx on 2013-01-23
But then you don't get the 5.1 sound?

---

### Post by jksj on 2013-01-24
You do get surround sound. The following link points to a thread by Jean-Yves Avenard who understands the issue properly. I just tried it and it worked for me.
use multi-channels PCM but force using AC3 or DTS only.
[http://www.mythtv.org/pipermail/mythtv-users/2011-January/308621.html](http://www.mythtv.org/pipermail/mythtv-users/2011-January/308621.html)

Best of luck.
I believe that early hdmi cables (version 1) only carried two audio signals so the stereo pcm setting tells myth to encode surround sound into these two signals but this is all second hand. Follow advice from Jean-Yves Avenard in the threads which address this issue.

---

### Post by PhonicLynx on 2013-01-24
Looks like it works nicely :)

---

