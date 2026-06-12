---
title: "Wireless networks found, but Gnome says no?"
date: 2006-07-16
forum: Networking &amp; Wireless
---

### Post by LCasler on 2006-07-16
I really hope this is an easy problem to correct, as I am not at all Linux savvy.  (No idea how to recompile things, should such a course be necessary.)

Okay, I have a wireless problem here.

Found a Belkin USB Wireless stick (model F5D7050) which many users are saying works, and many are saying doesn't.  It seems to be working for me, as far as using Wifi-Radar to find nearby networks, but Gnome Desktop seems not to communicate with the Network Manager tool.

Using Wifi Radar, I am able to see my network and choose to connect to it.  The progress bar flashes 'connecting to network', 'Got IP Address. Done.', and then shows Connected to None at the bottom once more. Hmmm...

I used Ndiswrapper to load the drivers for windowsxp off the CD that came with the USB adapter, and things seemed to go smoothly there.  The Wireless Network Drivers utility shows that the RT73 driver is correctly installed and the hardware is present.

Even though I get both of these confirmations from the two utilities that my hardware is there and somewhat functioning (I can see all the networks in my area), the little icon on the upper right desktop by the clock says "No Network Connection".  Clicking on it, I can get it to show both of my ethernet connections when I have them plugged in (a USB adapter and a PCMCIA adapter) but never any wireless connections.

If anyone has any insights, I would love to try them.  Getting pretty frustrated by wireless.  Everything else in Ubuntu rocks my world, and I don't think I'll ever go back to Microsoft.  Just wish I could use my laptop in the manner it was designed. =)

Thanks!

Louis

---

### Post by bluecherry on 2006-07-16
If you're running dapper, and I presume you are, try installing "network-manager-gnome".

Under breezy I had trouble connecting with wifi-radar, since I use network-manager everything works great!

Get network-manager and wpasupplicant (tool that n-m uses to connect to wpa encrypted networks):
> 
sudo apt-get install network-manager-gnome wpasupplicant


Backup /etc/network/interfaces:
> 
cp /etc/network/interfaces /etc/network/interfaces.backup


Then delete all entries in your /etc/network/interfaces that DO NOT contain lo:
> 
sudo gedit /etc/network/interfaces


Original /etc/network/interfaces
> 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


Edited /etc/network/interfaces:
> 
auto lo
iface lo inet loopback


Now reboot and you will find a new icon on your taskbar. It will detect the wireless networks your wlan picks up. Just click on a network to connect to it.

Hope this fixes your problem.

---

### Post by LCasler on 2006-07-16
Thank you, Bluecherry, for the response.

I did try everything you recommended, including 'marking for reinstallation' of various components that concerned networking wirelessly (such as Ndiswrapper, network-manager, gnome-network-manager, etc).  I had high hopes that something would work, but alas... =(

On a whim, I yanked the USB adapter and plopped it into my desktop Ubuntu machine, and, after trying your 'deleting entries in the interfaces' trick, it worked like a champ.  So it looks like, Yes, the Belkin USB Wireless Adapter works well for Ubuntu, with ndiswrapper and the proper driver installed, but it still left me with no working connection on my laptop.

I have a theory though.  One option might be my installation of Ubuntu on that machine.  

It's an older machine (Gateway Solo 5100 with I think 266 Mhz processer and 160 Mb of ram?) so I first tried Xubuntu.  After wrestling with the installer for a bit, I finally got it to install, but as soon as Xfce booted up the first time, my CD-rom no longer worked... or my PCMCIA slots.  Other than that, it ran fine.  So retrying with Ubuntu this time, I finally wrestled it into that tired laptop of mine, but not before it hung at a point in the installation.  After rebooting, it came up to the Gnome desktop and seemed to work fine.  I updated everything and then started trying the Wireless.

What I'm wondering is: maybe something didn't get install right/fully?  Is there a way to tell Ubuntu to check all of it's files against the repositories to tell if they're accurate?  I'm hoping I don't have to reinstall from the CD, since it took over 6 hours the first time. =(  But that may be me next course of action.

Idea 2:  The Belkin adapter says that it's compatible with USB 1.0, 1.1, and 2.0, but is Ubuntu?  Being an older machine, it's probably only USB 1.0.  Could that be causing a problem?

Thanks again in advance to whoever can shed some light. =)

-Louis

---

