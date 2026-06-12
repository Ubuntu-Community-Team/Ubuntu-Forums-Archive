---
title: "Ath5k Driver is Not Working"
date: 2009-02-15
forum: Networking &amp; Wireless
---

### Post by alea21 on 2009-02-15
I have a Compaq Presario C700 with an Atheros 802.11abg Wireless PCI Express Adapter and Realtek Semiconductor. I'm using Intrepid 8.10.
I got the wireless working last night but I installed some updates without checking what they were and went to bed, I woke up, rebooted my computer and the wireless wasn't working. I tried to do the "sudo athload ath5k" and it said it was loaded successfully but nothing changed.
I tried to reinstall it but nothing is happening.

Any ideas on what I did or have to do?

---

### Post by azwar on 2009-02-15
It had happen to me last month. 
It is say that "unable to wake the MAC Chip". Try to boot you laptop again, then press Alt + F1 to see any error when it load the ath5k driver. But not sure about your problem same with me or not. Just try it to check.

---

### Post by kevdog on 2009-02-15
After your sudo modprobe ath5k statement, did you check dmesg (system log) for any relevant output).  Can you also post lshw -C network

---

### Post by alea21 on 2009-02-15
Yes, it does say "unable to wakeup MAC Chip" in the dmesg file.

And this is the lshw -C network:

Hardware Lister (lshw) - B.02.13
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.13)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-c CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)
	-numeric        output numeric IDs (for PCI, USB, etc.)
Hardware Lister (lshw) - B.02.13
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.13)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-c CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)
	-numeric        output numeric IDs (for PCI, USB, etc.)

---

### Post by alea21 on 2009-02-15
Help?

---

