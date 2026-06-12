---
title: "DAW hardware advice"
date: 2006-09-11
forum: Multimedia &amp; Video
---

### Post by Aurora on 2006-09-11
Greetings,

I am considering building a Linux-based studio to do simple recordings on a budget. Mostly I will be recording direct voice and acoustic guitar, and importing, if possible, MIDI from two windows apps called Tune Assistant and  Digital Tradition.  These apps consist of libraries of traditional folk tunes with MIDI and some kind of notation output.  I intend to create take-home materials for family music classes.--CDs and sets of MP3s for those with portable players.  I'm not anticipating doing a lot of fancy sequencing or signal processing.  What do you think would be necessary in terms of processors, memory capacity, sound cards, audio interfaces, and other hardware in order to produce simple audio projects?

--Paul

---

### Post by zettberlin on 2006-09-12
> **Aurora said:**
> Greetings,

I am considering building a Linux-based studio to do simple recordings on a budget. Mostly I will be recording direct voice and acoustic guitar, 


So a 2 Audio IN/OUT - Card would do ?

> **Aurora said:**
> 
and importing, if possible, MIDI from two windows apps called Tune Assistant and  Digital Tradition.  These apps consist of libraries of traditional folk tunes with MIDI and some kind of notation output.


If those Apps produce generic(standardcompliant) MIDI, there should not be a problem to import their files in muse or rosegarden. The latter has a scoreeditor too, so it could be better for your needs, canorus can do also and has got even more for editing/printig notes.

 > **Aurora said:**
>  I'm not anticipating doing a lot of fancy sequencing or signal processing.  What do you think would be necessary in terms of processors, memory capacity, sound cards, audio interfaces, and other hardware in order to produce simple audio projects?

--Paul


Well, I see 2 possibilities:

1.) get a used machine with wellsupported, classy Hardwaresetup with specs like:

- PIV or Athlon-CPU with 2.5 GHz or better
- 512 RAM at least
- IDE-Harddisk with 40 GB or more

here in Germany you might pay the equivalent of around 150,- USD for such a box if it is really in very good shape.

2.) get the slowest PIV or AMD64 (avoid celerons and sempron - they will work, but realtimeprocessing depends on a cpu that is built for it... nominal speed is not that important.) box available with more then 512 RAM and a decent Motherboard (check Linuxcompatibility before you buy it. I hear often, that asus-boards do very well.)

I think, such a box might be available for about 300,- USD in a shop.

In both cases you will need to add a usable soundcard to the setup - 90% of the onboards have no acceptable AD/DA-converter and should be disabeled. 

Me and freinds of mine use cards with envy24-Chipsets. With a lot of luck you may get a terratec EWX that should be available 2nd hand for 50,- maybe. In the shop you should consider to get a MAudio Delta card the Delta 44 can be purchased for about 120,- USD. All of those have high-class converters so you can record simple stereo in professional quality.

---

### Post by Aurora on 2006-09-12
> **zettberlin said:**
> 
... a decent Motherboard (check Linuxcompatibility before you buy it. I hear often, that asus-boards do very well.)

I think, such a box might be available for about 300,- USD in a shop.

In both cases you will need to add a usable soundcard to the setup - 90% of the onboards have no acceptable AD/DA-converter and should be disabeled. 

Me and freinds of mine use cards with envy24-Chipsets. With a lot of luck you may get a terratec EWX that should be available 2nd hand for 50,- maybe. In the shop you should consider to get a MAudio Delta card the Delta 44 can be purchased for about 120,- USD. All of those have high-class converters so you can record simple stereo in professional quality.

Hi, and thanks for your reply.

I'm wondering the easiest way to check the mobo for compatability; I hadn't realized that was an issue. If I get a name-brand computer, they don't tell you the motherboard or chipset...I suppose I could search the company site?


