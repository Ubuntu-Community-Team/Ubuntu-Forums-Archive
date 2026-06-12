---
title: "Ubuntu 10.04, Enabling network"
date: 2010-09-16
forum: Networking &amp; Wireless
---

### Post by Rama123 on 2010-09-16
Hi,
I have installed Ubuntu 10.04 in My NEW personal Dell Inspiron Laptop....presently Ubuntu 10.04 is the only OS in my laptop.
I have Private network connection via Modem. If I connect the Network cable, "Ethernet" port will STOP blinking and I have no clue how to activate the internet in it.
If i connect the same cable to different PC or laptop which is having Windows OS, network is working fine.
 
Earlier I had Windows 7 in the same laptop in which network used to work without problem.
 
Thanks,
Ram.

---

### Post by dineshs on 2010-09-16
Pl post the result of```
sudo lshw -C network
```
Also ensure that Enable wired is ticked(Right click on the NM icon on top right of the panel)

---

### Post by Rama123 on 2010-09-16
Hi Dinesh,
Thanks for your quick response...Since I am a NEW USER to Ubuntu...request you to please elaborate your response...so that i can follow the steps and try.
Regards,
Ram.

---

### Post by dineshs on 2010-09-16
Open a terminal(applications -accessories-terminal)
copy and paste the command inside the box
```
sudo lshw -C network
```
hit enter
and let us know the result you get.(select the results all lines -rightclick and copy)

---

### Post by Rama123 on 2010-09-16
Hello Dinesh,
This is the message i am getting..
 
[EMAIL="pandurangi@pandurangi-laptop:~$"]pandurangi@pandurangi-laptop:~$[/EMAIL] sudo ishw -C network
[sudo] password for pandurangi: 
sudo: ishw: command not found
[EMAIL="pandurangi@pandurangi-laptop:~$"]pandurangi@pandurangi-laptop:~$[/EMAIL] sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: [EMAIL="pci@0000:03:00.0"]pci@0000:03:00.0[/EMAIL]
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0500000-f0503fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: [EMAIL="pci@0000:04:00.0"]pci@0000:04:00.0[/EMAIL]
       version: c1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
       resources: memory:f0400000-f043ffff ioport:2000(size=128)
[EMAIL="pandurangi@pandurangi-laptop:~$"]pandurangi@pandurangi-laptop:~$[/EMAIL] 

I do not know whether ethernet card that is compatible with Ubuntu 10.04 is there in my laptop.
 
Need help desperately.
 
Regards,
Rama.

---

### Post by l0stendeavor on 2010-09-17
I am having the same problem with a clean install of 10.04 64 bit on a dell inspiron system with an identical lshw readout.

---

### Post by dineshs on 2010-09-17
> product: AR8152 v1.1 Fast Ethernet
[Here]("http://ubuntuforums.org/showthread.php?p=9449490") is a similar thread
For installing build-essential see step-1 [here]("http://ubuntuforums.org/showpost.php?p=9738022&postcount=7")

---

