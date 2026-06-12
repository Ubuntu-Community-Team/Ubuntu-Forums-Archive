---
title: "Gateway 3522gz sound"
date: 2006-02-14
forum: Multimedia &amp; Video
---

### Post by DustoneGT on 2006-02-14
Apparently gateway felt the need to screw with the
AC97 standard and swapped the headphone and master
volume controls.
Somebody has been able to get this machine running
sound under fedora so I am not completely without
hope. 
[http://www2.netdoor.com/~horus/Gateway_3522GZ.html](http://www2.netdoor.com/~horus/Gateway_3522GZ.html)

I have set the last line in /etc/modprobe.d/alsa-base
to options snd-intel8x0 ac97_quirk=swap_hp
and then ran sudo update-modules in konsole

All right...ran "alsactl restore" in konsole and it spit this back at me:
alsactl: set_control:894: warning: name mismatch (Master Playback Switch/Line-Out Playback Switch) for control #1
alsactl: set_control:896: warning: index mismatch (0/0) for control #1
alsactl: set_control:894: warning: name mismatch (Master Playback Volume/Line-Out Playback Volume) for control #2
alsactl: set_control:896: warning: index mismatch (0/0) for control #2
alsactl: set_control:894: warning: name mismatch (Headphone Playback Switch/Master Playback Switch) for control #3
alsactl: set_control:896: warning: index mismatch (0/0) for control #3
alsactl: set_control:898: failed to obtain info for control #3 (Operation not permitted)
I am not sure what this output means...

Am I doing something wrong?
What else can I do to get the sound running?

---

### Post by DustoneGT on 2006-02-15
When I run alsamixer
there are some wierd inputs and outputs....
IEC958

I have been reading that IEC being on
can be a problem.
So I highlight them and press m to disable
but they wont disable.

Any way to manually remove/disable?

---

### Post by DustoneGT on 2006-02-20
I have read that maybe upgrading to newest alsa could help.
Anybody know of a good guide for that?

---

### Post by DustoneGT on 2006-02-24
I installed Fedora Core 4....sound works right out of the box...
I liked ubuntu better though.....

Anybody have any ideas?

---

### Post by hitjim on 2006-02-25
i just recently got the (what i presume to be alsa) default driver working on my gateway mx3215

it sounds like our hardware etc are pretty similar, which wouldn't surprise me.

i had messed around with running alsamixer form a cmd prompt ... and i think it finally worked b/c i turned off the external amplifier.

but just in case, here's a list of my settings in alsamixer
(i had an image to link to... but the ftp to my webserver isn't connecting)

i'll just list the muted channels

line
mic
mic boost
phone
iec958
iec958O
iec958 P
external

the rest are either on or have no setting options

hope that helps.  this laptop was brand new at BB, and i hadn't been able to find much of any documentation on putting linux on it... and i've pretty much gotten everything i need to work on it. wireless (still have to redo a bunch of crap on reboot), sound, and widescreen resolution (actually worked out of the box, thx to ubuntu).

let me know if that doesn't work...and fetch my specific hardware again, to make sure we're comparing apples to apples.

good luck.

---

### Post by hitjim on 2006-02-25
[QUOTE=DustoneGT]I installed Fedora Core 4....sound works right out of the box...
I liked ubuntu better though.....

Anybody have any ideas?[/QUOTE]

i also tried fc4 on my mx3215.  sound worked fine... but not the resolution.  and the up2date kept hanging to matter what i did. 

i also tried old school debian... but i couldn't get x to display my 1280x768 reso.  in centos, vi was acting really wierd (prolly my fault, or old currupted install disks?), and suse would just hang during the installation... granted it was a netinstall... but it's a new machine w/broadband.  and i just flat out don't have time for gentoo.

ubuntu seems to be the best distro for this machine at the time... the most things either worked or were detected out of the box than all the others (the correct screen resolution was a big step).  even the touchpad's scrollpad works by default.  none of the others did that.

well... that's enough from me.

---

### Post by DustoneGT on 2006-02-25
I have muted all of those lines except 
IEC958 Playback AC97-SPSA
IEC958 Playback Source [AC-Link]

When I press m to mute them it does nothing!

---

### Post by DustoneGT on 2006-02-25
FIXED IT!!!! w000t!

I opened alsamixer and moved over to 
IEC958 Playback Source [AC-Link]

Pressing the up/down buttons changes it to
IEC958 Playback Source [A/D Converter]

pressed escape

then:
sudo alsactl store
sudo alsactl restore

Sound!!!!!!!!

And I don't have to use fedora core!
(no offense to anybody who likes it, I dont)

---

### Post by manrui on 2006-11-27
Hi, I also have mx3215 from BB and I have the same problems. One  more problem is that I am pretty new to linux and don't understand too many things yet. Could you plese guide me with the sound and wireless?

thank you 

Marcel




> **hitjim said:**
> i just recently got the (what i presume to be alsa) default driver working on my gateway mx3215

it sounds like our hardware etc are pretty similar, which wouldn't surprise me.

i had messed around with running alsamixer form a cmd prompt ... and i think it finally worked b/c i turned off the external amplifier.

but just in case, here's a list of my settings in alsamixer
(i had an image to link to... but the ftp to my webserver isn't connecting)

i'll just list the muted channels

line
mic
mic boost
phone
iec958
iec958O
iec958 P
external

the rest are either on or have no setting options

hope that helps.  this laptop was brand new at BB, and i hadn't been able to find much of any documentation on putting linux on it... and i've pretty much gotten everything i need to work on it. wireless (still have to redo a bunch of crap on reboot), sound, and widescreen resolution (actually worked out of the box, thx to ubuntu).

let me know if that doesn't work...and fetch my specific hardware again, to make sure we're comparing apples to apples.

good luck.

---

### Post by hdweathers on 2008-03-14
[QUOTE=DustoneGT;770754]FIXED IT!!!! w000t!

I opened alsamixer and moved over to 
IEC958 Playback Source [AC-Link]

That works for my 3522gz. Just for other folks like me; I had interpreted DustoneGT's message to make a change from AC-link to A/D converter. The sound works with the AC-Link setting and IEC958 Playback Source. Thanks DGT, and sorry for the potential redundancy.

---

