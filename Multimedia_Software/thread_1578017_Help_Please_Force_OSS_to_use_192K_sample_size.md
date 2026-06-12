---
title: "Help Please: Force OSS to use 192K sample size"
date: 2010-09-19
forum: Multimedia Software
---

### Post by Mack McCormick on 2010-09-19
I would really appreciate some help. I am an Ubuntu novice using version 10.04 . The program I'm running will only access sound cards via OSS.

I'm trying to force OSS to run the three installed sound cards at 192K. Is there a command or a means to do this?

Also I have three identical sound cards in the system, I know the first one is at **device /dev/dsp** in the configuration file of the propriatry program I'm using. How do I determine the names for the other two cards? The program is working fine but only at 48k sample rate.

Here are the steps I've taken so far:
Followed the great instructions here to remove ALSA and install OSS. Confirmed the sound drivers work via sound recorder.

Installed OSSXMIXER and set the sample rate to 192K. 

All suggestions are MOST gratefully appreciated.

Mack

---

### Post by Mack McCormick on 2010-09-19
I should have mentioned that I'm using Creative Labs Xonar D1 cards capable of 192k sample rate.

---

### Post by Mack McCormick on 2010-09-19
I figured out how to force the sample rate to 192k with

  	 	 	 	p { margin-bottom: 0.08in; }  sudo vmixctl rate /dev/dsp 192000


However there is no sound out of the card when I switch from 48k to 192k. Any idea what I'm doing wrong?


Mack

---

### Post by cchhrriiss121212 on 2010-09-20
It could be that the program does not work at 192K, what program are you using?
You can find your card names using "aplay -l" and "lspci -v" in a terminal window.
Why did you switch to OSS?

---

### Post by Mack McCormick on 2010-09-20
I suspect that I've made a mistake by switching to OSS. I did so because the software will ONLY work with OSS per the author. I should have tried the ALSA wrapper first. 

The software is a proprietary package WebSDR which exposes software defined radios via a web server to the Internet. [http://www.websdr.org/](http://www.websdr.org/) Many other users are using this sound card at 192k with this package.

I guess I'll try to switch back to ALSA and use the wrapper to see if that will work unless someone has another idea on how to make OSS work.

Thank you for the response.

Mack

---

