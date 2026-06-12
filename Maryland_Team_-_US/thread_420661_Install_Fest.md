---
title: "Install Fest"
date: 2007-04-23
forum: Maryland Team - US
---

### Post by phr0ze on 2007-04-23
Lets post here about the install fest preparations. I have not seen too much posting in our forum since the meetup so I thought I would try to start it.

I installed 7.04 on a machine the yesterday which I imagine would be a lot like the type of machine we would encounter at the install fest. The machine was an average system (AMD Athlon, 512MB ram, 120GB HD, Integrated sound, video, network (nvidia)). This system has Windows XP on it which has been in use for about a year. At least 50GB of drive space had been used up. Finally, I did not bother to defrag the disk simply because we would not know if they did or didn't.

I started the Live CD and played around with it some. I even downloaded the proprietary drivers to play with Beryl. It let me do this without installing. Then I started the install. The first few steps are very simple language/locale type. Then the partitioner appeared. I simply left the partition screen with the default options and clicked next. It took only 10 minutes to repartition. Then I went on with the install. It was able to detect my profiles on the old windows drive and I chose to import these into Ubuntu. Very cool.

30 Minutes of installing and the system was done. The only trouble was on the reboot. X did not start. The xorg config file listed the proprietary driver for my video card. I switched it back to NV and started x. Everything was fine. I went and looked at my drivers and noticed the proprietary driver for video wasn't installed. Pre-Downloading that driver for the live CD must have confused the installer. I re-downloaded the 
driver and rebooted. Beryl and everything came right up.

That was my most recent experience with the latest installer. Fairly easy.

---

### Post by mohnkern on 2007-04-24
I can't come to the install fest, but I'll chime in with my experiences.  I've done two installs, one as an upgrade, and one as a build from the ground up, dual boot.

Both are 3 Ghz pentiums with 1 GB ram, IDE drives, Nvidia Geforce cards (albeit one is a 128 MB card, the other a 64).

First machine was direct networked, zero problems, upgrade went seamlessly.  

Second machine had an airlink101 wireless card in it.  I have not been able to get WPA to work on it, and its pretty frustrating to have to stick with WEP (and I installed the wpa utils so that's not it, WPA or WPA2 just isn't showing up on the network manager).

I want to move the hardwired machine to a static IP address, but every time I change it in network manager, it changes it back to dhcp.  I used ifconfig eth0 <ip address> and suddenly I lost net access to the outside.  It's probably something in the Linksys router (WRT54G) that I'm not setting, but for the life of me, I can't find out where the problem is.  

Though I was able to kind of fix the problem, I think.  I moved myself back to dhcp, grabbed an IP Address, moved it to manual, and put in that ip address.  That seems to have worked, however, I don't know for sure what the Linksys will do when I don't renew the IP Address.  I assume I'll find out in a few days.

Anyone done static IP address assigning with Feisty and a Linksys?

All and all, unless you've got something really extreme, it's just gonna work, but that's Ubuntu.

---

### Post by parma1 on 2007-04-25
When and where is the installfest?

---

### Post by ski309 on 2007-04-25
I've done two upgrades from Edgy to Feisty so far.  One for my Dell E1405 Laptop and one for my desktop computer/HTPC.

Laptop upgrade installed and works perfectly.  I worry about the problems I had with getting X running when installing Edgy; it required some x.conf editting but ran like a dream afterward.  I hope that pure Feisty installs don't come with this problem.

Desktop upgrade I did last night didn't do so well.  When I rebooted, the error "soft lockup on CPU#0" came up.  After looking through the forums it may have something to do with my wireless card; I'm going to try pulling it out since I don't use it right now, but for other people's installs that require the wireless card, it could cause problems...

---

### Post by ChuckFrain on 2007-04-26
> **parma1 said:**
> When and where is the installfest?

When has yet to be determined.
Where is planned to be at the Howard County Central Library.

---

### Post by ChuckFrain on 2007-04-26
My Fiesty experience so far has been decent. I did an upgrade on my laptop and only had one issue with my wireless nic that was easily resolved. I did a fresh install on my Windows box to make it dual boot. While the install went well, it did not detect my profiles on the Windows side. This may be due to the fact that my second disk in that machine has some stale windows info on the partion and Grub actually determined that drive to be another bootable windows drive. 

My next target is to get my hands on a PC and/or laptop that does not have a geeky owner and doing a dual boot setup with that to get the typical user environment. <Hmm....my gf's machine is just sitting there.......>

---

### Post by phr0ze on 2007-04-26
> **ChuckFrain said:**
> My Fiesty experience so far has been decent. I did an upgrade on my laptop and only had one issue with my wireless nic that was easily resolved. I did a fresh install on my Windows box to make it dual boot. While the install went well, it did not detect my profiles on the Windows side. This may be due to the fact that my second disk in that machine has some stale windows info on the partion and Grub actually determined that drive to be another bootable windows drive. 

It seemed to not find profile data on my computer at first, but a few minutes and a list appeared. If I wasn't patient I would have clicked next without waiting.

> 
My next target is to get my hands on a PC and/or laptop that does not have a geeky owner and doing a dual boot setup with that to get the typical user environment. <Hmm....my gf's machine is just sitting there.......>

