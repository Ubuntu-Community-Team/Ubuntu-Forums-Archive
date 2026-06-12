---
title: "Suddenly cannot play several old recordings"
date: 2009-06-12
forum: Mythbuntu
---

### Post by bcg30506 on 2009-06-12
I have several old recordings saved on my backend that have been playable for quite some time.  Suddenly today I tried watching one and got a black screen for a second or two then it exited back to the Watch Recordings screen.  I see this in the mythfrontend.log:

Couldn't find a matching decoder for: <path stuff>.mpg

The files are fine and can be played both with mplayer and from another frontend machine in our house over the network.  They only won't play on the combined backend/frontend machine that is connected to the family room TV.  Most other recordings still can play.  There are no differences in the files that play and won't play as they were all recorded on this machine using the same PVR-150 cards in mythtv.  I do not know exactly when they stopped playing as I haven't tried in a few months.

I'm running mythbuntu 9.04 with mythtv version 1:0.21.0+fixes-20674-openglvdpau-0ubuntu0 and nvidia driver version 185.18.14-0ubuntu3.

The machine containing the frontend that CAN play them all fine is a Mac running mythfrontend 0.21.20080304-1 exported.

---

### Post by klc5555 on 2009-06-12
> **bcg30506 said:**
> I have several old recordings saved on my backend that have been playable for quite some time.  Suddenly today I tried watching one and got a black screen for a second or two then it exited back to the Watch Recordings screen.  I see this in the mythfrontend.log:

Couldn't find a matching decoder for: <path stuff>.mpg

The files are fine and can be played both with mplayer and from another frontend machine in our house over the network.  They only won't play on the combined backend/frontend machine that is connected to the family room TV.  Most other recordings still can play.  There are no differences in the files that play and won't play as they were all recorded on this machine using the same PVR-150 cards in mythtv.  I do not know exactly when they stopped playing as I haven't tried in a few months.

I'm running mythbuntu 9.04 with mythtv version 1:0.21.0+fixes-20674-openglvdpau-0ubuntu0 and nvidia driver version 185.18.14-0ubuntu3.

The machine containing the frontend that CAN play them all fine is a Mac running mythfrontend 0.21.20080304-1 exported.

A guess, the affected old recordings (on an older mythbuntu) may have been recorded at a resolution that your current frontend installation and playback profile might have trouble with. Just as a test, try using a different playback profile on them, particularly one like "Slim" that doesn't refer to "xvmc" anywhere.

If the recordings now play, but the playback profile isn't one you want to use permanently, a simple lossless transcode with mythtranscode --mpeg2 usually renders the recording usable again.

If testing on different playback profiles doesn't give you a successful playback, then the problem must be something else on the frontend.

Good luck. :)

---

### Post by bcg30506 on 2009-06-12
Thanks, klc, but unfortunately I don't think that is the issue.  All my recordings, old and new, were done at the same resolution on the same box with the same mythbackend setup.  Plus I am already using the Slim profile to play them all and have been for quite some time.

---

### Post by klc5555 on 2009-06-12
> **bcg30506 said:**
> Thanks, klc, but unfortunately I don't think that is the issue.  All my recordings, old and new, were done at the same resolution on the same box with the same mythbackend setup.  Plus I am already using the Slim profile to play them all and have been for quite some time.

OK, sounds good.

You might, however, still want to see whether a lossless transcode renders one of the affected recordings playable by myth's current internal player. Could be a flaw, sound or other, in the affected recordings that doesn't bother older/other myth 0.21 installations, but is stopping your current frontend. A type of flaw that mythtranscode is good at fixing.

So, having found one of the affected files: <filename>.mpg you can use: mythtranscode --mpeg2 --showprogress -i <filename>.mpg

Then rename <filename>.mpg to <filename>.mpg.old; and rename the new <filename>.mpg.tmp to <filename>.mpg

And see whether this newer <filename>.mpg is playable by the frontend.

---

### Post by bcg30506 on 2009-06-12
Bingo!  You are right on the money.  Here is the log from when I tried playing a problem recording on the main frontend:

