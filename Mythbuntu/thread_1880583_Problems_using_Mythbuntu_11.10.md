---
title: "Problems using Mythbuntu 11.10"
date: 2011-11-14
forum: Mythbuntu
---

### Post by bpmod on 2011-11-14
Hello

I am new here and this is my first post. I am not new to linux, although I wouldn't call myself extremely knowledgable. And I am no stranger to computer hardware & software in general, being in the business for almost 20 years.

For the past year or so, I have been using GB-PVR & NextPVR on Windows XP using a couple of ATI TV Wonder HD 650's, one USB and one PCI-e. I have discovered that I no longer want to use Windows, and went in search of a good PVR for my computer. Since I had everything working on my XP machine, I decided to go brand new hardware. Here's what I got:

Motherboard: Asus P8Z68-V LX
CPU: i3-2120
RAM: 8GB Corsair DDR3
No tuners yet, but I plan to use an HDHomeRun (or more) and a Hauppauge 2250. I intend to initially use this machine as a combo frontend/backend and change it to a dedicated backend once I can afford to get another frontend.

I have a 10TB NAS (almost identical specs, running FreeNAS 8.0), so I plan to use that for all my files and have installed Mythbuntu to a CF card.

The initial installation went reasonably smoothly. Except no mouse. I have a ps2 mouse and keyboard and the board has only one ps2 port. If I connect the mouse to the ps2 port & the keyboard through a ps2-to-usb adapter, I get no keyboard or mouse. If I use a two-ps2-to-one-usb adapter and connect both kb and mouse through that, I get keyboard but no mouse. If I connect the keyboard through ps2 and the mouse through the ps2-usb adapter, no mouse.

So, I have not been able to click on any of the options I would like to select during installation. But I proceeded with the default installation, just to see how things went.

The next problem is that I get a notice near the top-right corner of the screen periodically that tells me I have lost the wired connection1 (or some such) and I have no idea why or how to get it back. When this happens, both the light on the ethernet port and the one on the switch are green, so I know it hasn't lost its connection.

Of course, I do not have the option to click anything anyway.

I have been trying to navigate around using the keyboard, but that usually gets me nowhere.

I am sure that if I could just get mouse support, I'd find this much much easier.

Any ideas?

Thanks

Brian

---

### Post by nickrout on 2011-11-14
Unless I missed something, have you tried a usb mouse? (go on splash out!)

---

### Post by bpmod on 2011-11-14
Actually, no. First because it was Sunday evening and no place open to purchase one, and second, because I do not want to have two mouses on my desk.

I suppose I can try to use a usb mouse to try the setup, as after everything is working, I won't need a mouse anymore. That is, I think I've read that MythTV can be controlled remotely through a web interface.

I'll let you know how that works

Thanks

Brian

ETA: I have almost the exact same system (LE rather than LX mobo; 4GB CF rather than 8GB) on my FreeNAS unit (as mentioned earlier), and the same mouse works on that when plugged into the 2-ps2-to-usb adapter. That's the main reason why I didn't even think to *try* a usb mouse.

---

### Post by bpmod on 2011-11-14
UPDATE:

I borrowed a usb mouse. The installation went swimmingly.

And whatever was causing my ethernet connection to intermittently disappear seems to have resolved itself.

However, when mythtv is running, my mouse disappears again. It is extremely difficult to set things up when you can't click and you can't find the correct keystrokes. It comes back again as soon as I exit, but clicking the OK button to exit is troublesome because I cannot find a keystroke that triggers it.

Now, it would just happen that my Windows XP machine went south on me. Completely dead. Power, but no post.

So now, getting this thing recording has become urgent.

My HDHomeRun has not yet been delivered, and I couldn't find stock in my local computer store of any tuner that will work in MythTV (or at least none that is known to work). There is some ambiguity as to whether my ATI USB unit will work. My research has shown that the ATI TV Wonder HD 600 USB works with a firmware download. But nothing mentions my HD 650 (there are many mentions of 650 combo, 650 PCI-e, etc., but none with my exact model name). So I am wondering if this tuner is supported.

