---
title: "HELP! Intel Chipset Setup issue (x-server bug?)"
date: 2009-07-25
forum: Multimedia Software
---

### Post by cmreaper on 2009-07-25
OK heres the issue im new to Ubuntu (hopefully not the only problem:)) 
i went threw the 			 			**[B]Sticky:**[/B] 			                          			 			[HOWTO: Jaunty Intel Graphics Performance Guide]("http://ubuntuforums.org/showthread.php?t=1130582")
did the " upgrade to the latest stable Xorg drivers (via the [X-Updates PPA]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/"))"

i put the (deb // deb-src) in software services with out a hitch(i think)

i get this when i enter key

 sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys af1cdfa9
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys af1cdfa9
gpg: requesting key AF1CDFA9 from hkp server keyserver.ubuntu.com
gpg: key AF1CDFA9: public key "Launchpad PPA for Ubuntu-X" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)

but when i enter :  

sudo dpkg-reconfigure -phigh xorg-xserver

i get 

Package `xorg-xserver' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

so i  

 sudo apt-get install xserver-xorg

and get

Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg is already the newest version.
The following packages were automatically installed and are no longer required:
  libtwolame0 libswfdec-0.8-0 libsidplay1 libmad0 libid3tag0 libmpeg2-4 liba52-0.7.4
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.

so again i 

sudo dpkg-reconfigure -phigh xorg-xserver

and get

Package `xorg-xserver' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xorg-xserver is not installed


Please help and im very sorry if this is something trivial that i should know:(

---

### Post by HappyFeet on 2009-07-25
You have 2 words backwards. Try:
```
sudo dpkg-reconfigure -phigh **xserver-xorg**
```

---

### Post by cmreaper on 2009-07-25
ok that helped, but but now instead of seeing

Section "Device"
	Identifier	"Configured Video Device"
	Option		"AccelMethod"			"uxa"
	Option		"EXAOptimizeMigration"		"true"
	Option		"MigrationHeuristic"		"greedy"
	Option		"Tiling"			"true" **# i8xx users: see note in guide**
EndSection

in xorg.conf

i see

Section "Device"
    Identifier    "Configured Video Device"
EndSection

 with no options?





# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

---

### Post by HappyFeet on 2009-07-25
You can also try
```
sudo dpkg-reconfigure xserver-xorg
```
and configure it the long way. Use the Tab and arrow keys to navigate. You can skip the sections about mouse and keyboard.

You can also boot into recovery mode and select the xfix option.

---

### Post by cmreaper on 2009-07-25
ok so i tried using 

sudo dpkg-reconfigure xserver-xorg


but it only went threw the keyboard config,   how do i boot in recovery mode?

sorry for my lack of experience :(

---

### Post by snssswc on 2009-07-26
Press Esc key at grub loading after restart the machine, then you will be prompted a list of options. One of the options is to boot in recovery mode.

---

### Post by cmreaper on 2009-07-26
ok so i did recovery boot then xfix but it kicks me back to main recovery area before i have a chance to really read options :confused:   lol now what?

thanks for any advice that may help me toward solving this issue:)

---