This is what I did, The machine I upgraded was used by my wife and son. Neither of them are geeky.  Something that surprised me is my wife sat down on that machine for the first time since I switched it. I only told her I reloaded the machine. She doesn't know anything about Linux but she sat down and started using it without flinching. I expected her to at least say 'What the hell is this', or 'Where do I find...'. Granted she only needed to use Firefox, but still.

---

### Post by phr0ze on 2007-04-26
I don't know how many members are checking this regularly, but should we try to get an approximate head count for who would be willing to help with a Saturday install fest provided it didn't conflict with some unforeseen schedule.

I'm definitely willing to help with planning, prep and execution. I have a friend who can help too with basic stuff like setting up PCs, getting CD-Roms to boot, and follow basic instructions through the install.

---

### Post by ChuckFrain on 2007-04-26
> **phr0ze said:**
> I don't know how many members are checking this regularly, but should we try to get an approximate head count for who would be willing to help with a Saturday install fest provided it didn't conflict with some unforeseen schedule.

I'm definitely willing to help with planning, prep and execution. I have a friend who can help too with basic stuff like setting up PCs, getting CD-Roms to boot, and follow basic instructions through the install.

We'll defiantly be interested in any and all help that is offered. I've already heard from three people saying that they are going to help less any conflicting interests.

---

### Post by ski309 on 2007-04-27
If it's on a saturday, it depends on when on that saturday the install fest is.  Late afternoon/evening, I should be able to make.

---

### Post by mohnkern on 2007-04-27
> **phr0ze said:**
> It seemed to not find profile data on my computer at first, but a few minutes and a list appeared. If I wasn't patient I would have clicked next without waiting.



This is what I did, The machine I upgraded was used by my wife and son. Neither of them are geeky.  Something that surprised me is my wife sat down on that machine for the first time since I switched it. I only told her I reloaded the machine. She doesn't know anything about Linux but she sat down and started using it without flinching. I expected her to at least say 'What the hell is this', or 'Where do I find...'. Granted she only needed to use Firefox, but still.

I should be doing the same in a couple of weeks (Installing a dual boot machine for a novice).  I'll let everyone know how it goes.

---

### Post by phr0ze on 2007-04-27
What kind of equipment and supplies will we need?

We should have CD's of course. Are we able to get official CDs, or should we look into burning our own?
We will need lots of power strips for the computers.
We will need Cat5 Cable, a switch and a way to connect that to the internet.
Are we going to have the monitor,keyboard and mouse or should they bring their own? In any case we should have at least one table with an open monitor/keyboard/mouse and KVM. I can bring all of this if needed.
If we provide the monitors, we should have some which support DVI or a DVI to VGA adapter.
Finally we should have a set of headphones just to test the soundcards before they take the PC home.

Any other suggestions?

---

### Post by ChuckFrain on 2007-04-27
> **phr0ze said:**
> What kind of equipment and supplies will we need?

We should have CD's of course. Are we able to get official CDs, or should we look into burning our own?
We will need lots of power strips for the computers.
We will need Cat5 Cable, a switch and a way to connect that to the internet.
Are we going to have the monitor,keyboard and mouse or should they bring their own? In any case we should have at least one table with an open monitor/keyboard/mouse and KVM. I can bring all of this if needed.
If we provide the monitors, we should have some which support DVI or a DVI to VGA adapter.
Finally we should have a set of headphones just to test the soundcards before they take the PC home.

Any other suggestions?

I'm trying to get some Feisty CDs for the group through ShipIt. As we are an unapproved group we're not entitled to them. 

Power strips/cat5/switch/internet we will be touching base with Luis to see what the library has available and then we'll put out the call for more as needed. 

Keyboard/mouse/monitor should be brought by the users just so we can have the best representation of their home system. However we should be able to get some stations available to be plugged into if they just bring their tower. 

And i agree with the adapter and headset comments.

---

### Post by phr0ze on 2007-05-03
I thought of one more thing. We should have a linux compatable USB Ethernet or Wifi adapter in case someone comes with a PC which only has dial up. I have a wireless adapter at home I can try on fiesty to see what happens.

Did I ask which version of Ubuntu we will be offering? I think it will help us all (simplify) if we just offer one.

---

### Post by ChuckFrain on 2007-05-03
If you could check on the wireless adaptor that would be great. I might be able to scrounge up a NIC for use but I hate to start cracking open people's PCs in such an enviornment.

As for the version my suggestion is to recommend Ubuntu 7.04, but have the alternate, server, X/K/Ubuntu's availible for those that want the choice. From my perspective of those that I've gotten to try Ubuntu they tend to be happiest off the start with Ubuntu. Some like the looks of KDE but tend to get overwhelmed with choices, and Xubuntu is a bit more stripped down than what most people prefer. 

Also we can install multiple environments for those with enough diskspace if they chose to. 

I'll probably bring along some of the 6.06 LTS disks/images for those few that would be interested in the support aspect. 

*As for scheduling this, I'm waiting back on an email I sent to Luis about room availiblity.

---

### Post by ski309 on 2007-05-03
I just received my 7.04 Shippit CDs--I can't believe how professional they look!  I have two copies of the 32-bit Live CDs and one copy of the 64-bit Live CD.

---

### Post by phr0ze on 2007-05-17
I will either get my adapter working or I will buy an appropriate adapter. np.

---

