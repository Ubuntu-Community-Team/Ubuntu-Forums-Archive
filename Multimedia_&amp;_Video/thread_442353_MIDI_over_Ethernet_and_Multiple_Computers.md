---
title: "MIDI over Ethernet and Multiple Computers"
date: 2007-05-13
forum: Multimedia &amp; Video
---

### Post by nicholaspaul on 2007-05-13
Are there any MIDI Over Ethernet capabilities in Ubuntu? 

If not, what would be the best way to set up a multiple-computer studio? I'm using a G4 as the main DAW (running Cubase on OS X) and would like to share the processing duties with other machines, just to lighten the load. Another machine running Feisty would be doable, if it's practical.
:guitar:

---

### Post by mzw! on 2008-01-13
I resurrect this topic... I am looking for the exact thing, MIDI over ethernet for Ubuntu. Did you get it working?

If this is not possible (what I doubt, in linux everything is possible hehehe) which way would be good for sharing info from a windows software which only can send MIDI and a linux machine?

---

### Post by xybre on 2008-03-08
I ressurect it again.. I know it can be done. It's done all over on Windows and OSX, Linux support is more difficult to come by, especially cross platform support.

---

### Post by mzw! on 2008-03-08
A fairly easy way would be to use a PD patch.

I found OSC (open sound control, [http://opensoundcontrol.org](http://opensoundcontrol.org)) which allows us to share data among computers in a network. MIDI can be encapsulated in OSC.

I do not know how to do it exactly because I have not tried yet, but I guess it is not so difficult.

Cheers!

---

### Post by xyblor on 2008-03-09
I asked xybre a similar question on ##music yesterday; by coincidence, we meet again :-)

My problem is convoluted: I'm running Finale for Windows through Virtual Box on Ubuntu, but Virtual Box doesn't seem to have access to my sound card's midi port, so I can't hear stuff on my electric piano like I want to.

I haven't found a solution yet, but these are my leads:

OSC (using PureData?)
IPMidi (w/ WINE) - not free
MIDIoverLAN (w/ WINE) - not free
qmidiroute - linux only, maybe doesn't work over LAN
Wormhole2 - seems to be for audio, not midi
Kevin's MIDI server (I don't know) - [http://www.kevinboone.com/download_windows.html](http://www.kevinboone.com/download_windows.html) 
dmidid - [http://www.dmidi.l4l.ie/](http://www.dmidi.l4l.ie/)
aseqnet - ALSA only
imidi (Mac only) - [http://www.grantedsw.com/imidi/](http://www.grantedsw.com/imidi/)

To be honest, I'd rather just use Finale through WINE instead of Virtual Box, but it just acts sluggish and the menu behaviour is buggy. I'm hoping the next version of WINE remedies this.

---

### Post by mzw! on 2008-03-09
PureData would simply encapsulate the MIDI data into OSC packets to send them through the network. I think it is no so difficult to make a patch doing this. If I find an example I'll post it.

---

### Post by revol on 2008-04-12
I found this...it seems a dead project, but interesting because it's opensource.
[http://www.linuxsampler.org/ethernetmidi/](http://www.linuxsampler.org/ethernetmidi/)

and this related discussion:
[http://www.northernsounds.com/forum/showthread.php?t=36461](http://www.northernsounds.com/forum/showthread.php?t=36461)

---

### Post by xyblor on 2008-04-12
> **revol said:**
> I found this...
thanks! I'll take a look at that

---

