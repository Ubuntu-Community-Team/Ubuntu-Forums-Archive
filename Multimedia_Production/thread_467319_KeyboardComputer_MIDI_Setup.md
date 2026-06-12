---
title: "Keyboard/Computer MIDI Setup"
date: 2007-06-07
forum: Multimedia Production
---

### Post by jeroloman on 2007-06-07
**[SIZE=3]I have a Casio 1630 synthesizer, which is a fancy piano keyboard, and I want to hook it up to my desktop computer so that I can write music on the computer and have the synthesizer play it form the computerized sheet music. I bought a Yamaha UX-16 MIDI to USB interface for $40 and connected it to my computer. After instalation, Windows seems to recognize it but I don't know about linux, since no linux driver was supplied. In order to do what I want in Windows, I would have to buy a program called "Sibelius" for about $100. But since I have Feisty Fawn running on my dual boot computer, I would like to save money by doing everything with Linux. I found a search of the Internet rather confusing. Some people seem to have successfully used the UX-16 with Linux but they don't say where the driver came from. There seem to be two Linux equivalents to Sibelius, "Rosegarden" and "Lillypad" but they don't seem to be available from Ubuntu nor in binary form.[/SIZE]**
 
**[SIZE=3]Does anyone know how I can set this up in Linux??[/SIZE]**

---

### Post by God Of Atheism on 2007-07-03
Sorry for the late reply, and I hope your problem was solved already.

I just checked, and Rosegarden does appear in the repositories, at least for Feisty Fawn (7.04). Are you sure you mean Lilypad and not Lilypond (which again is in the repositories)?

As to drivers, alsa does have drivers for usb audio devices, including yours, see [here](http://bugtrack.alsa-project.org/main/index.php/Matrix:Vendor-Yamaha). The actual instructions are under the details link for the UX16.

---

