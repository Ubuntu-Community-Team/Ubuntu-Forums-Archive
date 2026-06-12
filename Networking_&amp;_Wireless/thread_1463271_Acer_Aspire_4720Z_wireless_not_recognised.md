---
title: "Acer Aspire 4720Z wireless not recognised"
date: 2010-04-26
forum: Networking &amp; Wireless
---

### Post by Ignotus Angelus on 2010-04-26
Hello,
 
I just installed Ubuntu on my computer, and it will not display wireless.
 
I researched other posts and found something to do to display info, perhaps someone will be able to tell me what is wrong?
 
Here is what I did
 
**sudo lshw -C network **in Terminal. It came up with this information:
 
[FONT=Times New Roman][SIZE=3]ignotusangelus@ignotusangelus-laptop:~$ sudo lshw -C network[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]  *-network UNCLAIMED     [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       description: Network controller[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       product: BCM4311 802.11b/g WLAN[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       vendor: Broadcom Corporation[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       physical id: 0[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       bus info: pci@0000:04:00.0[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       version: 01[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       width: 32 bits[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       clock: 33MHz[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       capabilities: pm msi pciexpress cap_list[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       configuration: latency=0[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       resources: memory:80000000-80003fff[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]  *-network[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       description: Ethernet interface[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       product: NetLink BCM5787M Gigabit Ethernet PCI Express[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       vendor: Broadcom Corporation[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       physical id: 0[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       bus info: pci@0000:05:00.0[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       logical name: eth0[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       version: 02[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       serial: 00:1e:68:1b:e9:9a[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       capacity: 1GB/s[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       width: 64 bits[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       clock: 33MHz[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 firmware=5787m-v3.23 latency=0 link=no multicast=yes port=twisted pair[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       resources: irq:28 memory:80100000-8010ffff[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]ignotusangelus@ignotusangelus-laptop:~$ ^C[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]ignotusangelus@ignotusangelus-laptop:~$ [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
**Can anyone help me fix my problem? I would be very grateful**

---

### Post by Ignotus Angelus on 2010-04-26
ndisgtk is not installed on my laptop, by the way, I searched in Synaptic Package Manager.
 
How do I install it if I don't have an internet connexion on my laptop?
 
Can anyone help me, please???

---

### Post by Ignotus Angelus on 2010-04-26
I did a lspci too, not that anyone is really reading... :3
 
[FONT=Times New Roman][SIZE=3]ignotusangelus@ignotusangelus-laptop:~$ lspci[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]04:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]0a:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]0a:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]0a:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]0a:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]0a:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]ignotusangelus@ignotusangelus-laptop:~$ [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]

---

### Post by bkratz on 2010-04-26
You really shouldn't need ndisgtk (ndiswrapper) the 4311 is mentioned here

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by Ignotus Angelus on 2010-04-26
Uhm... what is the 4311?
 
Which of these sets of instructions should I follow?

---

### Post by Ignotus Angelus on 2010-04-26
:( I'm in deep sh*t now...
 
When I'm trying to reload the Synaptic Package Manager, it says 
 
"An error occurred
The following details are provided:
 
[FONT=Times New Roman][SIZE=3]W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg)  Could not resolve 'security.ubuntu.com'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: Some index files failed to download, they have been ignored, or old ones used instead.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
So now... what do I do? I'm really starting to panic here!!!

---

### Post by Ignotus Angelus on 2010-04-26
I am completely reinstalling Ubuntu on my computer right now, to start afresh. -.-
 
I will post the  lpsci and what not after I am done installing.

---

### Post by bkratz on 2010-04-26
From the listing above (post 3) the 4311

04:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

is your wireless card. The BCM4311 is in the first half of that thread.  Do you have the wired connection attached when trying to reload?

---

### Post by Ignotus Angelus on 2010-04-26
Wired Network is disconnected (normal, I don't have a cable)
 
Wireless Networks are disconnected (that is more annoying)
 
Now for the lspci in Terminal
 
```

[FONT=Calibri][FONT=Calibri]ignotusangelus@ignotusangelus-laptop:~$ lspci[/FONT]
 
[FONT=Calibri]00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)[/FONT]
 
[FONT=Calibri]00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)[/FONT]
 
[FONT=Calibri]00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)[/FONT]
 
[FONT=Calibri]00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)[/FONT]
 
[FONT=Calibri]00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)[/FONT]
 
[FONT=Calibri]00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)[/FONT]
 
[FONT=Calibri]00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)[/FONT]
 
[FONT=Calibri]00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)[/FONT]
 
[FONT=Calibri]00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)[/FONT]
 
[FONT=Calibri]00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)[/FONT]
 
[FONT=Calibri]00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)[/FONT]
 
[FONT=Calibri]00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)[/FONT]
 
[FONT=Calibri]00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)[/FONT]
 
[FONT=Calibri]00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)[/FONT]
 
[FONT=Calibri]00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)[/FONT]
 
[FONT=Calibri]00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)[/FONT]
 
[FONT=Calibri]00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)[/FONT]
 
[FONT=Calibri]00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)[/FONT]
 
[FONT=Calibri]00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)[/FONT]
 
[FONT=Calibri]04:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)[/FONT]
 
[FONT=Calibri]05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)[/FONT]
 
[FONT=Calibri]0a:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)[/FONT]
 
[FONT=Calibri]0a:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)[/FONT]
 
[FONT=Calibri]0a:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)[/FONT]
 
[FONT=Calibri]0a:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)[/FONT]
 
[FONT=Calibri]0a:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)[/FONT]
 
[FONT=Calibri]ignotusangelus@ignotusangelus-laptop:~$ [/FONT]
[/FONT]
```
 
So now... where do I go from here? Can anyone give me a precise step by step instruction about this?
 
My computer is a laptop Acer Aspire 4720Z 32 bits, if that will be of any help.

---

### Post by mcoleman44 on 2010-04-26
Is there anyway you can get a cable? This would be a very simple fix if you could.

---

### Post by Ignotus Angelus on 2010-04-26
No I can't, I'm afraid :(
 
its a wireless modem connected to a main computer. I cannot disconnect that without losing the connexion entirely.
 
I am presently working on it as we speak.

---

### Post by mcoleman44 on 2010-04-26
Try this:
1 Open Synaptic Pacakage Manager
2 Ensure the LiveCd is in CD drive
3 Settings > Repositories > Ubuntu Software
4 Check the "installable from cd" Box and close
5 Refresh
6 Search for "bcmwl-kernel-source"
7 Mark for installation
8 Install it
9 Reboot computer

This should take care of the problem.

---

### Post by Ignotus Angelus on 2010-04-26
Oh dear... everything is just fine until I reach the Refresh.
 
I have a pop up that says "An error occurred"
 
The following details are provided:
 
followed by a flop of "Failed to fetch" this and that and what not.

---

### Post by mcoleman44 on 2010-04-26
Thats fine, its not going to refresh the online sources seeing as you are unable to access the Internet but it should have added the cd to the search index. Did you search for bcmwl-kernel-source yet?

---

### Post by Ignotus Angelus on 2010-04-26
Yes, I installed it, and am now rebooting...
 
Oh my god, miracle!!!! :D
 
You, Sir, are a genius, and I would hug you if you were here!
 
Thank you !!!!!

---

### Post by mcoleman44 on 2010-04-26
Hate to burst your bubble but it probably wont work just yet. Lol 
after you reboot go to system>admin>hardware drivers and install the wireless driver if needed.

---

### Post by Ignotus Angelus on 2010-04-27
No, it actually worked!!!

:D

I logged in and immediately the wireless signal was picked up by my computer! I simply entered the WEP key and the password and poof! Instant internet!

Thank you again! I am now on the internet from my laptop and exploring all the awesome features!

Long live Ubuntu!

---

### Post by mcoleman44 on 2010-04-27
Im glad I could help!

---

