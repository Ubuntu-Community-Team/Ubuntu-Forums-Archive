---
title: "Recording my peacocks"
date: 2011-01-18
forum: Multimedia Software
---

### Post by hartz on 2011-01-18
Good day all

I would like to capture the sound of my peacocks.  These birds "crow" (for lack of a better word) only a few times in a day.

Usually they do so at around the time it gets light, about 6:00-ish.  They might call again once before I leave for work.

The problem is to capture a high quality audio clip of their sound I need to have the recording running when they call.  Turning the recorded on an hour before they call may be an option, but the size of the data file produced is rather obnoxious.

So I need something like a kind of time-lapse function for sound.  I'd like to set the recording to run and then have it fill a 10-minute circular buffer.

Then when the birds call, I can go and stop the recording and then I can extract the portions from the file that I like.

Now, finally, for the question:  Is there a ready-made linux application I can use for this?

I don't do a lot of audio work, and don't expect to use the program more than a few times, so I am willing to build something from source too, so long as it is easy to clean up afterwards and as long as it compiles without too many issues.

FWIW I am running Ubuntu 10.10.

Thanx,
  _hartz

---

### Post by gggecko on 2011-01-18
What I would do is install a sound editing program called Audacity and set it up near your peacocks a bit before you think they will crow, then set it recording. After you here the peacocks crow, tell audacity to stop recording and then you can easily cut out the bits that you don't want, on top of this, some versions come with a plug in that deletes noise below a certain level so you don't get their feet scratching the ground or the cat next door etc.
I hope I've helped you out with this problem,
     Yours,
            gggecko

---

### Post by aeiah on 2011-01-18
you'd probably have to put something together yourself, although it wouldnt require much audio-specific knowledge. i assume you can record manually already?

an option that might suit you better than a circular buffer is to encode the audio on the fly. if you aren't picking up much background noise, then most of the recording will be silent, and won't give you much of a filesize overhead. even with a lot of background noise, recording to high quality ogg or mp3 will cut down the filesize considerably compared to an uncompressed wav.

but if you still want a circular buffer (often called a ring buffer) then the easiest and scruffiest thing to do would be:
record a 10 minute segment as A
wait 5 mins (ie, halfway through segment A)
record another 10 minute segment as B
wait 5 mins
record a 10 minute segment as A (overwriting original)
etc etc

this way you'd have time to stop it once the peacock does its thing, and you'd always have a copy of the uninterrupted crows even if they crow during the deletion of one of the segments.


proper ways to do it may get complicated, but you might find something on the net. id be weary of record-on-sound solutions - anything could end up triggering the recording, not just the peacock crows.

---

### Post by hartz on 2011-01-19
Thanx all.

aeiah < Sounds workable but I fond a better solution.

I've been aware of Jack timemachine, but not mentioned it for two reasons - A) It requires jackd, and 
- B) it is a 10sec ring buffer only...

... Or so I thought.  There is in fact a command-line option to set a different buffer time length.

I've installed jackd briefly once, never really used it.  I need some more information about it, but I figure it deserves a post of its own.

---

