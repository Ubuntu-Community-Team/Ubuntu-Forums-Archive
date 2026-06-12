---
title: "Samba needs restarting if router is reset"
date: 2009-03-25
forum: Networking &amp; Wireless
---

### Post by jurialmunkey on 2009-03-25
Hi,

I've managed to get samba server set up on my ubuntu 8.10 machine to share to my wired network. I've got an XBMC and two XP machines connected. Everything is connected to a router which assigns addresses via DHCP. The shares are setup so anyone on the wired network can access without a password. Very occasionally the internet connection drops out and usually turning the router off then on again restores it. However, the problem is that when the router is reset, the samba shares stop working. Usually I have to restart samba manually via: ```
sudo /etc/init.d/samba restart
``` Its not a big deal, but slightly annoying as the ubuntu machine serves music/videos to the XBMC machine in the lounge room. This means I have to go and restart the samba server manually if someone wants to watch something. So if I am not at home then no one can watch anything on XBMC. Is there anyway to do this automatically? Everyone in the house is now familiar with using the samba shares so I don't really want to change to a different system of file sharing.

my /etc/samba/smb.conf
```
[global]
   workgroup = MSHOME
   netbios name = LINUXPC
   server string = 
   log file = /var/log/samba/log.%m
   max log size = 50
   map to guest = bad user
   socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
   local master = no
   dns proxy = no
   usershare owner only = False
   interfaces = lo eth0
   bind interfaces only = true
   security = share
   guest account = nobody

[Music]
   comment = Guest Access Share Music
   path = "/host/Documents and Settings/******/My Documents/Music"
   public = yes
   only guest = yes
   writable = no
   browseable = yes
   read only = yes
   guest ok = yes
   available = yes

[Videos]
   comment = Guest Access Share Videos
   path = "/media/LACIE Removable Harddisk/Videos"
   public = yes
   only guest = yes
   writable = no
   browseable = yes
   read only = yes
   guest ok = yes
   available = yes
```

---

### Post by jurialmunkey on 2009-03-27
No one?

This is driving me nuts. 

Can someone explain what the socket options do? I'm having trouble finding any detailed/comprehensible information on them. I have a feeling that possibly the SO_KEEPALIVE option may help. I'm not sure though.

This is just so annoying because on XP on the same machine the samba server stays on persistently/constantly. However, when in ubuntu, if the network gets reset then samba has to also be reset for the shares to be accessed.

Can anyone help?

Also, can someone tell me if my smb.conf is ok. Whilst I have a lot of experience in a DOS/Windows environment, I am very new to the Linux/Ubuntu one. Samba seems to work fine other than this one (slightly) annoying issue. I have purposefully tried to set it up in a similar fashion to XP simple file sharing - I hate password authentication, and regardless my router has a strong firewall which stealths the file sharing ports.

---

