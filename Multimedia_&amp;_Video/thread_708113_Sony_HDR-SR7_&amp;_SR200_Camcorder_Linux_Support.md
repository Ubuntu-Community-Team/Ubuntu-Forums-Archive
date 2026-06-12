---
title: "Sony HDR-SR7 &amp; SR200 Camcorder Linux Support"
date: 2008-02-26
forum: Multimedia &amp; Video
---

### Post by DNAspark99 on 2008-02-26
FYI:

I've been 'trying' some camcorders out lately, and have been drawn to the sony HDD based setups. Unfortunately, Sony loves the lock-in, so I was a bit disappointed, but not all that surprised, when the Sony [DCR-SR200]("http://reviews.cnet.com/digital-camcorders/sony-handycam-dcr-sr200/4505-6500_7-32306181.html") was not recognized as a usb-mass-storage device under linux. (ubuntu). I had heard they were doing strange things with their proprietary usb drivers. So to pull images/video off the camera, I'd need to use the crappy windows software. Not ideal, but I figured I could live with it since it is a nice camera anyways.
Next up, I wanted to try the Sony [HDR-SR7]("http://reviews.cnet.com/digital-camcorders/sony-handycam-hdr-sr7/4505-6500_7-32427828.html?tag=prod.txt.1") . This too is a nice camera, with a few extra features, but it's basically the same as the SR200 but with HD (High Def) support and a 6.1MP (vs a 4.0MP) camera built in. But - to my surprise - this model IS recognized when connected via USB, and I can pull movies+images off the camera without the need for the included software (or a windows installation to run it!)

This just surprised me! From my research, I was fully expecting it to NOT be recognized, ala the SR200 model... so I figured I'd share my discovery, incase anyone else is wondering about this.

Next up, AVCHD editing on Linux... but that can wait, I don't even have an HDtv yet :p

---

### Post by chewearn on 2008-02-26
One question, if you could be so kind to help answer:  what video file format does the sony camera spit out?  Anything weird about it, or is it using a standard format?

I asked because after owning a JVC one, it kind of sucks if the camera keep the files in a non-standard format.

---

### Post by DNAspark99 on 2008-02-26
The SR7 records HD (high def) in the [AVCHD]("http://en.wikipedia.org/wiki/AVCHD") codec, and can also be set to record SD (standard def) in mpeg2. 
Both HD & SD modes have different quality settings; HD has XP,HQ,SP,LP, and for SD - HQ, SP, and LP. But the codecs of recorded files will not be affected by this, just size and quality.

From what I gather, the AVCHD codec isn't too well supported by most software just yet, but can be converted to other formats. I havn't played with this yet, and as mentioned, I don't have an HDtv to play it on (yet), but figured it was best to get a HD camcorder now rather than later. (I was going to buy a camcorder regardless, and don't want to have an outdated purchase in a year or two from now). I've got some time and patience to allow the software support to catch up. (I do have a AVCHD editing program already installed on my windows laptop anyways). But even the SD vids have impressive image quality. (especially in good light... the single CMOS chip does have some slight drawbacks in low-light conditions, but that's where Sony's NightShot comes into play... excellent night vision tech, if you don't mind the UFO-green tinge to everything.)

As for the SD codec, no major problems with mpeg2 yet, just a minor hiccup of no sound when played on my first-gen xbox through XBMC, but I suspect an update of that software may help with this, as on my desktop, mplayer and the like have no issues at all with playing the vids.

The best feature? Hands down, the slow-mo recording at 240 fps... although it's limited to 3 second bursts, it's still a very fun thing to play with!

---

### Post by chewearn on 2008-02-26
Great, thanks for the info!
:popcorn:


One final question, and I will be out of your hair; in SD mode, is the mpeg2 files stored as ".mpg" or something else?  The JVC I had record in mpeg2, but for unknown stupid reason, the file extension is ".mod".

---

### Post by DNAspark99 on 2008-02-26
Yes, SD results in proper '.mpg' files. The bundled software, "Picture Motion Browser*' (*windows only) also creates .modd files for every mpg when you use it to pull the images off. They appear to be XML files with some various info relating to the clips for use in one of the other bundled programs, but I've just been deleting them with no ill effect.

---

### Post by DNAspark99 on 2008-02-26
One final note, I 'lost' the program that was auto-starting when I plugged in the camera... didn't take note of which program it was (nor do I know why it's no longer launching when the camera's HDD is mounted, but that's not the camera's fault).... took me a couple minutes to find it again: gthumb

---

