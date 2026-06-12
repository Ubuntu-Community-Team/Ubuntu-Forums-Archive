---
title: "Compatable audio interfaces?"
date: 2006-04-06
forum: Multimedia &amp; Video
---

### Post by DanielJapan55 on 2006-04-06
I am a musician, just got donated a computer with ubuntu and I want to use the computer for music editing.  Now I need to buy an audio interface that works with Ubuntu.  I want to buy something for around $100.  Any recommendations?  Is m-audio compatable?

thanks for your help!

daniel

---

### Post by dolson on 2006-04-06
It really depends on what card you're talking about.

To get a good list of supported devices, check this page: [http://alsa-project.org/alsa-doc/index.php?vendor=All#matrix](http://alsa-project.org/alsa-doc/index.php?vendor=All#matrix)

$100 isn't a lot of money, when it comes to audio interfaces, as far as I could tell. All I could afford was an Audigy2 card, which does an OK job for personal audio work... But I wish there was something much better I could afford.

If you can get a supported M-Audio card for $100, it's probably worth it.

---

### Post by bwanab on 2006-04-08
You don't say if this is a desktop or laptop. Assuming desktop, then I'll second Dana's suggestion and refine it by suggesting the M-Audio 96/24 Audiophile. Spec-wise it's as good as it gets. Not a gamer card, but a great musician's card and it has 1 midi in/out to boot. You can get one on ebay for under $100.

---

### Post by efflux on 2006-04-16
I've got a Delta 44. It works in Ubuntu. To get things really working properly you need a zero latency kernel. Hence the special music dists being worked on. I have Echo Audio cards which, although listed in the ALSA project, are very problematic to get working. Unless you are short of cash and have to use Creative, M-Audio are definitely the best or you could buy an RME but they are more expensive. M-Audio are good enough for pro audio work. That's what they are designed for. I don't know about the Audigy but I did once try a Soundblaster Live and it was very poor for proper audio production work compared to M-Audio but I guess these things are reflected in price.

---

### Post by dolson on 2006-04-16
As a user of Creative products, I'll tell you that I think the SB Live! 5.1 is better than the Audigy2 ZS because of the horrible mixer on the Audigy2... I wish there was a way around the crappy mixer, but I haven't found one yet. So if you have to spend only $20 or so, get the Live! 5.1 card. Not the standard Live! cards though, as they have corrupt ACPI headers which caused many data corruption issues, especially with Via chipsets.

---

### Post by libertyforever on 2006-08-19
Hey, these are my kind of people with similar hopes!  I am looking to do some recording of our family band and put out a CD this winter.  (We do acoustic/bluegrass music :-({|= )  I am running Dapper.  **Is there anyone out there that is having success with recording?**  If so, what audio interface unit are you using: M-Audio, Edirol, Presonus, etc.?  (Would like to get the Presonus Firebox - but don't know if I can make it work when I get it.:confused: )  Should I go with a firewire unit or is USB O.K.?  (Would like to go firewire.)  How does it work with Audacity, Ardour, etc.?  What tweeks were necessary to make it work in Dapper?  Drivers for the hardware?  How did you resolve latency issues?  Do I need a specific sound card with one of the portable interfaces?  I've spent a lot of time searching forums and googling to find out what audio interface I should buy that will work in Dapper, and have only found people saying certain set-ups "should work," or "try this and let me know what happens," but no one that can say, "Hey!  This works and this is what I'm using and how I did it!"  I hope I'm not being too idealistic.  There's got to be someone out there that's doing this!  [-o<  I'm still too much on the newbie side to pioneer such an effort, but I'm still researching and learning.  I have checked out ubuntustudio.com and checked their "Audio Hardware" list, but those listed do not apply to my situation (i.e., keyboards, midi, USB, no XLR inputs, etc.).  Is there anyone out there already doing something similar?  Thanks to all you out there who are helping guys like us!

---

### Post by zettberlin on 2006-08-20
> **libertyforever said:**
>  **Is there anyone out there that is having success with recording?** 


I have, for years.

> **libertyforever said:**
> 
 If so, what audio interface unit are you using:

Terratec EWX 24/96 - pretty much the same as MAudio Delta 44(same chipset, same mixer/driver)

> **libertyforever said:**
> 
 (Would like to go firewire.) 


I would not recommend firewire. Some oft the controllers are not properly supported, support for Audiointerfaces seems to be experimental still...

> **libertyforever said:**
> 
 How does it work with Audacity, Ardour, etc.? 

Audacity allways works quite well but cannot rival Ardour as a HD-Recorder/Arranger. Ardour needs jackd, jackd works OK out of the box in Dapper yet not perfectly, if not tweaked.

> **libertyforever said:**
> 
 What tweeks were necessary to make it work in Dapper?  Drivers for the hardware?  How did you resolve latency issues?  


I did not do anything, just the plain Dapper out of the box and most apps from synaptic. Have a look at the results:
[http://www.ubuntuforums.org/showthread.php?t=199803](http://www.ubuntuforums.org/showthread.php?t=199803)

> **libertyforever said:**
> 
Do I need a specific sound card with one of the portable interfaces?  I've spent a lot of time searching forums and googling to find out what audio interface I should buy that will work in Dapper,

MAudio Delta 44 PCI, Buy it, it works.Same should the USB-Version of any wellsuported Chipset, as long as the USB-controller works properly. A friend has no problems at all using the pcm-cia-Version of a hammerfallcard connected to a thinkpad.

good luck

Z

---

### Post by snowbum on 2006-08-20
I also recommend the MAudio Delta 44 PCI. I got that a loooong while ago when it 1st hit the streets. It's been good since. PCI generally really much better than firewire or USB if you have a desktop.

Right now I use RME in the studio and Presonus on the road, but that Delta 44 still kicks 8utt.

Dunno how far you'll get with Ubuntu. Glad to know peeps are using linux though. Have fun!

---

### Post by libertyforever on 2006-08-20
Thanks for the recommendation *zettberlin*.  I think I would lean more towards M-Audio than Terratec.  However, neither models you mentioned have XLR inputs.  Would the M-Audio Delta 1010LT work in a similar fashion as the Delta 44?  Also, this would be fine for a desktop application, but I have in my mind to also do this with my laptop to make recording portable.  Is your friend with the pcmcia hammerfall card running Dapper on his thinkpad?  What I/O box does he have it plugged into? *snowbum*, you mentioned you use *"Presonus on the road."*  What do you mean by that?  If I could use the Presonus Firebox with my desktop or my laptop, I would be in seventh heaven!  But, I am prepared to use something else until the experimental stage is passed.  Still researching . . .. :-k

---

### Post by floogy on 2006-08-20
What do you think abou the [julia@ from ESI]("http://www.digit-life.com/articles2/esi-julia/index.html")? Does anybody know, if the [issues with the mixer]("http://alsa.opensrc.org/ice1724") are solved? Maybe that's only an Issue with the alsamixer, and the [Envy24Control]("http://alsa.opensrc.org/Envy24Control") works? But that seems to work only for the ice1712 chip?

But there is still some developement going on: [http://kernel.org/pub/linux/kernel/v2.6/testing/ChangeLog-2.6.12-rc1](http://kernel.org/pub/linux/kernel/v2.6/testing/ChangeLog-2.6.12-rc1)

```
<perex <at> suse.cz>
	[ALSA] Added ICE1724 - ESI Juli@ code (not complete) + AK4114 code + AK4358
	
	Serial BUS drivers,AK4114 receiver,AK4XXX AD/DA converters
	ICE1712 driver,ICE1724 driver
	Initial incomplete driver for ESI Juli@ cardcards based on ICE1724, AK4114,
	AK4358 and AK5385. The ICE1724 and ICE1712 main files plus some drivers are
	also updated (cleanups and new callbacks).
	
	Signed-off-by: Jaroslav Kysela <perex <at> suse.cz>
```

Does somebody know more about the progress of the driver development?

---

### Post by drucer on 2006-09-18
ICE1712 based PCI-bus M-Audio cards are great (M-Audio delta series). These cards are professional audio cards and the quality is awesome! These cards have excellent ADDA converters and Linux kernel includes drivers for these. Go to Linux audio user mailing list and ask about these cards if you don't believe me. Majority of Linux musicians are using M-Audio cards or RME Hammerfall cards.

Linux audio user mailing list:
[http://www.music.columbia.edu/mailman/listinfo/linux-audio-user](http://www.music.columbia.edu/mailman/listinfo/linux-audio-user)
[http://music.columbia.edu/pipermail/linux-audio-user/](http://music.columbia.edu/pipermail/linux-audio-user/)

---

### Post by HanZo on 2006-09-19
I've got a Terratech DMX 6fire... not really a pro card but it's got some good features for a reasonable price. Works good with alsa  and jack, if you install the alsa-utils gui (or however that is called) package you even get a working control panel for it.
it's based on the envy32 chip (ICE1712) so pretty much the same as other cards listed here.
I haven't tried using it with ubuntu... but it works flawlessly with Studio2to and 64studio.

---

### Post by Wormsie on 2006-09-19
My Terratec PHASE 22 card isn't working (well, it isn't working with ALSA, otherwise it's OK), so I'd like to get a new soundcard: preferably an USB one, as I don't want to waste another $300 if I at some point upgrade to a Mac or a laptop. Any advice? The ALSA compatibility chart is slightly cryptic...

(But if that doesn't work, Delta44 it is...)

---

### Post by HanZo on 2006-09-20
isn't the phase22 the same as the DMX 6fire but with usb?

---

### Post by Wormsie on 2006-09-20
Phase 22 is PCI.

---

### Post by HanZo on 2006-09-21
oh right... was confusing it.

---

