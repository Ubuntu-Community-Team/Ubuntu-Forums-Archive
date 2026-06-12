---
title: "GRUB 2 Error at boot"
date: 2009-02-02
forum: Mythbuntu
---

### Post by Emp123 on 2009-02-02
Hey, so I recently installed Mythbuntu 8.10 which is my first time running Linux so please forgive my complete lack of knowledge. 

I started by using RAID 0 for my two 400gb hard drives and Mythbuntu installed just fine, but after I restarted I get the following message:

AMD Data CHange...Update New Data to DMI!
GRUB Loading Stage1.5.

GRUB loading, please wait...
Error 2

The bios doesnt recognize the hard drives when theyre in RAID mode, but the RAID software does. I dont know if this is normal or not as this is also my first time using RAID drives.

What does that message mean and how do I fix it? 

Heres a list of my system specs:
Mobo: Biostar A770 A2+
CPU: AMD X2 4850e
Memory: Kingston 512 DDR2 800
Hard Drives: 2 Seagate 400gb SATA drives
GPU: ATi Radeon 800xl
Tuner Card: Im thinking about going with the Hauppauge 1800 but as of right now Im not sure.

---

### Post by Emp123 on 2009-02-04
Update:

So I decided to reinstall Mythbuntu on a 30 gig IDE drive and now it will boot up and work normally, but it does not detect the hard drives in the RAID, or maybe it does and I just dont know how to see them. What are my options here?

---

### Post by Emp123 on 2009-02-05
No suggestions on how to get Mythbuntu to recognize the hard drives in the raid? Do I have to install Mythbuntu differently because Im using multiple hard drives?

---

### Post by lightsaber on 2009-04-20
When doing the install, on the final confirmation screen, click on the advanced options button.  If your drives are identified as sd*, then make sure it's not referenceing hd() or something like that.  I changed mine to /dev/sda and it booted right up.

---

### Post by ReddogOne on 2009-04-22
I had the same error. It was on a Dell so as the machine booted up I pressed Ctrl-I and turned the RAID stuff off and then all was fine. If you not got a Dell then I guess you'll have something similar.

Seems something like the install sees the drives as separate but grub sees them as a RAID. As turning the RAID controller OFF fixed the problem I lost interest in finding out any more details.

My second drive shows up as a media disk to happy with that.

---

