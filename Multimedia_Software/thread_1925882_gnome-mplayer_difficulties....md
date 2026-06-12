---
title: "gnome-mplayer difficulties..."
date: 2012-02-15
forum: Multimedia Software
---

### Post by zenlines on 2012-02-15
Hi Everyone,

I recently discovered the mplayer as well as the gnome-mplayer. They are both so sweet and soooo much more resource friendly than vlc, deadbeef, and pretty much anything else that I can think of. Plus (!), I only need one program to play _all_ types of media. I am almost surprised that (gnome)-mplayer is not the default player for ubuntu. It trump banshee and rhythmbox in my opinion. Enough about me being impressed with mplayer.

When using the GUI gnome-player the sound is strange... With the harder bass sections the speakers scratch / overextend. Using gnome-mplayer from the command line and then picking out my .mp3 (same thing with an avi):

~$ gnome-mplayer -v
GNOME MPlayer v1.0.4
...
setting up mplayer
mplayer -ao pulse -channels 4 -af-add export=/tmp/mplayer-af_exportjjecsu:512 -quiet -slave -noidle -noconsolecontrols -nostop-xscreensaver -identify -volume 100 -softvol -osdlevel 0 -delay 0.000000 -subdelay 0.000000 -subpos 0 -sub-fuzziness 0 -wid 0x3a0007e -brightness 0 -contrast 0 -hue 0 -saturation 0 -nomsgcolor -nomsgmodule -nokeepaspect -*** -embeddedfonts -***-font-scale 1.00 -***-color ffffff00 /D/Music/Alternative_Rock/91\ Words/01\ It's\ Oh\ So\ Quiet.mp3 
...


However, when I copy and paste the above command line and then remove the memory mapping stuff (-af-add  export=/tmp/mplayer-af_exportjjecsu:512):

mplayer -ao pulse -channels 4 -quiet -slave -noidle  -noconsolecontrols -nostop-xscreensaver -identify -volume 100 -softvol  -osdlevel 0 -delay 0.000000 -subdelay 0.000000 -subpos 0 -sub-fuzziness 0  -wid 0x3a0007e -brightness 0 -contrast 0 -hue 0 -saturation 0  -nomsgcolor -nomsgmodule -nokeepaspect -*** -embeddedfonts  -***-font-scale 1.00 -***-color ffffff00 /D/Music/Alternative_Rock/91\  Words/01\ It's\ Oh\ So\ Quiet.mp3 

the scratching of the speakers stops. 

Could someone tell me why? And how would I change the gnome-mplayer options to disable memory mapping? All of the manuals I have looked through are not helping me.... ;)  For now I guess I will be using the terminal... which is pretty nice too...

Thanks!
Brian

---

