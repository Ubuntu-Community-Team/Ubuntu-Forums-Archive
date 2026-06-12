---
title: "Question regarding shared NTFS drives on Ubuntu"
date: 2009-10-12
forum: Networking &amp; Wireless
---

### Post by boogyman19946 on 2009-10-12
First post on the forums ^_^ woot!

Ok, here's the scenario. We have a private network in our set up at home. Using IP Masquerading, I made my dad's computer the gateway to the internet for the rest of the computers in the house. He is running good ol' Windows XP because he's so used to it and knows where 'most everything is. I on the other hand like to spice up my experience once in a while so I decided to run Ubuntu. Here's where the question part comes in. Before I switched to Ubuntu, I was running Windows XP and I was the gateway in the house. Since my dad's motherboard has no SATA ports for his 300 GB hard drive, I have it plugged into my computer and shared the drive over the network so that he can access it. I'm currently on my XP because I'm not sure if I switch to Linux that he will be able to read/write to it over the network with little to no problem. How would his computer access the hard drive over the network? Is it going to be his Windows XP that reads and writes to the drive or is his windows simply going to make Ubuntu do the reading and writing? 

My assumption is that Ubuntu will simply make the hard drive visible "as is", meaning that Windows XP would use it's own drivers to manipulate the data on the drive. However, I came to another conclusion that Windows only sends Ubuntu requests for files and Ubuntu does the work as requested.

If it helps, here's how my network is set up:

ISP > Modem > Windows XP (my dad's computer)  >>[IP Masquerade]>> Ubuntu (my computer)

Thanks for all answers in advance :]

---

### Post by prshah on 2009-10-12
> **boogyman19946 said:**
> I'm not sure if I switch to Linux that he will be able to read/write to it over the network

How would his computer access the hard drive over the network? Is it going to be his Windows XP that reads and writes to the drive or is his windows simply going to make Ubuntu do the reading and writing?

Ubuntu will be doing all the hard disk access directly. It will NOT expose the hard disk drive to XP for direct, driver-based manipulation across the network.

You will need to setup Ubuntu as a Samba server (Linux equivalent of Windows file sharing SMB).

There are a number of easy to use guides; you can start with the [community documentation]("https://help.ubuntu.com/community/SettingUpSamba").

Once you have samba setup in Ubuntu, Windows can access specific shares ("directories") for both read/write access. However, it cannot perform low level operation such as a HDD check, etc. All file access will be transparent to Windows programs (especially if you have mapped a drive in XP).

Best of luck, and post back if you run into problems.

---

