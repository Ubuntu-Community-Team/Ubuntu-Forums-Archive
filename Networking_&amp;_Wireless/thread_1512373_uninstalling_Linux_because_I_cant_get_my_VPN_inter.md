---
title: "uninstalling Linux because I cant get my VPN internet connection to work :("
date: 2010-06-18
forum: Networking &amp; Wireless
---

### Post by Furki316 on 2010-06-18
Here's how I normally setup an internet connection in Windows XP or any other windows.
Connect the ethernet cable.
Setup a new internet connection.
 Connect using VPN.
Internet address(destination host address): green.connect.net.sa
Username: Furki
Password: *****

Properties> Security > Type of VPN: PPTP
Encryption: no encryption allowed.


I cant get this to happen in Ubuntu. I've downloaded many packages like pptpconfig, pptp-linux etc, they either dont work or simply do nothing.

Can anyone please help me in setting up my internet connection? This is the only thing that is keeping me from using Linux. 


Thank you for reading my post.

Regards,
Furki

---

### Post by wilee-nilee on 2010-06-18
I can't help with the vpn issue, but if you are actually dual booting which means grub is the bootloader don't remove Ubuntu until you restore the MS bootloader.

---

### Post by velle frak on 2010-06-18
Maybe this will help:

[https://help.ubuntu.com/community/SSH_VPN](https://help.ubuntu.com/community/SSH_VPN)

.

---

### Post by Joe of loath on 2010-06-18
Does the VPN configuration in network-manager not work for you?

---

### Post by Furki316 on 2010-06-18
Thank you for your replies. I'm kind of a newbie and I dont wanna let Linux go just yet. VPN configuration settings are not showing up in the Network manager. I installed pptp-linux but still there is no change in the Network manager.

I also tried to install pptpconfig (GUI) but it says that Dependency is not satisfiable.

---

### Post by Joe of loath on 2010-06-18
What do you mean? If you click the network manager icon in the notification area, then VPN connections, then Configure VPN, then add, and then it should prompt you for everything else.

---

### Post by cb951303 on 2010-06-18
network-manager-pptp comes preinstalled and you should be able to configure pptp vpn out of the box with network manager.

---

### Post by Furki316 on 2010-06-18
I'm sorry I should've been clearer. When I click on the network manager icon on the botton right corner, there is NO "VPN connections" to click on. I only see "Manual configuration" and "Wired Network".

---

### Post by Joe of loath on 2010-06-18
Are you using kubuntu/KDE, or have you put the Gnome menu at the bottom? If you're using kubuntu, ignore what I said. I don't know how to work KDE though...

---

### Post by doas777 on 2010-06-18
> **Furki316 said:**
> I'm sorry I should've been clearer. When I click on the network manager icon on the botton right corner, there is NO "VPN connections" to click on. I only see "Manual configuration" and "Wired Network".
if your in gnome, try right clicking the NM icon in your tray, and select "Edit Connections".
a window should pop up, with several tabs, including "VPN". click "Add" and set the connection details. 
after the connection details are set, you should be able to connect by Leftclicking NM and selecting your vpn connection from the list.

---

### Post by Furki316 on 2010-06-18
I'm using GNOME. Right-clicking on the NM icon shows 
Enable Networking
Connection Info
Edit Wireless networks
but NO "Edit Connections".

---

### Post by Joe of loath on 2010-06-18
Which version are you running? I just realised I'm going through the steps for lucid, which are probably different.

---

### Post by Furki316 on 2010-06-18
I'm using Ubuntu 8.04.1 Hardy Heron.

---

