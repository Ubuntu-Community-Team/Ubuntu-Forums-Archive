---
title: "Simultaneous Output to Two Sound Cards?"
date: 2009-06-23
forum: Multimedia Software
---

### Post by Literati on 2009-06-23
Hi,

I'm looking to get EVERY sound on my PC (So it doesn't have to be application specific) to be outputted to BOTH my onbaord sound (hooked up to my speakers) and my ESI Juli@ (hooked up to my amp > headphones). So that I can listen with my headphones, but if I want to take them off, I can just turn on my speakers and listen.

I tried creating a Pulse Audio "Simultaneous Output to all Sound Devices" but it doesn't seem to be working (Both sound cards are set to unmuted, each at same volume, and the Virtual Output is set as default, also unmuted, same volume)

I was (surprisingly) not able to find anything related to this specifically on google. People were looking for application specific rules on which sound card to output to, but I don't care for that, just send everything to both, and I'll use hardware controls to mute/turn off what I don't want. :) 

Anyway, thanks for the help in advance! :)

---

### Post by Literati on 2009-06-24
Bump. :)

---

### Post by Literati on 2009-06-24
I found this. But I'm not sure how to tailor it to my setup per se? Help?

[http://alsa.opensrc.org/index.php/.asoundrc#Dupe_output_to_multiple_cards](http://alsa.opensrc.org/index.php/.asoundrc#Dupe_output_to_multiple_cards)

---

### Post by Literati on 2009-06-25
:(

---

### Post by Literati on 2009-06-25
Still waiting on absolutely ANY input. I need this to work...

---

### Post by OscarFoxtrot on 2009-06-26
> **Literati said:**
> I'm looking to get EVERY sound on my PC (So it doesn't have to be application specific) to be outputted to BOTH my onbaord sound (hooked up to my speakers) and my ESI Juli@ (hooked up to my amp > headphones). So that I can listen with my headphones, but if I want to take them off, I can just turn on my speakers and listen.... I'll use hardware controls to mute/turn off what I don't want. 

Send all audio to either the onboard, or the Juli@, connect that to your amp, connect speakers to amp, and use your amp headphone socket when you want to use headphones?

---

### Post by Literati on 2009-06-26
> **OscarFoxtrot said:**
> Send all audio to either the onboard, or the Juli@, connect that to your amp, connect speakers to amp, and use your amp headphone socket when you want to use headphones?

No, that won't work. 
It's a headphone only amplifier (To power my Sennheiser HD650s).

The Juli@ has RCA outputs to lead to the RCA Inputs on the Amp. Whereas the onboard has those like, 5 or 6 coloured ones (Green, Blue, Orange, etc) to lead to my 5 Speakers + Sub.

---

### Post by alch on 2009-06-26
That's an impressive looking sound card. Does it have 2 separate outputs you could run one to each sound source?

What are you using to play sounds and music? You may be able to configure one application to use one output, ie vlc and another application to go to another output.

---

### Post by Literati on 2009-06-27
It doesn't unfortunately, it has a set of RCA In's, and RCA Out's, and then if I flip it it has balanced jakcs. But I don't have any balanced cables, so that's a moot point :P

Anyway, I think it'll have to stay as two seperate sound cards, so can anyone help me on that front?

---

### Post by Literati on 2009-06-28
Please? Or point me somewhere where I could maybe get some help?

---

### Post by tgalati4 on 2009-06-28
Get some RCA Y-splitters to  feed both signals.

There may be some conflicting settings in your ALSA configuration files.

---

### Post by jamh on 2009-06-29
My application is a bit different than yours, and I'm not done with my research yet.  Just wanted to point you to this for info only:

[http://ardour.org/node/2776#comment-13624](http://ardour.org/node/2776#comment-13624)

---

### Post by xthatrox on 2011-09-12
Just as an update to others, here is a solution. If you are running Ubuntu Natty: you can simply install "paprefs" through System-->Administration-->Synaptic Package Manager which will give you the easy to use PulseAudio Preferences GUI. It let's you combine all sound cards together into a combined output device which you can then select as your default output in order to have sound sent to all devices. As another benefit, it allows you to share your audio over the network. This is just a front-end to modify the /etc/pulse/default.pa config file, but it's quite convenient. 

[http://mygeekopinions.blogspot.com/2...ulseaudio.html](http://mygeekopinions.blogspot.com/2...ulseaudio.html)

Hope this saves someone else some time.

---

