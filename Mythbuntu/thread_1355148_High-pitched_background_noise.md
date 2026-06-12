---
title: "High-pitched background noise"
date: 2009-12-14
forum: Mythbuntu
---

### Post by NertSkull on 2009-12-14
So I installed a fresh copy of ubuntu and mythtv today, but I get this really annoying high-pitched background noise running on all channels when watching tv.

I've muted the line-in settings in alsamixer.  But I don't know what else to do.  The sound isn't super loud, less than the volume of the tv sound, but its loud enough that its definitely going to make it impossible to comfortably watch tv this way.

Any ideas on what I may be missing?  Thanks everyone

---

### Post by NertSkull on 2009-12-15
ideas?

---

### Post by nickrout on 2009-12-15
bumping a thread after less than a couple of days is rude. Please don't do this. If people had ideas they would reply.

Is this sound present when nothing is playing?

Is it present on videos (as opposed to recordings)

Can you use another program to play livetv, eg tvtime or mplayer or vlc or kaffeine and see if the noise is present?

I am trying to isolate whether this is a problem of interference in your TV signal, something in the computer, or something in myth itself.

You have told us nothing about your hardware or tuners or signal.

---

### Post by NertSkull on 2009-12-15
Fair enough..

I was not familiar with TvTime, but I just installed that and I have no sound issues in TvTime.

However it did slightly alter the sound in mythtv.  Its about the same, but it osscilates more now.  Like a higher pitch pulsating background noise.  

