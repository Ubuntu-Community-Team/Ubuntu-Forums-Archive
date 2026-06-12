---
title: "Radio FM Plugin for XMMS"
date: 2007-01-19
forum: Multimedia &amp; Video
---

### Post by CarlosinFL on 2007-01-19
I downloaded a XMMS plugin called "FM Radio Player 1.5" however I don't know I completely understand how to enable the plug-in. Can someone please give me a hand and let me know what I am missing?

---

### Post by CarlosinFL on 2007-01-20
Anyone?

---

### Post by Jose Catre-Vandis on 2007-02-10
Yes, you have to create an empty file with an .fmr extension - e.g. radio1.fmr

Then open this file in Xmms and set the frequency.

It works, but after a second or two I get white noise, and I do not know why?

(radio works fine with Gnomeradio)

---

### Post by Jose Catre-Vandis on 2007-02-28
> **Jose Catre-Vandis said:**
> Yes, you have to create an empty file with an .fmr extension - e.g. radio1.fmr

Then open this file in Xmms and set the frequency.

It works, but after a second or two I get white noise, and I do not know why?

(radio works fine with Gnomeradio)

Bump?

---

### Post by voltsy on 2007-04-21
I think I may have a related problem.

I set up gnomeradio and it was working fine with my LifeView FlyVideo 3000 TV/radio card. This card has a saa7134 chip(set) and a TV tuner for Australia (PAL-G - PAL-D/K).

Something has gone horribly wrong just about the time I was setting up station presets in the gnomeradio configure window. Specifically I was entering frequencies manually (by typing number keys on my keyboard, rather than tuning first then just adding the station ID in the configure dialog).

It was around that time, or possibly when I was trying unsuccessfully to configure xmms-fmradio, that the aforementioned "white noise" audio output occurred.

Please note that "radio -s" and "radio -i > ~/.radio" both appear to perform a normal scan but NO STATIONS are now detected. I have powered down and restarted the computer, but the FM tuner is dead. It is confirmed that dmesg is still reporting it loads the saa7134 modules, and finds the /dev/radio0 device.

It seems some buggy software might have fried my FM tuner chip. OTOH I might just be unlucky and had a hardware failure just as I was configuring the software. Thank goodness the TV tuner continues perfect operation!

Setup: Dapper Drake, Gnomeradio 1.6 (a downloaded binary from the standard repository sources)

---

### Post by voltsy on 2007-04-22
hmmmm...
the plot thickens!

I was about to give up when as a last resort, I decided to reinsall the xmms-fmradio plugin, and read its README file. This file resides in /usr/share/doc/xmms-fmradio

In this well hidden location, the authors describe the correct syntax/layout for all .fmr files:

the first line is the name of one radio station
the second line is the station frequency in kilohertz (kHz)

So here in Melbourne, Australia my ABC-FM-classical-radio.fmr file contains the following two lines:

ABC-FM
105900

...because it transmits on 105.9 MHz !!

After getting the station playing through XMMS, I shut down XMMS and discovered that the saa7134 FM tuner was again functional with all radio softwares - PHEW!!

(my apologies for implicating  the wonderful gnomeradio 1.6, which - wahrscheinlich - is blameless; Entschuldigung!)

---

