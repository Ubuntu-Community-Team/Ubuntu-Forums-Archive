---
title: "Sony Vaio Ubuntu 8.10  wireless"
date: 2009-04-07
forum: Networking &amp; Wireless
---

### Post by scott1541 on 2009-04-07
Okay, i think this problem is kind of common with wireless adapters not working on ubuntu. The wired connection works but the light doesn't come on in the on or off positions. I could do with some help and advice on what to do because things are quite strange and not like Vista or xp at all. My laptop is a SONY VAIO VGN-NR10E and the computer says the network adapter is a   (LAN-Express AS IEEE 802.11g PCI-E Adapter), I looked on the list in one of the sticky posts, but this wasn't there. Help would be appreciated...  

P.s. I have also tried the thing in that thread that i posted in about the terminal thing in

---

### Post by coffeecat on 2009-04-07
The important thing is to find out what the precise wireless chipset is. Open a terminal and post the output of

```
lspci
```

---

### Post by scott1541 on 2009-04-08
Here it is:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
08:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

---

### Post by coffeecat on 2009-04-08
This is the important line:

> **scott1541 said:**
> 06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

You have an Atheros chipset. The good news is that during 2008 Atheros decided to work with the Linux community, and Linux drivers for their various chipsets are rapidly being developed. The middling news is that this takes time to trickle down from the kernel developers to the distro developers and thence to the end-users. The bad news is that there were some issues with some Atheros chipsets in the 8.10 release.

But first, let's try something simple, since you are unfamiliar with the Ubuntu gnome desktop. Up at the top-right of the screen, just to the left of the volume control icon should be the network-manager icon, which should look like two computers with a red X superimposed (meaning no connection). By the way, before you do this, unplug your ethernet cable if you have one connected. Now click on the applet icon. If the driver for your card is already in situ, a small menu should drop down showing all the wireless networks in range, and their relative strengths. Click on the one of your choice, and enter your WEP/WPA passkey where prompted. You may be prompted for a keyring password as well. That can be whatever you choose. If you connect, all well and good. If not, right-click on the nm-applet icon and make sure 'Enable Wireless' is ticked. If that doesn't work, more drastic measures are called for.

Have a look at these two links:

[http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)

Scroll down and look for 'Atheros driver not enabled by default'.

And then:

[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

After which search the forum for your particular chipset.

However, you may not wish to be doing all this hacking. I have another suggestion. I'm running from Jaunty Beta (which I find much improved over 8.10) and from what I've read support for Atheros is much better in Jaunty for the reasons I've explained above. Try downloading the Jaunty Beta iso [here]("http://www.ubuntu.com/testing/jaunty/beta") and running it live. Don't install just yet. Test the wireless in the way I describe above. If it works, you have a choice: install the Beta and put up with the inconvenience of massive numbers of updates and possible system instability (it is a Beta - but my experience has been good), or wait until 23rd April when the final release becomes available.

**Edit:** if you do decide to install Jaunty Beta, you won't have to reinstall the final release. Just by keeping the Beta fully updated will ensure that you have the final release version on release day. In fact, you'll have a working release version several hours before all the eager crowds are trying to download their ISOs from the overworked servers. :)

---

### Post by t0mppa on 2009-04-08
Had some trouble with the very same chipset myself. And finished fixing it 10 minutes ago. Here's a thread that has helped lots of users, including myself: [http://ubuntuforums.org/showthread.php?t=902860]("http://ubuntuforums.org/showthread.php?t=902860") (see reasoners post for simple instructions).

A few things to note, if you go down this path:
[LIST]
[*]MadWifi changed their web address from madwifi.org to madwifi-project.org
[*]If you don't want to use subversion, here's a link where you can simply go with your browser for the download: [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz]("http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz")
[*] If you have no idea what to do with the tarball, just download it (doesn't matter where, long as you can still find it), open up with the package manager and extract it to some easy place - ~/MadWifi (a directory called MadWifi at your home directory) for instance. Open a terminal, go to that directory and follow the instructions in the thread.
[/LIST]

---

### Post by 3rdalbum on 2009-04-08
It can be made to work in Intrepid, and it's rather undaunting. You can find the procedure if you look up "ath5k" on the forum. But the wireless should work out-of-the-box on Jaunty. As Jaunty is a stable beta and is being released in a couple of weeks, you might as well just try the Ubuntu 9.04 (Jaunty) beta disc and if it works, install it and update it to the latest packages.

---

### Post by scott1541 on 2009-04-08
i think i am going to try the thing that t0mppa was talking about whilst downloading the 9.04 Beta iso, then if the first thing fails, i can try the second one

---

### Post by scott1541 on 2009-04-08
Latest news: tried 9.04 beta and the light didn't come on and there was nothing on the thingy list. I was going to try the madwifi thing but the installation is really confusing (unlike some .deb's i downloaded earlier)

       Is there anything else to try?

---

### Post by t0mppa on 2009-04-08
From what I've seen, I doubt you'll get the light (if you mean the led on your computer displaying whether your WLAN adapter is active or not) to work, it appears to be way too much trouble over such a small thing for the developers writing these drivers. Granted that's a little annoying, since then you'll never know which state your adapter is in, but other than that it doesn't really matter.

Too confusing? Sorry, but I don't think you'll find any one-click installers for this. All the solutions I've come across include manual compiling of the downloaded drivers and that means writing a few lines into the terminal.

But since you upgraded to 9.04 already, let's hope things are easier over there. Can't offer any help with that though, I'm still on 8.10.

---

### Post by scott1541 on 2009-04-09
> **t0mppa said:**
> 
But since you upgraded to 9.04 already, let's hope things are easier over there. Can't offer any help with that though, I'm still on 8.10.

I never said i upgraded, i just tried it with the 'Try ubuntu without any change to my system' option

I might install it on my desktop later maybe  :guitar:

---

