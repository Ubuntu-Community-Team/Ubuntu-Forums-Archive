---
title: "I cannot connect to a Deskjet 3070A from Ubuntu 12.04 or Ubuntu 10.10"
date: 2012-06-10
forum: Networking &amp; Wireless
---

### Post by molly.moggins on 2012-06-10
I have been trying to set up a wireless printer.

 

I can print to the printer when it is attached via the USB cable but it loses all connection as soon as the cable is unplugged.

 

I installed the latest version of HPLIP 3.12.4 on both PCs but it is unable to find the printer as a wireless device when trying the setup with the USB cable plugged in on either PC.

 

I cannot configure the printer via WPS because my router a PLUSCOM WR-AR2317 doesn't have a WPS button and if I try to add a PIN there is nowhere in the router homepage (192.168.1.1) for me to add in a PIN.

 

I have printed off the Network config page and it shows that it has discoveded my home network but the wireless capability seems to not work at all, even though it says wireless is switched on.

 

The wireless blue light only flashes, there is no solid, always on light. I have had the printer about a metre away from the wireless router and it still doesn't seem to connect at all.

 

I have run hp-check and the output is below

 

 

carole@carole-desktop:~$ hp-check -t

HP Linux Imaging and Printing System (ver. 3.12.4)
Dependency/Version Check Utility ver. 14.3

Copyright (c) 2001-14 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Note: hp-check can be run in three modes:
1. Compile-time check mode (-c or --compile): Use this mode before compiling the HPLIP supplied tarball (.tar.gz or
.run) to determine if the proper dependencies are installed to successfully compile HPLIP.                          
2. Run-time check mode (-r or --run): Use this mode to determine if a distro supplied package (.deb, .rpm, etc) or  
an already built HPLIP supplied tarball has the proper dependencies installed to successfully run.                  
3. Both compile- and run-time check mode (-b or --both) (Default): This mode will check both of the above cases     
(both compile- and run-time dependencies).                                                                          

Saving output in log file: hp-check.log

Initializing. Please wait...
 
---------------
| SYSTEM INFO |
---------------

Basic system information:
Linux carole-desktop 3.0.0-15-generic #26-Ubuntu SMP Fri Jan 20 17:23:00 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

Distribution:
ubuntu 12.04

Checking Python version...
OK, version 2.7.3 installed

Checking PyQt 4.x version...
OK, version 4.9.1 installed.

Checking for CUPS...
Status: scheduler is running
Version: 1.5.3
error_log is set to level: warn

Checking for dbus/python-dbus...
dbus daemon is running.
python-dbus version: 1.0.0


------------------------------------
| COMPILE AND RUNTIME DEPENDENCIES |
------------------------------------

note: To check for compile-time only dependencies, re-run hp-check with the -c parameter (ie, hp-check -c).
note: To check for run-time only dependencies, re-run hp-check with the -r parameter (ie, hp-check -r).

Checking for dependency: CUPS - Common Unix Printing System...
OK, found.

Checking for dependency: CUPS devel- Common Unix Printing System development files...
OK, found.

Checking for dependency: CUPS image - CUPS image development files...
OK, found.

Checking for dependency: DBus - Message bus system...
OK, found.

Checking for dependency: gcc - GNU Project C and C++ Compiler...
OK, found.

Checking for dependency: GhostScript - PostScript and PDF language interpreter and previewer...
OK, found.

Checking for dependency: libcrypto - OpenSSL cryptographic library...
OK, found.

Checking for dependency: libjpeg - JPEG library...
OK, found.

Checking for dependency: libnetsnmp-devel - SNMP networking library development files...
OK, found.

Checking for dependency: libpthread - POSIX threads library...
OK, found.

Checking for dependency: libtool - Library building support services...
OK, found.

Checking for dependency: libusb - USB library...
OK, found.

Checking for dependency: make - GNU make utility to maintain groups of programs...
OK, found.

Checking for dependency: PIL - Python Imaging Library (required for commandline scanning with hp-scan)...
OK, found.

Checking for dependency: PolicyKit - Administrative policy framework...
OK, found.

Checking for dependency: PyQt 4 DBus - DBus Support for PyQt4...
OK, found.

Checking for dependency: Python DBus - Python bindings for DBus...
OK, found.

Checking for dependency: Python devel - Python development files...
OK, found.

Checking for dependency: Python libnotify - Python bindings for the libnotify Desktop notifications...
OK, found.

Checking for dependency: Python XML libraries...
OK, found.

Checking for dependency: Python 2.3 or greater - Required for fax functionality...
OK, found.

Checking for dependency: Python 2.2 or greater - Python programming language...
OK, found.

Checking for dependency: Reportlab - PDF library for Python...
OK, found.

Checking for dependency: SANE - Scanning library...
OK, found.

Checking for dependency: SANE - Scanning library development files...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo apt-get install --assume-yes libsane-dev

Checking for dependency: scanimage - Shell scanning program...
OK, found.

Checking for dependency: xsane - Graphical scanner frontend for SANE...
OK, found.


----------------------
| HPLIP INSTALLATION |
----------------------


