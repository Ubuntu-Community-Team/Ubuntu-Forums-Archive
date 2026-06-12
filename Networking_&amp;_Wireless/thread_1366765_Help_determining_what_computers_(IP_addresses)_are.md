---
title: "Help determining what computers (IP addresses) are on my network"
date: 2009-12-28
forum: Networking &amp; Wireless
---

### Post by Volume on 2009-12-28
Hello All,

Can someone tell me how I can go about determining which IP addresses are currently connected to my network?  I have 3 PCs (2 windows, one linux), all connected to a netgear router.  

Ultimately, I want to share files between all 3 computers.  

Thanks

EDIT: Also, what is responsible for assigning these addresses?

---

### Post by lisati on 2009-12-28
If you have samba installed on your Ubuntu machine, you can find out which machines samba knows about with the findsmb command.
Some routers have a page for showing attached devices on their web-based control panel.

---

### Post by Volume on 2009-12-28
Great, thanks for your prompt reply.  This then brings me to my next question of course :P.  How do I add my other two machines to the network?

I believe that the one IP address, Samba "sees" is my Linux box--is there any way to confirm this?

Thanks again

---

### Post by DGortze380 on 2009-12-28
In a typical home setup, your router utilizes DHCP to assign IP addresses.

Samba will allow you to access machine by their hostname instead of their address, this can be handy. You could also assign static addresses instead of using DHCP. Or assign static DHCP Leases (if your router supports it).

nmap is a network scanning tool that will find which ip addresses have hosts that are up.

---

### Post by Volume on 2009-12-29
> **lisati said:**
> If you have samba installed on your Ubuntu machine, you can find out which machines samba knows about with the findsmb command.
Some routers have a page for showing attached devices on their web-based control panel.

Ok, my Netgear router allowed me to see which IP addresses that the router sees, and all 3 of my computers are listed.  However, when I try to use "gksudo shares-admin" I get the error message```
mokrunka@Engineer-Linux:/$ gksudo shares-admin
(shares-admin:6515): Gtk-WARNING **: Unknown property: GtkComboBox.items

** (shares-admin:6515): CRITICAL **: Unable to lookup session information for process '6515'

(shares-admin:6515): Gtk-CRITICAL **: gtk_entry_set_text: assertion `text != NULL' failed
mokrunka@Engineer-Linux:/$ findsmb

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION
---------------------------------------------------------------------
10.0.0.2        ENGINEER-LINUX [WORKGROUP] [Unix] [Samba 3.3.2]
```


It seems that SAMBA is not working... I tried to install samba and smbclient, but I cannot get to the SAMBA item in the menu (SYSTEM>ADMIN>SAMBA) or to the "shared folders" item.  

I would very much appreciate any suggestions you may have..

By the way, when I run > samba -h which is an invalid option, it says that samba is not currently installed.  What gives?

Thank you!

---

### Post by Volume on 2009-12-29
Ok. I have now managed to get Samba working.  I am able to access files in both directions (linux to windows or vice-versa).

My next question is how can I change the permissions for the folders I am able to access.  Right now, I have access to the default "Public" folders on Vista through linux, and access to /home/mokrunka/Windows (my linux shared folder), but I am not able to edit files in these locations from the other computer.  In other words, if I create a simple text file in my windows shared ("Public") folder, I am not able to edit it in Linux.  

How can I change these permissions?

Thank you!

---

