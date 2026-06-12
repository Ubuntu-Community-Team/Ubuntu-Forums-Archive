---
title: "Recommend a USB sound card"
date: 2007-08-24
forum: Multimedia Production
---

### Post by maruchan on 2007-08-24
I'd like to purchase a USB sound card with MIDI in addition to the normal audio stuff. I'm looking at the Tascam US-122 as it seems to be supported in Feisty - at least, that's how it looks. Any tips or suggestions? My budget for this is $150-$200.

I need to use Jack for audio production and my Dell Inspiron internal sound chipset is generating too many xruns.

---

### Post by linuxwizard on 2007-08-25
Look through here some supported sound cards
[https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards](https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards)

---

### Post by nimbledinosaur on 2008-01-06
I'm in the same boat and have been doing some research.  I've seen some how to's around for the tascam us-122 but I've also read that due to the usb 1 connection, it can only operate at restricted sample rates.  Also, it is discontinued.  The Tascam US-122L is the newer version.  You can find more about it and linux here: [http://www.pps.jussieu.fr/~smimram/tascam/](http://www.pps.jussieu.fr/~smimram/tascam/).  Looks like it should be a good choice in the near future.

Have you had any luck since you're original post?

---

### Post by Belibem on 2008-02-17
has anyone managed to apply the 122l patch? Is there any easier way to do it? (like a patched version of alsa)

---

### Post by sodasound on 2008-02-17
As a newbie, I could just be exhibiting cowardice, but I've got a US-122 and the alsa patch that's supposed to make it work is a huge hassle. I've seen a dozen different sets of instructions to install alsa-tools and, specifically usx2y loader, or whatever they call it this week. What I would say is keep looking. There must be an easier way. The US-122 didn't work too reliably in Windows either.

---

### Post by sodasound on 2008-02-17
By the way, I just scanned across the forum, and Lexicon Omega, and other Lexicon products seem to be relatively trouble free. Plug it in and turn it on. All that remains is to set your gains and buffer levels and you're in biz.

---

### Post by Stochastic on 2008-02-18
I was able to get my US-122 working but I would constantly get a buzz anytime I paused playback in my software.  There was also a high noise level in the playback (though recording was fine) - I think that was due to impropper grounding or laptop power shielding.  If you'd like to buy it off me I'd be happy to sell it.  I've moved onto higher-powered fish and it sits dormant in my drawer as a backup card.

---

### Post by Belibem on 2008-02-18
please don't confuse 122 with 122l. 122l is newer, comes with a different chip and requires another driver.

---

### Post by kayosiii on 2008-02-20
um my advice would be to go for firewire over usb for sound if at all practical  (firewire designed for realtime streaming data much moreso than usb)... you can look here for firewire cards that work under linux ([www.ffado.org](www.ffado.org))

if that is not practical then I suggest searching the linux-audio-user mailing list archives... and even joining if you like

---

