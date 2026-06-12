---
title: "Missing sound in recordings"
date: 2009-01-24
forum: Mythbuntu
---

### Post by bobmorningstar on 2009-01-24
Download the newest mythbuntu last night and fresh installed it.

Using a old ATI TV wonder card, has coax cable in and stereo audio output.  

I have the LCD TV audio in connected to the output (green) jack of the on-board sound. The audio cable from the TV Wonder card has been tried in both the aux and line-in ports (both work).

Problem are:
1) the recordings have no sound
2) the tv audio is on constantly, no matter what part  of Myth I am in, I can hear sound. Great when I'm watching the TV, but even if I exit Myth, the sound is still there.

I can mute using the alsa-mixer so I do have a control of the inputs and outputs.

Video is fine and the install seems stable.  I have been through the forums, googled, and after 3-4 hours I'm stumped.

Any ideas?
Thanks for any assist.
Bob

---

### Post by klc5555 on 2009-01-24
> **bobmorningstar said:**
> Download the newest mythbuntu last night and fresh installed it.

Using a old ATI TV wonder card, has coax cable in and stereo audio output.  

I have the LCD TV audio in connected to the output (green) jack of the on-board sound. The audio cable from the TV Wonder card has been tried in both the aux and line-in ports (both work).

Problem are:
1) the recordings have no sound
2) the tv audio is on constantly, no matter what part  of Myth I am in, I can hear sound. Great when I'm watching the TV, but even if I exit Myth, the sound is still there.

I can mute using the alsa-mixer so I do have a control of the inputs and outputs.

Video is fine and the install seems stable.  I have been through the forums, googled, and after 3-4 hours I'm stumped.

Any ideas?
Thanks for any assist.
Bob

Does the ATI TV card really require the use of an audio output bypass cable? Normally Myth expects the sound from a card like this to come in through the PCI bus, rather than an external cable hooked through the sound card input. I'm surprised you haven't been getting audio sync issues with livetv, since the tuner's output is buffered for a few seconds on the hard disk, which your audio cable to the sound card's input is bypassing. Also would explain why recordings have no sound, since that would never make it to the harddisk from the tuner.

---

### Post by bobmorningstar on 2009-01-25
That was the only way I could get it to work with SnapStream Beyond TV in the Windows box I took it out of.

What card do you use in your machine?  Maybe it's time for a new card?

---

### Post by klc5555 on 2009-01-26
> **bobmorningstar said:**
> That was the only way I could get it to work with SnapStream Beyond TV in the Windows box I took it out of.

What card do you use in your machine?  Maybe it's time for a new card?

Maybe... but try the card without a bypass cable first. The sketchy Mythtv docs for your card on the Mythtv wiki don't mention a bypass cable requirement, just the card's over-heavy CPU requirements.

As for new cards, a lot of it depends on what you want to record. Certainly you don't want to follow my experiences with capture cards, whose results have been, at best, spotty. The wiki has write-ups (of varying quality) for many cards here: [http://www.mythtv.org/wiki/Category:Video_capture_cards](http://www.mythtv.org/wiki/Category:Video_capture_cards)
The complete list of "Linux-supported" capture cards is likely on your system already, at: /usr/src/linux/Documentation/video4linux/bttv

I have a master backend/frontend running Mythbuntu and a couple of slave backends/frontends running Slackware. I'm using a couple of pcHDTV5500s, which are great for clear QAM digital, and easy to set up for same, but a bit too pricey and next to worthless for reliable analog recording. I have a Hauppauge PVR150 for analog capture and recording, and it has been by far the most reliable card I've ever had. So, naturally, as an analog-only device, it's not sold any longer in the US with the imminent digital cutover. I have a Hauppauge 1600, which, eventually, I was able to get working quite well for analog capture and recording, though it seems to be digitally almost deaf. Most recently, I've been scratching my head over a new-style Avermedia A180 (where all the inputs have been eliminated except for the one digital coax input). It "ought" to work, but to date I can't get the 2.6.27 kernel to load the firmware file when the modules load. 

Anyway ... good luck! :)

---

