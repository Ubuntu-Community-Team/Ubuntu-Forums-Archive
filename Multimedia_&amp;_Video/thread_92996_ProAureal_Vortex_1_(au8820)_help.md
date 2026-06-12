---
title: "Pro
	

Aureal Vortex 1 (au8820) help"
date: 2005-11-21
forum: Multimedia &amp; Video
---

### Post by jtrickey on 2005-11-21
Hi there,

Read through what I could find, including the "Sound Troubleshooting Checklist", before posting here. 

My issue is this - I installed 5.10 on a Dell Optiplex GX1 desktop yesterday - so far so good.  However, I can't get my sound hardware (which, from the [HardwareSupportMachinesDesktops]("https://wiki.ubuntu.com/HardwareSupportMachinesDesktops?highlight=%28au8820%29") list, indicates that it's an Aureal Vortex 1 (8820)) to be recognized.  This very much surprised me, as I receintly installed 5.10 on my 3 month old Dell Latitude D810 and it detected all of the hardware without incident, but I digress.

As far as my Linux skill level goes...  I'm a complete novice.  I've had tons of PC (OK, Windows) experience, and have already done the obvious steps (made sure the sound hardware was turned on within BIOS, ran the Dell diagnostic disk to test the sound hardware, etc. 

FYI - the sound hardware does not show up when I run "lspci" within a terminal window.  If it helps, here is the output from lspci:


-------------------------------------

jerry@machine:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:07.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:0d.0 Communication controller: Conexant HCF 56k Data/Fax Modem (rev 08)
0000:00:0e.0 Multimedia controller: Pinnacle Systems Inc.: Unknown device bede
0000:00:0e.1 FireWire (IEEE 1394): Pinnacle Systems Inc.: Unknown device 0015
0000:00:11.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 24)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c)

-------------------------------------

If you would spell out exactly what needs to be done, I would sincerely appreciate the help.  I say spell out, because I honestly don't know whether I need to download a driver and install (compile as part of the kernel?), add a command line parameter to have the hardware correctly detected on boot, ???

TIA,

Jerry

---

### Post by jtrickey on 2005-11-21
PS - if it helps to motivate anybody to give me a hand  :D  my plan is to build two more of these machines and donate to a local non-profit organization.

Thanks!

---

### Post by jtrickey on 2005-11-23
Or, I could buy someone a beer next time they're around Bakersfield, CA?  :)

---

### Post by Ciberblade on 2005-11-26
Hello jtrickey ~ I've loaded Ubuntu for the first time on the old Optiplex myself and had the exact same problem.  In my case, when I would enter the command "sudo modprobe snd-cs4236" followed by a log-out then log back in, my sound would work.

If that works for you, then all you have to do is add the "snd-cs4236" line to your /etc/modules file. :cool: 

Ciber~

---

