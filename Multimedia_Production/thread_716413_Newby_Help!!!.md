---
title: "Newby Help!!!"
date: 2008-03-05
forum: Multimedia Production
---

### Post by dynamo92 on 2008-03-05
I'm building my own home studio, I see ubuntu studio and i thought it's a good idea to install this in my pc, I have use Audacity and Hydrogen on windows, but now I find that Rosegarden can give me more power.

The problem is that I got an old Casio CTK-451 keyboard that have A midi-out and a midi-in as well. I got also a Soun Blaster PCI 128, can i use this with rosegarden? Do I have to get a sound module? How MIDI actually works?

Thanks for any help you could give me.
As you can see, I'm totally newbie on MIDI.

See Ya!

---

### Post by robeast on 2008-03-06
Here's an introduction to the software you'll be using:
[http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation](http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation)

Any MIDI device should work, so your keyboard will be fine. I don't know about your sound cards compatibility with JACK (see the link).

---

### Post by theorganloft on 2008-03-06
> **dynamo92 said:**
> I'm building my own home studio, I see ubuntu studio and i thought it's a good idea to install this in my pc, I have use Audacity and Hydrogen on windows, but now I find that Rosegarden can give me more power.

The problem is that I got an old Casio CTK-451 keyboard that have A midi-out and a midi-in as well. I got also a Soun Blaster PCI 128, can i use this with rosegarden? Do I have to get a sound module? How MIDI actually works?

Thanks for any help you could give me.
As you can see, I'm totally newbie on MIDI.

See Ya!

I dibble and dabble with US 7.10 and maybe you can use some of my tips.  check out my blog.

MIDI is simple as long as you have a good source interface. In my experience, I have had problems with the USB adapters.  But the game port adapters work fine. Think of MIDI as a network for musical instruments.  Each MIDI instrument, module, or VST instrument, light controller, gets an address.  You set that as your receiving address at the device.  Anything sent to that address from anywhere with in your system, controls that device.  
It gets more complicated in that when you control that device, you can send all types of control data like volume, velocity, pitch change, program change, change diapers, change sheets, etc. 

Your Casio can simply be the controller for many MIDI devices and there are many out there.  

At your DAW workstation, you can set up libraries of exclusive data about your instruments where your software knows the commands to control the instrument.  As you compose in tracks, you tell the module what module, instrument and how to play it.

---

### Post by dynamo92 on 2008-03-09
Well thanks both of you, that was useful, so in a nutshell, all i have to do is, configure JACK to work properly with all my MIDI interfaces and all my sound conections right? And I have to run Rosegarden for example and load a sound library, so when I play my keyboard, this is going to sent those instructions to rosegarden? Am I right?

One more question, I know that for using MIDI, you have to get a sound module, in the case of rosegarden, will my pc work as the sound module?

Thanks robeast and theorganloft.

---

### Post by theorganloft on 2008-03-11
Jack is  the center of the universe for sound and your MIDI connections.  I advise that you take a little time to learn the basics of JACK.  

When you open any application that supports JACK, Jack will automatically make the audio and Midi connections.  It works very well. You can also tweak the hell out of it but be careful with that!

Yes you can use virtual or VST instruments on your system and in your applications.  Hydrogen is basically a virtual drum machine and I use it all the time.  What is great about this is that I can also use my Alesis drum machine at the same time.  There are also all kinds of special effects for your sounds.  Some are good, some are mediocre.  I also use external hardware effects.  Do not rule out external modules and processors. 

With MIDI, you can really mix it up.

One program that I enjoy working with is Audacity.  It is not a sequencer but it is great if you want to record, mix, and edit live tracks.  It will also work with Jack so that you can have Hydrogen, Rosegarden, and/or Ardour running.  

Now you need to be aware that you need to invest in some good hardware for systems like this.  Especially if you plan to mix up some video.  I suggest no less than 2 gig of memory, the fastest SATA drives you can afford, and a good momma board and power supply.  This is music and video and you will need resources.  

I avoid SATA raids for music and video production and will only use them for large storage of files and data.  

USB is great but I find that you have to have a good momma board with a great on board chipset.  ASUS and ABIT are good choices. On 64 bit Momma's you can take advantage of dual-core and dual processors for video production.  

It is all about fun and I believe that a well designed Linux system can be equal or better than Windows or MAC.

Good Luck.

---

