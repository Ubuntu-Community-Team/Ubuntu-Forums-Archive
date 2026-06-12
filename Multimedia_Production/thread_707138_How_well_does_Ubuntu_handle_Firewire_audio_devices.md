---
title: "How well does Ubuntu handle Firewire audio devices?"
date: 2008-02-25
forum: Multimedia Production
---

### Post by em3raldxiii on 2008-02-25
I've been an Ubuntu user for quite some time, but I have never used a firewire device.  I just built a new system (AMD Phenom 9500, ASUS deluxe motherboard) that includes onboard firewire.  I would like to buy a more robust audio card, specifically one with several input/outputs, such as the M-Audio **FireWire 1814** - 18-in/14-out FireWire Audio/MIDI Interface w/ ADAT Lightpipe. (see this link:  [http://www.m-audio.com/products/en_us/FireWire1814-main.html](http://www.m-audio.com/products/en_us/FireWire1814-main.html))

My question is, however, how well does Ubuntu handle this type of device?  If I was to install Ardour, would I be able to use this for recording without much trouble?  I have done some searching, but I haven't been able to find information specific to this device, and barely anything regarding Ubuntu and Firewire.

Alternatively, I can certainly go with something like the m-audio delta 1010 ... which is a PCI based card.  So if the Firewire device is not recommended, how well does something like this PCI card work?

Any advice or suggestions are welcome!!  Thanks.

---

### Post by chipants on 2008-02-25
the delta pci cards should all work splendidly.

