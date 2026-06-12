---
title: "connect windows xp via network to ubuntu 12.04"
date: 2013-08-30
forum: Networking &amp; Wireless
---

### Post by dlw1145 on 2013-08-30
[http://www.noobslab.com/2012/03/configure-samba-sharing-between-ubuntu.html#ubuntu_to_windows](http://www.noobslab.com/2012/03/configure-samba-sharing-between-ubuntu.html#ubuntu_to_windows)

Using the above link to try and connect Windows XP to Ubuntu 12.04 via a hardwired network.
When getting to
"It's time to access your sharing on Windows, Now go to start and open '*Run*' then enter ip with double backslash. Like this (\\192.168.1.3)"
ifconfig tells me my PC is 192.168.1.108.
I keep getting a 'The network path was not found."

Any ideas on how to solve this?

dlw

---

### Post by TheFu on 2013-08-31
So you have storage on Ubuntu that you want to access from Windows?
The Windows PC needs to know the ip address of the Ubuntu "server" - you can use the IP address for that, setup DNS somewhere on your network or modify the Windows "hosts" table.  For now, just use the IP address for the ubuntu - which I think you said was 192.168.1.8 

\\192.168.1.8\ should be entered into Windows Explorer.  If that doesn't work, you'll want to review the samba (smb) log files on the ubuntu machine. They are usually in /var/log/samba/. From those, we should be able to figure out any error.

---

### Post by dlw1145 on 2013-08-31
Thank you for replying.
ifconfig shows my box as 192.168.1.118... yesterday it was 192.168.1.108.
Entering \\192.168.1.118\ in Firefox on Windows xp does nothing... just sits there.
Entering \\192.168.1.118\ in /Start/Run returns 'The network path was not found.'
There are 8 logs in /var/log/samba.
I checked each log before and after trying to go to \\192.168.1.118\... no changes in any of the 8.

Does having Exede (a satellite service) have anything to do with this?
I can not have my own mail server or web server.

Thanks again,
dlw

---

### Post by TheFu on 2013-08-31
Your ubuntu machine is using DHCP to get an IP address after ever reboot. This comes from the local router. If you want that to stop, you should set a static IP for it, then the IP address will never change again.  This has ZERO to do with your ISP.  It is part of running a LAN.

I have no idea what /start/run is. When we configure samba, we choose a name for the "share" inside the /etc/samba/smb.conf file.  **man smb.conf** explains all the settings for that file, but most people follow a guide and using something like:
```
  [homes]
           hosts allow = 127.0.0.1 192.168.1.0/24
           hosts deny = 0.0.0.0/0
           comment = Home Directories
           writable = yes
           create mask = 0644
           directory mask = 0755
           valid users = %S
           browseable = yes
```
to make their "home directory" available by each user.  That would mean that the URL to access the samba share would be something like **\\192.168.1.2\dlw1145** - this assumes you set a static IP for the server.

There is a little more to it - smb needs users and passwords. CharlesA has a guide on that. A google of "ubuntu samba" will fine a guide at help.ubuntu.org too.

Simple.

---

