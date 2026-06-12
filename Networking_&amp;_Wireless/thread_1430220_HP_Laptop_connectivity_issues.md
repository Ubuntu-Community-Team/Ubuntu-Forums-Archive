---
title: "HP Laptop connectivity issues"
date: 2010-03-15
forum: Networking &amp; Wireless
---

### Post by StephenOK on 2010-03-15
Hi Folks,

I recently uninstalled Vista and put Ubuntu 9.10 on the machine.
The machine was badly infected with viruses that I was able to get rid of.

The main problem with the HP Pavilion dv8500 is that it doesn't connect to the internet. When I removed the viruses and cleaned out the registry in Windows, I was still having connectivity issues, which were 'local only' and would not connect to the internet.

I figured this was due to infection and some traces of it were left on the system which were affecting connectivity issues. However, after installing Ubuntu, and using the full disk, I'm left with the same connectivity issues. I've even tried a tested, hard-wired ethernet cable to no avail.

I'm left with the suspicion that this has something to do with the network card in the machine. Are there any other tests that I can run to troubleshoot this issue, as I've never run into this with Ubuntu - or any linux distro. for that matter - and would like to confirm that it is either a configuration problem or a hardware issue. Although I'm beginning to suspect that the later is the case, I'm not entirely certain.

Thanks in advance for any input,

Stephen

---

### Post by StephenOK on 2010-03-15
Have to bump this post, as I haven't figured out any solutions and desperately need input from someone in the know.

Thanks

---

### Post by Iowan on 2010-03-15
From a terminal: ```
sudo lshw -C network
``` should provide information about the interfaces.

---

### Post by StephenOK on 2010-03-16
> **Iowan said:**
> From a terminal: ```
sudo lshw -C network
``` should provide information about the interfaces.


Hi Iowan,

Thanks so much for getting back to me on this issue! This is the report issued from terminal after typing in that command:

To run a command as administrator (user "root"), use "sudo <command>". 
See "man sudo_root" for details. 

jesse@jesse-laptop:~$ sudo lshw -C network 
[sudo] password for jesse: 
  *-network               
       description: Ethernet interface 
       product: MCP67 Ethernet 
       vendor: nVidia Corporation 
       physical id: a 
       bus info: pci@0000:00:0a.0 
       logical name: eth0 
       version: a2 
       serial: 00:1b:24:ac:1d:02 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 66MHz 
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII 
       resources: irq:27 memory:f6488000-f6488fff ioport:30f8(size=8) memory:f6489c00-f6489cff memory:f6489800-f648980f 
  *-network 
       description: Network controller 
       product: BCM4311 802.11b/g WLAN 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       version: 02 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list 
       configuration: driver=b43-pci-bridge latency=0 
       resources: irq:19 memory:f6000000-f6003fff 
  *-network DISABLED 
       description: Wireless interface 
       physical id: 1 
       logical name: wlan0 
       serial: 00:1a:73:a6:c4:9a 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg 
jesse@jesse-laptop:~$ 

Since it detects the interface, I'm not certain that it's a hardware issue; however, I was having a ton of trouble trying to get this machine online with Windows, and I'm much more familiar with troubleshooting network related problems on that platform.

The Network says that it's disabled, yet I went through the process of assigning an SSID, passphrase, etc, so I could get it on my wireless system. As noted earlier, even hard-wiring the network doesn't work.

Any additional input would be appreciated.

Thanks,

Steve

---

### Post by StephenOK on 2010-03-17
Sorry to have to bump this again, folks. I just haven't came up with a solution and was wondering if any others had any thoughts on the topic.

Thanks in advance

---

### Post by bkratz on 2010-03-17
> **StephenOK said:**
> Sorry to have to bump this again, folks. I just haven't came up with a solution and was wondering if any others had any thoughts on the topic.

Thanks in advance

Didn't quite understand whether this was a wireless or wired connection, but either way this thread should help you at least get wireless working, whether you have a wired or not. Your wireless is the BCM4311 by the way


[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

I reread and see that it is both--at least this should help with the wireless!

---

### Post by 2hot6ft2 on 2010-03-17
Is there a router and/or modem?
Have you tried unplugging them and restarting them by plugging the modem in first then once it's up and running plugging in the router?
The problem may be that they need restarting.

---

### Post by StephenOK on 2010-03-17
> **bkratz said:**
> Didn't quite understand whether this was a wireless or wired connection, but either way this thread should help you at least get wireless working, whether you have a wired or not. Your wireless is the BCM4311 by the way


[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

I reread and see that it is both--at least this should help with the wireless!

Thanks, bkratz.

---

### Post by StephenOK on 2010-03-17
> **2hot6ft2 said:**
> Is there a router and/or modem?
Have you tried unplugging them and restarting them by plugging the modem in first then once it's up and running plugging in the router?
The problem may be that they need restarting.


Yeah. I've tried restarts of the modem and router to no avail. I'm going to check the link that bkrantz offered and see if I can find a solution that way.

Thanks for the offering, though.

---

### Post by StephenOK on 2010-03-18
> **bkratz said:**
> Didn't quite understand whether this was a wireless or wired connection, but either way this thread should help you at least get wireless working, whether you have a wired or not. Your wireless is the BCM4311 by the way


[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

I reread and see that it is both--at least this should help with the wireless!

Thanks again, man. I followed the instructions for the BCM4311 and it worked great. Oddly,though, connectivity seems to be intermittent after having great connectivity within my network for a few hours.

Another oddity is that I'm having problems downloading O.S. updates. But I'll just go back through the process and make sure that install from CD isn't checked in synaptic, as I assumed it would return to default download after the restart. I haven't checked yet, but this is just a guess. I'll check it out in the morning.

Owe you big time, man. Told the guy who's computer I was working on that he may need a new nic, and since I put in more than a couple of hours fixing the Windows viruses, he was just happy that I backed up all of his files and burnt them to DVD-DL disc.
I gave him the disc and he told me to keep the laptop.

This is sweet. I think I'm going to set this up for my little niece and nephew.

Thanks again, bkrantz,

Steve

---

### Post by jrssystemsnet on 2010-03-18
> **StephenOK said:**
> Oddly,though, connectivity seems to be intermittent after having great connectivity within my network for a few hours.

That's par for the course with the Broadcom NICs - they suck under Windows, too.  The fix is yanking that sucker and replacing it with an Intel.  (I've done this with quite a lot of Dell laptops and netbooks; the default "Dell" mini-PCIe wireless NICs are actually rebranded Broadcom junk, and they invariably suck.)

---

### Post by StephenOK on 2010-03-18
> **jrssystemsnet said:**
> That's par for the course with the Broadcom NICs - they suck under Windows, too.  The fix is yanking that sucker and replacing it with an Intel.  (I've done this with quite a lot of Dell laptops and netbooks; the default "Dell" mini-PCIe wireless NICs are actually rebranded Broadcom junk, and they invariably suck.)

Yeah, I agree, and that's probably what I'm going to do. I didn't realize they were some troublesome until the last few days. However, when it comes to buying an affordable notebook, I think you get the most bang for your buck -- if you are on a strict budget -- with an HP. 

Now I have two of them - a high-end HP and the dv6500. I also have a MacBookPro, but I only use that for music - audio editing, composing and Max/Msp.

---

