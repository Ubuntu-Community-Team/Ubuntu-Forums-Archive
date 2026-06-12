---
title: "Getting my PVR-350 up and running"
date: 2008-01-12
forum: Mythbuntu
---

### Post by debest on 2008-01-12
So, after much searching of the archives here and on other sites, I am stumped.  (Disclaimer: I am only a shade better than a noob, so bear that in mind with assumptions about my expertise.)

Relevant info:
[LIST]
[*]Kubuntu Gutsy
[*]Hauppauge PVR-350 (works under WinXP)
[*]"older" system (1GHz Athlon, 1GB RAM, GeForce FX)
[/LIST]
The IVTV driver appears to have installed correctly (via the Mythbuntu packages in the repositories), with /dev/video0 assigned to the MPEG encoder on the PVR-350 (which seems to be the correct default behaviour).

Forgetting MythTV for a second, I just wanted to verify if I could record the input from my VCR/DVD player to the capture card (I haven't been wired for cable TV yet).  The standard way of testing this seems to be
```
cat /dev/video0 > test.mpg
```
for a little bit while playing something on the VCR.  I got an empty file for my trouble (a file titled "test.mpg" with a size of 0B).

I looked around a bit, and wanted to make sure that the VCR's signal was at least getting through.  I typed this:
```
ivtv-tune -c 3 /dev/video0
```
to make sure the card was tuned to Channel 3, and got back:
```
/dev/video0: 61.250 MHz (Signal Detected)
```
which seems to indicate that the card is seeing the signal.

So, what's up?  Anyone got any ideas of anything else I should try?  Thanks.

---

### Post by debest on 2008-01-13
Alright, so while I've been waiting for a reply on this, I went ahead with installing MythTV through the guide provided [here]("https://help.ubuntu.com/community/MythTV_Gutsy_Backend_Frontend_Desktop").  I got as far as "Video sources", since this is for programming info (as noted before, I've get to get my cable TV installed).

Is there any way to use MythTV as a way to test recording from a VCR?  Do I just set "Channel 3" somehow in the Video Sources screen?  I'm not confident that anything will happen, but I'd like to hear some thoughts.  Thanks.

---

### Post by Nimda1000 on 2008-01-13
Have you done this stuff?

[https://help.ubuntu.com/community/MythTV_Gutsy_hardware_pvr-350_TV-out](https://help.ubuntu.com/community/MythTV_Gutsy_hardware_pvr-350_TV-out)

Do all the tests work?

Let me know if you have done this, if you have, check the 2 bottom posts about a commonly ooops'ed setting messing up a number of pvr-350 users:

[http://ubuntuforums.org/showthread.php?t=641686](http://ubuntuforums.org/showthread.php?t=641686)

Nim

---

### Post by debest on 2008-01-13
Thanks for the reply!

> Have you done this stuff?

[https://help.ubuntu.com/community/My...pvr-350_TV-out](https://help.ubuntu.com/community/My...pvr-350_TV-out)
Hmmm, this article seems to be about getting the PVR-350's **decoder** to the TV-out working (something that, while cool, I don't need to get working yet).  Early in the article, it states "You should have the Gutsy version of Mythbuntu (or Gutsy and MythTV) up and running before attempting this howto."  The other post seems to be about the same topic.

My problem is that I have not yet got the **encoder** working yet (getting anything into the card, as opposed to out of it).  I suppose that my issue would be identical if I was using a 150, 250, or 500 card.

(I changed the Title line for clarification.)

I'm still futzing with it, not giving up yet!  Any other suggestions are appreciated.  Thanks.

---

### Post by debest on 2008-01-13
Alright, so I complete the Mythbackend setup, putting in a single channel (Channel 3) from my VCR/DVD.  Then I go to Mythfrontend, select "Watch TV", and holy old baldy, I see the tape playing on the computer!  I can record by "scheduling" an extra long time frame, hitting play, then (I suppose) trim off the start and the end.

So, I guess this is solved, but I still don't see why the "cat /dev/video0 > test.mpg" didn't work (I still get an empty file when I do this).

Oh, and the picture is really grainy, too, so I guess I have more work to do!  Thanks!

---

