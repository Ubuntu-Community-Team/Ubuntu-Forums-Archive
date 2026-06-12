---
title: "Best way to stream from PC to TV"
date: 2012-11-04
forum: Multimedia Software
---

### Post by madu on 2012-11-04
Hi,

I would like to know the best option to stream video files (possibly HD) in my Ubuntu machine to my TV.

The options I have are:

1) Playstation 3 - Install an application such as TVersity and stream through PS3.
2) Apple TV - Not possible since it can only be used with iTunes.
3) Buy a DLNA enabled BluRay player

I'm a little worried about option #3, as some players with advertised DLNA capability doesnt actually work. Especially when using with a Linux machine.

So if you guys can give me some information regarding this I'd really appreciate.

Thank you.

---

### Post by papibe on 2012-11-04
Hi madu.

Take a look at [MediaTomb]("http://mediatomb.cc/"). It is on the Software Center, btw.

Regards.

---

### Post by Derek Karpinski on 2012-11-04
Serviio works well with minimal configuration.  There are plenty of built-in configurations for many brands/models of TVs.

Memory usage seems a bit high though.

[http://www.serviio.org/](http://www.serviio.org/)

---

### Post by madu on 2012-11-04
Thank you very much Papibe and Derek.
I will try both. I do have a LG TV so maybe I would not need to buy a DLNA device afterall.

---

### Post by SeijiSensei on 2012-11-04
Can you not simply connect the PC to the TV with an HDMI/DVI/VGA cable?  I'm writing this on a computer attached to a Sony Bravia with an HDMI-to-DVI converter cable connected to my NVIDIA 9500GT card.  The TV also has a VGA port which I've used as well.  For audio, I just use the standard motherboard output with a mini-phono plug to RCA cable plugged into my rather ancient Harmon Kardon receiver.

If you want to stream from a PC to a DLNA-capable device, [PS3MediaServer]("http://www.ps3mediaserver.org/") is the way to go.  It's cross-platform as well.

---

### Post by whatthefunk on 2012-11-04
> **SeijiSensei said:**
> Can you not simply connect the PC to the TV with an HDMI/DVI/VGA cable?  I'm writing this on a computer attached to a Sony Bravia with an HDMI-to-DVI converter cable connected to my NVIDIA 9500GT card.  I just use the motherboard audio with a mini-phono plug to RCA cable plugged into my rather ancient Harmon Kardon receiver.

This is maybe the easiest option.  I have an HDMI cable going to my Panasonic TV and it works great.

---

### Post by Bucky Ball on 2012-11-04
> **SeijiSensei said:**
> Can you not simply connect the PC to the TV with an HDMI/DVI/VGA cable? 

Yep, that's what we do with VGA and HDMI cables and all good. Audio into the sound system via the headphone jack for VGA sound. You can even switch the laptop screen off in 'Monitors' or 'Display' (I use Xubuntu so don't remember in Ubuntu) to keep things a little cooler. Thinking about getting a Raspberry Pi, though, so we don't need to keep moving the laptop

