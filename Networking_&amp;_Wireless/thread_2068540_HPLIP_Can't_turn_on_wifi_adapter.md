---
title: "HPLIP Can't turn on wifi adapter"
date: 2012-10-09
forum: Networking &amp; Wireless
---

### Post by Grim-Fandango on 2012-10-09
When trying to run sudo hp-setup I encounter the following problem


```
HP Linux Imaging and Printing System (ver. 3.12.10)
Printer/Fax Setup Utility ver. 9.0

Copyright (c) 2001-14 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Searching on USB bus...
GET /IoMgmt/Adapters HTTP/1.1
Host: localhost
User-Agent: hplip/3.0
Content-Type: text/xml; charset=utf-8
Content-Length: 0


warning: Wifi Adapter turn ON request Failed. ResponseCode=500 AdaptorId=/IoMgmt/Adapters/Wifi0 AdaptorName=Wifi0. Trying another interface
GET /IoMgmt/Adapters/Wifi0/WifiNetworks HTTP/1.1
Host: localhost
User-Agent: hplip/3.0
Content-Type: text/xml; charset=utf-8
Content-Length: 0


error: Request Failed With Response Code 500
Traceback (most recent call last):
  File "/usr/share/hplip/ui4/wifisetupdialog.py", line 703, in NextButton_clicked
    self.showNetworkPage()
  File "/usr/share/hplip/ui4/wifisetupdialog.py", line 286, in showNetworkPage
    self.performScan()
  File "/usr/share/hplip/ui4/wifisetupdialog.py", line 324, in performScan
    self.loadNetworksTable()
  File "/usr/share/hplip/ui4/wifisetupdialog.py", line 390, in loadNetworksTable
    name = self.networks['ssid-%d' % n]
KeyError: 'ssid-0'

Done.

```

