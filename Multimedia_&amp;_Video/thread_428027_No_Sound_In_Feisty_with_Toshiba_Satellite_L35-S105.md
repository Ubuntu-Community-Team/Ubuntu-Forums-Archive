---
title: "No Sound In Feisty with Toshiba Satellite L35-S1054"
date: 2007-04-29
forum: Multimedia &amp; Video
---

### Post by cilaes on 2007-04-29
I have a Toshiba Satellite L35-S1054 laptop with a fresh install of Feisty 7.04 -- I've installed all of the codecs, etc, and consider myself a pretty advanced linux user. Everything works amazingly, except for the sound, and from a little research seems very common with the Toshiba family.

I've been told in the IRC channel there will be an update to fix this problem, are there any known working temporary fixes?

---

### Post by cilaes on 2007-04-30
*bumb*

Can someone atleast update me on the status of this? Is it being worked on at all? Any fix whatsoever? I've seen alot of people being turned away by these problems, and I haven't found ANY support for it whatsoever.

---

### Post by hvthao on 2007-05-01
What type of your sound card?

---

### Post by cilaes on 2007-05-03
#
################################
#
ALSA Information Script v 0.4.20
#
################################
#
 
#
 
#
Linux Distribution
#
------------------
#
 
#
Ubuntu 7.04 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 7.04"
#
 
#
 
#
Kernel Information
#
------------------
#
 
#
Kernel release:    2.6.20-15-generic
#
Operating System:  GNU/Linux
#
Architecture:      i686
#
Processor:         unknown
#
SMP Enabled:       Yes
#
 
#
 
#
ALSA Version
#
------------
#
 
#
Driver version:     1.0.14rc1
#
Library version:   
#
Utilities version:  1.0.13
#
 
#
 
#
Loaded ALSA modules
#
-------------------
#
 
#
snd_hda_intel
#
 
#
 
#
Soundcards recognised by ALSA
#
-----------------------------
#
 
#
 0 [SB             ]: HDA-Intel - HDA ATI SB
#
                      HDA ATI SB at 0xc0400000 irq 18
#
 
#
 
#
PCI Soundcards installed in the system
#
--------------------------------------
#
 
#
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)

---

### Post by romrix on 2007-05-04
I have exact same setup, Toshiba Satellite L35-S1054 laptop with a fresh install of Feisty 7.04. It also has no sound and I have found nothing yet.
  :confused:

---

### Post by cilaes on 2007-05-05
> **romrix said:**
> I have exact same setup, Toshiba Satellite L35-S1054 laptop with a fresh install of Feisty 7.04. It also has no sound and I have found nothing yet.
  :confused:

Yeah. Like I said, you find nothing more than a ghost town when trying to find a solution to this VERY aggravating, unsupported problem. I guess this community isn't all it's cracked up to be?

---

### Post by andreigbs on 2007-05-05
join the Toshiba gang who have no sound.  it's a software issue, not a community fault.  if anything, somebody here will be find the fix and post it for all to see and take advantage of.  some patience is necessary i guess.  till the fix is found, i'll go back to XP.

---

### Post by tyler22 on 2007-05-06
I had the exact same problem. I was able to fix it. I am by no means an advance Linux user. But I will see if I can find the guide that provided the solution. It was very simple. 

If any help can be gathered from this post, its that it can work!

I will start searching now!

---

### Post by tyler22 on 2007-05-06
[Solution can be found in this thread]("http://ubuntuforums.org/showthread.php?t=392350&highlight=toshiba")


Hope it works for everyone. Once I got the sound working on my laptop i was free, I use Ubuntu as my only OS now. No more windows.

---

### Post by Unreallinux on 2007-05-06
Did this fix your headphone jack as well?

---

### Post by tyler22 on 2007-05-06
Yes it did. Everything related to sound works correctly after this fix.

---

### Post by cilaes on 2007-05-06
My headphone jack still isn't working, but 3stack worked on my laptop. Thanks ALOT! But I must've messed something up because even after a reboot i dont have the volume control on my panel and can't find it anywhere...

---

### Post by tyler22 on 2007-05-06
I am afraid I can be no use with the headphone jack.

To get volume control back:

Right click on the panel you want it to be located --> Add to panel

It will open a window. Under the category System & Hardware there will be volume control. Select it.

This should add the control back to your panel.

---

### Post by cilaes on 2007-05-09
thanks alot. IF you happen to find a fix, post it here! PLEASE!

---

### Post by Donny K. on 2007-11-18
Maybe the fix, posted in this thread : [http://ubuntuforums.org/showthread.php?p=3796486#post3796486](http://ubuntuforums.org/showthread.php?p=3796486#post3796486)

will fix your headphone problems.

Good luck!

---

### Post by Yellow Pasque on 2007-11-19
Anyone try ditching ALSA and using OSSv4 with these lappy's?

---

### Post by Donny K. on 2007-11-20
Yes I tried, but that did not solve the problem. (I also tried ESD)

---

