---
title: "Wake on LAN"
date: 2011-07-19
forum: Networking &amp; Wireless
---

### Post by Epidural on 2011-07-19
So I've been at this on and off for a couple months. I'm using wakeonlan from a netbook running Ubuntu and I'm trying to wake a desktop on the same Modem/Router (SpeedTouch). Settings are configured as far as I can see in the BIOS, and using WakeOnLanMonitor (windows) I can see the netbook sending packets.

Some notes: It sends using port 9, to 255.255.255.255, which the Monitor picks up; however the monitor picks it up no matter which MAC address I use.

for instance:```
wakeonlan 00:12:34:56:78:90
```
produces:```
Packet recieved from 192.168.1.67 on port 40109
at 13:38:30 packet length : 102
00000000 : FF FF FF FF FF FF 00 12 34 56 78 90 00 12 34 56 
00000010 : 78 90 00 12 34 56 78 90 00 12 34 56 78 90 00 12 
00000020 : 34 56 78 90 00 12 34 56 78 90 00 12 34 56 78 90 
00000030 : 00 12 34 56 78 90 00 12 34 56 78 90 00 12 34 56 
00000040 : 78 90 00 12 34 56 78 90 00 12 34 56 78 90 00 12 
00000050 : 34 56 78 90 00 12 34 56 78 90 00 12 34 56 78 90 
00000060 : 00 12 34 56 78 90 
``` in the packet monitor. This works no matter what MAC I enter; this monitor picks up them all.

I once entered 00:00:00:00:00, and it unexpectedly woke up a different computer on my network. What I want to know is:
Why won't the desktop I'm trying to wake up wake up?
When powered off properly, the desktop in question (whose MAC address is known and I have tried) will not WOL. The only options in the BIOS are "Wake on Lan: Enable/Disable" from what I can see (it is of course enabled). What gives?

---

### Post by sanguinoso on 2011-07-19
This is not really a Ubuntu question, but in Ubuntu you can check the status of wol with ethtool. There must be something similar in Windows in which you can enable wake on lan from the OS.

---

### Post by Epidural on 2011-07-19
> **sanguinoso said:**
> This is not really a Ubuntu question, but in Ubuntu you can check the status of wol with ethtool. There must be something similar in Windows in which you can enable wake on lan from the OS.

Yeah, I know it's not specific to Ubuntu but I followed a tutorial from the forums (the manual way from [http://ubuntuforums.org/showthread.php?t=234588](http://ubuntuforums.org/showthread.php?t=234588) ) and figured there might be a way to help diagnose this using Ubuntu. I only used the windows packet monitor because I couldn't find a similar thing in Ubuntu.

How exactly do I check the status with ethtool?

---

### Post by jmoorse on 2011-07-19
Check this out, you may need to tweak some driver settings in Windows (the machine you are trying to wake run Windows right?)

