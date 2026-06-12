---
title: "sound card issues with toshiba satellite"
date: 2008-09-03
forum: Multimedia Software
---

### Post by dewek932 on 2008-09-03
Hey!

Im ejoying Linux on my Toshiba Satellite A135 S4527.

But the sound is way way low on all video and Audio. 

when I first migrated to Ubuntu Hardy Heron, it would play videos with sound from the internet, 

but when Itried to playback DVDs it was no go. 

SO I downloaded a bunch of software for playing DVD's and tried them all. now, I can see the video, but the sound, while there, is way way low. too low to hear.

I googled for a solution, researched chip compatability etc, and found of course that my chipset is incompatible. I even found a couple command line solutions to overwrite and get the thing working here; [http://d.cl1p.net/ubunttoshiba135s4527/](http://d.cl1p.net/ubunttoshiba135s4527/)

but it worked for the guy on Gutsy gibbon. Im running Hardy Heron

there are two commands on the page. One opens a new Terminal Like field with all the overwrite commands, the second finishes the process. I cant get the whole thing to finish, because there are two separate fields, and I can't execute the command. 

Here is the first commmand: gksudo gedit /etc/modprobe.d/alsa-base 

and here is the second command: options snd-hda-intel position_fix=1 model=3stack

My questions; how do I get the overwrite info generated in a new window by the first command to work in my original Terminal window? or, barring that what else might be done? The chipsets are firewire/ texas instruments gear.

HELP!!!!!I have zero audio (its so low I cant hear it even if I crane my neck). I've tried audio and edit graphical fields for every movie player I've tried. nothing does anything. Im on the verge of a dual boot, though I don't want to do. I'd rather tinker than meet roadblocks and have zero support. I don't much like MSOFT.

Thanx,
d

---

