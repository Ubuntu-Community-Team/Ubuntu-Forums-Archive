---
title: "Getting sound working in flash."
date: 2008-11-23
forum: Multimedia Software
---

### Post by Fulou on 2008-11-23
I've been using Linux for two days and i have to say, I'm impressed so far. Aside from Eve online and Wine, the only other issue which i'm sure others have encountered was getting sound to work in firefox, specifically in flash.

I managed to resolve this issue, although by chance or by following countless other tutorials im not too sure.

I thought i'd post what ive done to get it going.

For the record, im using Ubuntu 8.10
[B]
Step 1.[/B]

System > Administration > Synaptic Package Manager.

In the quicksearch field at the top, enter "Flash" and hit return.
In the list, make sure the following two have been ticked.

FlashPlugin-nonfree-extrasound
Flashplugin-nonfree

**Step 2.**

Install the latest flash from Adobe's website.

[http://www.adobe.com/shockwave/download/static/Linux/ShockwaveFlash/English.html](http://www.adobe.com/shockwave/download/static/Linux/ShockwaveFlash/English.html)

The version i chose was ".deb for Ubuntu 8.04 +"

[B]
Step 3.[/B]

This is the bit that got it working for me, if your using a seperate PCI sound card (or another expansion slot, im assuming you use PCI unless your ancient or plain disfunctional :) ).

**TURN OFF ONBOARD SOUND IN YOUR BIOS!!!**



There were various other things i tried, random commands in Terminal, alt versions of flash (Some made it keel over) but on the whole, those three are the main biggies.

Hope that helped.

Mike.

P.s. I'm not a traitor to my microsoft friends, im just one step ahead.

---