I ended up with a HP a1510n but I haven't even opened the box yet.  I was not happy with the purchase and was thinking of returning it.  I note they are now offering a Compaq SR1950NX for $500 US--AMD64 3800+, 1GB RAM, 250 GB HD, almost $300 less than the computer I just bought with a smaller HD and the same everything else.  They have all the media center stuff that I might like playing with but don't need to do my recording work...that's where I could save some money.  Do you think I'm better off building my own box, or is the hardware cheaper in factory boxes?

Thanks,

Paul

---

### Post by zettberlin on 2006-09-12
> **Aurora said:**
>   Do you think I'm better off building my own box, or is the hardware cheaper in factory boxes?



I have the impression, that factoryboxes offer more for the money - the question is: do you need that "more"? If you went to a smaller OEM-Shop you can say: That well supported Motherboard plus the sufficing and decent CPU plus a real quiet cooler and a money-saving no-trouble Graphicsboard.
Most predefined Computers are all-in-one and the more you pay, the more gamer-capabilities are on the bill. In an typical factorybox you pay for features and powers, you do not need for audio so buying a Computer.that you can configure yourself can give you a box for say... 600,- that is the same as good for audio as a factoryPC for 800,- AND: factoryboxes  almos allways come with MSWin preinstalled: that is about 80,- at least for a operatingsystem you dont need ;-)

Regarding the Mobo: this is quite underestimated. The Mainboard defines busspeed and integration/stability and nowadays it comes with half a dozen complex chipsets for USB, SATA, Ethernet and so on, that should be supported flawlessly by linux. I use to check the net before i consider to buy one. Most of them work properly but especially no-namestuff and brandnew boards can raise a lot of trouble so it is wise, to pick 3-4 boards that have the powers, you need and check the web for experience-reports with those.

---

### Post by Aurora on 2006-09-16
Hi,

I have been online all day, trying to figure out which board, soundcard, PSU (it matters--they can be noisy). My head is about to explode.  I am very close to just throwing money at the problem and buying a Mac Mini with an M-Audio Firewire Solo interface, and just using Garage Band.  Easy, but my income just disappeared, so I'm afraid to spend so much.

Is there a simple way to do this with Linux?  If I get a basic generic box and plug the mixer right into to audio input, will it sound horrible?

Is there one simple list of tried and true hardware?  I have been wading through list after list online.  Would you be willing to state clearly:

*Two sound cards.
*Two motherboards.
*At least one quiet PSU.

I wonder if we could use the Ubuntu Studio wiki create recipes for building several levels of Ubuntu boxes for recording, from simple and cheap to the ultimate high-end pro studio.  I would be willing to contribute my solution once I get it built--if I get it built](*,) .

Thanks for your willingness to help.

--Paul

---

### Post by dolson on 2006-09-17
Hardware specs change constantly, items go in and out of stock, etc. I don't think it's good to document such a thing on the wiki because in a year from now, these recommendations probably won't be consistently updated with the newest technology and people will be bugging me to update it. Honestly, you can make music on any decent PC. I make music on a system that is 5 years old, and also on a more recent Dell system that was given to me. I don't even know what motherboard is in the Dell system, nor do I care. My sound cards seem to matter the most, and they aren't ideal for my purposes, but they do suffice. Other people have commented on the wiki that the RME Hammerfall and also the M-Audio cards are good. My power supply in this PC is by Enermax, 431-Watt. The Dell, no idea. My motherboard in this system is ASUS, don't recall the model. In the end, it really doesn't matter, I think. Personally, I won't buy pre-built systems. I put them together myself. I get a good ASUS or EPoX motherboard with lots of PCI and RAM slots, as well as an AGP slot for an NVIDIA card, then I get the fastest CPU I can afford that isn't the lower model (ie: Not a Celeron, Not a Duron, Not a Sempron), then I get 1GB of DDR RAM, as big a hard drive as I can afford, and then put in a good sound card. I use a cheap Yamaha MG10/2 mixer so I don't have to constantly be plugging and unplugging from my sound card. And that's it.. It's pretty easy. My main music system is a factory Dell with no AGP slot and just an Audigy2 card added to it, and it does fine too... So either or. Don't worry about it so much.

---