[http://itworkerdaily.wordpress.com/2007/06/01/wol-wake-up-on-lan-how-to-set-it-up/](http://itworkerdaily.wordpress.com/2007/06/01/wol-wake-up-on-lan-how-to-set-it-up/)

You are sending to the MAC of the sleeping machine you want to wake up right?

```

wakeonlan [MAC of sleeping machine]

```

To check the status with ethtool on Ubuntu, install it and run it:

```

sudo apt-get install ethtool
sudo ethtool [eth adapter, likely eth0]

```

---

### Post by Epidural on 2011-07-19
I'm sending it to the right MAC address (the one given using ifconfig | grep HW) from the netbook using wakeonlan <MAC>

I was only using windows to use the packet monitor program (.exe), I'm back to Ubuntu on the Desktop.

Here is the output of ethtool eth0 :
```
mitch@mitch-ubuntu:~$ sudo ethtool eth0
[sudo] password for mitch: 
Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
	Link detected: yes
```

---

### Post by jmoorse on 2011-07-19
Can you run tcpdump on the desktop while it is up and ensure it is actually seeing the WOL frames?

```

sudo tcpdump -i eth0 port 9 -vvvv -s0 -n

```

Then send the magic packet from your netbook and see if it shows up?

---

### Post by Epidural on 2011-07-19
Results of tcpdump using 3 different MAC addresses (the first one was the correct MAC address for this Desktop):
```
tcpdump: listening on eth0, link-type EN10MB (Ethernet), capture size 65535 bytes
14:36:16.804401 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 130)
    192.168.1.67.52634 > 255.255.255.255.9: [udp sum ok] UDP, length 102
14:36:35.065990 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 130)
    192.168.1.67.35447 > 255.255.255.255.9: [udp sum ok] UDP, length 102
14:36:39.015521 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 130)
    192.168.1.67.40452 > 255.255.255.255.9: [udp sum ok] UDP, length 102

```

---

### Post by jmoorse on 2011-07-19
Ok, that makes sense.  In case you are curious the way the magic packet works is it will be broadcasted out to your whole subnet (255.255.255.255) but it *should* only be processed by the PC with the MAC address you specify.  The packet should contain 6 bytes of FF followed by the target mac 16 times.

At this point we have ruled out the network, so let's dig a bit deeper into WOL.  Can you put the machine to sleep (not shutdown) and try to wake it from the netbook?


Edit: Is this a motherboard integrated NIC or a PCI/PCIe card?

---

### Post by Epidural on 2011-07-19
> **jmoorse said:**
> Can you put the machine to sleep (not shutdown) and try to wake it from the netbook?


Tried it. I've always had issues with Ubuntu's suspend, though.. I've never been able to successfully get it out of sleep with this configuration.

It is a built in NIC adapter; from an ASROCK P43 Twins1600 motherboard (checked the doc's, it supports WOL, not like the BIOS option is an accident).

Thanks for your help, I'm going away to College and would have a lot of use for WOL with Remote Desktop so I could get things from my desktop from my netbook at school. (I'll deal with doing it remotely once local works).

EDIT: Glimmer of hope. I must not have waited long enough the first time. I put the computer in Suspend, and the fans spun down and lights went off etc (power light flashing), all is good. Sent the packet, computer revved back up! Didn't come out of Sleep but it's always had this problem (hardware vs. Ubuntu perhaps, not concerned). However, after doing a hard reboot to get out of the stuck sleep, then properly powering it down (using shut down in Ubuntu), it still will not wake.

---

### Post by jmoorse on 2011-07-19
I know what you mean about suspend, but things are getting better!

Do you dual boot this machine?
Are there any other power management related options in the BIOS?
Can you also try wakeonlan -p 7 [MAC of desktop]?

---

### Post by Epidural on 2011-07-19
> **jmoorse said:**
> I know what you mean about suspend, but things are getting better!

Do you dual boot this machine?
Are there any other power management related options in the BIOS?
Can you also try wakeonlan -p 7 [MAC of desktop]?

I do Dual-Boot, Ubuntu 9.10 and Win7 both 64-bit. I'll try booting back into windows and triple-check my NIC settings under Windows, at the same time I'll try -p 7 (though I had tried this previously).

EDIT: Now back into Windows 7. Still did not wake using port 7. In my NIC settings, Wake on Magic Packet is enabled (as is Wake on Pattern). The only other thing I see that may need to be configured would be "Auto Disable Gigabit (power saving)" which is currently disabled, and has "Disabled", "Re-link, Battery" or "Re-link, Batter and AC" as its options. Anything suspicious here? Another option I need to check?

---

### Post by jmoorse on 2011-07-19
Please provide any other BIOS power management related settings too, thanks

---

### Post by Epidural on 2011-07-19
Whoops. Sorry, Power Management settings in my BIOS don't really exist; there's no tab or obvious section. I could only find these in various places:

PCI Devices Power On : Disabled
Enhanced Halt State: Disabled
Boot Protocol: PXE (found directly under the Wake On Lan option, tabbed in as if it relates to wol. I've tried both PXE and R-something settings)

Would the mobo consider its own NIC a PCI device? Would this AND WOL need to be enabled?

---

### Post by jmoorse on 2011-07-19
It is possible, give it a shot

---

### Post by Epidural on 2011-07-19
Success!

Apparently this motherboard considers anything that isn't a drive a PCI device, even if it's built in. Seems redundant to have both a PCI Wake and a Wake on LAN, especially when you put them under different tabs (had to scroll through ACPI settings to find the PCI Devices Power On option).

But anyways, thank you Jeff for all your help. Now that you told me how to use ethtool and tcpdump a little, it will certainly speed up the process when it comes to trying to do this remotely. I won't have to power the thing off every time I want to check my port forwarding.

tl;dr, problem was motherboard PCI Power On option; had to be enabled, along with WOL enabled.

---

