---
title: "Did Win2K kill my Ubuntu DHCP?"
date: 2006-04-10
forum: Networking &amp; Wireless
---

### Post by LuftFan on 2006-04-10
Hi

I started with Suse - success fully loaded and connected to Internet (home network with DSL router).  Then I migrated to new harddrive, loaded Ubuntu.  Again success to get onto network. Then I repartitionied, loaded Win2K, and Ubuntu dual boot. Still successfully on the internet but Win2K complained about drive errors.  I fixed the partion (my mistake to double Dos fdisk extended partion with linux partion on top), reloaded Ubuntu (happy Win2K)and since then I can't get on the network in Ubuntu.

I've reinstalled 3 times, gave up, loaded Suse, loaded twice, still not on the network.  But if I reboot and go through Win2K I have perfect LAN connection to internet.

Now my question:  Did Win2K set something on my network card when I loaded the drivers (Service pack 4 + Motherboard)?  After that the problems started.

My system is AMD64 3200 with Biostar GeForce6100/nForce410 motherboard.  Linux (Suse) reports nVidia Corporation MCP51 Ehernet Controller.  

I noticed that during boot the "configuring network connections" is very slow at that point (~30sec) but then reports "OK" but cannot connect to internet.  I cannot ping, yet the Network tool (Ubuntu & Suse) reports that Eth0 is active.

Where do I start because I've tried everything that I've found on Forums.  Probably did more damage by now so here goes my 7th Linux installation in 4 days...Ubuntu again, 5.10 Breezy (original CD from Ubuntu) as before.

Newbie LuftFan

---

### Post by LuftFan on 2006-04-10
I reinstalled, fixed X (for VESA) and now I'm in Breezy.  No internet connection (chose to do manual during loading after Configuration Fail - gave static IP and provided router IP address - no luck)

Looking at thread "Wired Ethernet Troubleshooting Process", I wanted to do methodical step through problem solving guide.  
input:
xxxx@ubuntu:~$ sudo mii-tool eth0
output:
SIOCGMIIPHY on 'eth0' failed: Operation not supported.

I'm stuck at the first step!!  I need some help please.

Thanks

LuftFan

---

### Post by LuftFan on 2006-04-10
Ok, after trying everything I cuold read on the threads, including disabling ipv6, including commenting out ipv6 refences in /etc/hosts I gave up, got a clean harddrive off the shelve and did a fresh install with all the default settings as before.

Again the network configuration did not detect DHCP and I used the manual configuration option to specify router's IP, etc.

STILL NO CONNECTION.

Because it worked before I loaded Win2K on dual boot on my other HD, and then adding SP4 and the CD drivers that came with the motherboard, I now think that the MB CD changed firmware or something.

We even tried a third Linux, "Damn Small Linux (Debian)" and it also cannot get on to the network.

But my Win2K boot went through cleanly with fast Internet connection so I'm sure there is no hardware fault, except maybe my comment above.

Does anyone have any ideas?  My PC/Win/Linux knowledge and experience in exhausted.

LuftFan

---

### Post by LuftFan on 2006-04-10
Since I'm speaking tp myself, I'll keep it brief.

I took out old network card, installed it in my new system, used "Dman small Linux" and it went straight through.

Now I'm reinstalling Ubuntu on partioned HD, dual boot with Win2K, and already during installation we had network connection success.  So I'm hopeful.

Now just to reconfigure Win2K.

In summary - when nothing works and no-one is helping, replace the hardware ans start again.

Cheers

LuftFan

---

### Post by bscbrit on 2006-04-10
LuftFan - I'm sorry that you think you have been talking to yourself.  I've just logged on for the evening and caught up with your post.  

It sounds like the hardware card was not being correctly configured by linux (any version) .  You could have tested this by 'ping'ing the card from the computer it is installed in - you will have to set the IP address manually.  DHCP is only good if your network card is correctly configured and has a working connection to the DHCP server.  So, if the card was not working, you wouldn't get any DHCP response.  As I do not know your make and model of motherboard or network card, I cannot offer any advice as to what you could have done to correct the installation.

I hope it works after the new set up is completed. If not, come back here and, if I'm still online, I will be pleased to try and help.

edit: I've just found the hardware details in your first post - apologies for my mistake.

---

### Post by LuftFan on 2006-04-10
Thanks BSCBRIT

It works beautifully!  I'm am now typing this on the machine, out of Win2K though.  Had to dig on the net to find the old drivers for Win2K (I bought the original PC from where I ripped the Eth in 1999 so you can imagine no more install disks!)

I've tested Ubuntu and Win2K on dual boot and both work fine with new (old!) network card.

Now to configure the LAN so that I can see the other Linux (Suse) machine.  Tomorrow...

Cheers

LuftFan

---

### Post by boosted_sled on 2006-05-08
I'm having the exact same problem.

I have a shuttle with onboard eth0.

I am using fixed ip addresses for both windows & linux, though I don't think that has any bearing on this issue.  I have the same problem with both on dhcp.

The only thing that works is to pull the plug on the machine for 5 sec before rebooting to linux.  There seems to be something low level going on that causes linux to reject the ethernet hardware unless it is truly a cold boot.  Any further insight into this would be appreciated, as the fix is a pita.

---

