---
title: "Unable to access the internet."
date: 2013-03-08
forum: Networking &amp; Wireless
---

### Post by mstevens33 on 2013-03-08
I am relatively new to Ubuntu, so please be patient with me.
I am currently working on my friends laptop that had crashed, he requested I set up Ubuntu on his laptop.

I am currently running into two issues, 

1.) My eth0 ports are missing, so I cannot hard wire the computer to the internet.

2.) My wireless is not function either.

Now, when I log on the laptop I do get this error: (And I am unsure if this is affecting my issue at all)

PXE-E05 - Lan adapter configuration is either corrupted or not initialized. The boot agent could not continue.

Thank you for your help, please let me know what information you would need to help me.

---

### Post by grahammechanical on 2013-03-08
You might want to read this about PXE [http://en.wikipedia.org/wiki/Preboot_Execution_Environment](http://en.wikipedia.org/wiki/Preboot_Execution_Environment) It means that the computer is set up to connect to a network server to look for a boot loader. This set up was used on the computers that served as tills in the high street store were I used to work. It means unless the machine is connected to the network it will not boot an operating system. You may need to disable a setting in the BIOS. Other than that, I do not know. You may also find that Ethernet and wireless have been disabled in the BIOS. Until you fix the issue with PXE you cannot go any further.

---

### Post by prodigy_ on 2013-03-08
More info is needed. Did you try to boot the laptop with a LiveCD or LiveUSB? Did you check boot device order in BIOS? Make sure that the device you're trying to boot from (e.g. optical drive) is the first on the list (or the second, right after HDD).

> **grahammechanical said:**
> Until you fix the issue with PXE you cannot go any further.
I suspect that the laptop simply cannot find any boot media and proceeds to network (PXE) boot which is commonly the last option in boot device order lists.

---

### Post by sleash78 on 2013-03-08
press f2 (in general) when a computer turns on to view or modify the bios settings as needed

---

### Post by mstevens33 on 2013-03-10
The PXE error is fixed, I fixed the boot order, so its running properly again, however, Ubuntu is still not recognizing the Ethernet port. How do I go about fixing that?

@Prodigy_ I used a live CD.

Also, the laptop is an HP-530.

---

### Post by prodigy_ on 2013-03-10
Open terminal and run ```
sudo lshw -C network
``` command. Post the output here.

---

### Post by mstevens33 on 2013-03-11
> **prodigy_ said:**
> Open terminal and run ```
sudo lshw -C network
``` command. Post the output here.

Here you go:

```
*-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0000000-f0003fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64 maxlatency=56 mingnt=8
       resources: memory:f0101000-f0101fff ioport:2000(size=64)


```

---

### Post by prodigy_ on 2013-03-12
"Unclaimed" means no driver is loaded. For wired you need **e100**, try: ```
sudo modprobe e100
dmesg | grep e100
```

About W-iFi I'm not sure, never had Broadcom myself. Search the forum for BCM4311, there are a lot of threads. Or PM **chili555**, he's an expert. :)

---

### Post by mstevens33 on 2013-03-12
...and the results of the message:

```
[    0.212785] pci 0000:02:08.0: >Firmware left e100 interrupts enabled; disabling
[    1.485305] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
[    1.485311] e100: Copyright(c) 1999-2006 Intel Corporation
[    1.511165] e100 0000:02:08.0: >(unregistered net_device): EEPROM corrupted
[    1.536252] e100: probe of 0000:02:08.0 failed with error -11
```

---

### Post by prodigy_ on 2013-03-12
> **mstevens33 said:**
> EEPROM corrupted
To work around this error: ```
sudo modprobe -r e100
sudo modprobe e100 eeprom_bad_csum_allow=1
```

---

### Post by mstevens33 on 2013-03-12
You are my hero, that worked, thank you very much! BTW, I did notice, that typing what you said does make the eth0 port work, however, whenever I reset, so does that command, and I have to go into terminal to redo the entire thing, how do I make it stay that way?

Now, for the final issue:

```
*-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0000000-f0003fff
```

---

### Post by prodigy_ on 2013-03-12
> **mstevens33 said:**
> how do I make it stay that way?
```
echo "options e100 eeprom_bad_csum_allow=1" | sudo tee -a /etc/modprobe.d/e100.conf
sudo update-initramfs -u
```

> **mstevens33 said:**
> Now, for the final issue
[http://ubuntuforums.org/showthread.php?t=1997880&p=12001985&viewfull=1#post12001985](http://ubuntuforums.org/showthread.php?t=1997880&p=12001985&viewfull=1#post12001985)

---

### Post by mstevens33 on 2013-03-13
That solves it all, it is running properly! Thank you for all your help!

---

### Post by BlinkinCat on 2013-03-13
> **mstevens33 said:**
> That solves it all, it is running properly! Thank you for all your help!


Hi,

You could now mark thread as solved -

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Cheers - :p

---

### Post by mstevens33 on 2013-05-08
Friend updated his computer to 13.04 without knowing what he was doing, everything is down again.
I want into terminal and followed the previous steps, however when I try:
```
sudo modprobe e100
```
...give me the following error:
```
FATAL: Module e100 not found.
```

Please help.

---

