---
title: "comprehensive sound guide not enough for me"
date: 2006-12-05
forum: Multimedia &amp; Video
---

### Post by firfin on 2006-12-05
Hi there,
I have a problem with getting sound to emerge from my system. I have searched the forum en read the comprehensive sound solutions guide. So far, no luck. All seems to be fine, volume contorls and soundplayers all work. I just don't get any sound from my line out or headphone-jacks on my soundcard. I am using a fresh edgy kubuntu install ( i just copied over my /home ), the live cd produced soudn without a problem.

what sound system is preferred for kubuntu and are there specific guides for setting that up / troubleshooting it? Or some info about sound on (k)ubuntu or GNU/linux in general.

So far I've tried:

- 1 lspci 
02:09.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
02:09.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 07)

- 2 cat /proc/asound/modules 
0 snd_emu10k1

-3 aplay -l 
**** List of PLAYBACK Hardware Devices ****
card 0: Live [SB Live 5.1], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0  (this line repeats to #31)
card 0: Live [SB Live 5.1], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0  (this line repeats to #7)
card 0: Live [SB Live 5.1], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

-4 I changed the rights of /dev/dsp to 666, this had no effect.

-5 grep 'audio' /etc/group
audio:x:29:myusername

-6 I created a new user (maybe the prob is in my /home settings somewhere?  With this new user everything appeared fine too. Except there is no sound output.

Can someone enlighten me?

---

### Post by corporate on 2006-12-05
Did you mute the Analog/Digital Output Jack in alsamixer? It could be it.

---

### Post by firfin on 2006-12-05
> **corporate said:**
> Did you mute the Analog/Digital Output Jack in alsamixer? It could be it.

I am sorry but i cannot find that option in alsamixer? There is a lot of stuff about SigmaTel STAC9708,11 but none of that correspond / looks like analog / digital output.

by the way isnt this the orange-colored jack opening on the live soundcard?
I am not using that one ( just the black and green ones, i have a 4.1 speaker set connected)
Should the option be muted or unmuted?

---

### Post by mgmiller on 2006-12-05
I don't know about kubuntu, but in gnome, there is a sound icon in the top panel.  It may indicate a muted main.  A double click on it (again in gnome, I don't know about KDE) will bring up a graphic of sliders and you can see at a glance if anything is muted.  I have found that when everything seems to detect ok hardware wise, but there is still no sound, it's either a muted setting or I plugged the speakers into the wrong jack on the sound card.

---

### Post by corporate on 2006-12-05
> **firfin said:**
> I am sorry but i cannot find that option in alsamixer? There is a lot of stuff about SigmaTel STAC9708,11 but none of that correspond / looks like analog / digital output.

by the way isnt this the orange-colored jack opening on the live soundcard?
I am not using that one ( just the black and green ones, i have a 4.1 speaker set connected)
Should the option be muted or unmuted?
It should be muted. I was having trouble with the sound even after installing all the codecs and following the instructions from the wiki, and muting it got the sound working.

---

### Post by firfin on 2006-12-05
@corporate: 
I found the setting. It was unmuted. I muted it, unfortunately this didn't help. Do you have any other ideas?

@mgmiller:
In Kubuntu you have 'System settings' with a subsection 'Computer Administration' containing amongst other 'Sound System'.  In this I selected 'Enable soundsystem' . On the hardware tab I can choose Autodetect, OSS, ALSA , ESD, Network audio system and Threaded open sound system. It is defaulted on autodetect, but i tried oss and alsa.
There is also a application KMix , which controls volume. This is the first thing i checked. But everything is unmuted in this application.
Any ideas?

---

### Post by firfin on 2006-12-05
Thank you for your responses so far.

---

### Post by firfin on 2006-12-06
Unfortunately my computer is still without soundproducing capabilities.  :mad: 
Anybody out there with some other clues or tips?
Or tips on where to build up my linux and sound knowledge? :-?

---

### Post by corporate on 2006-12-06
Hey,
I've been helped here a couple of times: [http://groups.myspace.com/linuxgeeks]("http://groups.myspace.com/linuxgeeks")

Btw, that soundcard is an Audigy, right?

---

### Post by firfin on 2006-12-07
> **corporate said:**
> Hey,
I've been helped here a couple of times: [http://groups.myspace.com/linuxgeeks]("http://groups.myspace.com/linuxgeeks")

Btw, that soundcard is an Audigy, right?

Thanks for the link, I will check it out as soon as I get home or can log in remotely (bit hectic at work atm )

It's not an Audigy but a SB Live! , from the top of my head I believe it says SB0100 (or SB0200) on the card.

---

### Post by firfin on 2006-12-09
It works!
i did a complete reinstall of edgy (this time also reformatting my /home .) And now I can enjoy my music again. 
Apparently there some some config setting not correct.
Strange that creating a new user did not solve the problem then , right? :confused: 

Ah well, it works now. Thanks for helping me out.

---

### Post by newlinux on 2006-12-10
Anybody have any idea of what this config setting might be? Reinstalling didn't help from me, and I have permissions set right, lspci, and aplay seem to recognize my card, nothing is muted as far as I can tell...

---

### Post by drphilngood on 2006-12-10
> **newlinux said:**
> Anybody have any idea of what this config setting might be? Reinstalling didn't help from me, and I have permissions set right, lspci, and aplay seem to recognize my card, nothing is muted as far as I can tell...

I´m not sure if this will help you but here are my settings for an Audigy2 ZS Platinum, to get sound out of both front and back jacks:

[ATTACH]20837[/ATTACH]

and don´t forget to check the ¨Audigy Analog/Digital Output Jack¨ in the ¨Switches¨ tab.

---

### Post by newlinux on 2006-12-12
thanks, my issue ended up being missing jumper caps. the previous mobo owner used a different audio hardware setup than I want to use and needed to remove the jumper caps to do it - After much scouring of manuals and many guesses I found out what to do -

---

