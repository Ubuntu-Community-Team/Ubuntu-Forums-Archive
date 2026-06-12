---
title: "Wake on Lan Problems"
date: 2010-11-20
forum: Networking &amp; Wireless
---

### Post by Madman525 on 2010-11-20
Apologies in advance; I had no idea which category this problem should go into.

Anyway, I was trying to set up Wake on Lan for Ubuntu 10.10 with the help of these guides:
[http://ubuntuforums.org/showthread.php?t=234588](http://ubuntuforums.org/showthread.php?t=234588)
[http://ubuntuforums.org/showthread.php?t=360901](http://ubuntuforums.org/showthread.php?t=360901)

I followed everything in the first guide to the letter, and when that failed, did the things that I hadn't already done that were in the second guide. Still no dice.

The only thing I'm doing that isn't said in the the guides is using 'http://www.dslreports.com/wakeup' to send the magic packets rather than using another computer, as this is the only Linux system I've got access to at the moment.

I am behind a router but I forwarded port 9 (UDP), and when that failed, I even created a DMZ to ensure everything got through. I tried pinging the computer and that worked fine.

I checked that my NIC was capable of Wake on Lan with ethtool and I ensured that my (AMI) BIOS had Wake on Lan turned on (S3 in AMI). I've restarted a number of times to ensure that the computer was shutdown safely.

I can't think of anything else I can do, I've been Googling the problem for hours and I've tried everything. Please help me out. :(

---

### Post by tgalati4 on 2010-11-20
Use acpitool to keep power ON for parts of your bus.

[http://ubuntuforums.org/showthread.php?t=1380776&highlight=acpitool](http://ubuntuforums.org/showthread.php?t=1380776&highlight=acpitool)

---

### Post by tgalati4 on 2010-11-20
Duplicate post.

---

### Post by Madman525 on 2010-11-20
Thanks for the reply! I'm not quite sure how to do that. I thought that's what this line: 'ethtool -s eth0 wol g' in the script was for.:-s

---

### Post by Madman525 on 2010-11-20
Thanks. I've just installed acpitool and got the following output:

```

    Device	S-state	  Status   Sysfs node
  ---------------------------------------
  1. P0P1	  S3	*disabled  pci:0000:00:1e.0
  2. USB2	  S3	*disabled  pci:0000:00:1d.2
  3. USB5	  S3	*disabled  
  4. EUSB	  S3	*disabled  pci:0000:00:1d.7
  5. USB3	  S3	*disabled  pci:0000:00:1a.0
  6. USB4	  S3	*disabled  pci:0000:00:1a.1
  7. USB6	  S3	*disabled  pci:0000:00:1a.2
  8. USBE	  S3	*disabled  pci:0000:00:1a.7
  9. GBE	  S4	*disabled  
  10. P0P4	  S4	*disabled  pci:0000:00:1c.0
  11. P0P5	  S4	*disabled  
  12. P0P6	  S4	*disabled  pci:0000:00:1c.2
  13. P0P7	  S4	*disabled  pci:0000:00:1c.3
  14. P0P8	  S4	*disabled  pci:0000:00:1c.4
  15. P0P9	  S4	*disabled  pci:0000:00:1c.5
  16. NPE1	  S4	*disabled  pci:0000:00:01.0
  17. NPE2	  S4	*disabled  
  18. NPE3	  S4	*disabled  pci:0000:00:03.0
  19. NPE4	  S4	*disabled  
  20. NPE5	  S4	*disabled  
  21. NPE6	  S4	*disabled  
  22. NPE7	  S4	*disabled  pci:0000:00:07.0
  23. NPE8	  S4	*disabled  
  24. NPE9	  S4	*disabled  pci:0000:00:09.0
  25. NPEA	  S4	*disabled  
  26. USB0	  S3	*disabled  pci:0000:00:1d.0
  27. USB1	  S3	*disabled  pci:0000:00:1d.1
```

I'm about to restart and try again. I'll give an update then.

---

### Post by Madman525 on 2010-11-20
I just tried again. Still nothing. I also tried from within the LAN using AMD Magic Packet Utility in Vista, I also tried with a URL assigned to my IP by DynDNS, I tried both of the network card ports. No change.

---

### Post by Madman525 on 2010-11-20
I thought I ought to mention I that I do get a light from the NIC when the computer is shutdown. I'm assuming that that means my BIOS is properly configured?

---

### Post by tgalati4 on 2010-11-20
I would imagine that you need one or more parts of your computer bus "enabled"--Start with the pci slot that your network card is attached to.  Then maybe the USB ports that the keyboard and mouse are attached to.

It's possible that your computer acpi doesn't support WOL or it's buggy.  Just because the network card chipset supports it doesn't mean that the computer supports it.

And yes, the flashing lights on the network port are a necessary condition for WOL to work.  No lights--No wakey.

---

