---
title: "HDMI output (jst basic terminal knowledge needed!)"
date: 2010-11-24
forum: Multimedia Software
---

### Post by Joe Question on 2010-11-24
Hi, everyone
today I tried to connect my acer 1810tz to my tv set via the HDMI ouput. The video works fine, but the sound doesn't. I tried to follow the steps on this page

[http://wiki.archlinux.org/index.php/Advanced_Linux_Sound_Architecture#HDMI_Output_Does_Not_Work](http://wiki.archlinux.org/index.php/Advanced_Linux_Sound_Architecture#HDMI_Output_Does_Not_Work)

but as I am hopeless with the terminal I couldn't carry out the last bit.

This test was successful:

aplay -D plughw:0,3 /usr/share/sounds/alsa/Front_Center.wav

and a sound came out of the TV set, hooray!

but at this point I was supposed to:

"edit/create asound.conf in /etc to set HDMI as the default audio device, reboot, and audio should now work".

The suggested instructions to achieve that were: 
 
cat /etc/asound.conf
 pcm.!default {
      type plug
      slave.pcm {
              type hw
              card 0
              device 3
      }No such file or directory

 }


BUT nothing happened on my pc apart from a "No such file or directory" msg
... so how can I do that? I warned I was quite thick on the matter :) 
thanks to anyone

PS data from "aplay -l" is

card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Running on Maverick

---

### Post by Joe Question on 2010-11-26
Any ideas? Anyone?

---

### Post by stace3610 on 2010-11-27
Not being a very experienced user myself, I'm not sure if it's exactly the same problem, but this got my HDMI working a treat!

[http://ubuntuforums.org/showthread.php?t=1046137]("http://ubuntuforums.org/showthread.php?t=1046137&highlight=hdmi+asound.conf")

Regards,
Stace.

---

### Post by Joe Question on 2010-11-29
> **stace3610 said:**
> Not being a very experienced user myself, I'm not sure if it's exactly the same problem, but this got my HDMI working a treat!

[http://ubuntuforums.org/showthread.php?t=1046137]("http://ubuntuforums.org/showthread.php?t=1046137&highlight=hdmi+asound.conf")

Regards,
Stace.

Thanks Stace! 
Am now actually switching the sound output each time from System-Preferences-Sound-Hardware and that works fine.
But I'll try the script as well as it seems to fix other problems (it might get my internal mic to work, which isn't)...

Cheers

---

