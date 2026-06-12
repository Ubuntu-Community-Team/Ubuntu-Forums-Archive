---
title: "Cut and sync for H264 recordings - Project X replacement?"
date: 2013-02-13
forum: Multimedia Software
---

### Post by ceejay on 2013-02-13
Hi

For many years I have been recording UK Freeview programmes - most recently with MythTV - and then post-processing them into usable .mpg files for viewing on a variety of devices. This involves simple cutting (front, back and ads) but also (critically!) getting the audio in sync.

Project X has been doing that job for me for many years and I've got very used to it!

However, I have just upgraded to a new tuner which can record HD broadcasts, and Project X can't handle them as they are in H264 format.

What replacement tools should I be looking at?  Audio sync is critical...

TIA

---

### Post by BicyclerBoy on 2013-02-16
How about a user-job/script that runs from mythtv..The cutlist editor of mythtv is second to none..

There is the very polished "losslesscut" (outputs mkv file)

There are a few cutting scripts around that utilise mkvmerge or ffmpeg or avidemux.

They all have their limitations of output formats, transcoding lossing streams , can't handle LATM AAC.

The latest avidemux is now time based & works with H264 etc.
ffmpeg now has a workable cutlist format.

The fastest totally lossless method I have found is the not so polished MythCutKey..
[https://gist.github.com/BipedalTV/3174241](https://gist.github.com/BipedalTV/3174241)

Because of the fact that video packets precede audio you will loss a little audio at the end of cut piece if you cut too close..
So the "cut ends" need to be 2 sec early.

Any good player has no problem with PTS/DTS discontinuities of a cut ts file.

Note: there have been some very important recording fixes in 0.26+fixes & 0.27 of late..

---

### Post by ceejay on 2013-02-24
Hi 

thanks for the response, sorry I've been late in acknowledging (have been busy fixing an unrelated problem!)

Apologies if I am misunderstanding anything here, this isn't an area I know well (hence asking for help!)

There are two things about my current process that I really don't want to lose.

The first is that all the cutting and processing is lossless, and the most important thing about that is speed. It means I can completely process a video of multiple GB in a small number of minutes, rather than having to wait for my (not highly powered) backend to chunder for hours while transcoding.

The second is that I end up with a properly synced output file which I can play on ANYthing... and not be dependent on a player being able to resync audio, or understanding a TS format. Of course, if I want no transcoding then I have to accept the limitation of players being able to play H264!

And, as far as I know, mythtranscode doesn't work with H264 yet?

Still puzzled but grateful for the help so far....

---

