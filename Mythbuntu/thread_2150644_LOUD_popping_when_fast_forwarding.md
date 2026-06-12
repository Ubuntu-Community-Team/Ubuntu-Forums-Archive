---
title: "LOUD popping when fast forwarding"
date: 2013-06-01
forum: Mythbuntu
---

### Post by splg on 2013-06-01
I have mythbuntu 12.04 running mythtv .26 (updated just a few days ago with all the latest patches). The issue is about 5% of the time when I use the arrow keys to either fast forward or rewind I get a LOUD snapping/popping sound. I use the arrow keys in place or the < and > keys to skip around recorded shows because it's more convenient for me to hit the back arrow key or forward arrow key repeatedly rather then hit the < or > keys once and then hit play.  I'm pretty sure one day it's going to really damage my speakers (if it hasn't already).

I first thought it was the video card and/or the HDMI cable that goes to the AVR so I swapped the card/cable for different models and brands. Then I thought it was the keyboard so I changed that too. Needless to say it's still happening and wondered if anyone experienced it (or if anyone could replicate that when watching a recording). Just a warning it will be loud so keep your volume low.

I know that I can just use the other keys but I'd love to figure out if anyone else has this issue or any remedy.

Thanks

---

### Post by BicyclerBoy on 2013-06-02
This was always a common occurrence with older myth versions ..(loud shrieking hiss)
It happened more commonly wth latm-aac.
I have always used the keyboard left right arrow keys to navigate..

I think the noise/breakup was caused or made worse by incorrect seektables (mythtv creates incorrect seektables for H264 recordings).

Try to regenerate the seektable with:
mythcommflag --rebuild --file <your-recording>
& then try to play recording..

It can be fixed (& seeking errors with patch on mythtv trac).

---

### Post by splg on 2013-06-03
Thanks for the tip! I want to try this soon but finding the file name that goes with a specific recording is a bit of a pain. I found a script (mythlink.pl) but not sure if I can use it on a per case basis. I'd like to leave things as is (with the names) for now but definitely want to try the mythcommflag command to see if it fixes this.

Maybe something simpler would be to correct the bug. I've done some searching but not sure which patch I'd need. I uses the hdhomerun prime as my tuner. Doing a search brings up a lot of mythtv trac related fixes.

---

### Post by BicyclerBoy on 2013-06-03
From the recording screen hit <i> key twice..
Write down the recording name..use this with terminal

or setup a user-job in mythtv-setup..
mythcommflag --rebuild --%FILE%

But this may not really help because the same code-path (dtvrecorder/H264Parser) is used & this is not working right.

I have several HDHR samples & all that play/seek precisely & with no audio or video noise, no macroblocking or pixelization.
trac ticket 11435
Patch works in 0.26 or 0.27.

As a work around you could try change your audio output between PCM & AC3 or use the internal AC3 encoder..

---

### Post by splg on 2013-06-05
So that's where they hide the filename! I'd be nice if this info was in mythweb too but that's neither here nor there :).  I will try this and let you know. I'm not sure if I mentioned this earlier but the audio is actually perfect during playback. The audio popping only happens (sometimes) when I use the arrow keys to skip around. I'll report back with what I find.

---

### Post by splg on 2013-06-07
The rebuild didn't solve the issue. I ran:

$ mythcommflag --rebuild --file /full/path/to/file.mpg
2013-06-07 07:17:39.319031 C  mythcommflag version: fixes/0.26 [v0.26.0-171-gbfd2408] [www.mythtv.org](www.mythtv.org)
2013-06-07 07:17:39.319042 C  Qt version: compile: 4.8.1, runtime: 4.8.
...
2013-06-07 07:18:04.976368 E  decoding error
			eno: Unknown error 541478725 (541478725)
Rebuild completed at Fri Jun 7 07:18:05 2013

I read that the error may not be bad but it gets about 70% through, errors and says it's completed. Is there anything else I can try or does the Homerunhd just produce files that have these sorts of problems?

---

### Post by BicyclerBoy on 2013-06-08
Shame it didn't help..
What output format (audio) do you use over HDMI ? PCM or AC3 ?
I don't recall ever having extra noises with AC3 over spdif.

If mythcommflag exits at a point != 100% then this can mean the original recording seektable is wrong or has wrong duration.

you don't need the /full/path/to/file if the recording is in a storage group..just file.

I haven't noticed hissing or popping noises with samples of HDHomerun recordings..but the focus was on video parsing/decoding.

You're not trying to use pulse audio are you ?
Try an alsa device in myth..

---

### Post by splg on 2013-06-10
How would I be able to determine if I'm using PCM or AC3? I didn't see it in the audio setup on the frontend. My audio dev is Alsa:HDMI:Card so I don't believe pulse audio is being used.

Also after I run the mythcommflag --rebuild command, shouldn't a file that was exiting at 70% complete at 100% if I run the command twice? Running the command on the same file gives me the same < 100% result when it finishes the rebuild.

---

### Post by Akriss on 2013-06-16
Hello,

I had a similar issue a wile back, audio pops and such.

What it turned out to be was my audio buffers where set to low. 

At the time there was little info on how go about remedying it. However another MythTv user has a very good page with a working solution with easy to follow steps.

 The web page is [[COLOR="#0000FF"]_HERE_[/COLOR]]("http://www.baablogic.net/drupal/node/21")

I hope it helps.

---

### Post by splg on 2013-06-19
I've looked through the logs and echoed that value into the config however it did not work. Every so often when I use the arrow keys to skip around it "pops". At this point, I think i will use the < and > keys instead of jumping forward or back a few seconds at a time.

Thanks for the help though!

---

