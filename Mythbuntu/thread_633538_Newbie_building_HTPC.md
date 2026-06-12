---
title: "Newbie building HTPC"
date: 2007-12-06
forum: Mythbuntu
---

### Post by kirax2 on 2007-12-06
Dear Mythbuntu enthusiasts,

I have managed to obtain the following components:

ASRock ConRoe1333-D667 MicroATX Motherboard
Intel Celeron D 356 Cedar Mill 3.33GHz 512KB L2 Cache LGA 775 Processor
ASUS Black 2MB Cache SATA DVD±R DVD Burner with LS
Hauppauge WinTV PVR 350 Video Recorder, TV/FM Tuner Card PCI Interface
2 x Transcend 2GB 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) (I know this might be overkill, but I managed to get these cheap and all our other computers use DDR, so...*shrug*)
IN WIN Mt. Jade BK623 Case  (I love this case!)
200 GB Seagate IDE Hard Drive

I would like to build an HTPC out of these.  I have been thinking about trying Linux for awhile, and a friend recommended Ubuntu.  So...here I am.  

These are the things I would like to do with the system, with the most important being first:

1. My TV will be the monitor.  I would like to get the TV Out on the Hauppauge 350 working, if at all possible.  I've read varying reports of the feasibility of this, so I wondered if you could tell me if it's possible with the current version of Mythbuntu.  If it's not possible, I have a BIOSTAR V7302EL16 GeForce 7300LE I can put in, but I'd rather not if I don't have to.

2. Using the Hauppauge 350, I'd like to be able to record old VHS tapes and preserve them in digital format on the hard drive with a minimum of hassle.  Is this possible, or should I be thinking about building a dual-booting machine?

3. I'd like to be able to watch shows in Divx/Xvid and other standard encodings.

4. I'd like to be able to emulate old gaming systems, such as the Atari and the NES.  I have a USB device which supposedly allows one to use Playstation 1 and 2 controllers with the computer.  I haven't tried it yet, but it would be nice if it worked.

5. I'd like to be able to watch the occassional TV show or DVD.

What do you think?  Is Mythbuntu right for me?  Once everything is assembled, where would you recommend I begin?  I apologize for the Newbie questions - I CAN follow directions, and I'm just looking for a little help getting started.  I'd appreciate any help you can give me.

Thank you!
-kirax2

---

### Post by superm1 on 2007-12-06
> **kirax2 said:**
> Dear Mythbuntu enthusiasts,

I have managed to obtain the following components:

ASRock ConRoe1333-D667 MicroATX Motherboard
Intel Celeron D 356 Cedar Mill 3.33GHz 512KB L2 Cache LGA 775 Processor
ASUS Black 2MB Cache SATA DVD±R DVD Burner with LS
Hauppauge WinTV PVR 350 Video Recorder, TV/FM Tuner Card PCI Interface
2 x Transcend 2GB 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) (I know this might be overkill, but I managed to get these cheap and all our other computers use DDR, so...*shrug*)
IN WIN Mt. Jade BK623 Case  (I love this case!)
200 GB Seagate IDE Hard Drive

I would like to build an HTPC out of these.  I have been thinking about trying Linux for awhile, and a friend recommended Ubuntu.  So...here I am.  

These are the things I would like to do with the system, with the most important being first:

1. My TV will be the monitor.  I would like to get the TV Out on the Hauppauge 350 working, if at all possible.  I've read varying reports of the feasibility of this, so I wondered if you could tell me if it's possible with the current version of Mythbuntu.  If it's not possible, I have a BIOSTAR V7302EL16 GeForce 7300LE I can put in, but I'd rather not if I don't have to.

This is doable, it's just a bit of a pain due to a few last minute bugs.  It will especially be easier for Hardy.  More about it later in this post.

> 
2. Using the Hauppauge 350, I'd like to be able to record old VHS tapes and preserve them in digital format on the hard drive with a minimum of hassle.  Is this possible, or should I be thinking about building a dual-booting machine?

Yeah, you can do "manual" recordings in myth, or even command line capture if you please.

> 
3. I'd like to be able to watch shows in Divx/Xvid and other standard encodings.

Those 350's don't have a hardware video overlay, so these videos will lag if you play through them typically.  Much better off with the nvidia card.

> 
4. I'd like to be able to emulate old gaming systems, such as the Atari and the NES.  I have a USB device which supposedly allows one to use Playstation 1 and 2 controllers with the computer.  I haven't tried it yet, but it would be nice if it worked.

As long as you don't need to use the opengl renderer for these emulators, should be fine w 350.  If you use the opengl, go nvidia.  I've got a few USB adapters that convert USB->PS1/PS2 that work for me.

> 
5. I'd like to be able to watch the occassional TV show or DVD.

No hardware overlay for dvd playback in external players on the 350.  TV and internal dvd playback is fine since myth can use the 350's mpeg decoder directly.  You will need a few changes, packages from the ppa, configuration.

> 
What do you think?  Is Mythbuntu right for me?  Once everything is assembled, where would you recommend I begin?  I apologize for the Newbie questions - I CAN follow directions, and I'm just looking for a little help getting started.  I'd appreciate any help you can give me.

It's feasible, but if it's not already clear, put your nvidia card in.  It will save you a heck of a lot of hassle for now.

---

### Post by kirax2 on 2007-12-06
Wow, what a prompt and thorough reply!  Thank you so much!

I will take your advice and put in the Nvidia card.  I forgot to mention that my TV is pretty old - a 29" CRT from about 10 years ago, so I doubt it will handle anything but 640x480 very well.  Do you think it'll be difficult to get the TV out on the Nvidia working?  I tried to hook up a Windows box with a different NVidia card to my TV once, and it refused to output anything below 800x600.

Thanks again!
-Janice

---

### Post by superm1 on 2007-12-07
> **kirax2 said:**
> Wow, what a prompt and thorough reply!  Thank you so much!

I will take your advice and put in the Nvidia card.  I forgot to mention that my TV is pretty old - a 29" CRT from about 10 years ago, so I doubt it will handle anything but 640x480 very well.  Do you think it'll be difficult to get the TV out on the Nvidia working?  I tried to hook up a Windows box with a different NVidia card to my TV once, and it refused to output anything below 800x600.

Thanks again!
-Janice
Pretty straightforward through the installer.  Hopefully shouldn't have too much difficulty.

---

