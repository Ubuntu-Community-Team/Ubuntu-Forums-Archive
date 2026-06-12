---
title: "Samba Problems with NAS"
date: 2009-01-03
forum: Networking &amp; Wireless
---

### Post by bigfoot780 on 2009-01-03
Hi I've recently installed Ubuntu onto a laptop and I'm fairly new to it. I'm getting used to apt, terminal, commands etc.

I'm having a problem with a NAS on my network it shares its drives using samba and I've had no problems accessing it from Windows XP. 

I want to access it using Ubuntu 8.10 when i enter smb://<nas name>/ the drive contents appear (the drive is using FAT 32), a few directories but when I try and open one nautilus takes me back to my home directory. Has anybody had anything similar and been able to rectify it.

---

### Post by Iowan on 2009-01-04
Not an adequate solution, but see if it works:
> **superprash2003 said:**
> try typing smb://x.x.x.x where x.x.x.x is the ip of the windows machine.. it hopefully should open the shared folders.. [http://prash-babu.blogspot.com/2008/09/how-to-access-windows-shared-folders-in.html](http://prash-babu.blogspot.com/2008/09/how-to-access-windows-shared-folders-in.html)

---

### Post by brainerd on 2009-02-17
I have the exact same problem with my Eagle NAS on Ubuntu 8.10.  Typing //192.168.1.250 does not help.  I am able to connect to the ftp server, but I can't load a file from the NAS in my non-Ubuntu aps.  I have my Thunderbird mail folders on the NAS and would like to direct Thunderbird in Linux to it, but it doesn't see the NAS even after I mount the ftp.

---

### Post by Hamster1910 on 2009-03-04
Having same problems with Landisk NAS device and Ubuntu 8.10 which is  driving me to distraction.... :-s

I have a dual-booting WinXP/Ubuntu machine which was accessing multiple shares on the NAS with Hardy without any problems (using Nautilus).

Since I 'upgraded' to Intrepid I cannot connect to the shares via smb with "Mount error 5 - input/output error" being the most consistent result.

I have tried SMB4k, various command line methods and sticking mounts in fstab but all with no joy.
I also note that if I put //IPaddress/share into Nautilus I am presented with my home directory. 
I also sometimes see the share icon pop up on the desktop briefly before disappearing again.

I can use FTP to access the NAS and the same machine also connects to the shares when OK booted into WinXP.

I have a second PC which dual boots Win/XP and Hardy and this still connects to the NAS in either OS and I even have an eeePC which connects to the shares reliably too!

Anyone got any ideas (apart from the obvious one of reverting to Hardy)?
I'm about to try Samba 2.3.2.3-1ubuntu3.5 if I can work out how to get hold of it.

---

### Post by Hamster1910 on 2009-03-04
\\:D/  FIXED IT!!!!

samba 3:2.3.2-1ubuntu3.5 is the answer.

Here's how it goes...

[INDENT]1. Close synaptic if you have it open

2. Go to System: Administration: Software Sources

3. Select updates tab

4. Check 3rd and 4th check boxes (intrepid-proposed & intrepid-backports) if they are not already checked.

5. Close software sources dialogue and click 'Reload' in dialogue that pops up to include the new sources in Synaptic.

6. Open synaptic (Go to System: Administration: Synaptic Package manager)
7. Type 'Samba' in the quick search box and press enter

8. Find 'Samba-common', 'smbclient' & 'libsmbclient' in the list of results. They should all be marked with a green box and a star to a show they are installed but a newer version is available. The newer version should be marked 3:3.2.3-1ubuntu3.5.

9. Select these packages for installation, accepting any dependencies and then apply the changes.

10. When they are installed, close synaptic and go back to the software sources and remove the intrepid-proposed & intrepid-backports sources to prevent the system inadvertently applying unapproved updates.[/INDENT]

Hopefully you can now use Nautilus to connect to your smb share. (Places: Connect to server)
Enjoy!

---

