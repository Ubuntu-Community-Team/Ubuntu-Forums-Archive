---
title: "Is it possible to have Mythtv running on Ubuntu Server in a Virtual box partition?"
date: 2013-04-07
forum: Mythbuntu
---

### Post by grunge09 on 2013-04-07
I have kinda a Ubuntu Server kinda Mythtv question.

I have 2 PC's now I had the whacky thought of combining into one pc.  Using Ubuntu Server PC, installing virtual box and somehow converting my existing mythtv pc HD to a virtual box machine that autostarts after the server is up.  

1st PC - Mythtv

MSI MB - gigabit NIC
AMD 965 3.4GHz quad core CPU
4 GB RAM
1TB Sata II HD
DVD Rom Drive
Geforce 210 PCI Express video card with HDMI Out to 37" LCD TV)
Ubuntu 11.10 Desktop with Mythtv installed
HVR-2250 (using analong duners only)
2 x PVR-500 cards using each 2 tuners
(that makes 6 analog tuners)

Mythtv data os on my Ubuntu Server PC

2nd PC - Ubuntu Server (using Samba for 3 other machines also for backups)

Asus MB - gigabit NIC
AMD 6000+ dual core CPU
2 GB RAM
ATI mach 64 pci video card
1 8GB Flash Boot Drive
4 2tb drives in RAID5 with Hot spare USING MDADM and onboard sata controllers.
using Webmin

All my MYTHTV recordings are on the RAID5.  They started out being one a 1tb drive on the myth box, then using DD to copy that data and expand to a 2TB drive, then ran out of space and moved it over the network to a 4tb RAID5 array.

I can move the 210 HDMI video card & the 3 tuner cards over easy enough.  BUT if I can somehow virtualize the mythtv install can I run it and access the server RAID5 for the data.  

I always thought  that a virtual machine could not access the host hard drives?  Could I use another NIC in the same PC to access the server raid 5 data?

Can this even be done or am I spinning my wheels.

---

### Post by Cheesemill on 2013-04-07
The main problem you are going to come across is that your VM wont be able to use your tuner cards.

A VirtualBox VM doesn't have access to any of the physical hardware on the host machine, it has a virtual network card, video card and hard drive meaning it can't see what's plugged in to your PCI slots. You can pass through USB devices from the host machine to the guest VM but I'm guessing your tuners are PCI devices.

There are different virtualization solutions that you could use (KVM and ESXi) which have a feature called PCI passthrough which would let your VM have access to the PCI slots, but you need a CPU and motherboard combination that supports this feature for it to work. Most desktop processors don't have this feature which is usually only found on server hardware (look out for VT-d for Intel chips or AMD-Vi for AMD chips).

---