It is shown as "ID 0438:b003 Advanced Micro Devices, Inc." when I enter lsusb. That gives me some hope.

[http://linuxtv.org/wiki/index.php/ATI/AMD_TV_Wonder_HD_600_USB](http://linuxtv.org/wiki/index.php/ATI/AMD_TV_Wonder_HD_600_USB) shows the following:
> The device identifies itself as a "Advanced Micro Devices, Inc" and the  subsystem information provided by lsusb -v is 0438:b002.  

Has anybody used this tuner successfully?

Thanks

Brian

---

### Post by nickrout on 2011-11-14
> **bpmod said:**
> UPDATE:

I borrowed a usb mouse. The installation went swimmingly.

And whatever was causing my ethernet connection to intermittently disappear seems to have resolved itself.

However, when mythtv is running, my mouse disappears again. It is extremely difficult to set things up when you can't click and you can't find the correct keystrokes. It comes back again as soon as I exit, but clicking the OK button to exit is troublesome because I cannot find a keystroke that triggers it.

Now, it would just happen that my Windows XP machine went south on me. Completely dead. Power, but no post.

So now, getting this thing recording has become urgent.

My HDHomeRun has not yet been delivered, and I couldn't find stock in my local computer store of any tuner that will work in MythTV (or at least none that is known to work). There is some ambiguity as to whether my ATI USB unit will work. My research has shown that the ATI TV Wonder HD 600 USB works with a firmware download. But nothing mentions my HD 650 (there are many mentions of 650 combo, 650 PCI-e, etc., but none with my exact model name). So I am wondering if this tuner is supported.

It is shown as "ID 0438:b003 Advanced Micro Devices, Inc." when I enter lsusb. That gives me some hope.

[http://linuxtv.org/wiki/index.php/ATI/AMD_TV_Wonder_HD_600_USB](http://linuxtv.org/wiki/index.php/ATI/AMD_TV_Wonder_HD_600_USB) shows the following:


Has anybody used this tuner successfully?

Thanks

Brian

Try it and see!

---

### Post by bpmod on 2011-11-14
> **nickrout said:**
> Try it and see!
I guess my reason for asking is I don't want to download the firmware and find it doesn't work, only to discover that whatever I did will make it no longer work in Windows. Is that a possibilty?

I have had so much bad luck in the past 24 hours that I am almost afraid to do *anything*.

Thanks, though. I'll try it.

Brian

---

### Post by nickrout on 2011-11-14
> **bpmod said:**
> I guess my reason for asking is I don't want to download the firmware and find it doesn't work, only to discover that whatever I did will make it no longer work in Windows. Is that a possibilty?no, the firmware is loaded each time the computer is cold started. What does dmesg say about the firmware loading?

install linux-firmware-nonfree before downloading any firmware, as many of them are in the package.> 

I have had so much bad luck in the past 24 hours that I am almost afraid to do *anything*.

Thanks, though. I'll try it.

Brian

---

### Post by RideMan on 2011-11-14
When Mythfrontend or the mythbackend setup programs are running, you will lose your mouse pointer. This is by design because MythTV generally does not respond to mouse clicks. Arrow keys and space bar are your friends.

Did I see that you have an HVR 2250?  That card DOES work, but you have to download the firmware. There is a front page thread about it. Find that thread, go to the last page and find the links to LowSky's instructions. IMPORTANT! There is a ton of outdated information out there about this card; I spent three days trying to get modules to compile when all I really had to do was force the right firmware to load.

--Dave Althoff, Jr.

---

### Post by bpmod on 2011-11-14
> **RideMan said:**
> When Mythfrontend or the mythbackend setup programs are running, you will lose your mouse pointer. This is by design because MythTV generally does not respond to mouse clicks. Arrow keys and space bar are your friends.

Did I see that you have an HVR 2250?  That card DOES work, but you have to download the firmware. There is a front page thread about it. Find that thread, go to the last page and find the links to LowSky's instructions. IMPORTANT! There is a ton of outdated information out there about this card; I spent three days trying to get modules to compile when all I really had to do was force the right firmware to load.

--Dave Althoff, Jr.
Hi Dave

No. I *intend* to use an HVR 2250. But I cannot find one in stock anywhere nearby. I have purchased an HDHomeRun online, but it hasn't arrived yet. I spent all day today searching for an HVR 2250, but finally settled on a 1250 because it was all anybody had.

Great news, though. I plugged in the 1250, rebooted, and life is good. I was just about to start looking up how to install the drivers etc., when I realized that it was already there.

The only real issue that kept me from recording within the hour was my SchedulesDirect setup. And I am still fighting with that. I get more channels here than my SD lineup includes, so I always got around it by adding a second lineup in another city nearby. In NextPVR, I could just select one lineup or the other for each channel that I was mapping, but that doesn't seem to be possible in MythTV. If anybody has experience with multiple SD lineups, I'd love to hear from you.

However I did a partial setup so that I could get a very important show recorded, and have been playing with it since that ended successfully.

Which brings me to a new 'issue' (not a big one): The file format I am used to is .ts (transport stream), but it seems that MythTV saves files as .mpg (program stream). I thought I had read somewhere that .ts is the default setting, but I could have imagined that. Now all the info I am finding says that the default is .nuv, so I'm happy to have .mpg. But, is there a way to change that?

I did discover about the mouse on my own before I came back here too. Thanks for setting me straight on it though.

And I have completely disabled the frontend on that machine and am using the web interface. So cool!

I am going to try the ATI now. Wish me luck.

Thanks

Brian

---

### Post by bpmod on 2011-11-14
> **nickrout said:**
> no, the firmware is loaded each time the computer is cold started. What does dmesg say about the firmware loading?

install linux-firmware-nonfree before downloading any firmware, as many of them are in the package.
I'll give this a whirl and let you know my results.

Thanks

Brian

---

### Post by bpmod on 2011-11-15
> **nickrout said:**
> What does dmesg say about the firmware loading?
There is one line that says: > usb 2-1.2: new high speed USB device number 6 using ehci_hcd but mostly, the output of dmesg is hundreds of lines that all say the same thing (except for the initial numbers on each line): > [drm**[COLOR=DarkRed]:[/COLOR]**pch_irq_handler] *ERROR* PCH poison interrupt That doesn't look too healthy.

Thanks again for all your help

Brian

---

### Post by nickrout on 2011-11-15
> **bpmod said:**
> Hi Dave

Which brings me to a new 'issue' (not a big one): The file format I am used to is .ts (transport stream), but it seems that MythTV saves files as .mpg (program stream). I thought I had read somewhere that .ts is the default setting, but I could have imagined that. Now all the info I am finding says that the default is .nuv, so I'm happy to have .mpg. But, is there a way to change that?
 It is ts in a mpeg container. ask mediainfo, here is one of mine:
```
General
ID                                       : 28 (0x1C)
Complete name                            : /mnt/recordings1/recordings/2001_20111104204400.mpg
Format                                   : **MPEG-TS**
File size                                : 4.61 GiB
Duration                                 : 1h 9mn
Overall bit rate                         : 9 510 Kbps
<snip>
```

nuv is pretty well only for analogue cards where the cpu does the encoding I think.

---

### Post by bpmod on 2011-11-15
> **nickrout said:**
> It is ts in a mpeg container. ask mediainfo, here is one of mine:

Sorry. I think you may have misunderstood my question.

I know that they are currently in mpeg containers. I was asking if there is any way to save them as transport streams (.ts) by default. I always save them that way anyway after editing out commercials, but just thought I'd ask.

Also, did you get a chance to look at my dmesg output in my previous post?

Thanks

Brian

---

### Post by nickrout on 2011-11-15
> **bpmod said:**
> There is one line that says:  but mostly, the output of dmesg is hundreds of lines that all say the same thing (except for the initial numbers on each line):  That doesn't look too healthy.

Thanks again for all your help

Brian

I don't know what that error means, try google, there are plenty of responses.

What is your obsession about .ts over .mpg? Just forget it.

---

