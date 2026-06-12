---
title: "help: no sound - creative xfi"
date: 2008-09-07
forum: Multimedia Software
---

### Post by BeccyBug on 2008-09-07
Hi

Have just followed the oss installation guide, to try to get my soundcard working in Ubuntu - changed the options in 'sound preferences' to oss, and when I hit test I get 

"audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback. Device is being used by another application."

if I change the options to auto detect I get 
"audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect: Connection refused"

any ideas?

I also have a usb speaker plugged in, which did work until I installed the oss stuff - in the oss mixer it is muted, but haven't been able to get either working.

Any help much appreciated

---

### Post by erikthedrink on 2009-09-08
I've got logitech usb speakers.  In Xubuntu, go to Terminal, type

[FONT=Georgia][SIZE=4]asoundconf set-default-card 1[/SIZE][/FONT]

Then close and re-open your browser (Mozilla Firefox) or restart your system.
:guitar:
Note, if you unplug your usb speakers, your laptop speakers will take over.  In order to re-establish contact with the usb speakers, you will need to (plug them back in) restart the system.  If this doesn't work, substitute the "1" with a "2"

---