[http://www.raspberrypi.org/](http://www.raspberrypi.org/)

People are doing some weird and wonderful things with them. See my thread here:

[http://ubuntuforums.org/showthread.php?t=2021289&highlight=raspberry+pi](http://ubuntuforums.org/showthread.php?t=2021289&highlight=raspberry+pi)

Was fooling around with Media Tomb for awhile but then got busy. I was getting there and It was looking promising if you're wanting to go the network route. I think that could work.

---

### Post by cybrsaylr on 2012-11-04
> **whatthefunk said:**
> This is maybe the easiest option.  I have an HDMI cable going to my Panasonic TV and it works great.

I do the same connecting my laptop via HDMI cable to a LG HDTV. It was easy, works great and turned that HDTV into a super-smart TV.

---

### Post by madu on 2012-11-04
Thanks for the replies guys.
But I cannot connect to the TV with the HDMI because the TV and the PC are in different rooms. So I want a solution that uses the LAN. I was thinking about a NAS connected to the TV too but then I have to copy my files to the NAS, which is another extra step.

---

### Post by Bucky Ball on 2012-11-04
Just a question: What version of Ubuntu are you using? Your sig says 9.10!

But the NAS box is intended to be a dedicated media box so it will be accessible from all devices once on the network, not specific to the TV streaming setup. All audio/video can then just automatically go there, leaving space on the other machines.

---

### Post by madu on 2012-11-04
> **Bucky Ball said:**
> Just a question: What version of Ubuntu are you using? Your sig says 9.10!

But the NAS box is intended to be a dedicated media box so it will be accessible from all devices once on the network, not specific to the TV streaming setup. All audio/video can then just automatically go there, leaving space on the other machines.

I'm using 11.04. But I guess I have to upgrade because the LTS just ended for it.

So if I get a NAS with DLNA, I mount it as a network drive and then copy my files directly to it? That would work right?

---

### Post by Bucky Ball on 2012-11-04
> **madu said:**
> I'm using 11.04. But I guess I have to upgrade because the LTS just ended for it.

11.04 wasn't an LTS (long-term support) release. But yes, support has ended.

Don't know, or don't remember, anything about DLNA, sorry. You've inspired me to start playing around with that box again, though ...

---

### Post by cybrsaylr on 2012-11-05
> **madu said:**
> Thanks for the replies guys.
But I cannot connect to the TV with the HDMI because the TV and the PC are in different rooms.

You can find HDMI cables up to 50 feet long online at a reasonable price.

Just noticed you are in Japan where prices on these cables are probably better than here in North America....lol

---

### Post by madu on 2012-11-05
> **cybrsaylr said:**
> You can find HDMI cables up to 50 feet long online at a reasonable price.

Just noticed you are in Japan where prices on these cables are probably better than here in North America....lol

I had no idea HDMI cables can go up to 50 feet. Never seen ones more than couple of meters.

But in that case I would not be able to control the movie (unless I bring my keyboard and mouse with me to the living room :)

---

### Post by cybrsaylr on 2012-11-05
> **madu said:**
> But in that case I would not be able to control the movie (unless I bring my keyboard and mouse with me to the living room :)
Not sure how your appartment/house is laid out but I control mine using a wireless mouse. Laptop is plugged into TV with a short 6 foot HDMI cable. However I can control about 90% of laptop functions with wireless mouse from my easy chair or couch or as far as 20 feet away in the kitchen. In fact the wireless mouse works better than the infrared TV remote that came with the TV.

---

### Post by 337Manni on 2012-11-05
Just a note. I built a HTPC and was using a Nvidia XFX 768MB 8800 GTX XXX graphics card to power the TV. Worked fine once I got arround the overscanning issue.

I upgraded my card to AMD Radeon MSI 2GB 6950 Twin Freezer Pro and had problems powering the TV over the long cable (Blurry image). The cable was HDMI to HDMI 10M (33ft) and I had paid for a good quality one. I ended up moving the HTPC closer to the TV and getting the same cable in a smaller length. Works great now and in a better place ha. Picture is great and no overscanning at all.

---

### Post by whatthefunk on 2012-11-05
My TV is also in another room.  I can control it with the wireless mouse.  There are also ways to use a remote control with your computer, but you have to find a receiver which Ive found difficult.

---

### Post by madu on 2012-11-05
Thank you very much for all the replies guys.
I'm first going to try installing TVersity or MediaTomb on my PC and see if my LG TV can find it (its supposed to be DLNA enabled). 
If that works I will get a NAS.

If not I will probably end of getting a PS3 as that has proven to work with Tversity. I have read many stories that these so-called DLNA devices don't play all that friendly with PC's.

Cheers.

---

### Post by Bucky Ball on 2012-11-05
Glad you got some clues. ;)

If you are satisfied this has been solved, please mark it that way from 'Thread Tools' at top right  to help others and post a new thread when you're further down the track. 

Good luck with it.

---

### Post by nhtrader on 2013-01-11
> **madu said:**
> Hi,

3) Buy a DLNA enabled BluRay player

I'm a little worried about option #3, as some players with advertised DLNA capability doesnt actually work. Especially when using with a Linux machine.



