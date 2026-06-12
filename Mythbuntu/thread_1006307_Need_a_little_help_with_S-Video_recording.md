---
title: "Need a little help with S-Video recording"
date: 2008-12-09
forum: Mythbuntu
---

### Post by Tarrasque on 2008-12-09
Hello everybody.

Please pardon me if it's a stupid question, but I've been trying to find the answer myself on the wiki and honestly, English is not my native language, and I'm a complete newbie to linux tv and encoding, so I need some more help...

I've set up MythTV on an already running Ubuntu 8.04 machine following instructions on the web. Everything seems to be OK. The card is a Hauppage PVR-350. I'm able to watch Live TV and I can watch input from the S-Video connector.

What I really need to do with MythTv is actually capture analog video from the S-Video (or Composite) input in order to backup a my VHS and then edit the video with Kino or something.

The problem is that I think haven't understood well how the heck video recording works with MythTv. I tried to press "R" and it says it starts recording. But how do I stop it? I see the video file keeps growing even after I exit the frontend (which I suppose is good if you are recording a TV show and then go to bed).

All I need is a way to "press record" when I want to record video from the tape, and "press stop" when I want to stop. Is there an easy way to do this?

Heck, is there even a DIFFICULT way to do this? I wasn't able to stop the recoding when I tried at all. I had to shut down the computer! :P:P:P

Thank you very much.

---

### Post by EasyRiderOnTheStorm on 2008-12-09
I found [[this]("http://www.mythtv.org/wiki/index.php/S-Video/Composite_Input_Recording")] about recording inputs with MythTV. It doesn't say anything specific about ending the recording, but in my experience changing away to another channel starts recording in a new file under LiveTV (only as long as you keep watching it), ie. stops considering the new channel as "being intentionally recorded"...

---

### Post by Tarrasque on 2008-12-09
That's almost exactly what I did to configure MythTv in order to record from S-Video.

I just didn't bother to set channel numbers for the two video sources.

Sweet. It seems I'm not as bad as a newbie as I thought!! :P:P

Anyway, this doesn't solve the "stop record" issue. I mean, if recording continues even after i exit the frontend, how can I stop it? Do I have to kill the backend?

---

### Post by SiHa on 2008-12-09
As EROTS mentions, Myth automatically records the currently displayed video under the LiveTV group. If you tune to a different channel, or just stop watching, then it 'should' stop recording that input.

---

### Post by EasyRiderOnTheStorm on 2008-12-09
As I said, I don't think MythTV keeps recording even after you "exit recording", if you change away from the actually recorded source first. Either by changing the channel (if you have your source set up as a TV channel) or by changing capture input or card by "c" or "y" keys, if I remember correctly. Of course, I could be wrong about all this. Have you tried it like that?

---

### Post by Tarrasque on 2008-12-09
Let me think...

I used "c" to change "channels" (Live TV or S-Video). I pressed "r" and the OSD told: start recording"" (the two quotes appeared on screen as I wrote them).

Then, frankly, I don't remember whether I exited the frontend after switching again or not. Tonoght I'll try again.

Still, I got the mechanism that MythTv silently records everything while you watch (this is necessary for pausing and rewinding and all).

But from the moment I press "r" which means "ok, I really want to keep this program I'm watching", how can I just tell MythTv "the program finished" so that I can export the video to some other place for editing?

---

### Post by EasyRiderOnTheStorm on 2008-12-09
MythTV doesn't really work on the concept of "OK, stop recording NOW". Pushing the record button merely flags a recording that already existed anyway as "keep this". In normal TV recording, MythTV takes his cues of how much to record from the program guide (which obviously does not exist for a capture input), or records in 30 min. slabs if that's not available. That's why it records even the stuff you were watching **before** you pressed "record". Therefore, I assume the only way to make it stop recording a capture input would be to switch away from it. 

However, SiHa is correctly pointing out that you **don't actually need to press record** at all; Even if you just "watch" the stuff you want recorded, you'll find it recorded under LiveTV. And if you did not press record, MythTV will certainly stop recording when you exit "watching TV".

...if it's really short, that is. I think MythTV keeps only about 30 mins. of "just watched" stuff, unless you really **do** press record.

