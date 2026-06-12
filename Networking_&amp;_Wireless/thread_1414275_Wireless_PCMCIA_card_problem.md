---
title: "Wireless PCMCIA card problem"
date: 2010-02-23
forum: Networking &amp; Wireless
---

### Post by PeteUplink on 2010-02-23
Hi. Sorry if this has already been asked

My old Toshiba Satellite Pro 2100 laptop crashed a few days ago and the restore disk won't bring it back to life, it's an old machine (2002) and I can't get a replacement restore disk. So since the machine still runs fine and I didn't want to bin it, I tried installing Ubuntu. Everything went fine, but I can't seem to get the wireless network card to work. It works fine through Ethernet, but nothing at all through wireless. 

The network card is a Netgear WG511 v2 (made in China)

I followed this thread: [http://ubuntuforums.org/showthread.php?t=76804](http://ubuntuforums.org/showthread.php?t=76804) but I had a few problems.

When I tried to add prism54 to the blacklist file, I was unable to save the file because I didn't have the root priveledges.

When I got to the command 
[FONT=Courier New]sudo apt-get install ndiswrapper-utils[/FONT]
it said it was unavailable and suggested ndiswrapper_common, which I got.

However when I came to the command:
[FONT=Courier New]sudo ndiswrapper -i 2802W.inf[/FONT] It says ndiswrapper-utils is not installed.

And finally the driver on that thread seems to be wrong and netwg511.inf seems to be the correct driver. I have the original installation disk for the card, but I don't know how to get the driver extracted from it, because in the past all I've done is put it in the CD drive when the machine was running WinXP and clicked "setup".

Sorry this is a bit long-winded, but I thought as much info as I can provide might bring a faster solution.

---

### Post by bkratz on 2010-02-23
If you add ndisgtk (the gui for ndiswrapper) from synaptic it will automatically install the other ndiswrapper files and make it really easy to setup. It will show up in System>>Administration>>Windows wireless drivers

---

### Post by PeteUplink on 2010-02-23
Do I use the command 

[FONT=Courier New]sudo apt-get install ndisgtk 

to get that?

_edit_

Okay, maybe I should have just done that instead of asking. So ndistk is installed, and I've got the driver on disk but I can't get to it directly because it only extracts when I double click setup. Is there any way to get at the [/FONT]netwg511.inf [FONT=Courier New] on Ubuntu?
[/FONT]

---

### Post by bkratz on 2010-02-23
Why not just do it from Synaptic

System>>Administration>>Synaptic Package manager.  I know that it will add the dependencies, I don't think it will through the command line interface.

---

### Post by PeteUplink on 2010-02-23
I've got the ndisgtk installed. I just need to get the drivers from the install disk and onto the laptop, but when I goto the drivers folder on the disk, there's a setup.exe there, so I guess the drivers must be in that.. IS there a way to extract it to get the drivers?

_edit_

Okay I got the driver. Went into System>>Administration>>Windows wireless drivers selected the driver and it says it's invalid... (it is the correct driver because I've installed this card under windows from this installation disk before)

I'm kinda lost again... Any ideas?

---

### Post by PeteUplink on 2010-02-23
Okay, I really don't understand this.

I got the .inf file, but if I try to install it with windows network drivers it says that it's not valid. 

I tried installing it from a terminal window and it says:

couldn't create /etc/ndiswrapper/wg511v2: permission denied at /usr/sbin/ndiswrapper-1.9 line 194

_edit_ I don't think it's seeing the card as inserted into the PCMCIA slot... Any ideas?

---

### Post by PeteUplink on 2010-02-23
Ahh well... I gave up and got it working with a Trendnet TEW-424UB USb adapter instead.

---

