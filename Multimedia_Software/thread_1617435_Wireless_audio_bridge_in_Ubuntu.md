---
title: "Wireless audio bridge in Ubuntu?"
date: 2010-11-09
forum: Multimedia Software
---

### Post by rogerdean on 2010-11-09
Hello all

I'd like to stream my laptop's audio output wirelessly to my hifi, and my wife's laptop too so must also work from a Mac. I guess if it's based on analogue rather than usb then we could stream the iPod too, but I don't know what's available. Does anyone know how this might be done?

Many thanks
Roger

---

### Post by cchhrriiss121212 on 2010-11-09
You seem a bit confused. If something is analogue then it cannot be streamed with a wireless connection (as they are digital). I don't know what you mean with regard to USB.

Ubuntu can use pulse audio to send audio over a network, but a Mac will not have this. 

Your ability to send an audio signal to your hi-fi will also depend on what input capabilities it has. What model is it?

---

### Post by rogerdean on 2010-11-10
Thanks for your reply :-)

I don't think I'm confused. I'm just thinking about all the options - a wireless dongle of some sort sending digital audio to a receiver, or perhaps a wireless bridge for an analogue signal. Wondering what is out there.

As for the hifi, I don't think the model matters as I'd be using standard phono inputs

Any particular equipment or solutions you know of?

Cheers
Roger

---

### Post by cchhrriiss121212 on 2010-11-10
What you would like to have does/can not exist in any simple form. I thought from your first post you were talking about software but I see now that you wanted a hardware solution. I asked what model hi-fi you had as I thought it may have some basic network ability.

Here is the problem:
Phono inputs on your hi-fi are analogue inputs which cannot be modified to reiceive digital
Wireless bridges are used to transmit digital data only between computers
Analogue signals in the home are transmitted using cabling of some kind, to transmit wireless analogue you need broadcasting equipment (like what radio stations use)

If you want to know more, then read up on wikipedia. The solution I use for this is a cheap and easy cable with 1/8" jacks.

---

### Post by rogerdean on 2010-11-10
Thanks for the advice...

Well, I know Maplin do digital wireless audio bridges like this -

[http://www.maplin.co.uk/Module.aspx?ModuleNo=104993](http://www.maplin.co.uk/Module.aspx?ModuleNo=104993)

Just wondering if anyone has experience with them on Ubuntu

Cheers
Roger

---

### Post by rogerdean on 2010-11-11
Ok, in case anyone is following this, I've found details of what sounds like a great solution. 

The Logitech Squeezebox range connect to a hifi with phono cables and to a wireless network. There's a .deb for their server software, as well as software for Windows and Mac of course, so you can stream any audio to the devices

Links here
[http://www.logitech.com/en-gb/speakers-audio/wireless-music-systems?WT.ac=bc|50|5745](http://www.logitech.com/en-gb/speakers-audio/wireless-music-systems?WT.ac=bc|50|5745)
[http://www.mysqueezebox.com/download](http://www.mysqueezebox.com/download)
[http://wiki.slimdevices.com/index.php/DebianPackage](http://wiki.slimdevices.com/index.php/DebianPackage)

Might try to find one on the cheap somewhere...
Cheers
Roger

---

### Post by cchhrriiss121212 on 2010-11-11
Looks like you have found something good, shame about the price though. Just FYI, the items you are looking at transmit a digital signal over a network to the receiver box that will convert to analogue when it gets there.

---

