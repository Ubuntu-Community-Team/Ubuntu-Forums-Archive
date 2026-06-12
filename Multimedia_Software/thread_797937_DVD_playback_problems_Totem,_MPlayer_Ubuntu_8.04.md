---
title: "DVD playback problems Totem, MPlayer Ubuntu 8.04"
date: 2008-05-17
forum: Multimedia Software
---

### Post by lukjad on 2008-05-17
---------------------------------------------
Edit #0
I just wish to let anyone know that I will sum up the responses here so that you don't have to read all through the (hopefully non-existent) myriads of pages unless you like to do that type of thing (You masochist you.). 
---------------------------------------------
I have just upgraded from Feisty Fawn to Gutsy Gibbons and then to Hardy Heron. Here is a quick list that I compiled of my troubles with DVDs.
     1) DVD will not go to menu. Begins playing movie immediately.
     2) DVD is in black and white. Very little colour is apparent.
     3) Totem will not allow you to fast-forward or rewind. It locks up and then crashes.
     4) MPlayer: There is "No stream found to handle url dvd://"
     5) VLC is very choppy but has full sound and colour.

     I have searched for the error messages and have found much, little of which helped. I will continue to search and post and and all webpages that I see anything of interest. Below are the error outputs of all of the programs mentioned above, even VLC even though it caused me little grief.
     I wasn't able to get all of the errors of totem because there were so many. Here is what I did get.
---------------------------------------------
Edit #1

My first edit and I barely started. ;) I noticed that while totem will play movie clips already on my hard drive in colour it will only do so before I play an encrypted DVD. After playing an encrypted DVD the colour quality degrades sharply until almost complete black and white.
P.S. These clips are mostly, but not all, .flv and .avi types. So it is not solely the file format at fault.
---------------------------------------------
Edit #2

I did find a temporary solution to the video clips being black and white. Just go to Edit->Preferences->Display and click Reset to Defaults. 
(Will get the source.)
---------------------------------------------
Edit #3

I hadn't installed linux-restricted-modules but I had installed ubuntu-restricted-extras. After I tried installing it the problem was the same. The colour slides to B&W and I have to reset it every three minutes.
---------------------------------------------
Edit #4
Pjotr, I did do a clean install. I had first upgraded and when that didn't work, I did do a fresh install. Sorry I didn't mention it.

---------------------------------------------

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1571 ***
*** for c_adt->cell_adr_table[i].vob_id > 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1573 ***
*** for c_adt->cell_adr_table[i].cell_id > 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1575 ***
*** for c_adt->cell_adr_table[i].start_sector < c_adt->cell_adr_table[i].last_sector ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1571 ***
*** for c_adt->cell_adr_table[i].vob_id > 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1573 ***
*** for c_adt->cell_adr_table[i].cell_id > 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1575 ***
*** for c_adt->cell_adr_table[i].start_sector < c_adt->cell_adr_table[i].last_sector ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1571 ***
*** for c_adt->cell_adr_table[i].vob_id > 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1573 ***
*** for c_adt->cell_adr_table[i].cell_id > 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1575 ***
*** for c_adt->cell_adr_table[i].start_sector < c_adt->cell_adr_table[i].last_sector ***


