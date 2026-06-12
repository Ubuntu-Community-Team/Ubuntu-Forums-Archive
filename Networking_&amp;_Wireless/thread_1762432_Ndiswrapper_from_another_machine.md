---
title: "Ndiswrapper from another machine?"
date: 2011-05-19
forum: Networking &amp; Wireless
---

### Post by meddyuk on 2011-05-19
Ive just got a new pc but have only got wireless internet. Am i able to copy the relevant folders from the old pc to the new one and get the ndiswrapper working that way?

---

### Post by chili555 on 2011-05-19
Do you mean you want to copy ndiswrapper the program package or the .inf and, possibly .sys files?

If you are also running the same version of Ubuntu on the old computer and new computer, you can probably go to /var/cache/apt/archives on the old computer and find archived copies of ndiswrapper-common and ndiswrapper-utils. However, these files are on the install CD and could easily be found and installed from there.

If you are talking about the Windows XP .inf and .sys files, you could copy those over if and only if you have the exact same wireless device. If you run:```
lspci -nn
```Is the pci.id exactly the same? Here is a sample from my machine:> Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [[COLOR="Red"]8086:4227[/COLOR]] (rev 02)Are the two wireless devices *_exactly_* the same? If so, you may safely copy over the .inf and .sys files.

---

### Post by meddyuk on 2011-05-19
> **chili555 said:**
>  However, these files are on the install CD and could easily be found and installed from there.
 
.
 
I got the installation CD and went to software manager and deselected everything and selected CD in sources, but it failed to download it stating that there was no internet connection.

---

### Post by chili555 on 2011-05-19
After you put the CD as a source in Synaptic, press Reload so it indexes the files on the CD, can you see and select ndiswrapper to install? Of course, you can also browse the CD and go to pool/main/n/ndiswrapper and drag and drop the two files to your desktop. Then open a terminal and do:```
cd Desktop
sudo dpkg -i ndis*.deb
```The wildcard * selects all .deb files on your desktop that start with ndis; all of them!

---

### Post by meddyuk on 2011-05-20
Sorted found a way of getting it of the live cd. Thanks for your help.

---

