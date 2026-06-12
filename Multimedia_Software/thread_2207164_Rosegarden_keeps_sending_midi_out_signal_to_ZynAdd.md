---
title: "Rosegarden keeps sending midi out signal to ZynAddSubFX's channel 2"
date: 2014-02-22
forum: Multimedia Software
---

### Post by junglejuice on 2014-02-22
Hi there,
For years I've been using Rosegarden to send midi signals to ZynAddSubFX, but for some reason the same method I"ve been using all along does not seem to work any longer.
Briefly my setup would be to start up Jack, Rosegarden and Zyn, Then create a new midi playback device in Rosegarden (and name it zyn) and associate the port ZynAddSubFX is assigned to, as a midi output. This meant that when I create a track in rosegarden using the zyn midi device (i just setup) I could trigger ZynAddSubFX with the piano roll (from rosegarden)..... hmm I hope that makes sense?
The problem is that I can't seem to do that since I have been using Ubuntu 13.10 and Ardour3 (I don't know if either of those things have anything to do with it, though).
What happens now is I go through the usual setup, but Rosegarden does not seem to send the midi signal to the correct ZynAddSubFX channel. So if for example I create an instrument at channel 3 in ZynAddSubFX and setup Rosegarden to send a midi signal to channel 3 (of ZynAddSubFX) it always seems to go to channel 2?!?!
However if I activate channel 2 in Zyn, then rosegarden stops sending the signal. I can see the signal is being sent cause the levels in ZynAddSubFX jump when I hit a note in Rosegraden, but only when the channel is deactivated (not on), then when I switch the channel on the levels stop moving. 
It totally feels like Rosegarden and ZynAddSubFX are conspiring against me!

---

### Post by junglejuice on 2014-02-22
pls don't tl;dr this thread

---

### Post by Iowan on 2014-02-22
Please check [Posting Guidelines]("http://ubuntuforums.org/showthread.php?t=2158945").
> Do not shorten your words to acronyms or abbreviations or use URL-shortening services, as is often done when texting or in a Twitter-style update. It is very difficult to read and understand and you are not limited to a small number of characters.

Do not bump your thread more than once in any 24 hour period. Consider waiting longer than that before bumping - this may help to catch the attention of users outside of your timezone.


---

### Post by junglejuice on 2014-02-22
very informative, thanks Iowan.

---

