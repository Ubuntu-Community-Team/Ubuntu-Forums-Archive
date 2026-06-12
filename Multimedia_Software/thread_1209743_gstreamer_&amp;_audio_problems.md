---
title: "gstreamer &amp; audio problems"
date: 2009-07-10
forum: Multimedia Software
---

### Post by over_my_head on 2009-07-10
my sound (which i had working) suddenly died on me and now when i try to open volume control i get an error saying: "No volume control GStreamer plugins and/or devices found."

and when i run the command aplay -l it says >  aplay: device_list:215: no soundcards found... 
but when i run lspci -v it does find an audio device: 

> 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 30cc
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at f8600000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel


my computer is a laptop (HP pavilion dv6835nr) running Ubuntu 8.10
i tried working through the 'Comprehensive Sound Problem Solutions Guide' but when it got to finding a driver for my sound card on the alsa website, i couldn't find my soundcard listed. but i was using alsa before and it was working!! 

i also tried getting the Alsa drivers from a fresh kernel as suggested in the above mentioned guide but it didn't appear to change anything as after reboot i clicked on volume control and got the same error message as before. i am at a total loss as to what to try next. please help!

---

### Post by Yellow Pasque on 2009-07-10
Try: [http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

---

### Post by NinjaNumberNine on 2009-07-10
Try going in System > Preferences > Sound

and set all of the top three boxes to ALSA.

(Make sure the device you want is selected in the dropdown menu near the bottom)

If this doesn't work just play around with the options.

By the way, this is just a suggestion. I don't know what your situation is exactly.

:biggrin:I am not an expert at soundcardology.:biggrin:

---

### Post by over_my_head on 2009-07-11
i just upgraded Alsa and was about ready to throw my laptop out the second floor window because i thought it didn't work.... luckily it occured to me to try rebooting first and man, i about fell off my chair when i heard the ubuntu theme music coming out of my speakers. 
i once again have sound!! yay!
and thank you both for responding, these forums are an amazing help to n00bs like me. :-)

---