firewire is still not universally supported. all firewire audio devices are handled by the ffado project, formerly known as the freebob project ([http://freebob.sourceforge.net](http://freebob.sourceforge.net)).

here's the list of supported devices: [http://freebob.sourceforge.net/index.php/List_of_Supported_Devices](http://freebob.sourceforge.net/index.php/List_of_Supported_Devices)

right now, your device is NOT supported. it's doubtful that it will be supported anytime soon, as far as i can tell. but, like i said, the m-audio delta pci cards are all relatively well supported under linux using the regular ALSA drivers.

---

### Post by robeast on 2008-02-25
I have a Presonus Firepod that works perfectly.

---

### Post by Stochastic on 2008-02-25
My Presonus Firepod works great most of the time.

Chipants is quite right, though I'd look more at [www.ffado.org](www.ffado.org) even though it's not into the repos just yet.  There has been much more documentation of cards and upcoming support here.

---

### Post by chipants on 2008-02-25
i should also point out that, while many people are having no trouble using ffado/freebob, the stability is still not as good as if you were just using a pci sound card and alsa.

my recommendation is, if you don't need a mobile solution, pci is still the way to go.

---

### Post by robeast on 2008-02-25
Chipants makes a good point. I expect xruns every time I run JACK, but so far only one has been bad enough to mess up a recording. I tweaked the buffer settings and minimized errors significantly. As a counterpoint, I like breakout boxes over PCI because they reduce noise and are more accessible  by being outside of the computer. However I'm biased by owning a very noisy computer.

---

### Post by chipants on 2008-02-25
> **robeast said:**
> Chipants makes a good point. I expect xruns every time I run JACK, but so far only one has been bad enough to mess up a recording. I tweaked the buffer settings and minimized errors significantly. As a counterpoint, I like breakout boxes over PCI because they reduce noise and are more accessible  by being outside of the computer. However I'm biased by owning a very noisy computer.

good point. i have, indeed, had trouble with noise stemming from internal sound cards.

the echo audio pci cards have external breakout boxes that that are supposedly fairly well supported under linux. i haven't tried them, but am very interested. i wonder how that would work as opposed to a purely external solution.

it's sort of funny that i'm sitting here advocating pci solutions, really. i just put together a new shuttle box. although there's a pci slot, a full-sized card sits against the drive cage in the cramped case. that certainly can't be good as far as potential interference goes. so, i've been looking into external solutions, myself. it's not my main recording box, so it's not really a big deal. but, would definitely be nice to *be able* to do some work on it.

i've read many accounts of working setups using the firewire terratec phase series. sadly, it seems that terratec has discontinued them. ugh.

---

### Post by jouzts on 2008-02-25
I am dealing with a Ubuntu audio firewire configuration problem at the moment. I am trying to connect to a MOTU Traveler, which is supported by FreeBoB. Yesterday I installed gscanbus (which looks for things on the firewire bus), freebob and qjackctl. The ieee1394 module came up in lsmod. But I could not modprobe raw1394, nor were there any devices made.

This morning I booted the machine up and tried modprobe raw1394 and the module loaded and created /dev/raw1394 and (I believe) /dev/ieee1394-0.

gscanbus now shows an unidentified S400 item on the firewire bus. Most of the information I have found about FireWire on Ubuntu has been about digital cameras, where you need to modprobe video1394 as well to get the camera recognized. (I can modprobe video1394 successfully but the Traveler is still not seen). I assume there is another kernel module for audio devices.  Does anyone know what that is?

qjackctl has a Driver dropdown menu on the Setup page. It shows freebob, but without the Traveler on the FireWire bus, the critical input options are grayed out on Setup page. 

Many thanks,

John

---

### Post by robeast on 2008-02-25
When I installed the ubuntustudio-audio packages it took care of all my device setup. I'd recommend giving those a try if you haven't. What are these critical input options you mentioned?

---

### Post by em3raldxiii on 2008-02-26
Wow, fantastic help guys!  Looks like I will probably aim at the Delta 1010 with the breakout box.  I don't need mobile, although I can certainly think of times when I would use it.  I was kinda working against myself with the whole firewire thing anway - I've never used a firewire device for anything, ever, on any system.  I have, however, used plenty of PCI devices.

Just for some additional background, this will eventually (rather soon, actually) be for my wife's home studio.  The band-website link in my signature usually points to their webserver, but it's offline right now (new router, I forgot to configure http port forwarding, and now I am at work, 300 km away).  Anyway, ideally I will have enough inputs to connect a decent (8pc +) electronic drum kit and record each drum on it's own track.  Not to mention everything else involved with recording a full band.  Plus if they ever get their collective arses in gear, I could use a mobile solution to record them live.  But that's not quite as critical.

Anyway, thanks to everyone ... and by all means, keep discussing ... more info is better, and I bet I am not alone :D

---

### Post by chipants on 2008-02-26
> **em3raldxiii said:**
> Wow, fantastic help guys!  Looks like I will probably aim at the Delta 1010 with the breakout box.  I don't need mobile, although I can certainly think of times when I would use it.  I was kinda working against myself with the whole firewire thing anway - I've never used a firewire device for anything, ever, on any system.  I have, however, used plenty of PCI devices.

Just for some additional background, this will eventually (rather soon, actually) be for my wife's home studio.  The band-website link in my signature usually points to their webserver, but it's offline right now (new router, I forgot to configure http port forwarding, and now I am at work, 300 km away).  Anyway, ideally I will have enough inputs to connect a decent (8pc +) electronic drum kit and record each drum on it's own track.  Not to mention everything else involved with recording a full band.  Plus if they ever get their collective arses in gear, I could use a mobile solution to record them live.  But that's not quite as critical.

Anyway, thanks to everyone ... and by all means, keep discussing ... more info is better, and I bet I am not alone :D

nice. i love m-audio stuff.

so, what are you using on the software side of things for recording? ardour, perhaps? (errr... not to veer to far off-topic)

well, let us know when you've actually finished some recording with your new setup.

---

### Post by em3raldxiii on 2008-02-26
Yup, will be using ardour for sure.  I've used it to record them before, using a craptacular SB Live! audio card.  It worked okay, but I didn't really like how complicated getting JACK configured was.  Overall, I found what the app DID was very cool, but it's interface left a lot to be desired.  It'll be a couple of weeks before I am ready to roll because I am scheduled for a whole SLOUGH of overtime at work.  In the next couple of weeks, I am only going to be home for a day and a half.  But after that I am scheduled for a few sets of 5 days off in a row, so you can expect serious headway.

Ideally I'd get some decent monitor speakers too, but again, I can work with what I have for now.  The ones I have aren't totally unbiased, but they'll do.  

So, I will probably buy a Delta 1010 with breakout box, but I might rent one from the local music store first if I can.

And if you are mildly interested in the TYPE of music I'll be recording, my wife's band also has a myspace page ... it's [www.myspace.com/anxietyofinfluence](www.myspace.com/anxietyofinfluence) .... Check 'em out :D

---

### Post by ogden_freen on 2008-03-02
I unfortunately bought an 1814. It's a nice piece of hardware, BUT..
It is not supported in linux and wont be any time soon. Something about a different chip to most of the other firewire units.
FFADO says it's not supported, and M-Audio has told me they have no plans for linux support of any of their products (they even referred me to the now defunct FreBob project!)

Buying this unit is the only reason I still have a windows partition. I unfortunately didn't do enough research first. :(

If you have to go with the anti-linux M-Audio company, the 1010 or 1010LT seems the best option.

Me, I'm never giving them another cent until they join us in the 21st century and SUPPORT LINUX!

---

### Post by JæKæ on 2008-03-03
Hey guys, I'm new to Ubuntu, and exploring Ubuntu Studio. I'm considering getting the M Audio Audiophile Firewire interface. FreeBob list it as a device that 'should' work. However, I will need a PCMCIA firewire card to use it. 
I will be using it to record from vinyl to FLAC.
Any thoughts on this?

---

### Post by chipants on 2008-03-03
> **ogden_freen said:**
> (they even referred me to the now defunct FreBob project!)

Buying this unit is the only reason I still have a windows partition. I unfortunately didn't do enough research first. :(

If you have to go with the anti-linux M-Audio company, the 1010 or 1010LT seems the best option.

Me, I'm never giving them another cent until they join us in the 21st century and SUPPORT LINUX!

well, the freebob project IS the ffado project. they just recently changed their name. i'm actually pleased and surprised that m-audio directed you to them. it shows that they're becoming more aware of the community. that's a very good thing.

i hate to say it, but you'll be hard-pressed to find ANY company making professional audio gear that fully supports linux. the best we've really gotten is a small number of companies that have been relatively open with their hardware specifications or basing their products on common chipsets, thus allowing the OSS community to create drivers.

m-audio may not be releasing linux drivers, but either is anybody else. don't assume that just because some firewire audio interfaces are supported under linux, that means that the manufacturer helped at all. the reason the freebob/ffado project supports as many devices as it does is because all (well, most) of the devices they support are running the bebob firmware.

as far as audio hardware companies go, m-audio are generally more standards-compliant than most. almost every m-audio interface (except the firewire ones) is pretty much plug and play.

i have several m-audio products and have not had any trouble getting them to work under linux.

while i agree that linux support would be great in the professional audio hardware world, there are a more than a few reasons why the industry is unlikely to embrace us yet. first and foremost, musicians and engineers buying professional audio interfaces are a relatively small niche to begin with. the linux chunk of the professional audio market is effectively non-existent, from a fiscal point of view.

that sucks, but it's the truth, for the moment. our best hope is keep developing awesome open-source audio software. only with more users being drawn to the platform will support from the manufacturers come. in the meantime, we'll continue to do what we always have: reverse engineer and keep begging for hardware specs!

---

### Post by chipants on 2008-03-03
> **JæKæ said:**
> Hey guys, I'm new to Ubuntu, and exploring Ubuntu Studio. I'm considering getting the M Audio Audiophile Firewire interface. FreeBob list it as a device that 'should' work. However, I will need a PCMCIA firewire card to use it. 
I will be using it to record from vinyl to FLAC.
Any thoughts on this?

i wouldn't use any firewire interface unless you knew is FULLY supported. not just 'should work'. and by the way, the FW audiophile is NOT officially supported. it says it 'should work' if the firmware is downloaded first. this is NOT a plug-and-play solution.

since you really only plan to transfer your vinyl, latency is not very important. an expensive (and not well-supported) firewire interface is not the best idea. there are several well-supported USB audio interfaces that should be much more appropriate for your needs.

[http://www.qbik.ch/usb/devices/showdevcat.php?id=7](http://www.qbik.ch/usb/devices/showdevcat.php?id=7)

that site is pretty useful for finding out if a USB device is compatible with linux.

---

### Post by cryptout on 2008-03-10
I bought a Focusrite Saffire LE firewire device Saturday. I checked the [ffado]("http://www.ffado.org/?q=devicesupport/list") site first and it's in their supported list.

I installed Ubuntu Studio and also 64Studio but I could not get any sound out. I even compiled the latest ([snv]("http://freebob.sourceforge.net/index.php/Compiling_from_SVN_HOWTO")) sources but still no sounds.  

Then I [read something]("http://parumi.wordpress.com/2006/12/19/getting-firewire-audio-work-on-linux/#comments") about upgrading firmware via Mac or Windows but the focusrite site showed no firmware upgrades.


I really don't like M$ or O$X but I was at my wits end so decided to at least install windows and test if the device was broken so I could return it. To my relive it was not broken in windows and just worked. 

Now the good news, when I booted back in Unbuntu Studio (64bit) the device worked! 

So long story short, it seems that in some cases you need to "initialize" the Saffire Le before it works. I've spend a good 4 hours in Ardour last night without a single drop out or quirk. 

@jouzts 
Install a fresh Ubuntu Studio and go from there, my device worked "out of the box" (after initializing it…)

---

### Post by chipants on 2008-03-11
> **cryptout said:**
> I bought a Focusrite Saffire LE firewire device Saturday. I checked the [ffado]("http://www.ffado.org/?q=devicesupport/list") site first and it's in their supported list.

I installed Ubuntu Studio and also 64Studio but I could not get any sound out. I even compiled the latest ([snv]("http://freebob.sourceforge.net/index.php/Compiling_from_SVN_HOWTO")) sources but still no sounds.

that's good info. you should post on the ffado site's list of working setups and detail your experience. the developers and users always appreciate that sort of help.

---

### Post by theophane on 2008-04-03
> **cryptout said:**
> 


Now the good news, when I booted back in Unbuntu Studio (64bit) the device worked! 

So long story short, it seems that in some cases you need to "initialize" the Saffire Le before it works. I've spend a good 4 hours in Ardour last night without a single drop out or quirk. 

@jouzts 
Install a fresh Ubuntu Studio and go from there, my device worked "out of the box" (after initializing it…)

This might be the information I was looking for :)

---

### Post by Stochastic on 2008-04-04
> **cryptout said:**
> I bought a Focusrite Saffire LE firewire device Saturday

snip.

So long story short, it seems that in some cases you need to "initialize" the Saffire Le before it works. I've spend a good 4 hours in Ardour last night without a single drop out or quirk. 

@jouzts 
Install a fresh Ubuntu Studio and go from there, my device worked "out of the box" (after initializing it…)

This shouldn't be needed.  I had a Saffire LE before I returned it for my FirePod and it worked without initializing anything as I only run UbuntuStudio on my computer.  What you experienced may be something very small that caused the first hiccup.  Possibly not having the device plugged in and turned on when booting your computer?

---

