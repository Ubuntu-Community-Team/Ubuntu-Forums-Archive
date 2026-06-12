---
title: "Shared Network Printer Installation"
date: 2009-05-27
forum: Networking &amp; Wireless
---

### Post by butterman on 2009-05-27
I'm having trouble installing a shared network printer (HP LaserJet p1505n) to support a mixed Windows/Ubuntu 9.04 home network.  The printer is directly connected to a router with a fixed IP address.

```
$ ping 192.168.1.104
PING 192.168.1.104 (192.168.1.104) 56(84) bytes of data.
64 bytes from 192.168.1.104: icmp_seq=1 ttl=255 time=1.56 ms
64 bytes from 192.168.1.104: icmp_seq=2 ttl=255 time=0.185 ms
64 bytes from 192.168.1.104: icmp_seq=3 ttl=255 time=0.183 ms
```

```
$ snmpwalk -Os -c public -v 1 192.168.1.104 1.3.6.1.4.1.11.2.3.9.1.1.7.0
enterprises.11.2.3.9.1.1.7.0 = STRING: "MFG:Hewlett-Packard;MDL:HP LaserJet P1505n;CMD:HBS,PJL,ACL,PCL;CLS:PRINTER;DES:HP LaserJet P1505n;FWVER:20080505;"
```

I've been trying to install this printer for weeks with different versions of HPLIP, but now I can't install any version.

```
$ hp-toolbox
The program 'hp-toolbox' is currently not installed.  You can install it by typing:
sudo apt-get install hplip
bash: hp-toolbox: command not found
$ sudo apt-get install hplip
[sudo] password for rsmith: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  hpijs
Suggested packages:
  hpijs-ppds kdeprint gtklp xpp hplip-gui
The following NEW packages will be installed:
  hpijs hplip
0 upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/694kB of archives.
After this operation, 2478kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Selecting previously deselected package hplip.
(Reading database ... 189465 files and directories currently installed.)
Unpacking hplip (from .../hplip_3.9.2-3ubuntu4_i386.deb) ...
Selecting previously deselected package hpijs.
Unpacking hpijs (from .../hpijs_3.9.2-3ubuntu4_i386.deb) ...
Processing triggers for hal ...
Regenerating hal fdi cache ...
 * Restarting Hardware abstraction layer hald                                                                                [ OK ] 
Processing triggers for menu ...
Processing triggers for man-db ...
Setting up hplip (3.9.2-3ubuntu4) ...
Creating/updating hplip user account...
Can't open /etc/hp/hplip.conf: No such file or directory.
Can't open /etc/hp/hplip.conf: No such file or directory.

Setting up hpijs (3.9.2-3ubuntu4) ...

Processing triggers for menu ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
$ hp-toolbox
The program 'hp-toolbox' is currently not installed.  You can install it by typing:
sudo apt-get install hplip
bash: hp-toolbox: command not found

```

I see the error regarding hplip.conf, but I'm not sure what to do about it.

If I enter:

```
$ sh hplip-3.9.4b.run
```

I get:

```
RE-CHECKING DEPENDENCIES
------------------------
error: A required dependency 'cups (CUPS - Common Unix Printing System)' is still missing.
error: Installation cannot continue without this dependency.
error: Please manually install this dependency and re-run this installer.
```


Background: Initially I downloaded and successfully installed HPLIP from the HPLIP Project page.  My printer was recognized by CUPS and test pages printed successfully my multiple machine.  The only problem was that the printer was not show in the list of available printers from within an application.  Selecting System>Preferences>Default Printer displayed an error message that said something like CUPS scheduler not running.

Why I'm in this situation: I noticed this statement on the HPLIP Project page and retreated to the version available from the Ubuntu repositories: "We recommend using the already installed HPLIP unless your printer is not supported by that version of HPLIP."  That's where I got into trouble.  Anybody know how I can install hplip? I'd also be interested to know if anybody has had a similar experience with HP's Jetdirect (print server).

---

