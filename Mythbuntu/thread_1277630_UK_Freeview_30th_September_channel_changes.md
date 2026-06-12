---
title: "UK Freeview 30th September channel changes"
date: 2009-09-28
forum: Mythbuntu
---

### Post by gwagchunks on 2009-09-28
Hi Everyone

Do you think that this will affect channels for capture cards, ie. like my nova td-500 dvb card?

[http://www.dailymail.co.uk/sciencetech/article-1216567/Freeview-shake-means-25million-retune.html?ITO=1490&referrer=yahoo](http://www.dailymail.co.uk/sciencetech/article-1216567/Freeview-shake-means-25million-retune.html?ITO=1490&referrer=yahoo)

Cheers

---

### Post by SiHa on 2009-09-28
We'll almost certainly have to retune. I did after the reshuffle last year.

Pain in the @rse.

---

### Post by fatmonk on 2009-09-29
No reason for a DVB-T MythBox to behave any different to any other DVB-T receiver in this respect, so yes anyone receiving UK digital terrestrial broadcasts (FreeView) will have to retune.

Grrrr,

FM

---

### Post by gwagchunks on 2009-09-30
Thanks for the replies

Is it a matter of deleting all the channel into and then re-scanning? I won't be in front of my machine until late tonight, so I can't remember what to do! Sure I'll work it out?! Fingers crossed!

---

### Post by SiHa on 2009-09-30
From memory, last time we had to do this, I had to delete the video source then created a new one, and rescan. You might have to go through your scheduled recordings, as well, because they may have moved onto different channel numbers.

---

### Post by gwagchunks on 2009-09-30
> **SiHa said:**
> From memory, last time we had to do this, I had to delete the video source then created a new one, and rescan. You might have to go through your scheduled recordings, as well, because they may have moved onto different channel numbers.

Good call, Thanks SiHa. I'll have a look tonight and report back! Cheers.

---

### Post by SiHa on 2009-09-30
Think I'm going to be doing much the same...

---

### Post by howefield on 2009-09-30
Just retuned, don't seem to have lost anything, (at least, no channel I used) the only one I don't recognise is QUEST. Currently showing an old Police Academy film.

---

### Post by SiHa on 2009-09-30
I'm on the Rowridge transmitter, and lost at least channel 5. As my wife religiously records Neigbours every day I had to do a re-scan.

I have a Hauppauge Nova-T PCI (Single Tuner) and a Nova-T 500 (Not the -TD).
I found (and seem to remember now I had this last time as well) that I had to go back to the start and delete the capture cards. Just rescanning with the existing cards defined did nothing, I got the scanning for channels sceen, but no actual scanning window showing singnal strength etc.

After the scan all the channels are mixed up because last year they decided to give some of them 5-digit numbers, so I had to go into the channel editor to re-number them and remove all the chaff like bid-up tv.

If you want an easy way to renumber them, have a look at [[COLOR="Blue"]this[/COLOR]](http://ubuntuforums.org/showthread.php?t=914136) thread for a script to automatically do it. It's a bit outdated though, and some of the channel names have changed.
It only takes about 10mins with the channel editor. I just copied the numbers down from the guide on the TV and used those, most haven't changed, but there's one funny: ITV2 is on Channel 6, and Channel 33 is listed as 'ITV', but it's actually ITV2+1.

---

### Post by Neon Dusk on 2009-09-30
Are you using 0.21-fixes?

The freeview channel numbering bug ([link](http://svn.mythtv.org/trac/ticket/6040)) was fixed quite a while back (it was using the transport ID instead of the LCN).

---

### Post by SiHa on 2009-10-01
I had a feeling it had probably been fixed, after I posted the last statement. However, I am firmly of the "If ain't broke don't fix it" mentality.
This forum, and many others are littered with "it was working till I updated..." style posts. Unless I have a damn good reason to update something I won't. Myth has been stable for me for over a year now, and I don't want to trash the WAF.

I will be uptating to 0.22 for the new improved UI and VDPAU, but I plan on sticking to 8.04(1). I don't want to spend weeks trying to sort out the firmware on my Nova-T-500, or trying to figure out RTC wake on the newer kernel, or get resume from suspend working on the frontend, or get X to output to the DFP regardless of whether the TV is on, or all the other things that I spent several months on last year...

Anyway, it's nice to know I won't have to manually sort the channels when I install 0.22.

Cheers,

Simon

---

