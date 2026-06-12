---
title: "TV Tuner"
date: 2006-09-26
forum: Multimedia &amp; Video
---

### Post by confusimo on 2006-09-26
I'm a total noob so go slow.  I can't tell you how many times I've reinstalled Windows XP.  And I'm no linuxpert.  And I haven't used any in a while, few years.  Lot has chaneged since so I gave a few a try.  Ubuntu is the best so far.  6.06 64 bit.  No issues.  

I got this PCI thing to allow me to use my existing Orinoco Gold Classic Wireless B card and right away without any drivers I'm on the internet.  And thumb drives Auto detect without mounting them first.  Everything is smooth.

But I wan't to watch TV on my PC.  And I haven't found any good info here or on google.  I have a custom built ECS-915P-A v1.2, Celeron D 3.06 GHZ 64bit, 1gb PC2700 and running Ubuntu of a SATA II 160GB WD HD.  And BFG Nvidia PCI Express Video Card.

I already have a TV Tuner box.  Works well with XP.  But not ubuntu.  I managed to install TVTIME for the packager manager thingee.  I forget what it's called. 

It's a Cute TV USB from Startech.  They said VVMER is the chipset.  But not sure exactly which number.  I never found anyone else with VVMER here or any where else.

TVTIME keeps saing dev0 not found or something like that.

If not can I buy one of these.

[http://teenlounge.org/ubu/tvt](http://teenlounge.org/ubu/tvt)

Which is the best of those.

Thanks,
Confusimo

---

### Post by pseudonym on 2006-09-26
Don't know anything about your USB tuner, but if you want a recommendation from your list, Hauppauge have a good reputation. You should also check out [www.linuxtv.org](www.linuxtv.org) if you haven't already.

---

### Post by confusimo on 2006-09-26
Ya, but from what I've read most of Hauppauge work with BTTV or what have you.  But most is not all.  So specifically which one of the Hauppauge's is OK from that list.?

And is it auto detect or what?

Thanks,
confusimo

---

### Post by pseudonym on 2006-09-26
They all look like really old cards which Hauppauge don't appear to list at their website any more. Neither does linuxtv.org mention them. The fact that they are old may mean they are supported, but if you want to have more reliable information, have a look at [this list]("http://www.linuxtv.org/wiki/index.php/Hauppauge") . The newer model Hauppauge cards use the Conexant cx88 driver, which has been well supported since about kernel 2.6.13 . It's what my card uses and I can vouch for it's quality (even though it's a fairly cheap card).

---

### Post by confusimo on 2006-09-26
But was yours auto detect or did you have to do anything to it or the settings of Ubuntu.  And which application are you using.

---

### Post by pseudonym on 2006-09-26
When I bought the card I had to recompile my kernel with a special patch, but since 2.6.14 it has been natively supported. Put simply, if the kernel supports your card it will be autodetected at startup and the appropriate modules loaded. You then only need to tune the card with a scanning app (see below).

As for viewing apps, I recommend gxine or xine-ui, or the xine-based kaffeine if you use Kubuntu (probably the easiest to set up and use). Mplayer also works well but is less user friendly. Same with vlc last time I checked.

You also need some utilites packages to help with channel scans. I recommend dvb-utils and dvbsnoop for that purpose. The second one is handy for monitoring signal strength.

---

### Post by confusimo on 2006-09-26
I don't have KDE and this is what I downloaded.

