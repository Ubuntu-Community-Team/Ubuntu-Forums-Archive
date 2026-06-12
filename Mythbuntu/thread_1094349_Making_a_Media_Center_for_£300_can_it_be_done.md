---
title: "Making a Media Center for £300 can it be done?"
date: 2009-03-12
forum: Mythbuntu
---

### Post by amigang on 2009-03-12
hi guys I been wanting to put together a media centre for a while the problem is I dont have much money and plus I want a simple system as my parents may be using it (and putting money towards it) as all we have is a ageing DVD player and video player and need a new way to record programs, a digi box and be HD ready. so I kind of convince them the best system to get is a complete PC system and I'm thinking of using Mythbuntu as the OS to power it, this is what I want it to do.

receive / record / pause TV (digital Freeview)
output to component and HD
input of component
wifi access the net
able to handle 1080p res and video
can play flash vidoes, avi, mpeg, divx, mov
can play BBC iplayer
80gb or more would be nice
play cd & DVD and eventually Blue Ray discs
quite system
have a good remote control to use all this
and maybe a radio feature & 5.1 sound output.

So could i build a complete system able to do all the above for around £300.
So stuff a need hardware wise Motherboard, ram, hard drive, dvd drive, gfx card, tv tuner, psu, remote, and wifi

so if anyone knows which hardware works best with mythTv specially the Tv tuner that would help a lot.

thanks.

---

### Post by thesavager on 2009-03-12
Why not take a look at their website ?

[http://www.mythtv.org/](http://www.mythtv.org/)

:)

or

[http://www.pchdtv.com/hdtv_linux.html](http://www.pchdtv.com/hdtv_linux.html)

---

### Post by Hobgoblin on 2009-03-12
Hauppage cards have good Linux support, not sure about HD as there is no HD terrestrial Freeview as yet.

A video card with DVI and a DVI to HDMI cable will give you HD output, or a TV with VGA input, actual resolution will depend on your TV.

I built one a few years ago which does most of what you want, based around an AMD 2300+ CPU and an GEForce 2 card.

---

### Post by nickrout on 2009-03-12
> **Hobgoblin said:**
> Hauppage cards have good Linux support, not sure about HD as there is no HD terrestrial Freeview as yet.



yes there is see [here]("http://www.freeviewnz.tv/all_about_freeview/page/freeview_hd").

---

### Post by utar on 2009-03-13
> **nickrout said:**
> yes there is see [here]("http://www.freeviewnz.tv/all_about_freeview/page/freeview_hd").

Depends if the OP is in New Zealand or the UK.

---

### Post by nickrout on 2009-03-13
> **utar said:**
> Depends if the OP is in New Zealand or the UK.
indeed, which is why he should be more specific.

---

### Post by wyliecoyoteuk on 2009-04-20
The "£300" suggest he is in the UK, or does NZ use pounds too?

---

### Post by nickrout on 2009-04-20
> **wyliecoyoteuk said:**
> The "£300" suggest he is in the UK, or does NZ use pounds too?

Not since 1967.

---

### Post by Al_Vampyre on 2009-04-20
At the moment Blu-Ray playback is not supported and some people think it may never be, I have 2 Nova T PCI card (Hauppauge) that work no problem with Mythbuntu

---

### Post by AlecJ on 2009-04-20
I think you could with some ebaying get most the hardware together, you don't have to start with top notch stuff. 
Make sure you get a motherboard with 4+ pci slots and you need a Video card with TV-out, Svideo will do as long as you TV has that input.
Most the cards on ebay won't work with mythtv you have to check out each card here
[http://www.linuxtv.org/wiki/index.php/DVB-T_Devices](http://www.linuxtv.org/wiki/index.php/DVB-T_Devices)        or just google mythtv "card name/type"
Choose a power supply with a big fan that spins slowly and look for a non-fan cpu cooler to keep the noise down.
Mine has turned in a hobby that we both are glued too every night.

---

### Post by Scubdup on 2009-04-27
I'm interested in solutions to your question too.

I found a link to this [Silent MythTV Box]("http://www.parker1.co.uk/mythtv_silent.php") in another thread which looks very helpful.

---

### Post by fenian on 2009-04-28
> input of component

This is where it would begin to get expensive ,you would need something like [this ]("http://www.play.com/PC/PCs/4-/7791395/Hauppauge-HD-PVR-High-Definition-Video-Recorder/Product.html")which is rather new and may not be fully supported yet though the [Mythtv has a wiki to get it running ]("http://www.mythtv.org/wiki/Hauppauge_HD-PVR").

As far as the rest they are all possible.A few things to take into consideration...

Video Card-Get a Nvidia card series 8400 or higher as thet support VDPAU for improved HD.

Audio-Most motherboards come with 5.1 or 7.1 audio capabilities.Be aware that some motherboards will only have a pin header to attach an spdif connector so your computer case would need to have a spdif audio port or you would need to add one.An easier path would be to make sure the motherboard has spdif output ports.(Note:all this audio advice assumes you will be hooking the computer up to an external surround sound system,if you are you should make sure tthe motherboard has the correct type of spdif connection (optical or coaxial).If you are connecting speakers directly into the computer you just need to make sure the motherboard supports 5.1 or 7.1 sound.

---

