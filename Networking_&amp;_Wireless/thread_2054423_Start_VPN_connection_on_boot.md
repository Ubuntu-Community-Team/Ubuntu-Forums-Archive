---
title: "Start VPN connection on boot"
date: 2012-09-07
forum: Networking &amp; Wireless
---

### Post by foxy123 on 2012-09-07
I need to start VPN connection on boot on my mother's laptop so I could connect to it even if she's not logged in (she's currently got troubles with logging in in GDM and has to do it through command line and startx). I found [this]("https://help.ubuntu.com/community/VPNClient#PPTP") in Ubuntu help but wonder how to make it run on boot. Could anyone help?

---

### Post by TheFu on 2012-09-07
To start any service, including a VPN, there should be either a "service start" command or a "/etc/init.d/service-name start" command used.  What that command is depends completely on which VPN server you installed, configured and plan to run. For openvpn, it is:
```
/etc/init.d/openvpn start
```

To have that start automatically, you want to understand runlevels and use the **update-rc.d** command to step up which runlevels you want the service to start and stop automatically. If you don't want to control that, use the defaults with:
**$ sudo update-rc.d  openvpn defaults**

This only works if there is a /etc/init.d/ or "service" setup.  Sometimes we just want a command - any command - to run after reboot and there isn't a script created.  For those, I'm lazy and drop them into** /etc/rc.local** knowing that it is the last script run after a reboot to a multi-user runlevel.  I use this for things like trivial firewall rules or hdparm or other things I'm too lazy to setup a proper start/stop/status script for ... like blog software.

BTW, runlevels [https://en.wikipedia.org/wiki/Runlevel](https://en.wikipedia.org/wiki/Runlevel) are cool and good to have a general understanding about. The details can be looked up when you need to know.

For any lurkers ... 
Is the remote PC behind a firewall?  Do you need to open ports there?

For remote management of systems, it is usually easier to use **ssh** or ssh-based tools like** FreeNX** and an NX client (eg. QtNX).   Once installed has ssh-server, it will startup automatically and listen on port 22.  Of course, everyone in the world will try to connect on port 22 for a public IP address so moving that to some other port .... any other port will pretty much end all hack attempts.  For better security, use **fail2ban** - X number of login failures from an IP will band that address in the firewall.

Regardless, her router needs to have whatever port you are trying to connect through opened and forwarded to whatever the internal IP address is for her PC.

For maintaining my mother's box, I did the following:
* setup a free dyndns account
* setup management of her IP inside her router
* setup port forwarding and translation from some high port 61022 to 22 internal LAN IP.
* setup a static IP for her PC on the internal LAN.

I'm comfortable using ssh to do management, patches and installs, but once every few years, she needs a GUI program setup.  

FreeNX to the rescue.  Connections are over ssh, so there's no need to screw with the firewall again.

Backup systems work with ssh too, so I pull critical file backups to my box 5 states away every week.  She has local hourly snapshot backups taken too.  The remote backups use the same ssh tunnel.

Not all VPNs are created equal. Be aware that PPTP has been cracked for the second time and shouldn't be trusted.  IPSec or OpenVPN are the remaining choices known to be secure ... besides ssh.  I've never heard that either IPsec or OpenVPN has been cracked.  

In 2008, openssl (ssh uses this) on debian-based systems had a terrible issue introduced. Within a few days of uncovering the problem, the impacted systems had patches available.  So, even the best made software can have security issues.  I believe the cause was traced to someone optimizing code who wasn't part of the code openssl development team.  UNIX, BSD and RPM-based Linux distros were not impacted. Those teams had not altered the code.  No malice involved, just someone meaning well, but understanding all the subtleties of the code. [http://lists.debian.org/debian-security-announce/2008/msg00152.html](http://lists.debian.org/debian-security-announce/2008/msg00152.html)

---

### Post by foxy123 on 2012-09-07
Thanks a lot for the response. My mother has a external ip but need to connect to the external network through PPTP VPN (it is how it is set up by her ISP). So basically she needs VPN to get to the external ip.

I have helped her set up a vpn connection in the NetworkManager so she can easily start the connection manually. The trouble is that she's got a trouble with getting in her account at the moment, the trouble I am trying to resolve without any noticeable progress so far. The only way for her to get to her account is to do Ctrl+Alt+F1, log in in the console, stop GDM and start X with startx. That's why I need the connection being established on boot so I could ssh into her laptop. I have set up the manual connection as per the link I posted in the first post but I do not know how to to start it on boot.

---

### Post by foxy123 on 2012-09-08
I wonder if I put ```
pon myvpn nodetach
``` in the **rc.local** will it work and will it cause any problem?

---

### Post by TheFu on 2012-09-08
I don't know. I've never heard of any ISP requiring the use of a VPN for connections. That is completely new to me.

That code makes lots of assumptions that doesn't usually work in scripts.
* Never trust the PATH
* Never assume a CWD
* Always know which userid it runs under.

pon is their proprietary VPN app?  Specify it with a full path, not just hoping it is found in the $PATH somewhere

"myvpn" is probably the VPN configuration, correct?  That is probably stored somewhere in a file. You can't assume the file with the settings will be located automatically. You need to fully specify the path to it.

If any environment variables are required to be set before the VPN can work, then you need to set them. rc.local doesn't really have much environment at all. That is for safety. It does run things as root, after all.

"nodetach" might be the VPN endpoint from the ISP?  Is a FQDN possible?

Finally, when you run anything from rc.local, it runs as "root", not whatever the normal userid is.  That might work and be fine, but if it isn't you'll need to prepend an **su - {userid} -c **in front to switch to the desired userid.

Besides that, I think it should work just find.

---