[http://ubuntu-releases.cs.umn.edu//6.06/ubuntu-6.06.1-desktop-amd64.iso](http://ubuntu-releases.cs.umn.edu//6.06/ubuntu-6.06.1-desktop-amd64.iso)

I installed TVTIME.  Will that be enough.

[http://tvtime.sourceforge.net/downloads.php](http://tvtime.sourceforge.net/downloads.php)

Thanks,
confusimo

---

### Post by pseudonym on 2006-09-26
I tried tvtime a while back and found the current release didn't play well with my card. It also seemed to be best designed for analogue tuners, too. Plus you can't record with it either. 

But you may have better luck. It's really just a matter of trying out various apps and seeing which one a) works best with your card and b) you prefer for ease of use etc.

---

### Post by confusimo on 2006-09-26
I installed kaffiene but I don't see anythinbg about changing chanels.  All I see DVB.  But I've never used a Digital anything.

---

### Post by pseudonym on 2006-09-26
When you ran it for the first time did it detect your tv tuner? It is a digital tuner you've got, right? I haven't used kaffeine for a long time, but you first set up your channels in the configuration options. Check the menus at the top, they should be easy to follow. There should be a list of transponders for your area - pick the one that's closest to you, tell kaffeine to scan, and a list of channels should show up. You then choose which ones you want to add to your permanent channel list.

---

### Post by confusimo on 2006-09-26
No I've never used anything digital.  It's all analog.  No it didn't auto detect.

Thanks,
confusimo

---

### Post by pseudonym on 2006-09-27
Sorry, I must have misread your earlier posts. I assumed your usb device was for digital tv. I've never owned or used an analog tuner, but still might be able to give you some tips to get it working.

First, check what the system knows about it by opening a terminal and running the command 'lsusb' to list usb devices connected to your computer, and post back with what it says...

---

### Post by confusimo on 2006-09-27
[http://teenlounge.org/ubu/tv1](http://teenlounge.org/ubu/tv1)
[http://teenlounge.org/ubu/tv2](http://teenlounge.org/ubu/tv2)

TV 1 is when when I pluged in the USB tuner.

And TV 2 is when I unplugged it and reran lsusb.  So obviously the winbond thing is it.

Thanks,
confusimo

---

### Post by pseudonym on 2006-09-27
So it gets detected as a webcam? That's not looking good.

But because it's an analog device, tvtime should be the right application. For some info about the state of support for usb video devices in linux, go [here]("http://www.linuxtv.org/v4lwiki/index.php/Main_Page"). You should also hit up the [tv time website]("http://tvtime.sourceforge.net/") for help, too, because, for the device you've got, it's more of a linux support issue rather than an Ubuntu-specific one.

Sorry I couldn't be of more help, but I've never used that sort of video device and don't know much about them.

---

### Post by confusimo on 2006-09-27
Ya, I've seen those and it's not supported.  I just thought it might be something else.  Even as a web cam though it should say something other than dev0 not found in tvtime.  I at least should get it input something.  Cuz there is RCA and Svideo input.  So can I at least input something.  Do I need to add anything or am I completely in need of a new device.

---

### Post by pseudonym on 2006-09-27
To get any hardware to work in linux, the system must be able to create device files for it. If that's not happening yet with your hardware, then you won't be able to get anything out of it at all.

If you're looking for the easiest thing to do, my suggestion is to buy a tv card which you know is supported in linux. It will of course cost some money, but you will likely save a lot of time and possibly frustration.

If you want to keep trying with the one you've got, you're better off asking the experts -  like linuxtv and tvtime users/developers. Your device is not listed among the supported cards, but someone there may have written a kernel patch for it in the meantime. To make use of that you would need to rebuild your kernel. That's a challenging task for someone new to linux, but a very good learning opportunity as well.

---

### Post by confusimo on 2006-09-27
I'll just but a new one thanks.

[http://winbond-webcam.sourceforge.net/](http://winbond-webcam.sourceforge.net/)

[http://winbond-webcam.sourceforge.net/getreadme.php](http://winbond-webcam.sourceforge.net/getreadme.php)

[http://sourceforge.net/projects/winbond-webcam/](http://sourceforge.net/projects/winbond-webcam/)

They are working on something but I'll just get another one.  That'll be easiest.

Thanks,
confusimo

---

### Post by pseudonym on 2006-09-27
Well, now I'm confusimo, confusimo :) Are you saying the thing you plugged in yesterday actually was a Winbond Webcam, and not that Cute! TV Tuner you mentioned first up?

If so, then it should be supported. See [here]("http://www.linuxtv.org/v4lwiki/index.php/Webcams"), which includes a link to the 'official' webcam howto.

---

### Post by confusimo on 2006-09-28
No it is a tv tuner.  But its detecting as webcam in lsusb.  So maybe I can just use it as a webcam at least if nothing else.  Otherwise I'll just buy a new tuner.

---

### Post by pseudonym on 2006-09-28
So it's a TV tuner with webcam functionality? Bottom line - If it's *not* actually a webcam, or a device that doubles as a webcam, then you will *not* be able to use it as a webcam. The fact that it is detected as such by Ubuntu is immaterial - that's just a quirk in linux, common with unsupported hardware.

Sorry if this sounds trite, but for me to help you out correctly, I need to know we are talking about exactly the same thing.

---

### Post by confusimo on 2006-09-28
But even in Windows XP it detects as a capture device.  So if I just set it up as so in linux and not as a tv tuber it may work.  It doesn't say tv tuner in Windows either.  It says Capture device.  And their software does all the work.  Dirvers are imiterial.  The software handles the tv.  So if I just set it up as a capture device in linux it may work.  I can fiddle around with different softwars.  But if I just set the drivers as webcam, capture device, or what ever it might work.  If that's too confusing I'll just get another tuner.  No bigee.

Thanks,
confusimo

---

### Post by pseudonym on 2006-09-28
OK, that's up to you, of course. Just one thing FYI, though - Windows device manager always has TV cards listed under 'Video Capture Devices'. I know mine is. THey are just one of a family of such devices, because they all tend to include at least one video input port, apart from the TV tuning functionality.

---

