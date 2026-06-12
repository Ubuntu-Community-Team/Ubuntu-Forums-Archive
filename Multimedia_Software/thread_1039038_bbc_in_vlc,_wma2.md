---
title: "bbc in vlc, wma2?"
date: 2009-01-14
forum: Multimedia Software
---

### Post by pmcginley on 2009-01-14
ok, next problem (there's always one, isn't there?).  up until yesterday, i could listen to the bbc world service in vlc, via a playlist of streaming radio stations i made a zillion years ago.  the world service url is this:

mms://livewmstream-ws.bbc.co.uk.edgestreams.net/reflector:38968%20%20#%20butl1

now, suddenly, it doesn't work.  all the other stations in the playlist do, but if i try to play the world service, it tells me this:

"No suitable decoder module:
VLC does not support the audio or video format "wma2". Unfortunately there is no way for you to fix this."

well, fortunately, i know that can't be true, because it worked until yesterday.  i should also mention that yesterday i reinstalled every codec i could find on my machine in order to fix a problem with songbird, which worked, but left me with this.  so theoretically all plugins that were there when this worked are still there...

i'm running the latest vlc on intrepid...

---

### Post by 5BallJuggler on 2009-01-14
I've just tried your link in my VLC player and it works OK, 
I've checked the codecs i'm running and it looks like it is only "FFmpeg", is this still installed on your system?

EDIT:-
I just found A/52,  DCA,  twolame and Vorbis too

---

### Post by pmcginley on 2009-01-14
they were all there, but i selected them all for reinstallation nonetheless.  no joy, though; i still get the same error message, with that grating "unfortunately..."

---

### Post by pmcginley on 2009-01-14
hm, i did just notice another strange detail: after the error message, vlc *claims* to be playing.  it shows the right label (bbc world service) and counts time, but picks up time from where it last failed.  it's now at 621:37:11.  that must be the total time i've listened to that stream ever - is that possible?  so is there some kind of cache somewhere i could empty?  i've already reinstalled vlc as well...

---

### Post by 5BallJuggler on 2009-01-14
> **pmcginley said:**
> hm, i did just notice another strange detail: after the error message, vlc *claims* to be playing.  it shows the right label (bbc world service) and counts time, but picks up time from where it last failed.  it's now at 621:37:11.  that must be the total time i've listened to that stream ever - is that possible?  so is there some kind of cache somewhere i could empty?  i've already reinstalled vlc as well...

I think I noticed something similar, but can't check it now because I have this error :-

```
Your input can't be opened:
VLC is unable to open the MRL '%0Amms://livewmstream-ws.bbc.co.uk.edgestreams.net/reflector:38968%2520%2520#%2520butl1'. Check the log for details.
```

And i'm seeing this in my messages :-

```
main error: no access module matched "%0Amms"
main error: no access module matched "%0Amms"
main error: open of `%0Amms://livewmstream-ws.bbc.co.uk.edgestreams.net/reflector:38968%2520%2520#%2520butl1' failed: could not create access: no access module matched "%0Amms"
```

---

### Post by 5BallJuggler on 2009-01-14
OK, found the problem with my previous post, i'va added a screen shot showing the playing time, is this what you were talking about, if so i don't believe there is a cache.
I've also added a screenshot of the codec screen in preferences, mine says it IS using a wma2 codec, i don't know why yours is not

---

### Post by pmcginley on 2009-01-14
yup, everything looks like that for me too.  however, i believe that tells us which codec the stream *wants*, not which it is using.  so it's looking for a codec from wma2, and claims it doesn't have one, although it did, and nothing has changed.

so it's playing ok for you?  you have audio?

---

### Post by 5BallJuggler on 2009-01-14
Yeah, Playing OK with audio

---

### Post by pmcginley on 2009-01-14
> **5BallJuggler said:**
> Yeah, Playing OK with audio

hm.  well, as it should.  anyway, vlc *should* be playing this stream with no problem straight of the box (and it did until recently!) so it shouldn't need any external codec packs.  i've uninstalled and reinstalled vlc from synaptic, add/remove, and command line, i'm stumped.  anyone else have an idea?

---

