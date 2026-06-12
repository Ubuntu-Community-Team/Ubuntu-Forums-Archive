---
title: "MythTV Sound Encoding Problem"
date: 2007-03-12
forum: Multimedia &amp; Video
---

### Post by josesanders on 2007-03-12
I've been having a problem with encoding sound from the RCA input (from a cable box) with MythTV.  The audio is garbled, like it may be overloading the input, and there is a high pitched static.  I have no problems with the coax input.  I believe it must be an encoding issue because there are no problems when watching live TV through MythTV from that input.  I can even pause and rewind live with no sound issues.  The problems only come when trying to play the file after it has been recorded.  It is not simply a playback issue, though, because I've tried the file on multiple machines and multiple players (even burned one to DVD), and the problem remains.  My card is a Hauppauge 150.

I appreciate any ideas.

---

### Post by josesanders on 2007-03-13
Sorry to bump, but I am totally at a loss here.  Any suggestions would be very much appreciated.

---

### Post by majoridiot on 2007-03-14
you say that pause, rewind, etc. on livetv are fine... are you transcoding your recordings?  it sounds
to me like your transcode settings are wrong.

livetv is "encoded" and saved to the hd as you watch... if it were a mythtv prob, you should have probs
time-shifting livetv, too.

---

### Post by josesanders on 2007-03-14
I had never heard the term transcoding.  Is that something that MythTV does altomatically?  I checked in the setup, and there are settings for transcoding, but I haven't made any changes.

Just to check, I tried recording the audio direcly using Audacity, and there are no problems.  Maybe that's not the best solution, but is there any way for MythTV to take the audio for that input from the sound card, rather than the TV card?

---

### Post by majoridiot on 2007-03-14
i reiterate- if the sound is fine when watching and time-shifting (pause, FF, REW) livetv, then there is
NOT a problem with mythtv or your card, but either your settings or your  codecs.

to see if it is your codecs, watch a minute or so of livetv using the tuner in question.  then open a terminal
and do:

```
# ls -t -r <your mythtv video directory> 
```

the last .mpg file on the list is what you were just watching.  if you can not play it without sound errors
in any of your players, then you have codec problems and need to install them.

if it plays ok, then go through your mythtv frontend setup and make sure that any selections for transcoding
or jobs (except commercial flagging) are *disabled* and then see if you continue to have these issues.  if not, 
then it was the transcoder settings.

in any event, it's likely codec problems.  automatix will install most any you will need, all in one shot.

---

### Post by josesanders on 2007-03-14
The test from live TV is fine.  Unfortunately, I can't find anywhere that says that I have transcoding enabled.  I do not have the auto transcode box checked in any of the recording profiles, and I do not have the box checked in the general settings.

Is transcoding something that it would do after the recording is complete?  If I watch an in-progress recording (before the recording has completed) then I do still have the sound problem.

---

### Post by majoridiot on 2007-03-14
> **josesanders said:**
> If I watch an in-progress recording (before the recording has completed) then I do still have the sound problem.

a problem watching the in-progress recording with mythtv or an external player?

did you do the test i posted above?  if so, what was the result?

---

### Post by josesanders on 2007-03-14
What I did was watch live TV for a few minutes, then exit Myth frontend and go into the /var/lib/mythtv directory and open the last recording with VLC like you said.  It was what I was just watching, and there was no sound problem.  I then used VLC to open an actual recording from this afternoon from that input, and the sound problem was there, so it can't be a problem with playback.

The only way that I have watched an in-progress recording is through MythTV frontend, and I do have the sound problem there.

---

### Post by majoridiot on 2007-03-14
if the test you did was ok, then something is happening to the recordings *after* they are made and
it's not an issue with your card or stb.

on the frontend in Setup-->TV Settings-->General--Jobs (page 3 of general)... what are all of the 
settings on that page?  are you commercial flagging, running other jobs, etc?

---

### Post by josesanders on 2007-03-14
On that page, I have two boxes checked:

Commercial Flag New Recordings (Commercial skip method is "All available methods"
Strict Commercial Detection

---

### Post by josesanders on 2007-03-14
If I watch live tv on that input from a remote frontend, I do have sound problems.

---

### Post by majoridiot on 2007-03-14
that is *really* odd...

1.  does that happens only when using RCA audio in?  have you *confirmed* that the coax input 
does not have this prob on all frontends?

2.  does this problem occur *both* for recording from svideo-in/RCA audioiin *and* RCA video-in/RCA audio-in?

---

### Post by josesanders on 2007-03-14
Sorry, I made a mistake.  Live TV is fine on the remote frontends.  I just had the sound turned up too high, so it seemed like I was having the same problem.  I do have the problem if I watch an in-progress recording, even if I advance pretty much all the way to the live point.

I will try recording from SVideo-in/RCA audio-in and see if that makes a difference, but I suspect that you are right, that the problem is something that happens after the signal leaves the TV card.

---

### Post by majoridiot on 2007-03-16
you might want to also double-check the recording options...

last night, whilst poking around doing something else, i noticed that a recording i had recently set 
was set to transcode after recording, even though transcoding by default was disabled in both
the frontend and backend setup and jobs options-- somehow it was changed and at least some
of my recordings were transcoded by mistake.

the quickest check would be to set a new recording and then immediately edit the options from 
the "future recordings" sub menu.  check under "post processing" and see if the transcode is by 
chance enabled like mine was.

also, check the setting for saving the original recording after trandcode to make sure it saves them.
if it's transcoding without your knowledge, your recording directory will have files with ".old".

---

### Post by josesanders on 2007-03-25
Transcoding is not enabled under the properties for future recordings.  Besides, I'm pretty sure that it isn't a transcoding problem, since transcoding takes place after the recording has completed.  I still have sound problems even if I watch the in progress recording before it has completed.

---

### Post by josesanders on 2007-04-18
SUCCESS... sort of

The evil Comcast monopoly is eliminating basic cable entirely and forcing everyone to pay extra for digital.  This made the tuner input to my card essentially worthless, so I just plugged my cable box into the tuner input, rather than the SVideo or Composite input, and everything is fine.  For some reason, though, it wouldn't set the tuner to channel 4 as I told it to in the setup, so I had to do that manually, but otherwise it was pretty easy.

I still wish I knew what the problem was, though.

---

### Post by majoridiot on 2007-04-18
you might check to see if your firewire connection on the new stb is active: [https://help.ubuntu.com/community/MythTV_Edgy_Firewire](https://help.ubuntu.com/community/MythTV_Edgy_Firewire)

---

