---
title: "MythTV audio problem(too quite, practically silent) with flyvideo 2000 clone(mercury)"
date: 2006-12-10
forum: Multimedia &amp; Video
---

### Post by fragmental on 2006-12-10
I'm using a Flyvideo 2000 clone made by Kobian Mercury and I get perfect sound in tvtime.  I can also get sound and video through mplayer.

However, in MythTV I can always get video but not audio.  I tried dozens of different settings.  I tried using the saa7134-alsa module to get sound over the pci port, but I'm not sure it's possible with this card.  Currently I have both the capture and the output set to /dev/dsp.

I realized recently however, that there is sound coming out when I watch live tv, only I have to raise all the volume levels as high as possible and it's ridiculously quiet - almost silent - and there is static that is slightly louder than the tv audio.  I've spent at least a dozen hours working on this and it's really getting frustrating, especially considering how close I am.

I have absolutely no idea what to do after this. I may just have to give up, but it seems so close.

---

### Post by fragmental on 2006-12-10
I tried plugging an mp3 player into the line-in while mythtv was in  "watch tv" mode and the sound from that was fine.  This makes me think it's the way mythty handles the capture card in edgy.

---

### Post by fragmental on 2006-12-10
> **fragmental said:**
> I tried plugging an mp3 player into the line-in while mythtv was in  "watch tv" mode and the sound from that was fine.  This makes me think it's the way mythty handles the capture card in edgy.

I think I fixed it.

this is what I did:
First I installed all the xawtv packages in the edgy repository. Then I used v4lctl(which comes in one of the xawtv packages, not sure which one) to set the card's audio to 100% with
```
v4lctl volume 100%
```
90% might sound a little better but won't be as loud, of course.
Then I opened up mythtvfrontend, opened up watch tv alt tabbed back to my terminal and unmuted the card using
```
v4lctl volume mute off
```

After that watching tv with sound worked, recording with sound worked.   The sound mutes and unmutes automatically like it should.  Everything seems to work, and I can close mythfrontend and reopen it and everything still seems to work the way it should.  However, I have not restarted the computer to see if it works after a restart.

---

