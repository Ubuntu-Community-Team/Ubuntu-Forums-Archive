---
title: "No sound from Audio CDs"
date: 2007-10-02
forum: Multimedia &amp; Video
---

### Post by auquicu on 2007-10-02
Installed Ubuntu. The system itself is working fine. The desktop is a failure so far, maybe Ubuntu does not like my video card. But this thread is about the sound.
(So, please, if you give good advice: I only have a command line available.)

Sound itself works: a command like "play foo.wav" or "play bar.mp3" produces sound.
But I cannot play Audio CDs.

The machine came without the usual cable connecting CDROM drive and sound card,
and I added one, but that doesnt help.

Commands like "cdplay" or "cdcd" or "mplayer cdda://" see the CD, are willing to list
the tracks of the Audio CD and tell that they are playing it, but there is no sound.

---

### Post by greenstar on 2007-10-02
Open a terminal and do:

alsamixer

Check to see if CD is enabled.

Greenstar

---

### Post by auquicu on 2007-10-02
> **greenstar said:**
> Open a terminal and do:

alsamixer

Check to see if CD is enabled.

Greenstar

Thanks for replying. I do, and see a very wide window with 21 columns. Many of these columns have a vertical bar that is partly white and partly green. Below the bar a label in white-on-blue and digits in yellow. The very first column is labeled <Headphon> in red-on-blue, and no bar. The column labeled CD shows the number 74 (and the white/green bar). The last three columns are labeled "Input So" in white-on-blue and show, not a bar, but the yellow texts "CD", "Line", "Mic", respectively. The CD column (and most other columns) show white-on-green OO (and only the IEC958 column shows MM, presumably for muted). The top left corner of the window shows

Card: HDA Intel                                                                                                                                                                                                                                   
Chip: Analog Devices AD1988                                                                                                                                                                                                                       
View: [Playback] Capture  All                                                                                                                                                                                                                    
 Item: Headphone

This suggests that the current window output might be for "Headphone". If I use the Tab key this choice cycles between "Headphone", "Front Mic Boost" and "Front Mic Boost Capture".

I do not know how to "check whether CD is enabled" but at least it seems that CD is not muted.

---

### Post by greenstar on 2007-10-03
Go to:
System->Preferences->Sound

On the devices tab, Find the Music and Movies section. Test the curent selection by clicking <Test>. If no sound is produced, make a different selection from the option box and test again. While you're in there, test the other categories also.

Also, make sure your cable from sound out to speaker in is in working order and plugged into the correct jack. The sound out jack is usually lime green, but might be black or even another color and almost always has a hard-to-see symbol next to it. If you're lucky it may just say Audio Out. The symbol looks something like this:
[ATTACH]45180[/ATTACH]

---

### Post by auquicu on 2007-10-03
(Hmm It seems difficult to reply - I get thrown out repeatedly, have logged in at least six times.)

You advise "Go to: System->Preferences->Sound ..." but unfortunately, as I said: " I only have a command line available".

In the meantime I have upgraded to current Gutsy and that solves a few problems. In particular "mplayer cdda://" now also works.

So, right now the part of sound handling that involves AudioCD -> digital data and digital data -> sound seems to be fine and in working order. What I still cannot do is use the direct line from the CD reader to the sound card. In other words, cdplay and cdcd fail.
(They say that they are playing, list which track is being played etc, only - no sound.)

---

### Post by yabbadabbadont on 2007-10-03
If possible, try plugging a set of headphones into the front of the CD drive and see if that produces output.  I'm pretty sure that the headphone jack on the front of the drive only works when a CD is being played normally and not in DAE mode.  It should at least prove/disprove if normal CD audio is working at the drive level.

Edit: If it does work, then I would see about getting a different audio cable and/or try plugging it into another jack on the sound card (if possible).  Also, if the cable isn't keyed, most are these days, try rotating one of the connectors 180 degrees.  I once came across a cable that had been wired incorrectly.

---

