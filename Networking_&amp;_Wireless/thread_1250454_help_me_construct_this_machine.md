---
title: "help me construct this machine"
date: 2009-08-26
forum: Networking &amp; Wireless
---

### Post by drvista on 2009-08-26
I am having a private network with 10 computers all runing windows XP and my personal laptop is ubuntu jaunty and i am having an old machine with P4 cpu at 1.51 GHZ and 512 SDRAM and ATI GPU 64MB 
this machine is ubuntu capable i installed it but i want a basic ubuntu install that can do the following 
0. Conect the ADSL modem router to a eth0 and connect the switch to eth1 
1. Connect the network computers to the switch 
2. The machine should act as 
         [INDENT]a. DHCP server
         b. Print server
         c. Torrent client
         d. bandwidth allocator for XP users
         e. FTP server
         f. SMB sever 
         g. DNS server[/INDENT]
3. I need firefox installed and a way to add torrents by the internet so if i am out i can add torrents 
4. i need to have gnome desktop or xfce installed 

so plz what to do ??? i am not geek but i can do basic linux stuff like config and install and compile so please help me 
thank you

---

### Post by Iowan on 2009-08-26
Most of the packages you seek are available via Synaptic. For DHCP and DNS, I'm still planning to try **dnsmasq**, which ties the two together, and is supposed to be simple to set up. Samba, FTP (or SSH) are available. There are  How-To's on the forum and at [https://help.ubuntu.com]("https://help.ubuntu.com") - for example, [ICS]("https://help.ubuntu.com/community/Internet/ConnectionSharing").

---

### Post by drvista on 2009-08-30
Thank You I will try that

---

### Post by paulisdead on 2009-08-30
Transmission has a web client you can enable and access through a browser.  It runs on port 9091, by default, so you can forward that through your router to the machine, so you can add torrents from across the internet.  Just be sure to set a password on it.  I've even got an app on my phone called transdroid that lets me add torrents and control transmission from my android phone.  I did have to run the latest version of transmission in the PPAs in order to make that work.

I've had issues with reverse lookups when using dnsmasq.  It might not be a problem for you, though, and is much simpler than setting up bind.

---

### Post by w00ly on 2009-08-30
wine + utorrent + webui works great for me. I never liked the way transmission organizes it's torrents...utorrent is simple, light and effective

---

### Post by drvista on 2009-08-31
Thank you guys for help i will try out for test now and will post results here

---

### Post by cascade9 on 2009-08-31
I would try deluge over utorrent with wine. Sure, utorrent is nice, but deluge should do everything that utorrent does and its linux native.

---

