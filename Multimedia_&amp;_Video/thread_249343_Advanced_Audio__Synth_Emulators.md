---
title: "Advanced Audio / Synth Emulators"
date: 2006-09-02
forum: Multimedia &amp; Video
---

### Post by Brendt2 on 2006-09-02
This question is short and simple:

What is a good solution for virtual music apps ( IE Pro Tools ), and synth emulators ( IE Rebirth, Reason, Reaktor, Ect )?

Also how is Ubuntu's hardware support for MIDI I/O devices? Is there a prefered device?

How does Ubuntu support 24bit audio? Better than windows?

Sorry that I am such a noob!

:-\" 

Thanks!

---

### Post by Brendt2 on 2006-09-07
Does anyone have any idea at all?

---

### Post by McTek on 2006-09-07
Good luck with midi, I've been trying for a year to get midi to play on a linux distro.

P.S Your quote may have originated with Thomas Jefferson.
If you give up you liberties for the sake of security you will have neither.

---

### Post by eosyn on 2007-12-06
I've been searching on how to a) find a keyboard I can interface with linux to compose music (imagine that.. composing.. who does that  these days? and b) the software involved. 

I just started this search so, I'm not a wealth of information but I found one site worth looking at
[http://sound.condorow.net/]("http://sound.condorow.net/")
also [http://sound.condorow.net/hardware.html]("http://sound.condorow.net/hardware.html") for hardware info
I'll keep digging

---

### Post by Fingers &amp; Thumbs on 2007-12-06
I use an M-audio keystation pro 88, flawlessly with linux, this sends midi data over usb, and the midi in's can be "thru'd" to send over usb, this unit may be too big for many but M-audio do many smaller units with similar spec and is very inexpensive.

  Regarding linux itself, I would suggest using a realtime kernal, such as is packaged with ubuntustudio.

  As for software I'm still trawling through the huge abundance of software synths/ recording applications etc. but on the whole I am very impressed with the quality. The only gap I haven't managed to fill since migrating to linux is a physical modelled piano, but I dare say at the rate things are developing, it's only a matter of time.

  For analogue emulations, try MX44 for out of the box friendlyness, and great sounds, but for greater flexability, try one of the many modularsynth packages available (which one is really just a matter of personal preference.

  For playing back soundfonts (of which there are countless good quality ones free to download from the net, just google soundfont) fluid synth is very good, and exists as a lightweight dssi plugin in your sequencing software, but if want to run fluidsynth as a standalone you will need the qsynth gui frontend.

  As for recording, Rosegarden is an excellent sequencer, with everything you would expect never more than a couple of clicks away. While Ardour provides you with all your audio needs.

 I hope this helps.

---

### Post by Fingers &amp; Thumbs on 2007-12-06
I only realised after posting the previous message, that you are in Green Bay Wisconsin, you may be interested to know, that Mirror Image Studios in Minneapolis, runs a complete Linux system, much of the coding has been done in by the guys there. So you find some help from those guys.

---

### Post by zettberlin on 2007-12-07
> **Brendt2 said:**
> This question is short and simple:

What is a good solution for virtual music apps ( IE Pro Tools ), 


No.
BUT:

try ARDOUR: [http://ardour.org](http://ardour.org)

it has everything, a dedicated HD-recorder/arranger needs, including MIDI-remote control/sync features though NO MIDI-tracks.

again BUT:

in Linux-Audio everything can be synced/combined with everything using the audioserver jack. Thus you can sync Ardour with an advanced Cubase-style MIDI-Sequencer like Rosegarden:

[http://www.rosegardenmusic.com/](http://www.rosegardenmusic.com/)

Run both the same time, get unsurpassed flexibility, be free ;-)
BTW:
Do NOT try to download/install software packages from these pages. Get the software using Synaptic form the Ubuntu Repos instead. Get the Ubuntustudio-Packages and you are done :-)

> **Brendt2 said:**
> 
and synth emulators ( IE Rebirth, Reason, Reaktor, Ect )?


There are many but 3 are my most important, since they can do virtaully everything, I want in outstanding quality:

ZynaddsubFX: multitimbral, polyphonic softsynth more then 600 realtime-settable parameters per voice, still great fun to work with because the user interface works quite smart with metaphors from the world of hw-synths.

Alsa Modular Synth: still underestimated powerhouse monophonic modular synth (can be started into polyphony-mode) has lots of onboard modules for moogish stuff and fm, can load dozens of LADSPA plugins, any parameter can be set to be controlled by a MIDI-controller. Can store presets for a free configurable control-panel. outstanding sound-quality.

Specimen: nice, easy, trustable sampler with 256 voices per patch


again: none of them has an own sequencer that holds a candle to reason and the like. get Seq24, LMMS or Muse to play them or use them with Rosegarden.

> **Brendt2 said:**
> 
Also how is Ubuntu's hardware support for MIDI I/O devices? Is there a prefered device?


Any generic MIDI-device (USB or MIDI-Plug) is supported. Rule of thumb: if a device is build to work without a computer, it will work with Linux. A few others need firmware to be loaded to work - this can be done with a tool called alsa-firmware-loader. 

> **Brendt2 said:**
> 
How does Ubuntu support 24bit audio? 


With any soundcard, that is supported by alsa, 24bit works perfectly well with apps that can handle such data. Most apps use 32Float anyway...

> **Brendt2 said:**
> 
Better than windows?


hard to know... Is "perfectly" better than windows? ;-)


god luck and WELCOME to the realm of GNU :-)

---

### Post by Brendt2 on 2007-12-08
Thanks so much for your replys!

---

