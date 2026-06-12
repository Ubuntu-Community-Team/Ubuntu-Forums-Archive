---
title: "New to ubuntu and unsure of setting up home network"
date: 2010-11-03
forum: Networking &amp; Wireless
---

### Post by nicho J on 2010-11-03
Hello, 

I am new to Ubuntu, just downloaded it to my laptop as a trial last weekend and have decided that it fantastic and will be setting it up on my main home PC soon.

Currently I have the laptop networked through the Windows network and have managed to connect to the network printer. Not exactly sure how I managed it, bit of trial and error.

Once I update my main PC I will obviously lose the windows network. Please can someone let me know if there is a simple way to set up an Ubuntu network so I can share files between laptop and desktop PC and use the desktops printer when printing from the laptop.

I have never used scripts or programming in the command prompt so would like to be able to do this through an application. If anyone has any suggestions they would be welcomed.

Many thanks

Nicho

---

### Post by sikander3786 on 2010-11-03
You don't need anything really fancy to achieve it. No scripts/programming is necessary, not needed at all.

If you just want to access files from Windows machines, under Places menu, Connect to Server is sufficient to do the task.

If you want to share files from Ubuntu Laptop to the Windows machines, you'll need Samba Server. (it also has the ability to share printers)

[https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

Simple instruction for printing from Ubuntu to Windows,

> Printing to Windows XP printer from Ubuntu
Enable &#8220;Print Services for Unix&#8221; on Windows XP machine and share printer. (I&#8217;m not actually sure that this is necessary, it might be a red herring&#8230;)
When you add the printer in Ubuntu,
1. Choose &#8220;Network Printer&#8221; and &#8220;Windows Printer (SMB)&#8221;
2. put your Workgroup in the Host field
3. Put &#8220;guest@<host>/<printer>&#8221; in the Printer field (replacing <host> and <printer> with your host & printer names)
So, for example, if your Windows machine was called &#8220;Dozer&#8221; and your printer was called &#8220;LaserPrinter&#8221;, you would put &#8220;guest@Dozer/LaserPrinter&#8221;.
You should not need a name and password for the Windows machine for this to work.

Any further queries are welcome :-)

---

### Post by Iowan on 2010-11-03
> **nicho J said:**
> I have never used scripts or programming in the command prompt so would like to be able to do this through an application. Although many apps have a GUI for configuration, you'll eventually want too get familiar with the command line and configuration files. You'll discover that it's usually quicker/easier to edit a file (after making a backup)... :)

---

### Post by nicho J on 2010-11-04
THank you for the advice. Can I assume then that when I get my new desktop PC running Ubuntu that will need to have Sambe running to link the 2 Ubuntu computers together.

Also thanks for the comment about command lines. I am eager to start to get to know about this but really don't know where to start.

---

### Post by Boondoklife on 2010-11-04
yea samba is one of a few, but it works with windows too!

---

### Post by pricetech on 2010-11-04
> **nicho J said:**
> Can I assume then that when I get my new desktop PC running Ubuntu that will need to have Sambe running to link the 2 Ubuntu computers together.

You won't need Samba to connect the two Ubuntu boxen to one another, but you'll probably want to include it anyway if you think there's a possibility you'll want to share with windows boxen.

---

### Post by sikander3786 on 2010-11-05
For Sharing between 2 or more Ubuntu PCs, there are many options. NFS, personal file sharing, Samba. NFS also works with Windows. Just read that but never tried it actually. Some experienced mate might enlighten that more specifically.

I have always used Samba for file sharing as most of my Networks run a mix of Windows. NFS is an option but never had the time and courage to try that.

So my advice, Samba!

---

### Post by nicho J on 2010-11-12
Thanks to all replies. I now have my new desktop networking on Ubuntu with my laptop.

---

