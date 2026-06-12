---
title: "Line6 POD 2.0 patch manager!"
date: 2006-03-29
forum: Multimedia &amp; Video
---

### Post by dolson on 2006-03-29
Just as an FYI, I finally found a good patch editor/manager for my Line6 POD 2.0 device.

It's called JSynthLib, and it supports many different hardware synths and other MIDI gear.

The only limitation is that it can not load the *.l6t files that you get from the CustomTone page.

To work around this, I run PODMAN32 in Wine, load any *.l6t files I want, and save them to the POD. Then I can save/export/edit them in JSynthLib.

It's a very awesome application, and all you need to run it is Java. [www.jsynthlib.org](www.jsynthlib.org) is the URL.

I don't think it works with the PODxt devices, but you guys have a USB kernel driver included in Ubuntu anyhow (Dapper at least).

Here's a screenshot:
[IMG]http://ubuntustudio.com/wiki/images/b/bf/JSynthLibLine6POD2.png[/IMG]

---

### Post by rcmiv on 2006-03-31
Good info.  I am still deciding on a good, cheap method for getting guitar/bass/vocal signal into my box that will play nice in linux.

I am considering the impact of running Line 6 software in windows in a vm.  I have XP in vmplayer now, and it is very fast on my machine.  The sound, of course, is another story.

-rcmiv

---

### Post by dolson on 2006-03-31
If I were you, I would ignore the TonePort and just save up for the *useful* POD or PODxt.

I think that buying something that you KNOW will be a hassle and does not offer any kind of Linux support is kinda silly.

---

### Post by izle on 2006-08-02
hi, just to mention the drivers for the line 6 pod xt , pro , ... available at 
[http://www.tanzband-scream.at/line6/](http://www.tanzband-scream.at/line6/)

---

### Post by dolson on 2006-08-02
The podxt drivers are already a part of Ubuntu. Do not compile it from scratch, just modprobe it if you need it.

---

### Post by isabellf on 2006-08-08
podxtpro doesn't support POD 2.0 .

And it's been replaced by : line6usb [http://www.tanzband-scream.at/line6/](http://www.tanzband-scream.at/line6/)
that supports

<<driver.c:       "BassPODxt",
<<driver.c:       "BassPODxt Live",
<<driver.c:       "BassPODxt Pro",
<<driver.c:       "PODxt",
<<driver.c:       "PODxt Live",
<<driver.c:       "PODxt Pro",

so you need to build from source for a PODxt

---

### Post by philipacamaniac on 2006-08-09
Please, someone post back here when a GUI patch editor becomes available for the PODxt series. The driver from [http://www.tanzband-scream.at/line6/](http://www.tanzband-scream.at/line6/) makes that possible, and fairly easy (it creates a MIDI interface that can directly control any parameter), but I'm not a developer and so don't know where to begin to create a GUI myself. I started designing one in Glade, but that got old and frustrating real quick.

(and no, old POD 2.0 stuff doesn't work at all with the PODxt series - it's an entire structure redesign).

---

### Post by dolson on 2006-08-09
> **isabellf said:**
> podxtpro doesn't support POD 2.0 .

--snip--

so you need to build from source for a PODxt

What? How do you expect the USB driver for PODxt devices to support the POD 2.0, when it has no USB port?

And why are you saying that you need to build from source for a PODxt? The author of that driver told me that it would work fine. Just because there is a newer version doesn't mean that people have to go off and start compiling things.

Looking at the changelog, the only thing that was added was read-only support for the Variax, and a name-change. And the latest release supports HAL. I wouldn't be bothered to upgrade-by-compiling-source-code unless the included module did not work for me.

---

### Post by Maxwelinux on 2007-07-10
Hello,

I prefer update this thread instead of created a new one.

With my old 6.10 Ubuntu, the system detect my POD Xt Pro when I connect it on the USB port.
I use to use the POD like a external sound card. So I can play a backing track on the PC and I listen to it with my hearphones plugged on the POD. The advantage is that when I plug my guitar on the POD I can play my guitar "like an overdub track"over the mp3 of my laptop acting as a backing track.
I do not remember how I have done it on 6.10 and no way to do this again on 7.4.
Is it possible that the POD xt pro is not recognize anymore on Feisty Fawn even if it was recognized on Edgy Eft?
Do you now few commands/actions to help me to configure my POD Xt like explain above?

Regards

Max

---

### Post by Zimmer on 2007-09-02
I too have just tried using my PodXT Live on 6.10  .

It is recognised in the Device Manager and there are then entries in the Sound Preferences but without any options to configure and an option to change to that device in the ALSA mixer, again, no controls or options with it..
Audacity has no input or out put option for the device.
I tried recording from all inputs just in case...no joy...
Every thread I have read so far seems to end inconclusively ...

I have tried 'modprobe line6usb' out of desperation :) and gotten a Fatal Module line6usb not found..
I will keep trying, though.... oh, and yes, a project has been launched for line6  
[https://sourceforge.net/projects/line6linux](https://sourceforge.net/projects/line6linux)

---

### Post by fourmiii on 2007-12-14
I just successfully compiled line6usb from source under Gutsy and it works very well .. check out this thread :

[http://ubuntuforums.org/showthread.php?t=640785](http://ubuntuforums.org/showthread.php?t=640785)

have fun !

---