I run a backend/frontend setup with an nvidia geforce 6500 card, a hauppauge WinTV-express NTSC 44981 Rev E1B2 video card.  The sound card is the built-in one on the motherboard (Asus A8NE) with an AMD 64 (can't remember which one, can look it up if needed).  I'm running ubuntu 9.04 (32-bit) with winttv 0.21.  To get sound at all I hook a line up from the back out port of the tv-tuner into the line-in on the mother board sound card.  Then set alsa mixer to captuer that, but mute the line-in.

Then I have a remote frontend on a AMD Althlon64, Asus MB, geforce 8200 running Ubuntu 9.10 with winttv-frontend 0.21 (which I installed from the old jaunty repositories because the new 0.22 version would not work with my tuner).  Also using motherboard sound card

The pulsating sound on the local backend/frontend is present and intrusive, but not quite as problematic and loud as it is on the remote frontend.

I don't have another tuner, but if desperately needed I guess I could put that one into my remote frontend machine to see if tvtime works fine there.  But because tvtime works just fine on the backend/frontend machine, i doubt its the card but mythtv setups.  But I could be totally wrong on that, I am clearly no expert.

The sound is present on live-tv and recordings.  I don't have any videos ripped into that machine yet to try and see if it happens on non-recorded stuff.  Hopefully I can try that somewhat soon, but I don't have any dvds in my home right now to try that with.

The line coming in is just standard basic cable.  I don't know anything about signals though to saw much there.  I don't get the noise when connected directly to a tv however. 

I've tried working with volumes in alsamixer, changing levels, muting certain things and it doesn't seem to change the background sound, they just make everything louder or more quiet.  But the pulsating sound remains.

What else can I do that would be helpful to try?  

I appreciate the help.  Thanks everyone

---

### Post by nickrout on 2009-12-15
hmm odd.

Try downloading a video, any reasonable quality video will do, to /var/lib/mythtv/videos

then go into mythvideo and press the menu button, then scan for videos. Then try playing the video and see what happens with sound.

---

### Post by NertSkull on 2009-12-15
I found a video and downloaded it.  On the local backend/frontend it works fine.  No noise.  I couldn't get it to stream to the remote frontend though.  (I'll have to look into that more, I changed permissions for the videos folder, but it tells me on the remote frontend that the video can't be found and would I like to remove it from the databse).  

Anyway, So I don't know what the video sounds like on the frontend.  I still have the noise on live tv for everything however (worse on remote frontend).  So that's making me think it may be something with the tuner card getting the sound to the motherboard sound card.

Obviously I have no real idea though.

---

### Post by nickrout on 2009-12-15
to get the video onto the other frontend you need to mount the backend videos dir to the same place on the frontend. So on the frontend do:

```
mount -t cifs //backendhostname/videos /var/lib/mythtv/videos
```

this assumes you haven't changed any of the default locations.

but anyway your analysis sounds pretty right. worth  playing the video on the frontend just to be complete anyway.

It could of course be a faulty capture card?

---

### Post by Ronno6 on 2009-12-16
I don't know if your problem is the same as the one I experienced, but this was the solution:

[https://help.ubuntu.com/community/MythTV/Install/Feisty/Troubleshooting#Razzing/tinny/metalic%20sound](https://help.ubuntu.com/community/MythTV/Install/Feisty/Troubleshooting#Razzing/tinny/metalic%20sound)

I hope it helps.

---

### Post by SiHa on 2009-12-16
If it's only on LiveTV, then it could be interference picked up on the audio cable, especially if it's a cheap one (ie, the ones that come free). If your case is poorly screened at the back it might be leaking enough EMI for the cable to pick it up. Do you have any cables that coming through the case (ie, plugged into an internal connnector then being routed out through a gap/hole). These will also cause EMI leakage.

To test this, you could try covering the entire length of the audio cable with tinfoil, and ensuring the foil is grounded - touching a bare metal part of the chassis.

If it works, a good-quality screened cable should fix it for good. Then again, I had a foil-covered aerial cable for 18months, due to the crappy shielding on my old 'knocked-up-from-a-DVD-player-case' frontend.

Edit: Another thought. Do you have a video card (as opposed to on-board). In the goods old days of soundblaster, this was a common problem when the soundcard and video card were too close, the soundcard would pick up high-pitched interference from the video card (from the pixel clock, I think). This can be reduced by moving the cards as far apart, physically, as possible. Again, shielding can be used between the cards, but with extreme care inside the case. Probably better to sandwich some foil between a couple of pieces of cardboard, and just make sure there's a bare bit to touch the case.

Edit2: To check if it's interference from the video card, you can change the desktop resolution, see if the pitch changes.

---

### Post by NertSkull on 2009-12-16
So I tried all of those things tonight.  I tried a new cord, wrapping the cord in tin-foil, moving the tv tuner to a different slot.  Still to no avail.  I still have the sound coming through on mythtv.

I'd like to just say its the tuner is bad, and convince myself to get a new one.  But the fact that I get basically perfect audio using tvtime makes that difficult for me to believe, but maybe.

I can have tvtime on and perfect sound and immediately switch to mythtv (without touching anything) and still get the noise in mythtv.  I wish I could explain the sound better to see if that could help.  Its like an audible vibration.  Or kind of like those old time alien ufo ship noises that you would make from flipping your tongue back and forth in your mouth while humming.

Oh yeah, and I also changed the resolution of the desktop while mythtv is on mythtv and still no change.  

But...I have found something that may be useful.  Normally (at least last time I set up mythtv) I have to change settings in alsamixer.  Normally I have to put the "capture" on "Line" and turn the volume up.  But then I Mute the Line-in.  So I did that like normal and I get the sound I've been having above.

But I just noticed that if I put the "Capture" on anything else (say "CD") and un-mute the line in I get Normal sound.  BUT the sound is not synced up to the voices/picture in mythtv.

So hopefully that means something.  I know you can put the sound delay settings in myth, but  I always thought I read somewhere saying thats not the best option.  Is that what I should do?  Or is there a way to fix it so I get the clear volume from the line in, but not using the capture method?

I hope that made sense (and sorry for the long post, but I want to be as specific as I can)

Thanks everyone

---

### Post by NertSkull on 2009-12-17
So I have also discovered this morning that if I take the "capture" off of the line in, that when I record showings, the audio sync does not have a problem.  I only have a problem with audio sync when it is Live TV.

I also have discovered that Live TV (which gives me audio sync problems on the master backend/frontend) gives ZERO audio when streamed to my remote frontend.  I can watch recorded videos on my frontend just fine, but without the Capture set on the line setting, live tv on the frontend has no sound.

---

### Post by NertSkull on 2009-12-17
Weird... So get this.  It was quiet this afternoon and I tried watching live tv again on my remote backend.  Still with the audio capture NOT on line, and I still get no sound on the remote frontend.

But, as I turned on the live tv, I heard the speakers go on on the local backend/frontend upstairs.  So when it streams tv to the remote machine, I don't get sound on the remote machine, but I do on the local backend.  I assume this is because I have also unmuted the Line in volume (explained in above post) on the local backend.

Clearly that can't be what I want.  Everytime I watch tv on the remote front end, have sound go on on the backend.  weird.

---

### Post by NertSkull on 2009-12-31
Any ideas on why my sound card works fine with TvTime but not MythTV?

---