Currently installed HPLIP version...
HPLIP 3.12.4 currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.12.4

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/HP
ppdbase=/usr/share/ppd
doc=/usr/share/doc/hplip-3.12.4
icon=/usr/share/applications
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/share/cups/drv/hp

# Following values are determined at configure time and cannot be changed.
[configure]
network-build=yes
pp-build=no
gui-build=yes
scanner-build=no
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
internal-tag=3.12.4
restricted-build=no
ui-toolkit=qt4
qt3=no
qt4=yes
policy-kit=no
hpijs-only-build=no
lite-build=no
udev-acl-rules=yes
hpcups-only-build=no
hpijs-only-build=no


Current contents of '/var/lib/hp/hplip.state' file:
# hplip.state - HPLIP runtime persistent variables.

[plugin]
installed=0
eula=0



Current contents of '~/.hplip/hplip.conf' file:
[settings]
systray_visible = 0
systray_messages = 0

[last_used]
device_uri = "hp:/usb/Deskjet_3070_B611_series?serial=CN1AH4333905MQ"
printer_name = Photosmart_C4200_series
working_dir = .

[commands]
scan = /usr/bin/simple-scan %SANE_URI%

[refresh]
rate = 30
enable = false
type = 1

[polling]
enable = false
interval = 5
device_list =

[fax]
voice_phone =
email_address =

[installation]
date_time = 10/06/12 17:16:33
version = 3.12.4

[upgrade]
notify_upgrade = true
last_upgraded_time = 1339337816
pending_upgrade_time = 0
latest_available_version = 3.12.4



--------------------------
| DISCOVERED USB DEVICES |
--------------------------

  Device URI                                      Model                     
  ----------------------------------------------  --------------------------
  hp:/usb/Photosmart_C4200_series?serial=MY82SQQ  HP Photosmart C4200 series
  2RT04VP                                                                   

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
Deskjet_3070_B611
-----------------
Type: Printer
Device URI: hp:/usb/Deskjet_3070_B611_series?serial=CN1AH4333905MQ
PPD: /etc/cups/ppd/Deskjet_3070_B611.ppd
PPD Description: HP Deskjet 3070 b611 Series, hpcups 3.12.2
Printer /usr/lib/cups/backend/hp failed11 is idle.  enabled since Sun 10 Jun 2012 17:15:07 BST
error: Unable to communicate with device (code=12): hp:/usb/Deskjet_3070_B611_series?serial=CN1AH4333905MQ
error: Device not found
error: Communication status: Failed

Photosmart_C4200_series
-----------------------
Type: Printer
Device URI: hp:/usb/Photosmart_C4200_series?serial=MY82SQQ2RT04VP
PPD: /etc/cups/ppd/Photosmart_C4200_series.ppd
PPD Description: HP Photosmart c4200 Series, hpcups 3.12.2
Printer status: printer Photosmart_C4200_series is idle.  enabled since Wed 21 Dec 2011 17:43:25 GMT
Communication status: Good


---------------------
| PYTHON EXTENSIONS |
---------------------

Checking 'cupsext' CUPS extension...
OK, found.

Checking 'pcardext' Photocard extension...
OK, found.

Checking 'hpmudext' I/O extension...
OK, found.

 
-----------------
| USB I/O SETUP |
-----------------

Checking for permissions of USB attached printers...

HP Device 0x5c11 at 001:003:
    Device URI: hp:/usb/Photosmart_C4200_series?serial=MY82SQQ2RT04VP
    Device node: /dev/bus/usb/001/003
    Mode: 0664
getfacl: Removing leading '/' from absolute path names
# file: dev/bus/usb/001/003
# owner: root
# group: lp
user::rw-
user:carole:rw-
group::rw-
mask::rw-
other::r--



---------------
| USER GROUPS |
---------------

carole adm lp dialout cdrom floppy audio dip video plugdev scanner lpadmin admin netdev powerdev


-----------
| SUMMARY |
-----------

error: 2 errors and/or warnings.

Summary of needed commands to run to satisfy missing dependencies:
sudo apt-get install --assume-yes libsane-dev

Please refer to the installation instructions at:
[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)


Done.
carole@carole-desktop:~$

---

### Post by TVTrukChik on 2012-06-10
It sounds like the problem doesn't have anything to do with Ubuntu, but with the printer getting on the wireless network?  I have a different model HP, but I see what you mean about WPS and the PIN.  Mine also has a "Wireless Network Wizard" thing... does yours have that, and have you tried it?  Mine detected the wireless network without a problem when I tried it (I normally run it in wired mode, though).

I'm a little confused by your statement that the printer sees your home network, but the wireless isn't working.  Have you checked your router to see if it has assigned an IP address to the printer?  Can you try disabling security on the router temporarily and see if it connects then?

---

### Post by AUGit on 2012-06-18
I'm having exactly the same problem. When I try the hp set-up it doesn't show any wireless device at all. 
If anyone knows a fix it would gratefully be received.


Michael

---

### Post by Starfleet on 2012-07-13
If your wireless SSID is hidden the printer may not see your network. Make sure you are broadcasting the SSID. You can change that from inside the router wireless settings (sorry if you know that). Once your printer sees the network you can tell it to connect.

---

