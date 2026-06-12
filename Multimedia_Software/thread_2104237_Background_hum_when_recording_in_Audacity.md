---
title: "Background hum when recording in Audacity"
date: 2013-01-12
forum: Multimedia Software
---

### Post by Lars Noodén on 2013-01-12
I'm getting a background hum when recording in Audacity.  It's not present when using the same microphone with other programs, such as Jitsi.  How do I get rid of it?  Filtering after the fact only reduces the hum a little, I'd like it to not be there from the start.

Attached is a 4-second Ogg Vorbis of the background hum.

Edit: changing status to SOLVED.  It turned out to be a defective headset.

---

### Post by dabl on 2013-01-12
Usually such hums are from one of two sources:

- 50 or 60 Hz from the residential AC electrical service (fluorescent lights, the computer PSU, the monitor, amplifier in external audio system, etc.)

- digital noise from the CPU or GPU or motors (disk drives and fans) inside the computer

You may or may not be able to isolate the noise source. A mic picks up noise from outside the computer, and "line in" picks up noise from inside the computer, as well as whatever is put on the line by external sources.

It's not really an audacity issue, it is a "where is it coming from?" issue.  Audacity is just recording what is coming in.

---

### Post by Lars Noodén on 2013-01-13
With more careful checking it seems to also be present in the other applications.  It was just easier to spot in Audacity.  I'm not sure of what to do besides changing equipment.

---

### Post by agillator on 2013-01-13
I think changing equipment is the thing to do. Pick up an inexpensive microphone (or borrow a mike) and see if it still happens. That should tell you the source. It could easily be either the jack itself or the plug or a loose or bare wire, a connection within the mike, etc. Of course it could be dozens of other things, too.

---

### Post by coldraven on 2013-01-13
50 or 60Hz mains hum can also be due to a faulty earth or an earth loop.
Without knowing your set-up I can only make a guess.
To test your house wiring you probably need an electrical engineer.

You could try connecting a wire from your PC chassis to a water pipe but if your plumbing is plastic this won't work

To eliminate an earth  loop you could try this.
I'm presuming that you have a desktop PC connected to a stereo amplifier.
You need to disconnect the shield wires at one end of the audio cable so that it is earthed only by either the PC or the amp.

Edit: Ignore my advice for the earth loop, it won't work on normal (unbalanced) audio cables only professional (balanced) ones.

---

### Post by Lars Noodén on 2013-01-13
It's a USB microphone and generates the hum even in different USB ports.  I've tried the microphone on a different computer and it generates no hum there, so it is not the microphone itself.  

I don't have an oscilloscope available to check out the power line, but can try running the same hardware from a grounded outlet either today or tomorrow.  An electronic phone (runs off a wall wart) has a bit of hum, so it might be that we have bad power.  I'm hoping that it's only part of the house.  I'll also have to figure out a way to ground the computer and test that, it's not a case that is designed to be easily opened.

---

### Post by agillator on 2013-01-13
If you do not have grounded outlets or metal water pipes you could just run a temporary wire to a stake driven in the ground outside and fasten that to a metal part of the computer case. Also try turning appliances on and off, lights, etc. to try to find out what is causing the interference. Of course it could be something in a neighbor's home. Short wave radios play havoc with other tv and radio signals sometimes, perhaps your neighbor's microwave is causing a problem. At any rate it sounds as if the problem is grounding either of the computer itself, the boards in it, or the circuitry in your building. If none of this tells you anything, borrow a UPS. Make sure it is charged, plug in the computer and get it running, and then unplug the UPS so the computer is running off the battery, not the home electrical circuits. No hum will tell you it is caused by the home wiring. Still hum says it is in the computer or something like a light or appliance creating an interference signal in the air. Have you tried someone else's computer that does not normally have the problem? If, in the same location, there is no hum then it is your computer.

---

### Post by tgalati4 on 2013-01-13
Try different audio cables.  Higher quality cables have better shielding and that will reduce hum pickup from surrounding devices.  Many times, the hum comes from poor engineering of the sound chip--in this case the USB dongle.  Try wrapping the USB device in aluminum foil and see if that helps.  Add a ferrite coil and see if that helps.  What is the model of the USB sound device?

---

### Post by Lars Noodén on 2013-01-27
> **tgalati4 said:**
>  What is the model of the USB sound device?

It's ID 046d:0a0c Logitech, Inc. Clear Chat Comfort USB Headset.  I've tried it on other hardware, different grounding and on battery.  The hum is present when I use the set even when on another site, far away.   It's also present when using a different computer.  When I unplug the computer and run from battery, the hum is reduced but still there.  So I think it may be bad luck that the set picks up RF.  I may just have to buy another set, but will need to find a store where I can try them on my laptop before buying.

---

### Post by Lars Noodén on 2013-07-15
Thanks for the tips.  

It was the Logtitech headset itself.  The microphone eventually ceased to function and I've replaced it with another brand, Sennheiser, which seem to function just fine so far.

---

