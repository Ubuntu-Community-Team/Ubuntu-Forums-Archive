---
title: "Only front left sound available"
date: 2013-07-08
forum: Multimedia Software
---

### Post by TheHammer101 on 2013-07-08
So, I am for the most part very new to Ubuntu. I've been mucking around for a bit so I understand enough, but as far as Audio goes I'm a complete newbie. So, any logs I should include or configuration information please let me know, and I will be able to get back with a new post containing what you asked for within about an hour or two.

Here's the system info:
Pentium 4 3.2Ghz D865PERL 1.5GB RAM
Running Ubuntu Server 12.04 Precise with ubuntu-desktop installed
Installed kmix, no other modifications to the sound system have been done besides playing around in ssh with alsamix.

It will only output Front Left sound from the integrated sound card. If I change the balance fader in the sound properties it actually lowers the total volume fader from 100% to 0% when adjusting to go to right side only.

I have speakers in a monitor that everything from FL and FR need to go to, and a set of seperate speakers that I want RL and RR to go to. I have only one channel out apparently, and a 5.1 capable soundcard....

WHAT DO?

---

### Post by 1clue on 2013-07-08
Can you verify that your hardware is all functional?  Unplug the speakers and swap them, or try them in another device if it's a headphone type plug.

Other than that you can go into your sound setting panel, which is in the volume control widget.  I'm running Xubuntu so the names might be different, and so might the widgets.

On the right side of the sound control, you'll find a 'configuration' tab.  It's a good idea to turn off all the sound cards you don't want to use, and then make sure the one you ARE using is set to be something your setup can handle.  If you're using traditional speakers or headset, then it'll be Analog Stereo Duplex or possibly the same thing with microphone.

---

### Post by TheHammer101 on 2013-07-09
Yes, I've tried numerous configurations. While Windows XP was installed all the audio ports were working even. So I know that the hardware is not an issue. There is only one sound card (the integrated one) available, or installed. I don't see a configuration tab in the sound control options.

---

### Post by 1clue on 2013-07-09
OK so you have to go to the sound control panel (same place as the volume widget) and set the mode of the sound card you're using like I said at the bottom of my earlier post

---

### Post by TheHammer101 on 2013-07-09
Yeah, I've tried that. I have "Analog Surround 5.1 Output" selected there. It hadn't made any changes no matter which mode I was running in.

I  tried alsamixer through SSH once more and realized that the M key  actually mutes/unmutes channels. That's not very well documented... it isn't listed as an option in the menu above all the sound  options with the rest of the options. Also, any of the F key functions  just kick me straight out of alsamixer. This thing seems pretty buggy.  So it turns out that although the volume was at 100% on the surround  channel it was still muted.. I unmuted that, and for some reason now my  Front Right channel works fine. 0.o Problem solved, mostly. For some  reason the Left and Right sides are reversed on both the Front and  Surround.. not a big deal really.

This is one step closer to what I need to happen.

Now  how can I make the RL and RR surround channels my default instead of  the FL and FR? I am trying to get Subsonic to play in jukebox mode to  the RL and RR speakers, but for some reason none of the hardware  selections for my soundcard output to that.. so if I can get RL and RR as my defaults for everything else than I can use FL and FR as output for Subsonic.

---

### Post by Yellow Pasque on 2013-07-09
Try the latest driver. Hopefully, it's already been fixed: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

Can you give alsa info?: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by TheHammer101 on 2013-07-09
I'm not worried about the Left Right switch, because I just changed around the plugs. Both the Front and Rear sets of speakers are hooked up via 3.5mm plug>RCA plug cables, and it was easy enough to just switch the left and right plugs around.

[http://www.alsa-project.org/db/?f=aae89dc75413f78116482994e4ab6c35a94c38de](http://www.alsa-project.org/db/?f=aae89dc75413f78116482994e4ab6c35a94c38de)

---

### Post by TheHammer101 on 2013-07-09
```
# java audioDevList
Available mixers:
PulseAudio Mixer
ICH5 [default]
ICH5 [plughw:0,0]
ICH5 [plughw:0,1]
ICH5 [plughw:0,2]
ICH5 [plughw:0,3]
ICH5 [plughw:0,4]
Port ICH5 [hw:0]
```

I found a way to figure out available sound card options through Java that way I could specify which to use. The only option out of these that works is "ICH5 [plughw:0,0]", and it only plays through FL and FR. So if you can find a workaround I haven't thought of besides these two it would be much appreciated. I had figured that once I got the surround sound working one of these options would just work.. I was mistaken though.

---

### Post by 1clue on 2013-07-09
Are you sure the sound card is recognized correctly and that it has the right driver?  We're getting outside my area of expertise as far as sound cards go, but this is the sort of thing I ran into before with all kinds of hardware.  Is this an add-in card or the one on the motherboard?

If you're amenable to the idea, you might consider using a proprietary driver if there is one.

Is your card capable of surround 5.1?  I'm assuming you know and that the answer is yes, but just checking.

---