2009-06-12 11:43:41.708 TV: Attempting to change from None to WatchingPreRecorded
2009-06-12 11:43:41.710 DPMS Deactivated 
2009-06-12 11:43:41.716 NVP: Couldn't find a matching decoder for: /monolith/tv/1033_20080702130025.mpg
2009-06-12 11:43:41.717 TV Error: StartPlayer(): NVP is not playing after 20000 msec
2009-06-12 11:43:41.717 TV: Changing from None to WatchingPreRecorded
2009-06-12 11:43:41.718 TV: Attempting to change from WatchingPreRecorded to None
2009-06-12 11:43:41.724 TV: Changing from WatchingPreRecorded to None
2009-06-12 11:43:42.059 DPMS Reactivated.

Then I ran this:

mythtranscode --mpeg2 --showprogress -i 1033_20080702130025.mpg
mv 1033_20080702130025.mpg 1033_20080702130025.mpg.old
mv 1033_20080702130025.mpg.tmp 1033_20080702130025.mpg

After which the frontend on my TV played it fine!  Here is the log for it working after doing the lossless transcode:

2009-06-12 11:43:13.950 TV: Attempting to change from WatchingPreRecorded to None
2009-06-12 11:43:14.005 TV: Changing from WatchingPreRecorded to None
2009-06-12 11:43:41.708 TV: Attempting to change from None to WatchingPreRecorded
2009-06-12 11:43:41.710 DPMS Deactivated 
2009-06-12 11:43:41.716 NVP: Couldn't find a matching decoder for: /monolith/tv/1033_20080702130025.mpg
2009-06-12 11:43:41.717 TV Error: StartPlayer(): NVP is not playing after 20000 msec
2009-06-12 11:43:41.717 TV: Changing from None to WatchingPreRecorded
2009-06-12 11:43:41.718 TV: Attempting to change from WatchingPreRecorded to None
2009-06-12 11:43:41.724 TV: Changing from WatchingPreRecorded to None
2009-06-12 11:43:42.059 DPMS Reactivated.

Here is the output of du -h on the old and new files that show the size is basically the same so it truly was lossless:

73M     1033_20080702130025.mpg
73M     1033_20080702130025.mpg.old

Thanks a bunch!  Now one final question:  Can this process be done in the myth GUI using my remote by selecting Job Options, Begin Transcode, High Quality - which I have setup to do lossless mpeg2-to-mpeg2 for commercial cutting?

---

### Post by klc5555 on 2009-06-12
> **bcg30506 said:**
> 

Thanks a bunch!  Now one final question:  Can this process be done in the myth GUI using my remote by selecting Job Options, Begin Transcode, High Quality - which I have setup to do lossless mpeg2-to-mpeg2 for commercial cutting?

Should work fine, assuming there's no cutlist on these recordings for the --honorcutlist flag to chew on, or, if there is a cutlist, it's set up the way you want it.

Otherwise, you can just set up another user job for this operation, and every time you run across a funky recording, you can just drop it into the Job Queue from Job Options.

Glad you're back in business!

Cheers! :)

---

### Post by bcg30506 on 2009-06-12
Good idea about the job queue, but I have one simple question: how?  I'm embarrassed to say I've never setup a user job in myth before.

[EDIT]
Ok, I may have figured it out by reading the wiki on mythtv's site.  I'd like someone more experienced to confirm if this is correct or not before I screw things up.

I used the mythweb interface and filled in these fields with what is shown:

UserJob2  =  /home/mythtv/scripts/losslessXcode %DIR%/%FILE%
UserJobDesc2  =  Lossless MPEG-2 transcode to fix playback

Then I created this script in the scripts directory of my user's home directory:

#!/bin/bash
mythtranscode --mpeg2 --showprogress -i $1
mv $1 $1.old
mv $1.tmp $1

and finally I made it executable with:

chmod +x ~/scripts/losslessXcode

It seems from the wiki that since I used mythweb I have to restart the backend for this to take effect.  So is this all right or am I missing something or doing something wrong?

---

