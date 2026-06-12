---
title: "Wireless confusion -  ath242x chip driver"
date: 2009-05-02
forum: Networking &amp; Wireless
---

### Post by jrz on 2009-05-02
Finally got wireless working on my IBM, but nothing learned helps on my Compaq Presario A900 which has an Atheros AR242x wireless.
lspci -v gives the following info:
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Hewlett-Packard Company Device 137b
	Flags: fast devsel, IRQ 16
	Memory at 91300000 (64-bit, non-prefetchable) [disabled] [size=64K]
	Capabilities: [40] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [60] Express Legacy Endpoint, MSI 00
	Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Virtual Channel <?>
	Kernel modules: ath_pci
I'm assuming ath_pci is the driver installed by ubuntu 8.10? Googling, I've run across so many conflicting solutions stating that the ath5K, or ath9K, or another driver works with the AR242x wireless, and searching the file system for ath5k I find an ath5k folder located in /usr/src/linux-headers-2.6.27-11/drivers/net/wireless, containing 2 files, Kconfig and Makefile. Does that mean I have ath5k installed? Also there is the same files in an ath9k folder as well as a number of others which is all quite confusing.

lshw -C network produces the following output:
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
And if I understand correctly, there should be a mention of the driver being used, which appears to be missing.

Anyone know how I should proceed from this point? Nothing I've tried so far has produced any positive results, although I've crashed Firefox numerous times from having so many tabs open at once.

---

### Post by t0mppa on 2009-05-02
You can use 'lsmod' on the terminal to check which modules are loaded on your kernel. The UNCLAIMED means that no drivers are associated with your interface, so something is amiss.

AR242x is a bit of a tricky chip, since there are a variety of different solutions around and it's sometimes hard to tell which will work. Basically you have 3 choices though, the original MadWifi driver (ath_pci), ath5k and NDISWrapper (ath9k is mainly for 802.11n support). If you've tried each of them, then the problem is something more than just the drivers.

---

### Post by jrz on 2009-05-02
Thanks, and I got it working about an hour after posting. I still don't understand WHY it now works. What I did was blacklist ath_pci, thinking maybe that was being loaded instead of ath5k. I rebooted, and now lspci -v shows BOTH ath_pci and ath5k, but now lshw -C network shows driver=ath5k. I used Network Manager to assign a fixed IP address and unplugged the wired connection, and had to reboot to get it to work, but I can make switching between them easy by removing Network Manager and installing Wicd, which is what I had to put on my IBM notebook to get the wireless to work. I couldn't tell you how many web pages I've read trying to resolve the wireless problems I've had, but it looks like each individual computer might require a unique solution. This is an area that really could use some attention, especially if Ubuntu wants to attract converts from other OS's.

My next step will be attempting to upgrade one of the notebooks to 9.04, and see if everything continues to work.

Thanks for the response.

---

### Post by t0mppa on 2009-05-03
Ok, then it probably was just a conflict between ath_pci and ath5k. What you're describing is actually the same setup as what I have on my laptop, ath_pci is blacklisted, but lspci still lists it in kernel modules. Been following the "don't fix it, if it ain't broken" mentality, since I need this machine to get my job done. 

I agree with wireless (and gfx) solutions needing more attention, these look and feel upgrades (like the new 9.04) are pointless, when there are bigger issues to worry about.

---

### Post by jrz on 2009-05-03
I've now got 2 computers running 9.04, all my wireless problems solved, and now I have 2 more to go with even more difficult problems to solve. Hopefully I'll get done before 9.10 becomes available. Where I live there are very few people running Linux, actually only one other I know of, and I really would like to promote it, but I would also have to provide support and have yet to solve all my own problems. BTW I live in Thailand, near Laos.

---

### Post by Meindert Frouws on 2009-05-04
I had a lot of troubles with the ath5k driver on my eMachines laptop.
Very unstable and slow connection.
The problem was gone when I set my router to a fixed channel in stead of "auto".

The chip was AR242x, also known as AR5007EG from Atheros.

Maybe this is helpfull for other people.

---

