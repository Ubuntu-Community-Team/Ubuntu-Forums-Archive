---
title: "Turtle Beach Riviera Optical COnnection Problem"
date: 2009-01-01
forum: Multimedia Software
---

### Post by castratikon on 2009-01-01
First of all, I'm new to linux and have only just started learning.  I'm trying to get this turtle beach riviera 5.1 sound card to output sound from the optical connection.  The goal is 5.1 audio but right now I'd take mono lol.  I get no sound at all from it.  I went through the sticky to no avail.  I run alsamixer, and all it shows is a main volume and capture volume.  If I run alsamixer -Dhw I can at least unmute the iec958 but that changes nothing.  I set everything in the sound preferences to use the IEC958 and still no sound.  

Am I missing something here?  As I've said, I've used linux for all of a couple days now so I apologize if I make no sense.  I'm using ubuntu 8.10.  Thanks alot!

---

### Post by castratikon on 2009-01-02
Bump

---

### Post by doug1212 on 2009-01-02
Hi,
I think that there may be issues with digital pass through and Pulse audio, I have a trust card with the same IC as your TB and am able to get digital audio (stereo) out to my DAC using plain ALSA.

Doug.

---

### Post by perez08319 on 2010-04-10
Use the solution Found in [http://ubuntuforums.org/showthread.php?t=1046715 ]("http://ubuntuforums.org/showthread.php?t=1046715")
it works on my 9.10 Karmic

install the gnome-alsamixser

> sudo apt-get install gnome-alsamixer

run it

> gnome-alsamixer

on the top  the tab CMedia PCI should be visible.

Now check the IEC958 output  (if the option is not visible, go to Edit > Sound Card Properties and turn them on)

if you want to hear the output on the analog speakers as well check the IEC958 monitor

---

### Post by fryl0ck on 2010-09-25
Just wanted to chime and a confirm this fix action works with 10.04LTS and the [ TURTLE BEACH  TB120-3425-04 Riviera 6-Channel PCI Sound Card]("http://www.amazon.com/gp/product/B0001YAPL4/ref=oss_product")

Thanks for the quick/easy fix.

---

