---
title: "[Question]: Universal Graphics Driver?"
date: 2007-10-19
forum: Multimedia &amp; Video
---

### Post by Dethis on 2007-10-19
Is there such thing?

I have and Intel graphics chip and I can't find a driver for linux.

or Can I get a Windows version driver and install with COO (crossover office)?

---

### Post by carlinuxlearner on 2007-10-19
"or Can I get a Windows version driver and install with COO (crossover office)?" No this is not possible. And there is no "Universal Graphics Driver" but if you will post the output of "lspci" then we can help you find your driver.

C@RL

---

### Post by Dethis on 2007-10-19
> **carlinuxlearner said:**
> "or Can I get a Windows version driver and install with COO (crossover office)?" No this is not possible. And there is no "Universal Graphics Driver" but if you will post the output of "lspci" then we can help you find your driver.

C@RL

Edit:

Is this what you mean?

> 00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
05:01.0 Communication controller: Conexant HSF 56k Data/Fax Modem
05:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)
05:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 03)


---

### Post by carlinuxlearner on 2007-10-19
Yes that's what I meant. And you should now exicute this "sudo dpkg-reconfigure xserver-xorg" I f you need help answering all the questions just post them here.

C@RL

---

### Post by Dethis on 2007-10-19
thx dude, ill try this

---

### Post by Dethis on 2007-10-19
ok, i went through that thing and at the end it said this in term.

> xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20071019214153


---

### Post by carlinuxlearner on 2007-10-19
That's fine, it was just telling you that it edited the file (which is a good thing), and it told you the name of the backup of the original.

C@RL

---

### Post by carlinuxlearner on 2007-10-19
Oh and I'm assuming that you told it to use the i810 driver, right? If not do it all again, and tell it to.

C@RL

---

### Post by Dethis on 2007-10-19
why i810 if i have..

> 0:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
ok, i picked i810 instead of Intel this time

---

### Post by carlinuxlearner on 2007-10-19
the i810 is an intel driver.

C@RL

---

