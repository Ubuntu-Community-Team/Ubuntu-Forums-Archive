---
title: "How to Connect to Network on Vista Host Machine?"
date: 2009-07-31
forum: Networking &amp; Wireless
---

### Post by sdbpastor on 2009-07-31
I just installed the latest version of VirtualBox by Sun Microsystems on my Vista Ultimate PC. I then created a virtual machine to run Windows 2000, mainly to synchronize my old HP PDA because Vista will not work with it.The Windows 2000 virtual machine works great for this purpose. I also set the Windows 2000 virtual machine to recognize and be recognized by Vista's shared drives and my network storage drive in order to share files between Vista and Windows 2000. It also sees my wireless notebook's shared drives\folders.

I just created another virtual machine to run Ubuntu and then installed the latest version of Ubuntu desktop. I want to set up Ubuntu to be able to see my shared drives on Vista and if possible to have Vista see the drives on the Ubuntu virtual machne. 

Since I am new to Linux and Ubuntu can someone talk me through the setup on Ubuntu, and\or Vista as well as the settings in VirtualBox if anyone has done this successfully. 

Info you may need to know: Latest version of VirtualBox running a Ubuntu virtual machine with the latest version of Ubuntu desktop. Host machine is Vista Ultimate. Workgroup on the host machine in Home_Office. The host system (Vista) connects to other computers on the network through a wireless router but is connected by cat5 cable whereas the notebook uses the wireless.

Any help would be greatly appreciated.

Thanks,
Rev. Michael L. Burns
[EMAIL="sdbpastor@charter.net"]sdbpastor@charter.net[/EMAIL]

---

### Post by dmizer on 2009-08-01
So, Places > Connect to server doesn't work?

---

### Post by sdbpastor on 2009-08-01
The network does not use a server so I don't know how to setup Places > Connect to server.

Michael

P.S. A stupid question, how do I check whether Samba is installed and/or install it if needed to connect to the network?

---

### Post by dmizer on 2009-08-01
> **sdbpastor said:**
> The network does not use a server so I don't know how to setup Places > Connect to server.

Michael

P.S. A stupid question, how do I check whether Samba is installed and/or install it if needed to connect to the network?

Any computer sharing a resource to other networked computers is a server. If you have files shared by a Windows computer via Windows networking, then your Windows computer is acting as a server. So, yes ... Places > Connect to server should work perfectly fine for you.

As soon as you click on Places > Connect to server, you will be prompted to install the necessary tools to connect to your Windows share.

---

### Post by sdbpastor on 2009-08-01
When I click on Places > Connect to Server I am not prompted to install any tools to connect to my Windows share, just a dialog box to  connect to the server. I select the server type as Windows Share but don't know what to put in the box for **Server:**, etc.

Michael

---

### Post by dmizer on 2009-08-03
> **sdbpastor said:**
> When I click on Places > Connect to Server I am not prompted to install any tools to connect to my Windows share, just a dialog box to  connect to the server. I select the server type as Windows Share but don't know what to put in the box for **Server:**, etc.

Michael

Next to "Server" simply enter the IP address of the Windows computer. Any other information you can enter will probably help things along.

---

### Post by sdbpastor on 2009-08-04
I know this sounds stipid, but how do I find the IP address on the Windows maxgune?
 
Muchael

---

### Post by latev on 2009-08-04
on the windows machine:
type
ipconfig /all
in cmd.exe

on the Lin machine:

type 
arp
in console and see what happens

---

