---
title: "Two new networking issues with new core i7 system on a Gigabyte ga-ex58-ud5 m/b"
date: 2009-03-15
forum: Networking &amp; Wireless
---

### Post by BatteryKing on 2009-03-15
I just upgraded the core of one of my boxes from an AMD based Tyan S2915 m/b to an Intel Core i7 based Gigabyte ga-ex58-ud5 m/b.  After experiencing some networking problems, I flashed the BIOS up to version f5, but no dice, so I am writing this now.

Problem #1 (and I mentioned this on another thread that I am parting from because there seems to be those who cannot see their network adapters and are dual booting where what I am now seeing is an improper initialization while single booting Linux):
On a cold boot with the TP (twisted pair) RJ-45 jack connected, on the connected tap I come up in 100 Mb/s mode (physically) with ethtool reporting the only physical interface on the tap being FIBRE running at 1000 Mb/s (not reality), so there is a definite break between reality and the mode Linux thinks the adapter is in.  I noticed something peculiar in that the tap not connected correctly reported the availability of the TP physical device.

The work-around I stumbled upon is to shut down the box, turn off the power supply, and unplug the Ethernet cable.  Then turn on the computer and boot Linux all the way to the login prompt.  Once to this point, plug in the Ethernet cable.  At this point when I log in and run ethtool it correctly reports the use of the TP (twisted pair) interface and 1000 Mb/s operation on the tap along with the switch reporting 1 Gb/s operation, so I am back up to full speed.


Problem #2 (packet loss):  Both before and after working around the initialization problem, I ran into a very peculiar UDP packet loss issue.  Before I was running a TeamSpeak server on an old Trixbox 2.2 VM running under VMware 2.0 server on under 64-bit Ubuntu 8.10 Intrepid Ibex on my Tyan S2915 m/b.  Changing just the variables of m/b, CPU, and RAM all of a sudden most people both inside and the LAN and over the Internet could still access the server just fine as before, but it failed (server never replied error) for one person in particular.  When I ran Wireshark on the Ubuntu 8.10 host I could see that most people would have multiple UDP exchanges right away, but with this one person I would just see the initial login UDP packet hit my tap device, but no reply would come back out that I could see.  On my local tests trying everything I could think of, the TeamSpeak server always sent a reply.  The question is with this one person in particular, why does a core system upgrade suddenly and consistently result in a UDP packet loss for one individual on my end while it works for everyone else?

---

### Post by Anthon berg on 2009-03-24
FWIW I'm having networking problems with the same motherboard and Ubuntu 8.10.

---

### Post by BatteryKing on 2009-04-11
Realtek had me install a kernel module that I downloaded off of their website.  The actual process seemed fairly painless, but I haven't fully tested it yet as this is a heavily used always on system and I need to reboot to fully test things out and I need to wait for a certain user to come online.

For Gigabyte EX58-UD5 users in order to grab Realtek's driver go to [www.realtek.com.tw](www.realtek.com.tw), then > Downloads > Communications Network ICs > Network Interface Controllers > 10/100/1000M Gigabit Ethernet > PCI Express > Software.  From here when you download the only 2.6 Linux kernel driver on the page you should see a file with r8168 in the name.  This is what you will be replacing the already running r8169 kernel module with, just follow the readme in the extracted files.

If anybody else tries this please post back with results and I will post back once I have done more testing.

---

### Post by mcn on 2009-04-15
Has there been any resolution to these issues?  I'm thinking of buying this motherboard, but I want to make sure all is well before I proceed.  How is everything else with ubuntu and this setup, any other issues besides networking?

Also, this will be my first custom build machine.  Most motherboards have software to configure the clocking and other options, however this software is for windoz.  Are there any packages on linux that you can use for this purpose, or can you do most of this in the Bios?

Thanks...

---

### Post by BatteryKing on 2009-05-30
I finally got a good chance to test out the kernel patch with the failing applications and they continue to fail.  I have since purchased a gigabit Ethernet card in order to work around this brokenness because it is definitely the network adapter.  At this point in time I still need further testing, but so far so good.

---

### Post by BatteryKing on 2009-06-06
I take back what I said in the previous post.  While the replacement NIC initializes on boot, which is a nice thing missed by the onboard NICs by default, I am still experiencing packet loss issues and am not sure why.  This started after a hardware refresh while the software stayed the same, so I blamed the hardware, but swapping out suspect hardware also did not solve the issue.

It seems I am doomed to a two physical box solution running round the clock and higher power bills until I can figure this out.:icon_frown:

---

### Post by gartss on 2009-06-08
Hi all,

Obviously I encountered the same problem with my onboard LANs.
I followed the BatteryKing recommandations and got the r8168 driver that I successfully compiled and installed in my brand new Ubuntu server (8.04) install.
The result is that I succeed to ifup my eth0 and got it working but not the second one !
The other port is activated in the BIOS but is not detected later by the OS...
If any of you have some hints, you are welcome.
I keep trying and will post as well if I find something. ;)

---

### Post by gartss on 2009-06-09
Hi,

After 2 reboot, my eth0 completly disappeared, and apparently forever ... and for no reason.
I tried everything and I was so exhausted that I totally gave up ...
I found two Broadcom network PCI cards in other computers in my lab that I plugged in. And they were totally and immediatly compatible.

I know it is not a solution. But it is such a shame for Gigabyte that these fu***** RJ45 ports can not normally work, especially for a 280 euros MB.

Hope somebody will find a robust trick someday to fix this.

Tchao ):P

---

### Post by BatteryKing on 2009-07-06
I figured out one issue. The issue with loosing UDP packets with the virtual machine seems to have been due to old VMware tools on a guest being used with the newer version of VMware Server 2.0.  Installing a new guest operating system with the updated guest tools did the trick for that one.

However with NICs and also now with my 3ware 9650, proper detection and usage of peripherals seem to be doomed with this board.  It can take multiple tries for the BIOS to properly add the 3ware controller to the boot sequence and I ended up bypassing the integrated NICs with a not-so-cheap gigabit PCIe card so that I have one less thing messing up on boot.  Needless to say once this system is going, I try not to reboot it if I don't have to.

---

### Post by BatteryKing on 2010-07-03
Gigabyte boards = defective.  Gigabyte 3 year warranty = sham.  Don't buy this board.  Don't buy Gigabyte.

This board comes faulty out of the box and only gets worse over time.  When your system no longer can boot exclusively because of Gigabyte's poor quality, they just ship the same defective board back to you claiming that it "passes all tests" after weeks of thumbing their noses at you.

This is not acceptable behavior by a company I am willing to to business with and will therefore no longer buy Gigabyte products.

---

