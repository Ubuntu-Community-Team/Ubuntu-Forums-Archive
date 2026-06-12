---
title: "Netgear Ga311 Multi-Distro Absurdity"
date: 2009-02-07
forum: Networking &amp; Wireless
---

### Post by FrozenFox on 2009-02-07
**_*** SOLVED *** : See 3rd post_**

Okay everyone, here's the situation, it's crazy, so bear with me..


SHORT: 

My wired netgear ga311 works in Win XP, Mac OSX, and Arch Linux (ie works on linux w/o extra drivers..!), but not in any other distro live or not, including Ubuntu for some bizarre reason. I've already tried ALL sorts of google/forum hunting and screwing around myself to no avail. Help?

LONG:

I have my machine set up with Grub2 as the bootloader, with this working multi-boot:

1) Arch Linux (Overlord)
2) Ubuntu Linux (Jaunty)
3) Debian Linux (Lenny)
4) Max OSX 10.5.5 (Leopard)
5) Windows XP (Trashbin)

I bought a Netgear Ga311 ethernet (wired) card in order to have internet access on OSX, because it is incompatible (according to the Wiki and experience) with some parts of my motherboard, including its onboard ethernet. 

When setting it up, I had all sorts of problems with the thing not working in 1 OS or at all, for reasons generally unexplainable by me. After a day of screwing with it, I got it to work without problems (insanely, it seemed to be the same bloody settings I started with!) on ALL of WinXP, MacOSX, and Arch Linux. 

I wanted to try out ubuntu jaunty recently, so i installed it.. on the livecd, I noticed no internet was working. Figures. Maybe I'll get lucky? .. Nope. 

After another day of screwing with it and googling for possible solutions, and removing networkmanager and replacing it with wicd (chroot environment + copying stuff over from Arch), I am still coming up blank. 

The closest I have come to a solution is adding 'noapic' to my grub boot line, which had the gnome network-manager thingo actually grab net info (ie, gave it 192.168.1.101 instead of just sitting there trying then disconnecting). However, naturally, it STILL didn't go anywhere no matter what settings I used, manual or automatic. I tried with dhcp, with my own manual settings entry using OpenDNS as the nameservers, etc. Nothing worked, ever. Couldn't connect to any website by name or by ip address, including my local linksys router.

Out of curiosity, I loaded livecd's to test if it was an installed ubuntu issue, which I doubted..

The internet results: 

1) OpenSUSE 11 KDE4: Dead as a doornail
2) Fedora 10 Gnome: Dead as a doornail
3) Ubuntu Jaunty Alpha (again): Dead as a doornail

I load back into XP, OSX, or Arch? Works perfectly again. I don't bloody get it. Manual or auto, nothing works. Even more bizarre -- in every distro (working or not), lspci shows the ethernet card as being detected properly, Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet.

Does anybody have any clue as to what's going on? How I might be able to make it work in any other OS before I give up from frustration and return the card for something else that will hopefully work on all the OS's? I notice a lot of ga311 posts on the forums, and many people seem to have it working without any fuss or special configuration, so I don't understand at all.

If it is of any help, here is my working netcfg2 profile from Arch:

CONNECTION="ethernet"
DESCRIPTION="A less basic ethernet profile, using static configuration"
INTERFACE=eth0
IP="static"
IFOPTS="192.168.1.2 netmask 255.255.255.0 broadcast 192.168.1.255"
GATEWAY="192.168.1.1"
DNS1=208.180.42.100
DNS2=208.180.42.68

Relevant system information:

Asus P4S800D-X Motherboard
Netgear GA311 Ethernet Card

EDIT: I just went to the BIOS to double check to see if my onboard ethernet is disabled, and it is. So that's not the issue...

---

### Post by FrozenFox on 2009-02-08
Bump?..

---

### Post by FrozenFox on 2009-02-08
Finally. I figured it out on my own.. thank you for reading though, forum-goers..

After screwing with boot flags when finding the 'noapic' did -something- and remembering seeing something about acpi/apic in the BIOS, I tried:

noapic nolapic noacpi irqpoll

.. which worked, my net was working properly. I then proceeded to dwindle down the list to the absolute minimum settings that worked through trial and error:

nolapic irqpoll

NOTICE THE L in the first flag, meaning "local", apparently!

I don't have a clue why this isn't necessary on Arch but it **is** on Ubuntu (and presumably, Debian and the LiveCD's I tried) but whatever, it works. Hopefully this post will be of use to someone who doesn't appreciate the "solution" of many ga311 posters, "buy a new card".

EDIT: **_I needed to install wicd_** to replace networkmanager on Debian in order for the network to work properly, **_in addition to using those 2 boot flags_**. I assume the same is true for Ubuntu. This is probably why it isn't necessary on Arch, at least as far as wicd goes, because arch doesn't use NetworkManager in my setup. I'm not sure about the boot flags still.

My motherboard settings are:
"ACPI APIC Support: Enabled" (Haven't tested, but judging by the nolapic flag, I'm sure this will make a difference)
"ACPI 2.0 Support: Enabled"  (Enabled or disabled makes no difference).

---

