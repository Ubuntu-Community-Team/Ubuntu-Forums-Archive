---
title: "Nautilus &amp; Samba &amp; Networked USB harddrive on router"
date: 2009-02-20
forum: Networking &amp; Wireless
---

### Post by -::Bas::- on 2009-02-20
First let me explain the situation.

I have a (wireless) router with a usb harddrive connected to it. The router (asus wl500w) uses the Samba protocol to share the folders on the drive.

Here's the problem:
Browsing the network works perfectly fine on Windows XP and it worked perfectly on Intrepid and Hardy until a few days ago. When clicking 'Places' -> 'Network' -> 'Windows network' -> 'Workgroup' it used to show the wireless router, and I could browse the folders.

For the past few days (Hardy and Intrepid) after going through the same routine ('Places' -> 'Network' -> 'Windows network' -> 'Workgroup') I get this error message: *Unable to mount location. Failed to retrieve share list from server.*

The odd thing is, that when I take the following route: 'Places' -> 'Connect to server' and providing the ip-address of my router, domain name, share name, folder name and my login, then I can browse the drive if nothing is wrong. 

I haven't changed anything in the router/harddrive, it's still usable through ftp and Win XP. Have rebooted the router several times to no avail. Is there some update of samba or nautilus (in Hardy as well as Intrepid), that breaks it? I did notice a new kernel this Hardy and Intrepid (didn't boot the Hardy laptop for a while), could that cause the problem?

Does anyone recognise this probleme, or even better, knows a solution?

---

### Post by superprash2003 on 2009-02-20
its a nautilus bug!!

---

### Post by -::Bas::- on 2009-02-21
Could you point me to your source?

---

### Post by superprash2003 on 2009-02-21
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/241139](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/241139)

---

### Post by -::Bas::- on 2009-02-25
That doesn't seem to be my problem, but I now use a workaround: i made a bookmark with the 'connect to server' button. Works for me.

---

