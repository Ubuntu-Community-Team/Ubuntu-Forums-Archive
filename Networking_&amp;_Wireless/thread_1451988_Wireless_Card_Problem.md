---
title: "Wireless Card Problem"
date: 2010-04-11
forum: Networking &amp; Wireless
---

### Post by jlmclean on 2010-04-11
First, let me say that I am totally new to Linux ( and at this point, I "think" I'm going to really like it). All the termonology and ways of running programs are still total greek to me at this point, therefore any help will have to be in simple easy to understand terms. I am however doing some reading and have started getting a better understanding of the concept. I recently installed Ubuntu 9.10 on my older IBM laptop that uses a D-Link DWL G630 wireless card for internet connection. I tried to install ndiswrapper off the main CD but I'm not sure I even did that right, anyway it didn't help. I also found where you do the three downloads which includes ndisgtk but I'm doing my searching on a Windows machine and I really don't get to the place to download anything, in other words, everywhere I've been seems to be set up for Ubuntu to connect to and do the download automatically. I did find a good site that told how to do this in several layouts, including what I'm trying to do "download the drivers on the Windows machine and then install them on the Ubuntu machine", by as luck woud have it, I didn't make note of it and I have not been able to relocate it. If anyone has time and knowledge to walk me through the proper process, I would really appreciate it.
Thanks
Jerry

---

### Post by chili555 on 2010-04-11
We may be able to get your card going without ndiswrapper and its graphical interface ndisgtk. There are several versions of this card and we need to know the version you have. Let's ask the computer. Please open Applications > Accessories > Terminal and do:```
lspcmcia -v
```Write down the essential details, Product Name and Identification. Here is an example from my computer:```
Product Name:   INTERSIL HFA384x/IEEE Version 01.02 
	Identification:	manf_id: 0x0156	card_id: 0x0002
```With this information, we will know how to proceed.

---

### Post by jlmclean on 2010-04-11
Hey, Thanks, I now know where to type in all those commands. I will learn Ubuntu. 
I dont think I got what you're wanting , here's what I got: 
 
 
Socket 0 Bridge:  [yenta_cardbus]   (bus ID: 0000:00:02.0)
Configuration:   state: on      ready: unknown
Socket 1 Bridge   [yenta_cardbus]   (bus ID: 0000:00:02.1)
Configuration:   state: on      ready:unknown
Voltage: 3.3V  Vcc:3.3V  Vpp: 3.3V
CardBus card -- see "lspci" for more information
 
00:0.0 Host Bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX  Host bridge (AGP disabled)  (rev 02)
00:02.0 CardBus bridge: Texas Instruments PCI1250 (rev 02)
00:02.1 CardBus bridge: Texas Instruments PCI1205 (rev 02)
00:03.0 VGA compatible controller: Neomagic Corporation NM2160 [MagicGraph 128XD] (rev 01)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 01)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 01)

---

### Post by chili555 on 2010-04-11
Isn't your card a PCMCIA card? [http://www.dlink.com/products/?pid=DWL-G630&tab=3](http://www.dlink.com/products/?pid=DWL-G630&tab=3)

Was it actually inserted when you ran the command? Would you please remove it and reinsert it and run the command again? Maybe we can get a better result.

---

### Post by jlmclean on 2010-04-11
It gives the same information after unplugging and replugging and I unplugged, rebooted and then plugged it in and got the same results every time.

---

### Post by jlmclean on 2010-04-11
Yes that's the card I'm using. It did work fine when I had Windows on the computer. I formatted and installed Ubuntu last weekend and it had been working up to that point.

---

### Post by chili555 on 2010-04-11
Let's throw the kitchen sink at it. Please look in:```
lsusb
lspci -nn
```Do you see anything resembling your device?

---

### Post by jlmclean on 2010-04-11
The "lsusb" gets: 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 
"lspci -nn" get what I listed in the 2nd part of post #3 under where it says  see "lspci" for more information. When I put the "-nn" at the end if it, there were some difference in the number identifications but basically the same listings, nothing about the wireless card.

---

### Post by chili555 on 2010-04-11
I'm not too sure we can help a card that isn't even detected by the system; let's try. Please do:```
sudo modprobe rt61pci
iwconfig
dmesg | grep rt6
```Let's see if we have affected it in any way.

---

### Post by jlmclean on 2010-04-11
Remember, I'm new to Ubuntu. Is that three different commands or all one? Whats the mark between dmesg and grep in the third command?

---

### Post by jlmclean on 2010-04-11
OK, I think I figured it out. 
sudo modprobe rt61pci, I get nothing
iwconfig, I get: lo   no wireless estension
dmesg | grep rt6, I get nothing

---

### Post by chili555 on 2010-04-11
Sorry about that. It's three commands. Enter *sudo modprobe rt61pci* and press Enter; see what the result is. Probably nothing, but report any errors or warnings.

Enter *iwconfig* and press Enter. There will be some networking interfaces with 'no wireless extensions.' You can ignore those. Are there any with details? Post them if there are.

Enter *dmesg* | *grep rt6* and press Enter. That pipe symbol | means pipe the results of dmesg through another command grep; roughly, it means print out all the meaningful kernel messages and only tell me the ones with rt6 in the message. Post the results.

The pipe symbol | is on the right side of my US keyboard on the same key with \.

---

### Post by jlmclean on 2010-04-11
I'll get there, just a little slow sometimes (you have to draw me a picture if it's very complicated)
 I posted my results about the same time you posted your answer and it shows up before your last post. The results were:
sudo modprobe rt61pci, nothing
iwconfig, lo    no wireless extensions
dmesg | grep rt6, nothing

---

### Post by chili555 on 2010-04-11
No problems; we were all new once upon a time, even old Chili!

I am checking here: [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink)

Can you see any markings on the card telling us what version it is?

---

### Post by jlmclean on 2010-04-11
It says:
H/W Ver.:B1  F/W Ver.:1.2.0.30

---

### Post by chili555 on 2010-04-11
Do you have the original driver CD? What is the name of the WinXP .inf file?

I need a tranquilizer, a martini and an anti-depressant.

Just kidding...

---

### Post by mark bower on 2010-04-11
the "|" is called a pipeline and takes output from one command and inputs it into another. you will find it on your keyboard, maybe over the "\" key.  it is actually two vertical lines separated by a small space, but shows as a single vertical line.  If chili555 does not get you thru this, then consider getting hardware that works "out of the box" which is equivalent to "plug and play".  this means that the linux kernel already has the built in drivers and so you do not have to mess with drivers.  i've worked at this a bit, but now have all of my hardware natively driven.  i am free of windows except for my scanner, autocad and tax software.

mark

---

### Post by jlmclean on 2010-04-11
Hey, I agree, especially on the martini, you need and deserve a BIGGGGGGG martini. I'm following you on some of your other post. You're working my butt off and working with at least two others. You've got to be good to keep up with all of us rookies. 
The XP file is TNET1120.INF
I discovered that I do not have ndiswrapper installed. Do I need to go through installing it again. And by the way, the page that I mentioned in my first post about telling me how to install with another computer that connects to the internet, the one I couldn't find anymore, it's the link you posted for the other new guy that's trying to get his going. Thanks again.

---

### Post by chili555 on 2010-04-11
Here is a little secret, don't tell anyone, shhhh!

ndiswrapper is on the install CD! Drop the CD in the tray and open System > Administration > Synaptic. Go to Settings > Repositories and under Other Software, make sure the CD is enabled. Press reload and allow Synaptic to index the contents of the CD. Search for ndiswrapper and install everything in sight.

Drag and drop the WinXP drivers to your desktop. Now do:```
sudo ndiswrapper -i Desktop/drivers/TNET1120.INF  [COLOR="Red"]<--or wherever you placed the files.[/COLOR]
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m
```Now is your wireless working?> You've got to be good to keep up with all of us rookies. I have to get busy and get a few others started; I've had a couple of SOLVED, so I have to start some new ones!

I hope you are SOLVED in a few moments.

---

### Post by jlmclean on 2010-04-11
It still doesn't work. Think I'll take a break for a while and think about that martini, maybe take some head ache medicine. Thanks for all your help

---

### Post by mikey_likesit on 2010-04-12
decided to remove my post and start a new thread ([here]("http://ubuntuforums.org/showthread.php?p=9117388#post9117388"))

Sorry if that's bad etiquette...

---