[I cut a lot out here because it was just too long. If more is needed I'll put some back in.]


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1575 ***
*** for c_adKilled
-------------------------------------------------------------------------------------------------
Next:

:~$  mplayer dvd://

MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel Celeron 2/Pentium III Coppermine,Geyserville (Family: 6, Model: 8, Stepping: 3)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://.
Couldn't open DVD device: /dev/dvd
No stream found to handle url dvd://


Exiting... (End of file)

--------------------------------------------------------------------------------------------------------


:~$ vlc
VLC media player 0.8.6e Janus
[00000300] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
[00000283] main playlist: stopping playback

---

### Post by lukjad on 2008-06-05
I know it's rude but...
Bump.

---

### Post by p_quarles on 2008-06-05
Moved to Multimedia & Video.

Bumping is fine, by the way, as long as you don't do it excessively. ;)

---

### Post by AndyCee on 2008-06-06
I always apologise before this suggestion. I'm sorry.

Have you installed the Ubuntu-restricted-modules from the add/remove application menu? Could they have been overwritten in the upgrade?

If you've searched much, I'd assume you've done it. But just trying to get the ball rolling until someone more knowledgable rocks up...

---

### Post by Pjotr123 on 2008-06-06
Try this as well:
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

But a clean install of 8.04 to start with, would be better. Upgrading is always inferior to a clean install, for every operating system under the sun.

Greeting, Pjotr.

---

### Post by ubuntu-freak on 2008-06-06
Even VLC goes straight to playback, yeah? 
 
Regarding the choppyness of VLC, make sure vlc-plugin-pulse is installed and select "pulse" in VLC's sound output preferences. Also, take a look at Part 4 of my [how-to](http://ubuntuforums.org/showthread.php?t=766683) and perhaps purge/install the DVD-related packages. If VLC starts to behave, you can also make it launch by default for DVDs with the instructions in Part 4.

---

### Post by lukjad on 2008-06-13
> **AndyCee said:**
> I always apologise before this suggestion. I'm sorry.

Have you installed the Ubuntu-restricted-modules from the add/remove application menu? Could they have been overwritten in the upgrade?

If you've searched much, I'd assume you've done it. But just trying to get the ball rolling until someone more knowledgable rocks up...

WHAT!!! YOU THINK THAT I DIDN'T DO [SIZE="5"]THAT[/SIZE]?!?!? OF course I (*Clickedy clickedy click*) DID! What do you think... Ummm... Aah... Ahem. Ok So it wasn't installed. ;) 
Thanks for the tip. I had the ubuntu-restricted-extras installed and not the linux-restricted-modules. The image is still choppy though and the picture still seems to be going to B&W.
I will go and play a few clips and a movie to test it out. Thanks a lot! (And I mean that in a good way.)
_________________________-
Edit
I tested it and it still goes to Black and White. I did find a very good post on Ubuntu forums telling me how to reset the colour but it still slides back.

---

### Post by lukjad on 2008-06-14
*Sigh*
It looks like I'll just have to bite the bullet and reinstall Ubuntu. I have backed up my prefs and will see if erasing everything and doing a completely fresh install with no hidden files will help. Hope to see you on the other side.

P.S.
Until I fix the problem I have been using a live CD called TEENpup. I really like it, it plays everything I had and was fairly simple. Check it out.

By for about 2 hours,

Luke

---

### Post by Pjotr123 on 2008-06-14
> **lukjad007 said:**
> *Sigh*
It looks like I'll just have to bite the bullet and reinstall Ubuntu. I have backed up my prefs and will see if erasing everything and doing a completely fresh install with no hidden files will help. Hope to see you on the other side.

P.S.
Until I fix the problem I have been using a live CD called TEENpup. I really like it, it plays everything I had and was fairly simple. Check it out.

By for about 2 hours,

Luke

