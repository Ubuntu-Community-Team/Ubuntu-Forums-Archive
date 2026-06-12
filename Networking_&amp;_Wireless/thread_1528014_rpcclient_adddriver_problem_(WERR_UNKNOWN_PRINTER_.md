---
title: "rpcclient adddriver problem (WERR_UNKNOWN_PRINTER_DRIVER)"
date: 2010-07-10
forum: Networking &amp; Wireless
---

### Post by hosseinyounesi on 2010-07-10
Hi everyone,
I'm trying to add my printer driver via adddriver. My distro is Ubuntu 10.04, cups 1.4.3 and samba 3.4.7.
this is my smb.conf:
```

[global]
	load printers = yes
	printing = cups
	printcap name = cups 

[printers]
	comment = All Printers
	path = /var/spool/samba
	browseable = no
	public = yes
	guest ok = yes
	writable = no
	printable = yes
	printer admin = root

[print$]
	comment = Printer Drivers
	path = /etc/samba/drivers
	browseable = yes
	guest ok = no
	read only = yes
	write list = root 

[mysmbtstprn]
	printable = yes
	path = /var/spool/samba
	guest ok = yes
	printer admin = root
	browseable = yes
	public = yes

```

I've done these:
```

lpadmin -p mysmbtstprn -v parallel:/dev/lp0 -E -P /etc/samba/drivers/HP_LaserJet_2420.ppd
rpcclient -Uroot%123456 -c 'enumprinters' localhost | grep -C2 mysmbtstprn
rpcclient -Uroot%123456 -c 'getprinter mysmbtstprn 2' localhost | grep driver
rpcclient -Uroot%123456 -c 'getprinter mysmbtstprn 2' localhost | grep -C4 driv
rpcclient -U root%123456 -c 'getdriver mysmbtstprn' localhost

smbclient //localhost/print\$ -U 'root%123456' -c 'cd W32X86; put /etc/cups/ppd/mysmbtstprn.ppd mysmbtstprn.ppd; put /usr/share/cups/drivers/cups6.ini cups6.ini; put /usr/share/cups/drivers/cupsui6.dll cupsui6.dll; put /usr/share/cups/drivers/ps5ui.dll ps5ui.dll; put /usr/share/cups/drivers/cupsps6.dll cupsps6.dll; put /usr/share/cups/drivers/pscript.ntf pscript.ntf; put /usr/share/cups/drivers/pscript5.dll pscript5.dll'

smbclient //localhost/print\$ -U 'root%123456' -c 'cd W32X86/3; put /etc/cups/ppd/mysmbtstprn.ppd mysmbtstprn.ppd; put /usr/share/cups/drivers/cups6.ini cups6.ini; put /usr/share/cups/drivers/cupsui6.dll cupsui6.dll; put /usr/share/cups/drivers/ps5ui.dll ps5ui.dll; put /usr/share/cups/drivers/cupsps6.dll cupsps6.dll; put /usr/share/cups/drivers/pscript.ntf pscript.ntf; put /usr/share/cups/drivers/pscript5.dll pscript5.dll'

```
and when I enter this command:
```

rpcclient -U'root%123456' -c 'adddriver "Windows NT x86" "mysmbtstprn:pscript5.dll:mysmbtstprn.ppd:ps5ui.dll:pscript.hlp:NULL:RAW:pscript5.dll,mysmbtstprn.ppd,ps5ui.dll,pscript.hlp,pscript.ntf,cups6.ini,cupsps6.dll,cupsui6.dll"' localhost

```

I get this error :
[color=red]result was WERR_UNKNOWN_PRINTER_DRIVER[/color]

I don't know what's wrong and it's really disturbing me  :cry:  :cry: 

I'm following these instructions:
[http://www.linuxtopia.org/online_books/network_administration_guides/samba_reference_guide/29_CUPS-printing_105.html](http://www.linuxtopia.org/online_books/network_administration_guides/samba_reference_guide/29_CUPS-printing_105.html)
and I'm now in step 6.

cupsaddsmb with '-v' option shows me the same problem as shown below and never ends  :( 
```

Running command: rpcclient localhost -N -A /tmp/064734c45013b -c 'adddriver "Windows NT x86" "mysmbtstprn:pscript5.dll:mysmbtstprn.ppd:ps5ui.dll:pscript.hlp:NULL:RAW:pscript5.dll,mysmbtstprn.ppd,ps5ui.dll,pscript.hlp,pscript.ntf,cups6.ini,cupsps6.dll,cupsui6.dll"'
result was WERR_UNKNOWN_PRINTER_DRIVER

Unable to install Windows 2000 printer driver files (1)!

```

I know that people in Gentoo have done this before and [here]("http://forums.gentoo.org/viewtopic-t-456501-postdays-0-postorder-asc-start-0.html") is the tutorial. Can this be done in ubuntu too?!

Thanks for your consideration

---

### Post by raerek on 2010-10-29
Same problem for me. Did you find a solution?

---

### Post by hosseinyounesi on 2010-10-29
Hi again,

My problem solved.
I stopped "ufw" and "apparmor" in Ubuntu and these:

```
cp * /usr/share/cups/drivers/
if doesn't exist => mkdir /usr/share/cups/drivers
chmod 777 /usr/share/cups/drivers/
chmod 777 /usr/share/cups/drivers/*
```

```
mkdir /etc/samba/drivers
chmod 777 /etc/samba/drivers
```

As my problem was with permissions, here are my file permissions:
```

root@linlab-desktop:/etc/samba/drivers# ll /etc/samba/        
total 28
drwxr-xr-x   3 root root  4096 Jul 10 14:03 ./
drwxr-xr-x 136 root root 12288 Jul 10 13:55 ../
drwxrwxrwx   3 root root  4096 Jul 10 13:59 drivers/
-rw-r--r--   1 root root     8 Apr  9 19:57 gdbcommands
-rw-r--r--   1 root root   502 Jul 10 14:03 smb.conf


root@linlab-desktop:/etc/samba/drivers# ll /etc/samba/drivers/
total 12
drwxrwxrwx 3 root root 4096 Jul 10 13:59 ./
drwxr-xr-x 3 root root 4096 Jul 10 14:03 ../
drwxrwxrwx 3 root root 4096 Jul 10 14:03 W32X86/


root@linlab-desktop:/etc/samba/drivers# ll /var/lib/samba/
total 316
drwxr-xr-x  5 root root        4096 Jul  9 22:40 ./
drwxr-xr-x 64 root root        4096 Jul  9 19:21 ../
-rw-r--r--  1 root root       16384 Jul  9 17:41 account_policy.tdb
-rw-------  1 root root       77824 Jul  9 17:41 group_mapping.ldb
-rw-r--r--  1 root root        8192 Jul 10 14:03 ntdrivers.tdb
-rw-r--r--  1 root root         696 Jul  9 17:41 ntforms.tdb
-rw-r--r--  1 root root       20480 Jul 10 14:03 ntprinters.tdb
-rw-r--r--  1 root root       36864 Jul 10 14:02 passdb.tdb
drwxr-xr-x  2 root root        4096 Jul  9 17:41 perfmon/
drwxrwxrwx 10 root root        4096 Jul 10 12:55 printers/
-rw-r--r--  1 root root       53248 Jul  9 17:41 registry.tdb
-rw-r--r--  1 root root       45056 Jul  9 21:01 secrets.tdb
-rw-r--r--  1 root root       36864 Jul 10 12:43 share_info.tdb
drwxrwxr-T  2 root sambashare  4096 Jul 10 12:43 usershares/
-rw-r--r--  1 root root         696 Jul  9 22:40 winbindd_idmap.tdb


root@linlab-desktop:/etc/samba/drivers# ll /usr/share/cups/
total 412
drwxr-xr-x  17 root root   4096 Jul  9 19:26 ./
drwxr-xr-x 320 root root  12288 Jul  9 19:42 ../
drwxr-xr-x   2 root root   4096 Jul  9 17:40 banners/
-rw-r--r--   1 root root 331836 Feb 12 14:35 calibrate.ppm
drwxr-xr-x   2 root root   4096 Jul  9 17:39 charmaps/
drwxr-xr-x   2 root root   4096 Jul  9 17:39 charsets/
drwxr-xr-x   2 root root   4096 Jul  9 17:40 data/
drwxr-xr-x  12 root root   4096 Jul  9 17:40 doc-root/
drwxrwxrwx   2 root root   4096 Jul 10 13:57 drivers/
drwxr-xr-x   2 root root   4096 Jul  9 17:39 drv/
drwxr-xr-x   2 root root   4096 Jul  9 17:40 examples/
drwxr-xr-x   2 root root   4096 Jul  9 17:40 fonts/
drwxr-xr-x  21 root root   4096 Apr 29 18:49 locale/
drwxr-xr-x   2 root root   4096 Jul  9 17:40 mime/
drwxr-xr-x   2 root root   4096 Jun 10  2008 model/
drwxr-xr-x   2 root root   4096 Jul  9 17:40 ppdc/
drwxr-xr-x   2 root root   4096 Apr  9 19:40 profiles/
drwxr-xr-x  10 root root  12288 Jul  9 17:40 templates/

root@linlab-desktop:/etc/samba/drivers# ll /usr/share/cups/drivers/
total 2352
drwxrwxrwx  2 root root    4096 Jul 10 13:57 ./
drwxr-xr-x 17 root root    4096 Jul  9 19:26 ../
-rw-rw-r--  1 root root      72 Jun 18  2005 cups6.ini
-rw-rw-r--  1 root root   12568 Jun 18  2005 cupsps6.dll
-rw-rw-r--  1 root root   13672 Jun 18  2005 cupsui6.dll
-rwxr-xr-x  1 root root  728576 Apr 14  2008 ps5ui.dll*
-rwxr-xr-x  1 root root   26038 May 15  2007 pscript.hlp*
-rwxr-xr-x  1 root root 1060548 May 15  2007 pscript.ntf*
-rwxr-xr-x  1 root root  543232 Apr 14  2008 pscript5.dll*

```

Good luck

---

### Post by jopes on 2011-12-28
I had an similar issue (only with my x64 drivers, 32 bit drivers working fine).

I was getting WERR_UNKNOWN_PRINTER_DRIVER when running the "cupsaddsmb" script. Been scratching my head for a couple of hours but finally realized what was wrong.

I was running cupsaddsmb in the folder **/usr/share/cups/drivers/x64** and what actually was happening was that all driver files in the folder were being overwrited by them selves, resulting in 0 byte files. What i ended up doing was I copied the non broken files to **/usr/share/cups/drivers/x64** again and then issued the 'adddriver' command manually (normally run last by cupsaddsmb):

```
rpcclient localhost -N -A /tmp/030404efb2ecc -c 'adddriver "Windows x64" "MyPrinter1:pscript5.dll:MyPrinter1.ppd:ps5ui.dll:pscript.hlp:NULL:RAW:pscript5.dll,MyPrinter1.ppd,ps5ui.dll,pscript.hlp,pscript.ntf,cups6.ini,cupsps6.dll,cupsui6.dll"'
```

And this was on Ubuntu server 10.04.

It may be slightly off topic, but I thought I'd post my solution here hopefully saving some future headaches.
Cheers!

---

