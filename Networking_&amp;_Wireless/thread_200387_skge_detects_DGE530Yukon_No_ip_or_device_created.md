---
title: "skge detects DGE530/Yukon: No ip or device created"
date: 2006-06-20
forum: Networking &amp; Wireless
---

### Post by mfigley on 2006-06-20
dapper 6.06, 

   # dmesg | grep skge
   skge 1.3 addr ... irq 10 chip Yukon rev 1
   skge eth0: addr 00:00:00:00:00:00

Also have an old ne2000 in the box:

   NE*000 ethercard probe at 0x300
   eth%d: NE2000 found at 0x300, using IRQ 3.

The NE card becomes eth0 and nothing for skge.

I've seen somthing like this with breezy, but put it
off until now.  Anyone else?

---

### Post by mfigley on 2006-06-27
Must be a harware problem but, that's not all.

Put in another card of the same type and still no eth0
- had to fix the new MAC in /etc/iftab

Yes, it was a hardware issue, combined with the saved info in iftab

---

### Post by DigitalXpert on 2006-07-09
I too am having similar problems with this card.  I built the new 2.6.17.4 kernel and all is well.  Only other problem I have is my PCI IDE card doesnt work in the new kernel.  I'm looking into trying 5.10 server since 6.06 is being a pain.  Maybe I can get both working then.

---

### Post by mdmbkr on 2006-07-10
Hi,

I have used a few Marvell cards (branded as DLink DGE-530T and Linksys EG1032v2).  Currently I use the skge driver but have also used sk98lin in the past.

I've experienced a similar problem with these cards.  If power is cut unexpectedly, the cards often do not work when the system is powered back up.  The driver loads with no errors or warnings, and ifconfig works fine too.  Link LEDs on the card and switch are normal.  But ifconfig reports the MAC address as 00:00:00:00:00:00.  And there is no connectivity.  I've tried setting the MAC back to the correct value, which seems to work, but the card still doesn't work.  Example:

eth0      Link encap:Ethernet  HWaddr 00:13:46:99:59:16  
          inet addr:192.168.0.2 Bcast:192.168.0.255 Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:209 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18675 (18.2 KiB)  TX bytes:0 (0.0 b)
          Interrupt:12 

For months I assumed this was a hardware failure, in spite of the fact that there are no errors of any type reported.  But, I put one of these card in a Windows XP system, and it works fine.  What gives?

---

### Post by DigitalXpert on 2006-07-10
I never had any issues with the mac address.  Was never able to get it detected in 6.06 server but when I installed the newest kernel I had to add skge to /etc/modules to force it to get detected.

I learned than you can add module names to /etc/modules.d/blacklist to try and force the kernel into using a certain module if the default it tries to use is giving you troubles.

As for me, I have installed the 5.10 server and all is well, gigabit card and pci ide card.  If I had the time I'd mess with it more.

---

### Post by mholmes on 2006-07-11
Hi there,

I got this card to work fine on Dapper. This is what I did:

-Copied the linux driver folder off the CD that came with the card.

-Found the README file.

-Followed the instructions to unpack the stuff.

-Went and got the linux header files using Synaptic (never had to recompile my kernel before!)

-Tried to run the install.sh file for the driver.

-Got an error message to say it didn't know where the linux header files were, along with a really helpful example showing me how to make a symbolic link to where the header files actually are.

-Successfully ran install.sh, which recompiled the kernel and loaded the driver.

-Rebooted, then configured and activated the card (on eth1), and set it as default.

-Rebooted again, this time with the network cable connected to the new card instead of the old card.

-Bingo!

Hope this helps&#65294;I'll post a copy in a couple of other threads on the same topic -- sorry about the duplication but people may not find it if I leave it in just the one thread.

Cheers,
Martin

---

### Post by mfigley on 2006-07-12
further clarifications:

With the stock kernel (Ubuntu 6.06LTS) skge did detect my DGE530 cards - by "detect" I mean the driver prints it's "hello" message in the system log:

skge: ....

However, the card i initially installed produced a bogus MAC address (zero)
Swapping the card fixed the MAC problem *but* here's the interesting bit -

My /etc/iftab contained eth0 with a MAC from a different card!
So, it would not assign the device name to my *good* DGE530 until I

1) deleted or modified the contents of /etc/iftab reflect the new card/MAC 

Are the udev rules/mappings lacking something?

---

