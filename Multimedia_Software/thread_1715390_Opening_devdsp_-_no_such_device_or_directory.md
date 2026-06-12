---
title: "Opening /dev/dsp - no such device or directory"
date: 2011-03-26
forum: Multimedia Software
---

### Post by jbernardis on 2011-03-26
I am trying to get a package named xoscope running on my PC.  This is a PC-based oscilloscope that uses the inputs from your sound card.  I used the Synaptic Package manager to install it - no problems, but I couldn't get past square one with it - every time I tell it to use the soundcard as it's input device, I get the above error message.

I googled the message, and everything told me I needed to install/configure ALSA.   So I downloaded the ALSA driver, libraries, and utilities and started my way into ALSA hell.  Now I have a PC where the sound card is not recognized by anybody - ALSA comes up but does not see anything, and everytime I try to load any media player, etc - I get some kind of error.

Now this is an old system in my shop - I don't really use the sound capabilities - but I would like to be able to use xoscope.  This is a clean install - I can reinstall without too much fuss, and that is probably what I'll do, but it doesn;t solve the original problem - xoscope seems to want to open a device named /dev/dsp which simply doesn't exist.

Could anybody offer any words of wisdom?

Thanks

---

### Post by Yellow Pasque on 2011-03-27
/dev/dsp is used by programs that use OSS (OpenSound). Ubuntu kernels no longer have OSS support (for political reasons), but you can still run them using padsp:
```
padsp <some_app_that_still_uses_OSS>
```
Of course, your sound has to work first, so you should reinstall if it's easy to do so, or give us more detail on what you did, so we can help you undo it.

---

