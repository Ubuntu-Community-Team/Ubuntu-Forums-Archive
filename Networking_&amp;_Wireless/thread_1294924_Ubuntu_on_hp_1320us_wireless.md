---
title: "Ubuntu on hp 1320us wireless"
date: 2009-10-18
forum: Networking &amp; Wireless
---

### Post by flyn_brian on 2009-10-18
I installed Ubuntu on my hp 1320 us laptop because vista is terrible:mad: and now im having trouble getting my wireless setup to work. when I boot it up it shows that its connected both on Ubuntu and physically on the computer. But when I go into the terminal this is what I get.
 
[LEFT][FONT=NimbusRomNo9L-Regu]brian@brianlaptop:~$[/FONT]
[FONT=NimbusRomNo9L-Regu]sudo lshw C[/FONT]
[FONT=NimbusRomNo9L-Regu]network[/FONT]
[FONT=NimbusRomNo9L-Regu][sudo] password for brian:[/FONT]
[FONT=NimbusRomNo9L-Regu]*network[/FONT]
[FONT=NimbusRomNo9L-Regu]description: Wireless interface[/FONT]
[FONT=NimbusRomNo9L-Regu]product: BCM4328 802.11a/b/g/n[/FONT]
[FONT=NimbusRomNo9L-Regu]vendor: Broadcom Corporation[/FONT]
[FONT=NimbusRomNo9L-Regu]physical id: 0[/FONT]
[FONT=NimbusRomNo9L-Regu]bus info: pci@0000:03:00.0[/FONT]
[FONT=NimbusRomNo9L-Regu]logical name: eth1[/FONT]
[FONT=NimbusRomNo9L-Regu]version: 03[/FONT]
[FONT=NimbusRomNo9L-Regu]serial: 00:1a:73:8d:2b:cd[/FONT]
[FONT=NimbusRomNo9L-Regu]width: 64 bits[/FONT]
[FONT=NimbusRomNo9L-Regu]clock: 33MHz[/FONT]
[FONT=NimbusRomNo9L-Regu]capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless[/FONT]
[FONT=NimbusRomNo9L-Regu]configuration: broadcast=yes driver=wl0 driverversion=5.10.79.10 ip=10.42.43.1 latency=0[/FONT]
[FONT=NimbusRomNo9L-Regu]module=wl multicast=yes wireless=IEEE 802.11abgn[/FONT]
[FONT=NimbusRomNo9L-Regu]*network[/FONT]
[FONT=NimbusRomNo9L-Regu]DISABLED[/FONT]
[FONT=NimbusRomNo9L-Regu]description: Ethernet interface[/FONT]
[FONT=NimbusRomNo9L-Regu]physical id: 1[/FONT]
[FONT=NimbusRomNo9L-Regu]logical name: pan0[/FONT]
[FONT=NimbusRomNo9L-Regu]serial: c6:84:94:81:13:74[/FONT]
[FONT=NimbusRomNo9L-Regu]capabilities: ethernet physical[/FONT]
[FONT=NimbusRomNo9L-Regu]configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes[/FONT]
[FONT=NimbusRomNo9L-Regu]multicast=yes[/FONT][/LEFT]
[FONT=NimbusRomNo9L-Regu]brian@brianlaptop:~$[/FONT]
 
[FONT=NimbusRomNo9L-Regu]This has me pulling my hair out if any body can help me I would be more than greatfull. Right now I'm on the dreaded vista and hate it. Any help would be greatly appreciated and thank you in advance[/FONT]

---

### Post by flyn_brian on 2009-10-18
I just connect a patch cord and tried it and it works. Now If I can get the wireless up and running I wouldnt need vista

---

### Post by flyn_brian on 2009-10-19
Please somebody Im begging and I dont usually beg

---

### Post by bkratz on 2009-10-19
> **flyn_brian said:**
> Please somebody Im begging and I dont usually beg



Here is an interesting thread which might help you.

[http://ubuntuforums.org/showthread.php?t=1134631&highlight=BCM4328](http://ubuntuforums.org/showthread.php?t=1134631&highlight=BCM4328)

---

### Post by flyn_brian on 2009-10-20
Thank you for your reply it really is appreciated. I've tried turning the wireless off and then back on. Also I tried disabling the driver then enabling it but to my dismay it didn't work. I may try a different router I have a buffalow router that I never used. The wierd thing is is that it says Im hooked up to the belkin but I have no internet. I hope its not the broadcom driver:(

---

### Post by houstonbofh on 2009-10-21
Those broadcom card have been bad for a while... But recently they really went off the deep end.  You can try this [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) and keep up on the forums for a fix.  I too am still waiting.  But I also am using an old Orinco card till it gets fixed.

---

### Post by flyn_brian on 2009-10-23
I changed the settings on my router from 128 bit wep to 64 bit wep now my issue is resolved.I might try to go back to 128 bit wep just to see if it was my dumb self getting the password wrong.:)

---