I just bought a Samsung BD-E5400 from Walmart $78. It is a BluRay/DVD/CD player with WiFi, and allows Netflix, Pandora ... more stuff.

I just got it to work with my Mythbuntu PC. Here are the details:
(BTW, to see Windows stored media content you must install Samsung's client software called AllShare. My point is that Samsung's implementation of DLNA doesn't play nice with windows either.)

But for us Linux/Ubuntu users, DLNA works!

(source URL: [https://wiki.archlinux.org/index.php/MiniDLNA](https://wiki.archlinux.org/index.php/MiniDLNA))

My Mythbuntu PC:
1. Ubuntu 12.04.1 (64bit)
2. MythTV v25.3
3. minidlna v1.0.21

Instructions:
install minidlna (2 methods)
1.use Synpatic
2.terminal mode:
        sudo su
	apt-get update
	apt-get install minidlna

Check current network intface in terminal mode
	ifconfig (output will tell you if you are using eth0 or eth1, etc.)
	

Prepare minidlna folders (quirk: it runs as user nobody and it installs the user nobody by default, but it doesn't add the group nobody)
        sudo su
	mkdir /var/{cache,log}/minidlna
	groupadd nobody
	chowm nobody:nobody /var/{cache,log}/minidlna
	

Configure minidlna from terminal mode
        sudo su
	pico /etc/minidlna.conf (change parameters/settings)
                        verify: port=8200 (that your not using this port already)
                        verify/uncomment: network_interface=eth0
(note: the following 3 lines are specific to my media collection. I chose only to allow video access. Did not add music, photos (other stuff). Change to use your DIRs)
			remove: media_dir=/var/opt
			add: media_dir=V,/var/lib/mythtv/recordings
			add: media_dir=V,/var/lib/mythtv/videos
			uncomment/modify: friendly_name=Myth DLNA Server
			uncomment/modify:db_dir=/var/cache/minidlna
			uncomment/modify:log_dir=/var/log/minidlna
			uncomment/modify: presentation_url=http://192.168.10.10:8200 (address of the PC your running minidlna with port 8200 [default in conf])
			uncomment/modify:notify_interval=600
	exit/save
	
Reset Database in terminal mode
        sudo su
	minidlna -R
	
Restart minidlna
        sudo su
	service minidlna restart

exit su root


COMMENTS:

As you can see, the installation of minidlna has a peculiar twist and I'm sure this has to do with DLNA's specs. The user nobody must be implemented properly so that the database and log DIRs work appropriately.

Even if you did that (groupadd nobody,  chown nobody:nobody) The DLNA device didn't see my DLNA server b/c there was no database. So the second step is to create the database (minidlna -R), 

After I did this, my DLNA server on my Mythbuntu PC worked properly and my DLNA device (Samsung BluRay Player/Media Player) was able to see all of my content that is compatible with Samsung's media formats. 

This brings me to the last obstacle in the process - Media Content Compatibility. This BluRay Player/Media Player accepts MP3, MPG, MP4, M4V, MKV, and some recent variants of AVI and WMA formats (not all AVI or WMA). Also note that the Samsung BD-E5400 does not play VOB formatted files (a MPG variant). My point is to check the specs of your potential new media player and make sure that it is compatible with your media content.

---

### Post by dannyboy79 on 2013-01-11
i happen to see that the OP mentioned he couldn't use an apple tv because of itunes and I would like to say that is farther from the truth. I have an original apple tv 1 running crystalbuntu and it can handle streaming HD content from my main media server downstairs. It's almost the easiest/cheapest way to take a quality looking device and have yourself a great media frontend device. Heck, i can even stream stuff from my iphone due to crystalbuntu having a form of airplay installed. It's awesome and it was free as a hand me down, they didn't know what to do with the old apple tv 1 white box.

---

### Post by evilsoup on 2013-01-11
There's one option that I see has not been mentioned in this thread, and that is ps3mediaserver. In spite of its name, it should actually work on any DLNA renderer. Unlike mediatomb, it doesn't really require any setup - though there are plenty of settings to fiddle with to get the best results for your particular system. It's in the repos.

---

