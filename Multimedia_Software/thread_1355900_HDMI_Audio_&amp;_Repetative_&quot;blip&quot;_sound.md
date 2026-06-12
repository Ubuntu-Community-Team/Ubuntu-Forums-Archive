---
title: "HDMI Audio &amp; Repetative &quot;blip&quot; sounds"
date: 2009-12-15
forum: Multimedia Software
---

### Post by jingo_man on 2009-12-15
hello all

i am trying to get hdmi audio to work on my HTPC system (Asus P5N7A-VM board, Ubuntu 9.04)

this motherboard has an HDMI connection from the systemboard. i have already setup the system to use the VDPAU aspects of the latest NVidia restricted driver (v190.42) to playback HD content. this is amazing!

i had previously used the standard 2.5mm jack from the "Front" ports of the S/PDIF connectors, also provided from the motherboard (by only plugging in the Front/green port, this only plays through the front speakers). i have pulseaudio installed (by default, though dont think the system uses it) and ALSA installed (again, the default install) and this was configured for use within MythTV and XBMC as the "ALSA:default" device in both app's configs.

following the guide [here]("http://ubuntuforums.org/showthread.php?p=8485647#post8485647"), i updated the ALSA version to 1.0.19 and added the "options snd-hda-intel model=6stack-dig" to the alsa.conf file. then updating the config of both apps to use "ALSA:hdmi" device and the sound is working.

but, when i exit either app with sound playing (or stop the "Test" option from the sound control panel - presumably this will happen for any sound that is made, though!) i get this repetative "blip" sound of the tone of the last sound made. one such example of this is attached to this thread, though this was recorded from my iPhone held up to the speakers, so isnt very loud (as opposed to actual volume in my living room!)

i tried restarting the ALSA alsasound and alsa-utils daemons, no joy. i upgraded pulseaudio to 0.9.15 (even though i dont think its in use), no joy. if i unplug the HDMI cable, then plug back in or reboot, it resolves the issue.

can any one help troubleshoot the issue? i can provide any system details or configs, but wasnt sure what would be needed...

regards

jingo_man

---

