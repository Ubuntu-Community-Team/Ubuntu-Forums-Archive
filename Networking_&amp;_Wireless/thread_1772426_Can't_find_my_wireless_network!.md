---
title: "Can't find my wireless network!"
date: 2011-05-31
forum: Networking &amp; Wireless
---

### Post by Naderino on 2011-05-31
I was using ubuntu 9.04 and everything was working flawlessly with my network. The only problem with 9.04 is that it was unsupported and I couldn't install the packages I wanted to such as Cairo dock so I decided to upgrade to 9.10 which is a lot better. However I ran into a problem that I never had on 9.04. I cant connect to MY wireless network (my Belkin wireless card can detect networks but not mine) I have a netgear router WNDR3700v2 with WPA2 encryption. I thought that the encryption was the problem so I turned it off and ubuntu could still not find the SSID through the network manager. My SSID broadcast is on. What do I do in order to fix this?

Edit : I forgot to add that all my other devices are able to find the network so my router is definitely not the problem (I guess?)

---

### Post by Naderino on 2011-05-31
Oh and by device I mean machines 
I.e iPod touch, windows PC, etc

My wireless adapter is IEEE 802.11bgn

---

### Post by Joe of loath on 2011-05-31
IEEE 802.11bgn is just the class of wifi adaptor. Is it USB or PCI?

---

### Post by Joe of loath on 2011-05-31
IEEE 802.11bgn is just the class of wifi adaptor. Is it USB or PCI?

---

### Post by Joe of loath on 2011-05-31
IEEE 802.11bgn is just the class of wifi adaptor. Is it USB or PCI?

---

### Post by Naderino on 2011-05-31
It's usb

---

### Post by Joe of loath on 2011-05-31
Then can you post the output of lsusb please?

---

### Post by Naderino on 2011-06-01
> **Joe of loath said:**
> Then can you post the output of lsusb please?

Here it is :

> naderino@Naderino-desktop:~$ lsusb
Bus 001 Device 013: ID 050d:805c Belkin Components 
Bus 001 Device 008: ID 03f0:5c11 Hewlett-Packard PhotoSmart C4200 Printer series
Bus 001 Device 007: ID 1019:0c55 Elitegroup Computer Systems (ECS) Flash Reader, Desknote UCR-61S2B
Bus 001 Device 006: ID 046d:08da Logitech, Inc. QuickCam Messanger
Bus 001 Device 005: ID 067b:2507 Prolific Technology, Inc. PL2507 Hi-speed USB to IDE bridge controller
Bus 001 Device 002: ID 17d0:0115 Sanford L.P. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
naderino@Naderino-desktop:~$ 

---

### Post by Naderino on 2011-06-02
It's been like this for a while and I really wanna use my Internet on ubuntu. Can anyone help? If anyone had the same problem and solved it it would be great to let me in on what to do...

---

### Post by Naderino on 2011-06-13
Seems like my problem was solved! :p I realized that after updating, grub bootloader was showing me two different 9.10 installations (each of them had their own recovery mode, but the same settings). I realized that I never even booted the second one, so I gave it a shot and guess what? My wireless network was found and it successfully connected :D

Maybe this is an update bug, but I figured that it wasn't my wireless network because of the fact that it wasn't the only problem. For example, I couldn't play media files because their "suitable plugins were not found" well now that I booted with the second option, all plays well!

Thanks again everyone who tried to help, but were unable to. I really appreciate taking your time to read this!

---

### Post by Joe of loath on 2011-06-14
You might want to update again, 9.10 is unsupported too. 10.04 is an LTS version, so you'll get another two years of support if you upgrade now.

---