Wise of you. Apply this checklist right after a fresh installation:
[http://ubuntutip.googlepages.com/thefirstthingstodo](http://ubuntutip.googlepages.com/thefirstthingstodo)

Is teenpup derived from Puppy Linux, by the way?

---

### Post by lukjad on 2008-06-14
Yes. Puppy Linux has saved my bacon countless times. (It also has fried my bacon a couple times too, but that's another story.) I find that of the "Puppies" that I have tried this one is the best. It strikes the right balance between usability, size (for older PC like mine), and eye candy. Most of the puppy distros that I saw either were small and looked like Windows 95, or were so bloated that it took my PC 15-33 minutes to load it to RAM.
I'm back and am planning on doing that checklist. Thanks.

(PS Does anyone know whether or not Ubuntu Studios is a good choice for an older PC or is it only useful for a brand new PC?)

---

### Post by notidefix on 2008-06-15
Did you manage to get the DVD menu to work with reinstalling?

I followed the steps in:
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

and still no dvd menu in totem. VLC flashed teh menu up for a bit and then jumps to the 1st program

---

### Post by ad_267 on 2008-06-15
Have you run this?
```
sudo apt-get install build-essential debhelper fakeroot
sudo /usr/share/doc/libdvdread3/install-css.sh
```

From [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by notidefix on 2008-06-15
yes. And libdvdcss2 is already installed through the process described in: [http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

Is this a common problem for 8.04? My last installed verion was 6.10 and I cannot recall any problems with such trivialities.....

---

### Post by ad_267 on 2008-06-15
> **notidefix said:**
> yes. And libdvdcss2 is already installed through the process described in: [http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

Is this a common problem for 8.04? My last installed verion was 6.10 and I cannot recall any problems with such trivialities.....

I didn't do anything with medibuntu, I just followed the steps outlined in the link above and dvd playback works fine in 8.04 for me.

---

### Post by notidefix on 2008-06-16
the medibuntu link and yours end up in the same place: download and install libdvdcss2

in the end I installed totem-xine, which works with DVD menus

[https://bugs.launchpad.net/totem/+bug/219838](https://bugs.launchpad.net/totem/+bug/219838)

seems a reported and accepted bug - just not assigned or actioned yet....

---

### Post by lukjad on 2008-06-18
This is becoming quite a popular thread! I have now gone over to Ubuntu Studio in hopes that since this is a VIDEO editing suite it would work better with, y'know, VIDEOS! Well, no, it doesn't. The problems are the same, actually worse since I had to start from scratch. (They don't even have OpenOffice!) Well, Notidefix, I did the same as you and found that it didn't help me. But, then again, perhaps it's a hardware problem. How old is your PC? I have read of a bug of this type all The way back to at least Feisty Fawn.
[http://ubuntuforums.org/showthread.php?t=233860](http://ubuntuforums.org/showthread.php?t=233860)
[http://ubuntuforums.org/showthread.php?t=432197](http://ubuntuforums.org/showthread.php?t=432197)
ryP seems to have found the workaround for movie _clips_. However, movies are still a problem. I thought that I should give him a plug here since his hint did help me with this problem. My other workaround is this:

1)   Download a version of Puppy Linux. (I suggest TEENpup-> [[http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/TeenPup-31563.shtml]](http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/TeenPup-31563.shtml]))

2)   Burn the .iso to disk (I use k3b but for those who don't want to bother-> [http://ubuntu-tutorials.com/2007/03/15/how-to-burn-an-iso-image-in-3-clicks-cd-or-dvd/](http://ubuntu-tutorials.com/2007/03/15/how-to-burn-an-iso-image-in-3-clicks-cd-or-dvd/))

3)   Insert CD into the bootable optical drive

4)   Reboot

5)   Pop in your DVD an watch it!

More to come. I just a few minutes so popped this in. See you soon!

---

### Post by lukjad on 2008-07-13
Coming back to the problem at hand, I tried to fix it by deleting the hidden files pertaining to the playback of DVDs but that didn't work either. I was wondering if the other people who have this problem might all have older PC and therefore do not have the resources necessary to crack the encryption on the disk. Do any of you that have older PCs and are running Hardy Heron have this problem?

---

### Post by cor2y on 2008-08-17
Almost 2 months late to the party.
I ran into this with a copy of Blade Trinity i bought second hand (its a region 2 disc)
Apparently the reason this is happening is because of deliberate bad sectors on the dvd put there to stop copying (not too good since you can actually copy the disc fine) these bad sectors confuse libdvdread and thats where the error comes from.
To fix it you need to either patch libdvdread or use a version from debian sid unstable.
I recommend you install both the dev and non dev versions of libdvdread ,if you compile your media players like mplayer vlc etc, you will have to recompile them to get them working with this version of libdvdread.
After doing this mplayer was able to fully play the disc without an error as did vlc.

Edit
For the curious on which dvds are affected.
Region 2 dvds produced by New Line and Universal Studios

---

### Post by standingOnMyTipToes on 2008-08-17
...I installed Ubuntu 8.04 yesterday and VLC is working fine? But I did a clean install....

---

### Post by musarraf172 on 2009-12-12
I have never found the play back control of DVD i.e the menu options working since my ubuntu 8.10 ..

VLC, Mplayer or totem they just directly play the movie. Totem is jerky but VLC plays fine. The same DVD works fine in windows.:(

---

