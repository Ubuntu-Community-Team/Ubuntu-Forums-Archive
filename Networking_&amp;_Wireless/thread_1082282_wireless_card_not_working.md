---
title: "wireless card not working"
date: 2009-02-27
forum: Networking &amp; Wireless
---

### Post by chronicsmoke2k on 2009-02-27
Hi i just got done installing ubuntu.  windows sucks and i want something new.  the problem i have is i can not get ubunbtu to install my wireless card i have a Linkys pci card model wmp110 I know the card works i tested it out on another computer using win xp.  I have the disk but ubuntu dose not want to read it is there another way i can install this card so i can use the internet ??

---

### Post by Kevbert on 2009-02-27
Welcome to Ubuntu.
What you need to do is find out what chipset the wireless card uses. To do this go to Applications-Accessories-Terminal and type
```
lspci
```
to list all pci devices. Select all text with the mouse and then press Ctrl-Shift-C to copy it, open a new post and press Ctrl-V to paste it here.
It may be necessary to use the Windows XP drivers. Do you have a driver disk with the .sys and .inf files as these may not be available as open source drivers ?

---

### Post by chronicsmoke2k on 2009-02-27
er #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
03:00.0 Network controller: Atheros Communications Inc. AR5416 802.11abgn Wireless PCI Adapter (rev 01)
03:01.0 Mass storage controller: Integrated Technology Express, Inc. IT/ITE8212 Dual channel ATA RAID controller (rev 13)
ubuntu@josh-desktop:~$

---

### Post by Kevbert on 2009-02-28
Please take a look at [[COLOR="Red"]this[/COLOR]]("http://probing.wikidot.com/ubuntu-intrepid-8-10-replacing-ath9k-by-madwifi"). Unfortunately you have the infamous Atheros chipset and so need to use madwifi drivers. Run steps 1 to 3. With a few commands you need to use 'sudo' to give privileges to the commands such as
```
nano /etc/modprobe.d/blacklist
sudo apt-get install linux-headers-generic
```
Good luck.

---

### Post by AvengerX9 on 2009-02-28
when trying to blaclist them I get "error writing. Permission denied" :confused:

---

### Post by Kevbert on 2009-02-28
> **AvengerX9 said:**
> when trying to blaclist them I get "error writing. Permission denied" :confused:

You need to use 'sudo' to open the file. This will allow you to write to the file.

---

### Post by chronicsmoke2k on 2009-02-28
no this did not work is there A way i can  i put the driver in my self?   :confused:

---

### Post by chronicsmoke2k on 2009-02-28
i did the commands and theen went to adamin the windows wireless drivers and it worked

---

### Post by ScarySquirrel on 2009-03-01
Good job, Kevbert.

---

### Post by ScottyP431 on 2009-03-01
> **Kevbert said:**
> Please take a look at [[COLOR="Red"]this[/COLOR]]("http://probing.wikidot.com/ubuntu-intrepid-8-10-replacing-ath9k-by-madwifi"). Unfortunately you have the infamous Atheros chipset and so need to use madwifi drivers. Run steps 1 to 3. With a few commands you need to use 'sudo' to give privileges to the commands such as
```
nano /etc/modprobe.d/blacklist
sudo apt-get install linux-headers-generic
```
Good luck.


Edit- got it working

---