hp-check -r produces:
```
| SYSTEM INFO |
---------------

 Kernel: 3.0.0-26-generic #42-Ubuntu SMP Wed Sep 5 08:37:08 UTC 2012 GNU/Linux
 Host: aaron-K53E
 Proc: 3.0.0-26-generic #42-Ubuntu SMP Wed Sep 5 08:37:08 UTC 2012 GNU/Linux
 Distribution: ubuntu 11.10

-----------------------
| HPLIP CONFIGURATION |
-----------------------

HPLIP-Version: HPLIP 3.12.10
HPLIP-Home: /usr/share/hplip
HPLIP-Installation: Auto installation is supported for ubuntu distro  11.10 version 

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.12.10

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/HP
ppdbase=/usr/share/ppd
doc=/usr/share/doc/hplip-3.12.10
icon=/usr/share/applications
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/share/cups/drv/hp

# Following values are determined at configure time and cannot be changed.
[configure]
network-build=yes
libusb01-build=no
pp-build=no
gui-build=yes
scanner-build=yes
fax-build=yes
dbus-build=yes
cups11-build=no
doc-build=yes
shadow-build=no
hpijs-install=no
foomatic-drv-install=no
foomatic-ppd-install=no
foomatic-rip-hplip-install=no
hpcups-install=yes
cups-drv-install=yes
cups-ppd-install=no
internal-tag=3.12.10
restricted-build=no
ui-toolkit=qt4
qt3=no
qt4=yes
policy-kit=no
hpijs-only-build=no
lite-build=no
udev-acl-rules=yes
udev_sysfs_rules=no
hpcups-only-build=no
hpijs-only-build=no


Current contents of '/var/lib/hp/hplip.state' file:
Plugins are not installed. Could not access file: No such file or directory

Current contents of '~/.hplip/hplip.conf' file:
[upgrade]
notify_upgrade = false
last_upgraded_time = 1349775706
pending_upgrade_time = 0
latest_available_version = 3.12.10 Public Release</a><br />');document.write('</li>');document.write('<li class="rss-item"><a class="rss-item" href="http://sourceforge.net/news/?group_id=149981&id=309222" target="_self">HPLIP 3.12.9 Public Release</a><br />');document.write('</li>');document.write('<li class="rss-item"><a class="rss-item" href="http://sourceforge.net/news/?group_id=149981&id=308288" target="_self">HPLIP 3.12.6 Public Release</a><br />');document.write('</li>');document.write('<li class="rss-item"><a class="rss-item" href="http://sourceforge.net/news/?group_id=149981&id=307195" target="_self">HPLIP 3.12.4 Public Release</a><br />');document.write('</li>');document.write('<li class="rss-item"><a class="rss-item" href="http://sourceforge.net/news/?group_id=149981&id=306048" target="_self">HPLIP 3.12.2 Public Release</a><br />');document.write('</li>');document.write('<li class="rss-item"><a class="rss-item" href="http://sourceforge.net/news/?group_id=149981&id=305159" target="_self">HPLIP 3.11.12 Public Release</a><br />');document.write('</li>');document.write('<li class="rss-item"><a class="rss-item" href="http://sourceforge.net/news/?group_id=149981&id=303762" target="_self">HPLIP 3.11.10 Public Release</a><br />');document.write('</li>');document.write('<li class="rss-item"><a class="rss-item" href="http://sourceforge.net/news/?group_id=149981&id=302308" target="_self">HPLIP 3.11.7 Public Release</a><br />');document.write('</li>');document.write('<li class="rss-item"><a class="rss-item" href="http://sourceforge.net/news/?group_id=149981&id=300330" target="_self">HPLIP 3.11.5 Public Release</a><br />');document.write('</li>');document.write('<li class="rss-item"><a class="rss-item" href="http://sourceforge.net/news/?group_id=149981&id=298857" target="_self">HPLIP 3.11.3a

[installation]
date_time = 09/10/12 13:28:02
version = 3.12.10


 <Package-name>        <Package-Desc>      <Required/Optional> <Min-Version> <Installed-Version> <Status>   <Comment>

--------------------------
|  External Dependencies |
--------------------------

 gs                   Ghostscript               REQUIRED        7.05            9.04            OK         -
 network              Network-wget              OPTIONAL        -               1.12            OK         -
 dbus                 DBus                      REQUIRED        -               1.4.14          OK         -
 scanimage            Shell-Scanning            OPTIONAL        1.0             1.0.22          OK         -
 policykit            Admin-Policy-framework    OPTIONAL        -               0.102           OK         -
 xsane                SANE-GUI                  OPTIONAL        0.9             0.998           OK         -
 cups                 CUPS                      REQUIRED        1.1             1.5.0           OK         'CUPS Scheduler is running'

-------------------------
|  General Dependencies |
-------------------------

 reportlab            Python-PDF-Lib            OPTIONAL        2.0             2.5             OK         -
 libcrypto            OpenSSL-Crypto-Lib        REQUIRED        -               1.0.0           OK         -
 pil                  Python-Image-Lib          OPTIONAL        -               1.1.7           OK         -
 pyqt4-dbus           PyQt4-DBUS                REQUIRED        4.0             4.8.5           OK         -
 libjpeg              JPEG-Lib                  REQUIRED        -               -               OK         -
 libpthread           POSIX-Threads-Lib         REQUIRED        -               2.13            OK         -
 python-dbus          Python-DBUS               REQUIRED        0.80.0          0.84.0          OK         -
 python-devel         Python-SDK                REQUIRED        2.2             2.7.2           OK         -
 pyqt4                Python-Qt4                REQUIRED        4.0             4.8.5           OK         -
 cups-devel           CUPS-SDK                  REQUIRED        -               1.5.0           OK         -
 sane-devel           SANE-SDK                  REQUIRED        -               1.0.22          OK         -
 libusb               USB-Lib                   REQUIRED        -               1.0             OK         -
 sane                 Scan-Lib                  REQUIRED        -               1.0.22          OK         -
 cups-image           CUPS-Image-Lib            REQUIRED        -               1.5.0           OK         -
 libnetsnmp-devel     SNMP-Networking-SDK       REQUIRED        5.0.9           5.4.3           OK         -
 python-xml           Python-XML-Lib            REQUIRED        -               2.0.1           OK         -
 python-notify        Desktop-notifications     OPTIONAL        -               -               OK         -

----------------------
|  Python Extentions |
----------------------

 cupsext              CUPS-Extension            REQUIRED        -               3.12.10         OK         -
 pcardext             PhotoCard-Extension       REQUIRED        -               3.12.10         OK         -
 hpmudext             IO-Extension              REQUIRED        -               3.12.10         OK         -

-----------------------
|  Scan Configuration |
-----------------------

 hpaio                HPLIP-SANE-Backend        REQUIRED        -               3.12.10         OK         'hpaio found in /etc/sane.d/dll.conf'
 scanext              Scan-SANE-Extension       REQUIRED        -               3.12.10         OK         -

------------------------------
| DISCOVERED SCANNER DEVICES |
------------------------------

device `hpaio:/usb/Photosmart_5510_series?serial=CN1BM219KX05NR' is a Hewlett-Packard Photosmart_5510_series all-in-one


--------------------------
| DISCOVERED USB DEVICES |
--------------------------

  Device URI                        Model                    
  --------------------------------  -------------------------
  hp:/usb/Photosmart_5510_series?s  HP Photosmart 5510 series
  erial=CN1BM219KX05NR                                       

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
Photosmart_5510
---------------
Type: Printer
Device URI: hp:/usb/Photosmart_5510_series?serial=CN1BM219KX05NR
PPD: /etc/cups/ppd/Photosmart_5510.ppd
PPD Description: HP Photosmart 5510 Series, hpcups 3.12.10
Printer status: printer Photosmart_5510 is idle.  enabled since Tue 09 Oct 2012 13:15:25 BST
Communication status: Good


--------------
| PERMISSION |
--------------

error: groups   user-groups                    Required        -        -        MISSING  ['lp', 'lpadmin']
USB             Photosmart_5510                Required        -        -        OK       Node:'/dev/bus/usb/003/002' Perm:'  root  lp rw- rw- rw- rw- r--'

-----------
| SUMMARY |
-----------

Missing Required Dependencies
-----------------------------
None

Missing Optional Dependencies
-----------------------------
None


Total Errors: 1
Total Warnings: 0

Re-run 'hp-check --fix' command to prompt and fix the issues. 

Done.

```

Unfortunately, I am a complete novice.
Thanks in advance for any help.

---

### Post by Grim-Fandango on 2012-10-09
The only problem was my inability to properly read the setup utilty.

---

