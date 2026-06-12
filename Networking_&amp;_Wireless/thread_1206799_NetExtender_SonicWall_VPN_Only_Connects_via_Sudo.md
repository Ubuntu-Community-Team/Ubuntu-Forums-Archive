---
title: "NetExtender SonicWall VPN Only Connects via Sudo"
date: 2009-07-07
forum: Networking &amp; Wireless
---

### Post by kendoori on 2009-07-07
We have a SonicWall SSL VPN appliance that I reliably can connect to via the Windows NetExtender client. I've tried to do the same with Ubuntu Jaunty but was unsuccessful until I ran the program via sudo as follows:

```

sudo /usr/bin/netExtenderGui

```

I'm not that smart about this stuff, but when running as my normal user, I saved a diagnostic file, and found the following errors:

```

=== Command: ls -lart /etc/ppp/peers ===
ls: cannot open directory /etc/ppp/peers: Permission denied

```

```
=== Command: cat /etc/ppp/peers/sslvpn ===
cat: /etc/ppp/peers/sslvpn: Permission denied

```

```
=== Command: /usr/sbin/pppd --version ===
sh: /usr/sbin/pppd: Permission denied
```

```
=== Command: cat /etc/ppp/peers/sslvpnparams.diag ===
cat: /etc/ppp/peers/sslvpnparams.diag: Permission denied

```

I would like to run this via my normal user. Anyone with any experience on this?

---

### Post by quaternion on 2009-07-14
When you run a program in linux it runs with the same authority that you do.  Running as the super user will let you get at everything but isn't convenient in Ubuntu and rightly so.  

You are going to need to change the permissions on some files.  My system is not a clean install of Jaunty but an upgrade over several versions so I don't know if what you experience is normal or not but the normal install which you find in the README after downloading and saving the netextender worked fine for me.  That is I can run the program without sudo.

Anyways first determine your permission issues:

```
ls -l /etc/ppp/peers

Output:

total 20
-rw-r----- 1 root dip  1093 2008-06-30 22:41 provider
-rw-r--r-- 1 root dip   220 2009-07-14 09:56 sslvpn
-rw-rw-rw- 1 root dip   134 2009-07-14 11:06 sslvpn.params.diag
-rw-r--r-- 1 root root   30 2008-01-03 12:28 wvdial
-rw-r--r-- 1 root root   75 2008-01-03 12:28 wvdial-pipe
```

If you are not comfortable working in the shell, perhaps changing the permissions in a GUI would be easier, but first you do need the gui:

```
sudo nautilus
```

... Will create a super user file manager. Then browse to the files, right click: Properties => Permissions and make them look like the above.

You will also need to change the other files that it is complaining about such as:

```
ls -l pppd

Output:

-rwsr-xr-- 1 root dip 277352 2009-02-20 10:25 /usr/sbin/pppd
```

Note "dip" is the group... make sure you have access to dip:

```
groups yourUserName
yourUserName adm cdrom floppy audio dip video plugdev fuse lpadmin admin sambashare

```

You should see dip in the above output.
If you do not see dip in your output:
```
sudo adduser yourUserName dip
```

If you are a memeber of dip the following should work:
```
/usr/sbin/pppd --version
```


If there are further issues: What version of netExtender are you using?

```
netExtender -h

Output: 

NetExtender for Linux - Version 2.5.87
Copyright (c) 2008 SonicWALL, Inc.
Usage: netExtender [OPTIONS] server[:port]
	-u user
	-p password
	-d domain
	-t timeout	Login timeout in seconds, default is 30 sec.
	-e encryption	Encryption cipher to use.  To see list use -e -h.
	-m		Use this option to not add remote routes.
	-r filename	Generate a diagnostic report.
	-v		Display NetExtender version information.
	-h		Display this usage information.
	server:	Specify the server either in FQDN or IP address.
	The default port for server is 443 if not specified.
	Example:
		netExtender -u u1 -p p1 -d LocalDomain sslvpn.company.com
```

There is something strange going on, on my system I simply connected to the sonicwall-vpn and logged on as a normal user (non admin) then I was able to download the netExtender.  I saved it to my desktop and ran the install script with sudo.

You will notice that you can run netExtender without running netExtenderGui... once you get a connection using netExtender with the correct command line arguments then you can make a script to run this process in the background and make a nice icon on the desktop for this... then you can avoid a window.  Although the window does let you know if the session has timed out.

Good luck.

---

