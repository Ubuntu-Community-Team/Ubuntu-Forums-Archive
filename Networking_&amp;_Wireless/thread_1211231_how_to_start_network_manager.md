---
title: "how to start network manager"
date: 2009-07-12
forum: Networking &amp; Wireless
---

### Post by raymondvillain on 2009-07-12
Jaunty 64 bit, D-Link DWA-556 wirless N adapter pci express.

I'm tweaking the network settings by right-clicking on the wireless network icon on the taskbar.  Is that the only way?

I know I have network manager installed, but there is no "launcher" under System>preferences, System>administration, or applications.

Is network manager something the system uses when I click on System>Preferences>network connections ?

If not, how does one start up network manager?

---

### Post by superprash2003 on 2009-07-12
network connections is the new network manager :)

---

### Post by raymondvillain on 2009-07-12
Thank you supersprash2003.

I have an Ubuntu box (Jaunty 64 bit) and 2 windows boxes.  Ubuntu can access the internet and with Nautilus I can see the shared files on the Ubuntu machine, but not the windows machines.

The windows machines can see each other (and access the internet) but not the Ubuntu machine.

I'm using Samba.  In /etc/samba/smb.conf, I have set:

security = share

#Myshare here
[Myshare]
    comment = Myshare
    path = /myshare
    read only = no
    guest ok = yes

   workgroup = correct_workgroup_name
   netbios name = correct_name_for_this_computer

and I've created a share directory, /myshare, with permissions 0777.

And I've modified /etc/nsswitch.conf to include wins support (hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4).

Everything used to work fine.  Then a couple of days ago I replaced my router with a "dual band N router" and I installed an "N" wireless adapter in the Ubuntu machine.

I wasn't expecting those alterations to have disrupted the network.

Does anyone have any suggestions?

---

### Post by superprash2003 on 2009-07-13
have you tried accessing via ip? like smb://x.x.x.x ?

---

### Post by raymondvillain on 2009-07-13
I am giving up.

It is not worth all this time and trouble to have wireless to a box that is plugged into the wall anyway.  Maybe soon Ubuntu will handle wirless adapters with ease but right now the ethernet cable is free and works just fine.  Maybe even faster that wireless N.

Thanks for all the help.

---

