---
title: "multiple sound channels"
date: 2010-09-10
forum: Multimedia Software
---

### Post by nikko91 on 2010-09-10
Hi guys, what i want to do is use my onboard sound card to reproduce three stereo signals

ideas?

mother: ASUS M4A77TD

ubunutu 10.04

---

### Post by whit on 2010-09-10
> **nikko91 said:**
> Hi guys, what i want to do is use my onboard sound card to reproduce three stereo signals


Do you mean mixing them together? Or switching between them? Or ...?

---

### Post by nikko91 on 2010-09-11
i want to reproduce different songs in each channel

---

### Post by cchhrriiss121212 on 2010-09-11
I'm still not clear on what it is you want to achieve. 
You want to have 3 separate channels of stereo audio, and each with a different song playing at the same time. 
And you want to send these three channels to three different places, or do you want to hear them all through the same set of speakers?
Any info on why you are wanting to do this is also helpful.

---

### Post by nikko91 on 2010-09-11
i want to have 3 separate channels of stereo audio, and each with a different song playing at the same time and i wan to to hear them through different sets of speakers

---

### Post by cchhrriiss121212 on 2010-09-12
For that you would need 3 outputs that can handle stereo, I'm not sure your board can do this. Try opening up alsamixer from a terminal then see how many playback channels you have.

---

### Post by nikko91 on 2010-09-12
[http://yfrog.com/49screenshotsksp](http://yfrog.com/49screenshotsksp)[IMG]http://yfrog.com/49screenshotsksp[/IMG][IMG]http://yfrog.com/49screenshotsksp[/IMG]

---

### Post by pfs35 on 2012-02-22
bump

I'd actually like to do something similar, although it would rather involve playing two different stereo sources to two different outputs of my sound card (both plain old analog jack outputs). The sounds card is 5.1 and thus has several of these outputs. Not sure if there is any way to manage them independently though... 

Here's my ideal situation:
XBMC Live (ubuntu based if I recall correctly) running VMware server
->*Stereo only sound outputted to one of the jacks of the sound card*
Ubuntu server running in VMware server
->Ampache (->mpd)
-->*Stereo only sound outputted to another one of the jacks of the sound card*
Other OSes running in VMware server without any need for sound access

Any idea on how this could be done (or if it's even possible)?

If not, I might consider immediately upgrading to a new sound card with an optical output, since I'll most probably be upgrading to a 5.1 system (which I'd play the output from XBMC on) in the near future.
In that specific case where I'd have two sound cards (the motherboard's one, and a PCI one), would it be possible to allocate them like this:

Internal sound card: Ubuntu server running on VMware server (or just mpd if that is necessary)
PCI sound card: XBMC Live (host OS)

Thanks!
Philippe

---

### Post by mak2aure on 2012-02-22
Please explain your concept. What you really want me to do with this sound card?????????

[Download Psych Episodes]("http://psych.otavo.tv/") , [Download The Tudors Episodes]("http://the-tudors.otavo.tv/")

---

### Post by pfs35 on 2012-02-22
Sorry if I wasn't clear.

Basically I have a sound card with multiple outputs (like this [one]("http://2.bp.blogspot.com/-mzXSzRZAHH4/Td9R9iUuuCI/AAAAAAAAAEQ/nYMg2piWeKE/s1600/Sound+Card.jpg")), except mine is integrated. It has the exact same set of outputs as the one in this picture (i.e. no digital).

I would like one of its jacks (say the green one) to output the stereo signal from XBMC, while another one (say the orange one) would output the stereo signal from the mpd instance running in a VM.

I would then connect the green output to the television in my basement along with my VGA output, and my orange output to the stereo receiver in my living room. They'd be playing completely different things.

---

