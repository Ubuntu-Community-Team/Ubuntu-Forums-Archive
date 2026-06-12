---
title: "A very troubled Ubuntu virgin"
date: 2009-12-25
forum: Networking &amp; Wireless
---

### Post by thomasthefinch on 2009-12-25
Let's pretend for a moment, that I am a complete idiot and don't know much about Ubuntu.
 
Alright, we don't need to pretend.
 
My name is Thomas, and I am sick of Windows, and I hate Macs. I decided, as a bit of a test, to install Ubuntu on my Laptop after one too many windows problems.
 
I am running a HP NX6235 laptop, and I can't get the wireless to work. I've read about having to convert the drivers for windows to Ubuntu, but I don't really understand them. Could anyone post a few simplistic steps on how to actually set it up? I'm a bit confused by all the "guides".
 
Secondly, when I close my screen, my laptop sleeps itself. However when I open it up and press the power button, it doesn't wake from this state, the lights come on but the screen doesn't and the fan doesn't start up. Again, I don't know what I'm doing.
 
I hope to see some of the legendary linux community help :)
 
Thanks
 
Thomas

---

### Post by thomasthefinch on 2009-12-25
Update:
 
After doing a bit more reading, I have read that for many their wireless card works straight away on 9.10?  So I'm not sure.  Am I just being stupid and not having a box checked or something similar?  If I click the connectivity bars (which are reading no connection), the wireless networks option is greyed out, and says device not ready underneith it.  I'm not sure if this info is any use for anyone?

---

### Post by bruno9779 on 2009-12-25
It may sound stupid, but since it is grayed out, is the switch for the wifi on? if it is, could you please post the result of the following command in terminal?

```
lspci
```

Regarding the laptop lid, you should be able to configure it's behaviour in power manager.

to access it right click on the battery icon

---

### Post by GregBrannon on 2009-12-25
Is this one of the guides you're confused by?

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

If not, give it a try and report results.  If this guide is too much, provide more details:  What are you seeing, not seeing?  What have you tried?  What were the results?  Is your wireless device recognized?  Etc.  Anything you can add will help at this point.

The experts here will get you through this.  Be patient, especially considering the season. The answer is nigh.

---

### Post by thomasthefinch on 2009-12-25
[FONT=Times New Roman][SIZE=3]thomas@thomas-laptop:~$ lspci[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]02:01.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]02:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]02:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]02:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]02:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]30:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][EMAIL="thomas@thomas-laptop:~$"]thomas@thomas-laptop:~$[/EMAIL] [/SIZE][/FONT]
 
 
 
 
 
 
 
 
And in response to the second poster, thank you for your positive attitude!  I'll check out that link now and see if it provides any results.  You are going to have to treat me like an idiot, I literally know nothing.  I'm coming in completely clean.  The latest thing I am trying is following broadcoms own readme file, but I can't seem to get the path right in the command lines?  It's just a tar file (i'm assuming that means compressed?) on my desktop.  I can't get the command line right for it's location?
 
And I appreciate the season :)  this is my form of relaxing almost haha!  Although I'm sure computer problems on Christmas day usually revolve around people not being able to install new games heh

---

### Post by thomasthefinch on 2009-12-25
> **bruno9779 said:**
> It may sound stupid, but since it is grayed out, is the switch for the wifi on? if it is, could you please post the result of the following command in terminal?
 
```
lspci
```
 
Regarding the laptop lid, you should be able to configure it's behaviour in power manager.
 
to access it right click on the battery icon
 
 
Oh, the button by my F buttons isn't working.  It isn't reacting to being pushed, either way.

---

### Post by thomasthefinch on 2009-12-25
> **GregBrannon said:**
> Is this one of the guides you're confused by?
 
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
 
If not, give it a try and report results. If this guide is too much, provide more details: What are you seeing, not seeing? What have you tried? What were the results? Is your wireless device recognized? Etc. Anything you can add will help at this point.
 
The experts here will get you through this. Be patient, especially considering the season. The answer is nigh.
 
I just tried the lshw command, and among a huge list of bits and pieces, it said *-network DISABLED under the wireless controller part.  Could this be my problem?

---

### Post by snowpine on 2009-12-25
Broadcom 4312 is easy to get working.