---

### Post by Tarrasque on 2008-12-09
Well, since I'm backing up old VHS, those go up to 4 hours.

So, if I get it straight, the only way to do what I want is pressing "r" and then wait until the tape is over, and then switch to another channel?

And then I'll get my videos in 30 min pieces on the hard disk? Well, not the most intuitive thing, but if there's no other way to do it I'll live with this for the moment.

Thank you all very much, I'll try as soon as I can if this works.

---

### Post by SiHa on 2008-12-09
> ...if it's really short, that is. I think MythTV keeps only about 30 mins. of "just watched" stuff, unless you really do press record.

Well, I often get home and find the wife has left the FE in the bedroom on after Neighbours (!) and there's 5 or so hours of live TV. It will be split up into programmes as per the EPG, but I guess if there isn't one (as in your case) it should just stick it in one recording. As far as I know, Myth will keep recording LiveTV until either:

You exit 'Watch TV'
The HDD runs out of space - and even then it'll try to auto-expire old stuff to make room.

4 hours should be no problem, I reckon

---

### Post by ###Nick on 2008-12-09
Not quite a mythtv solution, i tend to stop the back & front end and use the terminal to capture the video.  Then chop it up and put it in my myth videos folder to use in myth.

In a terminal something like:
# set input to s-video
v4l2-ctl --set-input 1
# record (background process
cat /dev/video0 > /path/to/record/to/filename.mpg &
# stop recording
ctrl-c  

this can be done as a script to start recording and stop after x amount of time.  Have a look in the ivtvdriver.org examples page.
[http://ivtvdriver.org/index.php/Example_script_to_schedule_recordings]("ivtv example scripts")

hope this helps.

---

### Post by Tarrasque on 2008-12-10
> **###Nick said:**
> Not quite a mythtv solution, i tend to stop the back & front end and use the terminal to capture the video.  Then chop it up and put it in my myth videos folder to use in myth.

In a terminal something like:
# set input to s-video
v4l2-ctl --set-input 1
# record (background process
cat /dev/video0 > /path/to/record/to/filename.mpg &
# stop recording
ctrl-c  

this can be done as a script to start recording and stop after x amount of time.  Have a look in the ivtvdriver.org examples page.
[http://ivtvdriver.org/index.php/Example_script_to_schedule_recordings]("ivtv example scripts")

hope this helps.

I will surely try this next time. I'm not scared of a little CLI. ;)

Anyway, I tried last night to record something "the mythtv way". I went to Watch Tv and it began recording the source as usual.

Then I tried various things. If I press "r" I noticed that I cannot change channel anymore, if I exit Watch Tv it keeps recording and if I get back to Watch Tv it asks me to "connect" to the ongoing recording (logical, since I only have one tuner).

If I then press "r" again to cancel the recording and then change channel, the old .mpg file seems to remain on disk anyway, so I think it could work.

Of course the CLI method seems to be much better, since I can choose to capture just the pieces of video I wish.

P.S. for some strange reason, the input i get from S-Video is black and white (Tuner source is OK). I think I set MythTV to PAL correctly (recorded video is 25 frames).

The source I'm making tests with comes from an hard disk player (I still have to set up the real VCR) with an Euro SCART connector, so I have a connector that "should" convert to 2 RCA for audio and S-Video for video (the PVR-350 does not have a RCA video input).

Could it be some known kind of cable problem?

---

### Post by EasyRiderOnTheStorm on 2008-12-11
> **Tarrasque said:**
> P.S. for some strange reason, the input i get from S-Video is black and white (Tuner source is OK). I think I set MythTV to PAL correctly (recorded video is 25 frames).

The source I'm making tests with comes from an hard disk player (I still have to set up the real VCR) with an Euro SCART connector, so I have a connector that "should" convert to 2 RCA for audio and S-Video for video (the PVR-350 does not have a RCA video input).

Could it be some known kind of cable problem?

Are you sure your HDD player does output S-video? S-video carries color on a separate wire, so it may well be either a cable/adapter problem or a complete lack of true S-video signal at the source. You might also try to view the same source as if it were a Composite source, see if it gets you any color.

---

