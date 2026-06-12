---
title: "Running wireless card with Prism54 chipset"
date: 2006-06-03
forum: Networking &amp; Wireless
---

### Post by brad103 on 2006-06-03
Hi there!

I downloaded dapper the other day and a new wireless pcmcia card (3Com 3CRWE154G72) arrived for my laptop (Advent 6410) today ( I got this card because it apparently worked fine  [in Hoary]("https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards"). After boot, ubuntu saw the card fine and identified it. The 'Link' light was lit on the card, but never the 'Activity' light. I configured the network through 'Networking', but have not managed to ping anything other than my own IP (192.168.1.33). I can't ping my router (192.168.1.1) as I get: 
destination host unreachable.
Running ifconfig eth0 (there is no wlan0) showed my that it was allocated the IP address and the status was UP BROADCAST MULTICAST, but not RUNNING.

To try and work around this I [blacklisted]("http://www.beginningubuntu.com/dapper_tips.html#Using_Ndiswrapper_to_get_wifi_working") the Prism54 module, and installed ndiswrapper. After installing the windows drivers for the card, I have still had no luck.

I did notice (after blacklisting prism54, hadn't checked before then) that dmesg gave:
 
```
[4294667.296000] Linux version 2.6.15-23-386 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue May 23 13:49:40 UTC 2006
...
[4294698.856000] ieee80211_crypt: registered algorithm 'NULL'
[4294698.861000] ieee80211: 802.11 data/management/control stack, git-1.1.7
[4294698.861000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[4294699.035000] Loaded islsm_pci driver, version 0
[4294699.036000] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
[4294699.860000] lp0: using parport0 (interrupt-driven).
[4294699.990000] Adding 730916k swap on /dev/hda5.  Priority:-1 extents:1 across:730916k
[4294700.158000] EXT3 FS on hda1, internal journal
[4294700.497000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294700.497000] md: bitmap version 4.39
[4294700.758000] eth0: no 'reset complete' IRQ seen - retrying
[4294701.393000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294701.758000] eth0: no 'reset complete' IRQ seen - retrying
[4294701.758000] eth0: interface reset failure
[4294701.758000] prism54: Your card/socket may be faulty, or IRQ line too busy :(
[4294701.808000] islusb: unable to boot device
[4294702.967000] eth0: no 'reset complete' IRQ seen - retrying
[4294703.967000] eth0: no 'reset complete' IRQ seen - retrying
[4294703.967000] eth0: interface reset failure
[4294703.967000] prism54: Your card/socket may be faulty, or IRQ line too busy :(
[4294704.017000] islusb: unable to boot device
[4294705.535000] NET: Registered protocol family 17
...
```

And this is after I added 
  acpi=noirq
to the Kernel line of my default image in /boot/grub/menu.lst to try and prevent this pci interference.

What direction can I take now? Laugh if I've done things wrong!

Big thanks in advance
Brad

---

### Post by roboguy on 2006-06-03
Hi Brad,

Unfortunately I can't help you but I am having exactly the same problems. My prism card that worked fine under Hoary refuses to work with Dapper.

Lets hope someone figures this one out soon!

Cheers!

---

### Post by brad103 on 2006-06-04
Got it going! Check it out over [here]("http://www.linuxquestions.org/questions/showthread.php?t=387024") (there I'm known as jbond3007 ;) )

---

