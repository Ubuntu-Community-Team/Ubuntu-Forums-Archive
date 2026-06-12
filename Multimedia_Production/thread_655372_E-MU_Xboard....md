---
title: "E-MU Xboard..."
date: 2008-01-01
forum: Multimedia Production
---

### Post by Pocadotty on 2008-01-01
Im thinking of picking up an E-MU Xboard 25 MIDI controller and I wanted to know if anyone has had any experiences with it, or other E-MU products...

How well do you guys think it would work with Linux.  If the USB MIDI interface works with Linux is basically what I want to know... or how people feel about the hardware itself.

I am sick of everyone saying PC/MAC compatible, and completely ignore or neglect to say whether it works well with linux.


Cheers.

PS. Here is a link to info about the Xboard 25 from E-MU if you can find something usefull 

[Xboard_25]("http://www.emu.com/products/product.asp?category=532&subcategory=533&product=13556")

---

### Post by rupert on 2008-04-26
I push this up.
I have an emu xboard connectecd and lsusb seems to find it.

Bus 002 Device 005: ID 041e:3f01 Creative Technology, Ltd 

how can I now use this in hardy?
I installed bristol for testing, but how can I map the keyboard to this?

thx

EDIT:
after some testing, i have the keyboard running, I had to do change nothing.
Just install  kaconnect, this list the keyboard, then start amsynth, select on the left side the keayboard and on the right amsynth and press connect, after that you can assign all the knobs to the effects/filters, work great, its only a bit slow.

---

### Post by ncopeland on 2008-06-09
To get this to work with bristol, assuming the device is recognised, is to use aconnect or similar to link the Bus device to bristol. If you want to control the GUI rather than just play the synths then you also need to connect it to the 'brighton' user interface.

Once that is done you should get the brighton keyboard graphics to track the midi notes you press (disable this with -tracking) and pressing the 'Middle_Mouse_Button' with the pointer inside one of the GUI devices, then moving any of the controllers on the surface should allow you to start manipulating the sounds.

Most synths should have some default GM registrations. The conntroller mappings you assign are per synth, not per memory, and are saved whenever you save a new sound.

Does anyone have a review of the this keybaord? I know it has 'after touch' however I think it is Channel Pressure rather than Poly Pressure. I could do with a portable with Poly Pressure to develop the CS80 emulator whilst on the road.

Regards,

Nick.

---

### Post by knocz on 2008-07-11
Hi! I have a xboard 25 for a couple of years now.

On my most recent installation of Hardy I cant get the controller working in lmms, but a believe a fresh installation will fix the problem.

I only have good things to say about the controller. The after touch is good, and adjustable to your playing because it has 8 selections of velocity curve select. The knobs, although the rubber coating is a little cheap and a careless person will quickly rip them off, are quite smooth, going from 0 to 127 in a rotation of 270º (3/4 of a full circle) so they aren't like most of the 360 degree endless knobs you will find in every other midi controller. The pitch bend is a little tricky to use, especially for learning.

It has a great knob bypass button good for reseting your knobs back in place, a latch buton to play long notes like a on/off button, 16 midi channels and 16 user patches.

For a 25key Midi controller, it has great characteristics and is perfect supplement for your home studio or on the road.

---

