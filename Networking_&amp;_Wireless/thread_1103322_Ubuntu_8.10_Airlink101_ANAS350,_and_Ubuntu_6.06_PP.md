---
title: "Ubuntu 8.10 Airlink101 ANAS350, and Ubuntu 6.06 PPC"
date: 2009-03-22
forum: Networking &amp; Wireless
---

### Post by markosjal on 2009-03-22
I now have two ubuntu installations running. 

I have an Airlink101 ANAS350 with one internal Hard Disk and one external USB hard disk (to NAS USB Port) as well as using it as an PPR/LPD print server (to NAS USB Port)

I have managed to connect Ubuntu through SMB to the ANAS350 as well as the printer, and that all works fine.

What I want to know is that if anyone has had any success at connecting to this device WITHOUT SMB , perhaps over another protocol. The documents claim Linux and Mac compatibility, however I suspect the compatibility as stated relies on SAMBA. 

Since I know this device uses a Linux Kernel, and I have seen the Linux boot partition, would any likely Linux protocol be NFS? Is there another protocol possibility? 

What is the correct procedure for connecting to an NFS share? I have tried
sudo mount mnt:/192.168.1.253 /mnt/NAS_C
Where 192.168.1.253 is the ANAS 350 IP /mnt/NAS_C is the mount point that I have created a blank folder for. Perhaps there is something wrong in my syntax?

I would like to eliminate Microsoft Networking/SAMBA from my network if Possible as I will not be needing it anymore if I keep no windows machines on my network. 


On an unrelated note, why does Ubuntu REQUIRE the IP address of windows shares before it will see them? It seems I can not browse the network but if I enter the IP address of the ANAS350 it can connect via SMB. I have seen others post this here and I have to date, not seen a solution for it.

---