1. Connect to internet using wired ethernet
2. Go to the System menu and choose Administration, Hardware Drivers
3. Click to activate the Broadcom STA driver
4. Reboot and enjoy!

(this assumes you're using the latest Ubuntu 9.10)

---

### Post by thomasthefinch on 2009-12-25
> **snowpine said:**
> Broadcom 4312 is easy to get working.

1. Connect to internet using wired ethernet
2. Go to the System menu and choose Administration, Hardware Drivers
3. Click to activate the Broadcom STA driver
4. Reboot and enjoy!

(this assumes you're using the latest Ubuntu 9.10)


I am now writing to you from my Ubuntu laptop!! But unfortunately I'm still hardwired...

Am I missing a step here?  I have connected to the internet, and having gone to system menu and choosing admin, hardware drivers, nothing appears in the list.

Am I missing out a step such as searching for drivers online etc?

---

### Post by Avidanis on 2009-12-25
> **thomasthefinch said:**
> I am now writing to you from my Ubuntu laptop!! But unfortunately I'm still hardwired...

Am I missing a step here?  I have connected to the internet, and having gone to system menu and choosing admin, hardware drivers, nothing appears in the list.

Am I missing out a step such as searching for drivers online etc?


Did you click on Hardware Drivers while connected ? It should of searched your system for hardware and downloaded drivers. You need to click on Hardware Drivers while connected to internet .

---

### Post by snowpine on 2009-12-25
> **thomasthefinch said:**
> I am now writing to you from my Ubuntu laptop!! But unfortunately I'm still hardwired...

Am I missing a step here?  I have connected to the internet, and having gone to system menu and choosing admin, hardware drivers, nothing appears in the list.

Am I missing out a step such as searching for drivers online etc?

That's funny; Ubuntu automatically detected my Broadcom 4312-equipped Dell Mini. Ubuntu usually has excellent hardware detection. Sorry I am out of ideas... :(

---

### Post by thomasthefinch on 2009-12-25
Yep I did that! Shall I just try it again?  Or maybe I already have the hardware for it, and it's just not enabled?  Seems more likley perhaps if it isn't detecting the hardware?

---

### Post by bshosey on 2009-12-25
OK go into terminal and type this

sudo apt-get install b43-fwcutter.

Then when done reboot system and you should have wireless.

---

### Post by Avidanis on 2009-12-25
When you click on hardware drivers a little applet runs and it tells you it is searching your system for hardware and will download any needed drivers.

When it is done ( In about 20 sec.) You should see something like this.

---

### Post by thomasthefinch on 2009-12-25
> **Avidanis said:**
> When you click on hardware drivers a little applet runs and it tells you it is searching your system for hardware and will download any needed drivers.
 
When it is done ( In about 20 sec.) You should see something like this.
 
Yeah, the little box sometimes pops up and searches, other times it doesn't.  Sometimes it just skips straight to that screen, but it's always completely empty and just says "your system contains no proprietary drivers" or something similar.

---

### Post by Avidanis on 2009-12-25
> **bshosey said:**
> OK go into terminal and type this

sudo apt-get install b43-fwcutter.

Then when done reboot system and you should have wireless.


Did you try this ?

---

### Post by thomasthefinch on 2009-12-25
Ok! I read some info that said if you see the -*DISABLED thing when you use the lshw command, that is generally the problem.  So the device is working but not enabled.  However the button on my computer to activate the wireless doesn't work in Linux, so I need to find out how to enable it.  But the article also said there is so many variabled.
 
Anyone have any idea?

---

### Post by thomasthefinch on 2009-12-25
> **Avidanis said:**
> Did you try this ?
 
Just tried it now, and it says E: Couldn't find package b43-fwcutter... do I need to be online for it to work?

---

### Post by bshosey on 2009-12-25
Yes you need to be wired in first

---

### Post by thomasthefinch on 2009-12-25
> **bshosey said:**
> Yes you need to be wired in first


I'm wired online now and it's still coming up with this

thomas@thomas-laptop:~$ sudo apt-get install b43-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package b43-fwcutter

---

### Post by bshosey on 2009-12-25
OK Try this. 
go to System>Administration>Software Srouces
Enable all in the Ubuntu Software tab

Then try running the command

---

### Post by thomasthefinch on 2009-12-25
*-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:ee:97:c2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg



This appears when I do lshw command.  Is this indicative of everything working but it not being enabled??

---

### Post by Avidanis on 2009-12-25
Check your software sources. These can be found under System/Administration/Software Sources

Does yours look like this ?

---

### Post by thomasthefinch on 2009-12-25
> **Avidanis said:**
> Check your software sources. These can be found under System/Administration/Software Sources

Does yours look like this ?


Yep, except it says United Kingdom instead of United States

---

### Post by thomasthefinch on 2009-12-25
Just a quick note, might be of use because it seems similar to the not being able to find anything to download problem...
 
I just tried to view something that needed flash, and it found the different pluggins for Ubuntu, but wouldnt download any of them because it said it couldn't locate the file?

---

### Post by bshosey on 2009-12-25
Try changing the to Main Server in Software Sources.

---

### Post by thomasthefinch on 2009-12-25
Good show! that allowed me to select the driver, but it's still not letting me connect to wireless.

Still though, that's one step made :)

---

### Post by bshosey on 2009-12-25
Did you restart after install the b43-fwcutter? and also sound crazy but make sure the antenna is on.

---

### Post by thomasthefinch on 2009-12-25
> **bshosey said:**
> Did you restart after install the b43-fwcutter? and also sound crazy but make sure the antenna is on.
 
 
Ah! I'll try the restart now.  But! Like I've said, I have a button on the laptop for switching the antenna on and off, but it doesn't seem to be supported.  The blue light is off, and pressing the button doesn't turn it on.  Does this mean it's disabled?

---

### Post by bshosey on 2009-12-25
It will not untill the firmware is loaded and the firmware will not load until reboot is done.

---

### Post by bshosey on 2009-12-25
One common problem I have noteiced with the fwcutter is that if the intenna is off during boot some times you have to reboot after turning on the antenna. But I also have this problem with windows at times too.

---

### Post by thomasthefinch on 2009-12-25
My wireless is working :)

Guys, I can honestly say this is the best community support - for anything - I have ever recieved.  Thank you for your speedy replies and patience with my inexperience.  Merry Christmas to you all.

Having said that, I'm sure you will all grow sick of me over the next week or two when I ask a million and one questions ;)

---

### Post by Avidanis on 2009-12-25
I usually have to leave my radio switch off until right after I login . For some reason if I don't the wireless network is not connected to .

---

### Post by bshosey on 2009-12-25
I am very glad it worked. I always try to help when I can. Every one of us at one time was new to linux. To be honest you will learn even more helping people.

So Ask a way. I will help when I can.

Merry Christmas to you too and everyone else in the forums.

---

### Post by Avidanis on 2009-12-25
Good job bshosey. You were basically a step ahead of me so I just followed the thread. I'm really glad he got you on track  mr. finch . Merry Christmas to all of you as well.

---

### Post by Avidanis on 2009-12-25
One last thing if you could **mark this thread as solved** it will help others who may encounter the same difficulties you had and save everyone some time.

---

### Post by bshosey on 2009-12-25
Tell you a funny story. I have a Dell Inspiron 1721. That is proabably one of the worst machines to have linux one. Not because it is a bad machine. It just has allot of hardware that is a pain to get working. I was about to give up acouple times. Then I decided to try to put Windows XP on. I had to locate drivers from other machines to get it to work and then was disappointed by the performance. I decided to try linux again. I struggled with it but always got it to work. Using this forum. This machine only has support for Vista from dell. Vista was real slow on it crashed al the time. Now I started with ubuntu 7.04 on the 1721 every version of ubuntu gets beter and beter on this machine. I am not kidding. This actually gets faster for every release and easier to set up. So yes ubuntu is getting better and better.

---

### Post by thomasthefinch on 2009-12-25
I'm not sure, how do I mark it as solved?

Also guys, I think I'm getting the hang of this already.  I've managed to install several programs through synaptic, it's great.  I love this OS already.

---

### Post by bshosey on 2009-12-25
This is funny I forgot how to mark a thread resolved. I thought it was in the Thread Tools.

update. It is in the Thread Tools

Mark Thread as Solved.

So when you get a chance could you please mark it as resolved.

---

