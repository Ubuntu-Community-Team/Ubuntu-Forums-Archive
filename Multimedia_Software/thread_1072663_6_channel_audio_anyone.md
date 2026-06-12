---
title: "6 channel audio anyone?"
date: 2009-02-17
forum: Multimedia Software
---

### Post by Reeman on 2009-02-17
Here are some screenshots of alsamixer working on three different devices  in the latest reinstall of Ubuntu Studio 8.10. I have for the first time three separate 24/96 audio devices installed and tested to work with all three at the same time! In theory with Ardour now I can record 6 channel audio by setting each stereo channel to a separate track. My board is the asus m2a-vm and it allows the user to run the onboad dsp alc883 at full 24/96 a/d with a 2 channel line level input. The other two pci cards are the ice1712 and the ca0106 both of which allow a/d conversion at 24/96 from stereo line level in.

Does anyone have any experience recording multi-track 4-6 channel with Ardour2? I am about to bite the bullet and could use all the help I can get.](*,)

---

### Post by markbuntu on 2009-02-17
You will most likely have some problems keeping those cards is sync as their clocks drift. This could make live recording problematic. How do you have jack set up to use them all?

---

### Post by Reeman on 2009-02-17
> **markbuntu said:**
> You will most likely have some problems keeping those cards is sync as their clocks drift. This could make live recording problematic. How do you have jack set up to use them all?
My thinking was to set each pair of different card's hw0 to a different track in Ardour first because each pair will have cross tracking anyway. Then by making sure that the master clock is to 96000 jack should reset the three pcms before recording anything. Of course any other processes that effect sound like the pulse server will have to be killed first. 

My IRQ list is such that I don't have any of the devices sharing with eth0 or usb0-10. No 1394 getting in on the action and 3 spare irqs 5 plus (com) and (parrallel) re-assigned to the pci bus. If I use only the ice1712 hw out to monitor things in stereo then nothing should cause a clock drift during the a/d conversions. 

Ardour should be able to write to sda (sata) as the data comes in. Since I will not be receiving or sending any iec958 connections then the clocks should stay stable. I have found that clock drift mostly occurs using midi and digital in sources. My main concern is that the system bus will handle the load of data being sent to ram and then the harddrive without causing dropout! The system bus on my board seems up to the task. I will increase Ardours frame buffer to the max possible without locking up the system and make sure every thing except the essential components of X for the software is out of the way first. For example shut down all inet and related stuff, only use what is absolutely necessary to run the OS. I have 4gig of pc2 800 and an athlon 64X2 2700  (the special edition black box one) with 3meg of processor cache so the components are in place for the adventure. It is just questionable as to whether or not Ubuntu Studio and a realtime kernel with Ardour and jack will do it.   

My thinking is that until a stable 64bit realtime kernel becomes available I will be swimming up stream. I have done successful 4 track before with the m-audio, an audigy and Ardour but that was with a realtime kernel and a 32bit intel board and dual p111s. But that was two years ago when the 32bit realtime kernel really smoked. Maybe I should have not sold the board!

---

### Post by markbuntu on 2009-02-18
The clocks will start out the same but will drift. You need to understand thae nature of these clocks on sound boards. They use quartz crystals running at about 10Mhz or so and then divide that down to to arrive at the timing clock. No two of these crystals are the same and they drift with changes in temperatue and voltage and due to aging. They also use very sloppy division which makes it even worse card to card. This is not a problem in their intended use which is as stand alone sound devices. 

Some M-audio and RME Hammersmith professional audio cards are designed for master clocking from one card to eliminate this problem and that is why they are used by professionals. For other cards timing drift can vary from unnoticable to extremely annoying but in any case will get worse the longer your recording time. 

Pulseaudio does timing re-sync when running multiple sound cards but even they do not reccomend using this for recording since they report a slight drift to the left occurs when the clocks are resynchronized. ALSA has no resync mechanism. You may be able to use netjack to keep your cards in sync but I am not too familiar with that, the documentation I can find is sketchy at best.

Anyway, good luck with that.
PS
keep this thread open and let us know how it all works out.

---

### Post by Reeman on 2009-02-18
> **markbuntu said:**
> The clocks will start out the same but will drift. You need to understand thae nature of these clocks on sound boards. They use quartz crystals running at about 10Mhz or so and then divide that down to to arrive at the timing clock. No two of these crystals are the same and they drift with changes in temperatue and voltage and due to aging. They also use very sloppy division which makes it even worse card to card. This is not a problem in their intended use which is as stand alone sound devices. 

Some M-audio and RME Hammersmith professional audio cards are designed for master clocking from one card to eliminate this problem and that is why they are used by professionals. For other cards timing drift can vary from unnoticable to extremely annoying but in any case will get worse the longer your recording time. 

Pulseaudio does timing re-sync when running multiple sound cards but even they do not reccomend using this for recording since they report a slight drift to the left occurs when the clocks are resynchronized. ALSA has no resync mechanism. You may be able to use netjack to keep your cards in sync but I am not too familiar with that, the documentation I can find is sketchy at best.

Anyway, good luck with that.
PS
keep this thread open and let us know how it all works out.
I was hoping by using newer stuff to avoid the old SB clock issues. I remember them well with sb32 and 64 isa cards. The asus board and the zen power supply that I am using should help to keep the voltages stable. If push comes to shove I will ditch the SB card and onboard and just use ganged M-audio with ICE1712 chips. I know it is the crystal on the board and not the DSP but alot depends on design. Some of the newer SB stuff is getting better at shutting down crap like the mike pre-amp and therefore making the voltages more stable. The SoundBlasters are starting to use better caps and seem to be more clock friendly than before. So I will give them a shot.

Jack can sync the clocks but it all depends on the software pipes to and from the Ardour record functions. I hope that the software has become as quick as what some 64 Studio users are saying.

---

### Post by Reeman on 2009-02-21
Well I sorted out the problems and ditched the ca0106. My lucky day happened when I found a second M-audio Audiophile 24/96 for 70 bucks!

Strangely enough the ca0106 chip borked and started to drop bits in combination with the onboard. But the onboard alc883 with the M-audio ice1712 didn't. Quite a surprise to find an onboard that does not bork at 24/96 ganged with a pci!

So now I am set up with two M-audios which will gang their work clock automatically and an onboard that does not seem to stutter or drift. So it just might be that I have created a usable 6 channel a/d in with a mini-atx form factor pc with stable ZEN fanless power. If I can find a piece of wood I will knock very hard! 6 channel 24/96 a/d in a professional studio costs a fortune.

---

### Post by markbuntu on 2009-02-21
You are one lucky guy, lol.

---

