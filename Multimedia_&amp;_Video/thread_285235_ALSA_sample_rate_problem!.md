---
title: "ALSA sample rate problem!"
date: 2006-10-26
forum: Multimedia &amp; Video
---

### Post by theslut on 2006-10-26
What the hell is wrong with ALSA now ](*,) 

ALSA is playing back ok but all my sound is like 2,3 tones lower than it should be :confused: Obviously, the sample rate is too low but i've no idea who to fix it.

OSS is playing back just fine.

---

### Post by jimbone on 2006-10-27
Hi,

I'm having the same issues right after upgrading to Edgy.  I tried getting rid of my .asoundrc file, but it seems to have done nothing.

I'm running an Envy24HT sound card.

I'll see if OSS works.

EDIT:  Running through OSS doesn't seem to work, but it's not real OSS, just the alsa compatibility layer, so it doesn't surprise me that it's still not working.

---

### Post by jimbone on 2006-10-27
I found a solution!

I noticed that the volume controls are different with whatever alsa version/drivers Edgy installed.  There is a switch called "Multi Track Rate Locking" enabled, and the "Multi Track Internal Clock" is set to 8000 (obviously far too low for most playback).  Disabling the rate lock has returned playback to normal.

Hope this works for you.  I imagine this will be a problem common to Envy24HT soundcard users.

---

### Post by theslut on 2006-10-27
cheers! You've made my morning waking up to your post. Now the sound is perfect.

---

