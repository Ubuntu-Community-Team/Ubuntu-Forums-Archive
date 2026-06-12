---
title: "Samba + Raid Array issues"
date: 2009-01-22
forum: Networking &amp; Wireless
---

### Post by synthetic_fenix on 2009-01-22
I just recently upgraded my home server from a dual Xeon 1.6Ghz setup with a 1.2TB raid 5 array on an LSI logic Mega Raid controller. To an AMD Phenom 9850 with 8Gb of Ram, an Areca PCI-E 8x hardware raid card (ARC-1210) running a 4.5TB array along with my 1.2TB array still on the LSI Logic card. I moved everything over from my old array to my new one with no problems. Reconfigured my samba config to point to the new locations of my shares on my new array and I will be using my old array for VMware, and backups. Tonight I was copying stuff of my gaming rig which is running XP PRo x64 and I Was copying an directory that is 913MB in size with quite a few small files in it. It was going to take over an hour to copy so I canceled it and decided to do some network testing. My network tests fine everything running at gigabit speeds. My server has dual Broadcom gig nics on its Asus Server board, and my Gaming rig has an Intel Pro PCI-E gig card. So I then decided to test if it was the array so I copied the same directory to my old array in the server over the network and it copied in about 2 minutes or less. So to check if its the new array not liking small files I did a timed copy between arrays and the copy took 8 seconds for the 913MB directory. So after this I figure ok its not the array. To further prove to myself that its not the array, I got on my mythbox which also has a PCI-E intel pro gig card in it and copied the directory to it via NFS and back over the the share on that array in a different location and via NFS i was able to copy that data in 30.321s. So my question is, what would cause these issues in Samba to where a copy of files takes substantially longer onto a faster array then an slower one but only over Samba. FTP, NFS all copy to their full bandwidth capability on my network.

Full System specs

File server:
Motherboard: Asus M2N-LR
CPU : Phenom 9850 Quad Core 2.5Ghz
Ram : 8Gb of DDR2 800
Array 1 : LSI Logic Megaraid 150-6 PCI-X 100Mhz with 6x250GB Maxtor Sata 1.5Gb/s Hard drives in raid 5 (1.2TB total)
Array 2 : Areca ARC-1210 PCI-E 8x with 4x1.5TB Seagate Sata 3Gb/s hard drives in Raid 5 (4.5TB total)
OS: Ubuntu 8.10 64bit

Gaming Rig

Motherboard : Gigabyte GA-MA790GP-DS4H
CPU : Phenom II 940 Quad Core 3.7Ghz
RAM : 4Gb of DDR2 1066
Hard Drive : 750GB Seagate HArd drive
OS : Windows XP x64


Also as a final note, to check if this was maybe an issue with the gig cards being on the same bus as the ARECA card, I installed a PCI intel gig card tested and only got the 431Mb/s in IPERF between my server and my mythbox. This did no help that problem. if requested I can post my samba config and anything else that may help with this matter.

---

