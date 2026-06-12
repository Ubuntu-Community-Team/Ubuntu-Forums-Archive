---
title: "Unable to mount location - Failed to retrieve share list from server"
date: 2012-12-18
forum: Networking &amp; Wireless
---

### Post by Hawgs_Fan on 2012-12-18
I have a Dell Inspiron laptop with Ubuntu 12.10 and a home made desktop running Windows 7.  With flavors of Ubuntu prior to v12 I had no problems in accessing my Windows machine from my laptop (files, printing, etc).  However, since v12.10 am having a problem accessing my desktop.  I get a pop-up window stating "Unable to mount location: Failed to retrieve share list from server".   I have tried modifying nsswitch.conf, uninstalling and reinstalling SAMBA, and modifying the hosts file.  Nothing works and any help is appreciated.  Please note that I am well versed with esoteric scripts, etc so keep any responses on a kindergarten level....  :)

Thanx,
Bill Baumgardner

---

### Post by wagoner on 2012-12-19
Can you open a terminal and type?

```
smbtree
```

Do you know the ip address of the windows share?  If so type
```
sudo smbclient -NL xxx.xxx.xxx.xxx
```
using the ipaddress of the windows machine.

---

### Post by Gwaro on 2012-12-19
Do the two belong to the same workgroup?

---

### Post by Hawgs_Fan on 2012-12-19
Thanks everyone for your suggestions but I was at put into the position of needing this linkup now so I reinstalled Win7 on my laptop and dumped Ubuntu.
Baumgardner

---

### Post by martimcfly on 2013-01-04
I have the same problem. I tried modifying the smb.conf as mentioned in this thread [http://ubuntuforums.org/showthread.php?t=1953097&page=2](http://ubuntuforums.org/showthread.php?t=1953097&page=2) but the problem still remains.

The share used to work fine before updating to 12.10 and since then I've never been able to access it via nautilus. It's a media box that also runs a ftp server which I can access with no problem. I can also access it via telnet.

The /etc/hosts contains an entry to IP address of the media box:
192.168.1.106	nmt

smbtree doesn't give any output.

$sudo smbclient -NL 192.168.1.106

Anonymous login successful
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.32]

	Sharename       Type      Comment
	---------       ----      -------
	Hitachi         Disk      
	share           Disk      
	IPC$            IPC       IPC Service (Samba Share)
Anonymous login successful
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.32]

	Server               Comment
	---------            -------
	PALOMITAS            Samba Share

	Workgroup            Master
	---------            -------
	WORKGROUP

---

