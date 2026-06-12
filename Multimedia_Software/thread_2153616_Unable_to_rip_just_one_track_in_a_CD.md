---
title: "Unable to rip just one track in a CD"
date: 2013-06-11
forum: Multimedia Software
---

### Post by oxf on 2013-06-11
OK before anyone accuses me of illegal copying I'm not, I'm just ripping om of my CD's to my personal MP3 player. That out of the way here's whats happening.

There are 11 tracks on this CD. All 11 tracks play normal on my CD player. If I play the CD on my PC using Banshee it only recognises tracks 1 through 10. Track 11 is missing. If I try to rip the tracks again only 1-10 are ripped as mp3. When it get to track 11 it stall half way through and that incomplete track is listed as .wav.

My suspicion is that the reason is that there's also a music video on this disc and that track 11 (the same song as the video) are linked in someway (although plays just as music on the CD player). Also if I look at the CD in the file browser track 11 seems the same as all the other audio tracks. Is my reasoning correct here? Is there any way around this problem? because track 11 happens to be my favourite track!

Thanks
Katelyn

---

### Post by andrew.46 on 2013-06-11
It might be helpful to abandon the gui for a moment and test your cd directly with cdparanoia. Here is an example with a 5 track audio cd:

```

andrew@skamandros~$**[COLOR="#FF0000"] cdparanoia -vsQ[/COLOR]**
cdparanoia III release 10.2 (September 11, 2008)

Using cdda library version: 10.2
Using paranoia library version: 10.2
Checking /dev/cdrom for cdrom...
	Testing /dev/cdrom for SCSI/MMC interface
		SG_IO device: /dev/sr0

CDROM model sensed sensed: HL-DT-ST DVDRAM GH22NS70 EX00 

Checking for SCSI emulation...
	Drive is ATAPI (using SG_IO host adaptor emulation)

Checking for MMC style command set...
	Drive is MMC style
	DMA scatter/gather table entries: 1
	table entry size: 131072 bytes
	maximum theoretical transfer: 55 sectors
	Setting default read size to 27 sectors (63504 bytes).

Verifying CDDA command set...
	Expected command set reads OK.

Attempting to set cdrom to full speed... 
	drive returned OK.

Table of contents (audio tracks only):
track        length               begin        copy pre ch
===========================================================
  1.    54552 [12:07.27]        0 [00:00.00]    OK   no  2
  2.    20517 [04:33.42]    54552 [12:07.27]    OK   no  2
  3.    35923 [07:58.73]    75069 [16:40.69]    OK   no  2
  4.    50133 [11:08.33]   110992 [24:39.67]    OK   no  2
  5.   103576 [23:01.01]   161125 [35:48.25]    OK   no  2
TOTAL  264701 [58:49.26]    (audio only)

```

(Check with your own cd for the phantom track 11!). Then if you wished to rip a single track something like the following:

```

andrew@skamandros~$ **[COLOR="#FF0000"]cdparanoia -w 5 track05.wav[/COLOR]**
cdparanoia III release 10.2 (September 11, 2008)

 
Ripping from sector  161125 (track  5 [0:00.00])
	  to sector  264700 (track  5 [23:01.00])

outputting to track05.wav

 (== PROGRESS == [                            + | 264700 00 ] == :^D * ==)   

Done.


andrew@skamandros~$ 

```

This will give you a wav file named track05.wav to then convert to the format of your choice. Hopefully you can get this to work for your elusive track 11 :)

---

### Post by VanillaMozilla on 2013-06-11
Can't you just copy it with a file browser?  Then, once you have the .wav file, you can convert it to whatever you want.

---

### Post by oxf on 2013-06-12
@andrew.46 

Thanks, I'll try that, I have cdparanoia already installed apparently but never knew it!

@VanillaMozilla
I can copy it in file browser but can't do anything with it which is what I suspected. Also it's a .wma file

---

### Post by oxf on 2013-06-12
Well same result using cdpananoia. It starts ripping track 11 and then starts outputting errors

```
outputting to track11.wav

 (== PROGRESS == [                         >    | 204165 00 ] == :-) . ==)   scsi_read error: sector=204331 length=27 retry=0
                 Sense key: 5 ASC: 64 ASCQ: 0
                 Transport error: Illegal SCSI request (rejected by target)
                 System error: Invalid argument
scsi_read error: sector=204331 length=13 retry=1
                 Sense key: 5 ASC: 64 ASCQ: 0
                 Transport error: Illegal SCSI request (rejected by target)
                 System error: Invalid argument
scsi_read error: sector=204331 length=6 retry=2
                 Sense key: 5 ASC: 64 ASCQ: 0
                 Transport error: Illegal SCSI request (rejected by target)
                 System error: Invalid argument
 (== PROGRESS == [                         >    | 204165 00 ] == :-0   ==)   scsi_read error: sector=204358 length=27 retry=0



```

Its would seem that since track 11 is the one with the video that when I play it in a cd player I'm just playing the audio of the video. When I try and rip it I must be trying to rip the audio off of a "video" so that's why a cd ripper wont work.
At least thats my theory.

Katelyn

---

### Post by andrew.46 on 2013-06-12
I am afraid that I cannot work that one out :(. Hopefully somebody can interpret what is going on there... I gather the process did not end? In your post it looks like it is continuing. From the cdparnoia faqs:

```

Transport or drive error. This is normally not a cause for concern; cdparanoia can repair 
just about any error that it actually detects. For more information about these errors,
 run cdparanoia with the -v option. Any all all errors and a description will dump to stderr. 

```

---

### Post by oxf on 2013-06-12
> **andrew.46 said:**
> I am afraid that I cannot work that one out :(. Hopefully somebody can interpret what is going on there... I gather the process did not end? In your post it looks like it is continuing. From the cdparnoia faqs:

```

Transport or drive error. This is normally not a cause for concern; cdparanoia can repair 
just about any error that it actually detects. For more information about these errors,
 run cdparanoia with the -v option. Any all all errors and a description will dump to stderr. 

```

No it just kept on trying scrolling down until I stoped it. I'm pretty sure the reason is that this is the music video track although until now I never realised that having only played it in my cd player. Thanks for trying!

---

### Post by mc4man on 2013-06-12
I don't remember if you use wine, if so it's likely EAC in wine could rip that track. 
(there are several threads on getting EAC going, ect.

Otherwise don't think it's worth installing wine for just 1 track. 
If you have a windows box or friend with one then should be quite simple also.

As far as linux, no idea, don't have any Enhanced (CD-Extras, multi-mode)  audio cd's

(- did you ever get rid of that matshita laptop drive?

---

### Post by andrew.46 on 2013-06-12
> **mc4man said:**
> As far as linux, no idea, don't have any Enhanced (CD-Extras, multi-mode)  audio cd's

Indeed, neither do I :(

---

### Post by mc4man on 2013-06-12
> **andrew.46 said:**
> Indeed, neither do I :(
I feel like buying one, just may do so... (have to order a customer something from amazon, will have a look around

---

### Post by shantiq on 2013-06-13
well   oxf   let us not rip it but copy it [if it is ok with your system and allows it]


to my mind the very easiest route here is this:


load CD
open folder manually
drag track 11 to desktop

use easytag or puddletag   [in repo]   to tag


add to the other 10

---

