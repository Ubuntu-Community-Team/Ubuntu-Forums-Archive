---
title: "CPU Usage ksoftirqd"
date: 2009-07-24
forum: Mythbuntu
---

### Post by smi402 on 2009-07-24
I have installed mythbuntu-amd64 Jaunty (9.04) on a frontend only machine. It is served by a mythbackend running on a separate Quad Core machine running the Jaunty 9.04 desktop version. Both the backend and frontend work well, but I note the frontend machine has about 25% usage of one of its dual core CPUs even though nothing but the Xfce desktop is running on that machine. Curious to find out what processes may be causing this I ran the **top** command and find that **ksoftirqd** is the culprit.

```
PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND 
 4 root      15  -5     0    0    0 S   24  0.0   8:14.42 ksoftirqd/0
```

Other processes are using a trivial amount of CPU and system monitor reveals there is no network traffic.

Running **cat /proc/interrupts** produces the following output:
```

           CPU0       CPU1       
  0:        115          2   IO-APIC-edge      timer
  1:        147        141   IO-APIC-edge      i8042
  6:          3          2   IO-APIC-edge      floppy
  8:          1          0   IO-APIC-edge      rtc0
  9:          0          0   IO-APIC-fasteoi   acpi
 14:      34626      34639   IO-APIC-edge      ata_piix
 15:       3094       3091   IO-APIC-edge      ata_piix
 16:       2651       2670   IO-APIC-fasteoi   uhci_hcd:usb5, eth0, nvidia
 18:       2537       2519   IO-APIC-fasteoi   uhci_hcd:usb4
 19:          7         11   IO-APIC-fasteoi   uhci_hcd:usb3, CMI8738-MC8
 23:        589        585   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb2
NMI:          0          0   Non-maskable interrupts
LOC:     482586     486173   Local timer interrupts
RES:       1103       1133   Rescheduling interrupts
CAL:       1385        579   Function call interrupts
TLB:        918        844   TLB shootdowns
SPU:          0          0   Spurious interrupts
ERR:          0
MIS:          0

```

Clearly something is triggering soft interrupts that are being queued and results in this level of CPU usage. I would be grateful if anyone can help interpret what may be going on in this frontend machine. I also note that the hard drive activity light blinks about once per second even though the machine is sitting idle with just the Xfce desktop displayed. Just in case I had a bad drive I did a clean Mythbuntu installation on a new drive but the problem persists.

My setup on this frontend machine is:
Intel 2.4GHz Core2Duo CPU
Gigabyte GA-G31M-S2L motherboard
Gigabyte GeForce 8500GT Graphics Card
CMedia Striker 7.1 PCI Sound Card
ANTEC Media Centre case and 430Watt Power Supply

There are no such problems on my 9.04 backend Quad Core machine - **top** indicates no **ksoftirqd** activity on any of the 4 cores on that machine and system monitor indicates CPU usage only just above the baseline when the machine is running only the Gnome desktop.

Thanks in advance,
Frank

---

### Post by smi402 on 2009-07-24
A couple of additional pieces of information that I should have supplied in my first post above:

This machine has 2 GiB of memory
The hard disk is formatted with the ext4 filesystem
Mythbuntu is running the 2.6.28-13-generic kernel

Frank

---

### Post by smi402 on 2009-07-25
bump!! Has anyone any ideas about what may be generating this CPU usage?

I removed the Striker 7.1 sound card in case that may have been generating interrupts but that had no effect on CPU usage - it remained up around 26% for one of the cores.

Frank

---

### Post by smi402 on 2009-07-26
I have located the problem with excessive CPU usage. In listing my hardware above I had forgotten that I had an Agere Systems ET-131x PCI-E gigabit NIC card in the PCIe x1 slot on the motherboard. The 2.6.28-13 kernel in Jaunty has a driver module for this PCIe NIC card and **lspci** indicates that driver is loaded at startup. It establishes a network connection and does work, but has a bug in it that causes wakeups from the processor sleep states 250 times per second. This triggers **ksoftirqd** and the observed increase in CPU usage. This bug has been reported and we hope that it will be fixed in the next release of the kernel.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/308705]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/308705")

Unfortunately the on-board NIC connection on my motherboard is unreliable so I have it turned off and simply installed the PCIe NIC card in the PCIe x1 slot and used that. Unfortunately these microATX motherboards that fit in the Media Centre cases have only 1 PCIe x1 slot and 2 PCI slots, one of which is unusable because the heat sink on the graphics card covers that slot. So, I will have to look around for another solution until the et131x driver for Jaunty is fixed (or perhaps just put up with the extra load on the CPU for the time being).

Frank

---

