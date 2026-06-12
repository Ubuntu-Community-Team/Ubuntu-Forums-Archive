---
title: "Digidesign hardware: Does it work in Linux yet?"
date: 2007-06-10
forum: Multimedia Production
---

### Post by Dynaflow on 2007-06-10
I've gradually converted every member of my local family to some flavor or another of Ubuntu (even my grandma with her newly-Xubuntu'ed Compaq from circa 1999) . . . except for my dad, who is putting together a home-studio setup of some sort, centered around his PC.  

My dad has a couple hundred dollars sunk into a Digidesign MBox 2 Mini, the ubiquitous Windows version of Pro Tools LE, and some other peripherals; and Digidesign's products' reputation for being useless outside Mac and Windows environments is the main obstacle between my extremely cautious father and Ubuntustudio.  

I believe Ardour and everything that can be run through JACK will take care of any objections about not having Pro Tools available in Linux, but I want to know if that Digidesign box will work, or if I will just have to advise my dad to not patronize Digidesign in the future and wait for one of my mom's pets to ruin that particular piece of hardware.

What I've found elsewhere on the Internet doesn't look promising, but perhaps someone here knows something I don't.

---

### Post by nalmeth on 2007-06-11
I think you may be biting off more than you can chew in this case, but I won't tell you not to try.

Studio people often form funny relationships with their tools, as do others who consider themselves professionals, or power-users. 

You may find him not happy with Ardour, and craving his ProTools and other apps. Make sure you dual-boot, give him a run-down about the differences with Ardour, and most of all, streamline everything. That includes setting up easy-to-access places (like for project data, samples, etc). You'll also have to setup the plugins for him, which will be a task if he wants a lot of VST plugins.

A good place to start your search on compatibility with that device is here:
[http://bugtrack.alsa-project.org/main/index.php/Matrix:Main](http://bugtrack.alsa-project.org/main/index.php/Matrix:Main)

In theory, anything that works with ALSA works with JACK.

Don't say I didn't warn you, power-users are the most difficult to change. Be ready accept temporary setbacks, or even defeat in your Ubuntu Conquest :)

---

### Post by Dynaflow on 2007-06-11
Thanks for the link.  I'll continue my search there. 

My intention is to set up my dad's installation on a brand new, 160-gig hard drive on his computer, split between the ext3 and swap partitions for Linux and a fat32 partition that both Ubuntustudio and the Pro Tools-laden Windows OS can write and read to and from.  

He seemed pretty juiced when he watched me use Add/Remove Applications to download and install programs with all the features he uses on Pro Tools (onto my vanilla Ubuntu Feisty installation) in the time it takes to drink a glass of orange juice -- and all for free.  There's definite interest on his part.  I have a feeling that, if I can't figure out how to make the Digidesign box work, he'll still be more than excited enough about Ubuntustudio to mothball the proprietary hardware, get another interface, and start going whole hog for Ubuntu.  He might even evangelize it to his NAMM show buddies at some point down the road if all goes well.  He's the type.

Onward with the Penguin Crusade...  :D

---

### Post by epidemiks on 2007-08-18
I've just been converted to the cause - in principle, but the only thing holding me back is not knowing if my old mbox will work..
If push comes to shove, I'll have a dual boot setup for Tools, Reason, Cubase etc on xp, and ubuntu for everything else.

---

### Post by kayosiii on 2007-08-21
How does this card interface with the computer. If it is USB then you want to look at the ALSA support list if it is firewire you want FFADO.

---

### Post by stmiller on 2007-08-22
Just boot up an Ubuntu live CD, and connect the USB Mbox. It will automatically use the snd-usb-audio module if it is a compatible USB audio device.

---

### Post by RJARRRPCGP on 2007-08-23
> **Dynaflow said:**
>  wait for one of my mom's pets to ruin that particular piece of hardware.



LOL! I was laughing for at least about 1 minute on that one.

---

### Post by eddyvillagran on 2007-08-24
Is there any pro audio interface that works with linux? Im in the way to have an audio studio but i don't have an a/d audio device. I just have an e-mu midi controller and some audio processors. Thanks.

---

### Post by Mike'sHardLinux on 2007-08-26
The MAudio Delta series is a good bet. I have a 1010 that works perfectly. I used to have a Delta 66 that also worked fine. I don't know if you could consider these pro-audio; more like prosumer.

I believe the RME Multiface works in Linux as well. I think it uses the HDSP PCI card.... although I found some threads in this forum with people having some issues.

I have a Fireface 800 that I used before I made the switch to Linux. It is a beautiful piece of hardware. Unfortunately, there will be no Linux drivers for it.

---

