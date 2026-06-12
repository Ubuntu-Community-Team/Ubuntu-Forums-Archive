---
title: "How to Connect to Shared Folders in Ubuntu from Windows 7?"
date: 2010-01-30
forum: Networking &amp; Wireless
---

### Post by efrenefren on 2010-01-30
I have just upgraded from Windows XP to Windows 7 and I just couldn't figure out how to connect to a shared folder in Ubuntu. It was pretty easy to do in Windows XP.

Can anyone help me on this?

---

### Post by johnson.d on 2010-02-08
If you want to use the IP address or the Hostname of the Ubuntu PC

1) Press windows Key + R, It shows Run window (Similar to windows XP), 
In the box type

\\<Ip-address>\<Share name> or \\<Hostname>\<Share name>

If you want to browse through the network

1) Start Menu -> Computer

After the window opens, Click on Network. It shows all the network computers connected to your PC. You can now browse through the network

---

### Post by efrenefren on 2010-02-08
> **johnson.d said:**
> If you want to use the IP address or the Hostname of the Ubuntu PC

1) Press windows Key + R, It shows Run window (Similar to windows XP), 
In the box type

\\<Ip-address>\<Share name> or \\<Hostname>\<Share name>

If you want to browse through the network

1) Start Menu -> Computer

After the window opens, Click on Network. It shows all the network computers connected to your PC. You can now browse through the network

I tried doing Start Menu -> Computer -> Network but it doesnt show the Ubuntu Share. I just dont why it doesnt show the Ubuntu Share. I havent tried \\<Ip-address>\<Share name> or \\<Hostname>\<Share name> yet but i've already switched back to windows XP.

Thanks anyway. :)

---

### Post by karmic-koala on 2010-02-08
One way to resolve this is to run a ftp server on your ubuntu machine and then use ssh to connect to it from windows machine.

---

