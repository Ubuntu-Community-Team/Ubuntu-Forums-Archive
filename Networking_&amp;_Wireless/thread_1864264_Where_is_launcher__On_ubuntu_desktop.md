---
title: "Where is launcher?  On ubuntu desktop??"
date: 2011-10-18
forum: Networking &amp; Wireless
---

### Post by smalleeepc on 2011-10-18
Followed Shannon Vanwagner's (url?) instructions for setting up droid tethered to ubuntu system.  Most of the work was getting his python script downloaded and executed on my Asus Eeepc900.  Here is the terminal window screenshot:

[INDENT]brad@brad-900:~/Downloads/Droid-Tether-SV$ sudo ./install_droidtethersv.py
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  liblzo2-2 libpkcs11-helper1 openssl-blacklist openvpn-blacklist
Suggested packages:
  resolvconf
The following NEW packages will be installed:
  liblzo2-2 libpkcs11-helper1 openssl-blacklist openvpn openvpn-blacklist
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 7,938kB of archives.
After this operation, 16.3MB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main openssl-blacklist all 0.5-2 [6,338kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main liblzo2-2 i386 2.03-2 [63.4kB]                              
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main libpkcs11-helper1 i386 1.07-1build1 [43.8kB]                
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main openvpn-blacklist all 0.4 [1,068kB]                         
Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main openvpn i386 2.1.0-3ubuntu1 [425kB]                         
Fetched 7,938kB in 26s (296kB/s)                                                                                     
Preconfiguring packages ...
Selecting previously deselected package openssl-blacklist.
(Reading database ... 141446 files and directories currently installed.)
Unpacking openssl-blacklist (from .../openssl-blacklist_0.5-2_all.deb) ...
Selecting previously deselected package liblzo2-2.
Unpacking liblzo2-2 (from .../liblzo2-2_2.03-2_i386.deb) ...
Selecting previously deselected package libpkcs11-helper1.
Unpacking libpkcs11-helper1 (from .../libpkcs11-helper1_1.07-1build1_i386.deb) ...
Selecting previously deselected package openvpn-blacklist.
Unpacking openvpn-blacklist (from .../openvpn-blacklist_0.4_all.deb) ...
Selecting previously deselected package openvpn.
Unpacking openvpn (from .../openvpn_2.1.0-3ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up openssl-blacklist (0.5-2) ...
Setting up liblzo2-2 (2.03-2) ...
Setting up libpkcs11-helper1 (1.07-1build1) ...
Setting up openvpn-blacklist (0.4) ...
Setting up openvpn (2.1.0-3ubuntu1) ...
 * Restarting virtual private network daemon(s)...                                                                     *   No VPN is running.
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service udev restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the restart(8) utility, e.g. restart udev
udev start/running, process 4260
 * Reconfiguring network interfaces...                                                                                Ignoring unknown interface wlan0=wlan0.
                                                                                                               [ OK ]
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service network-manager restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the restart(8) utility, e.g. restart network-manager
network-manager start/running, process 4328
**Everything is setup on Computer-side at this point. Now for adding azilink to the phone..
* daemon not running. starting it now on port 5037 *
* daemon started successfully *
1396 KB/s (48509 bytes in 0.033s)
    pkg: /data/local/tmp/azilink-2.0.2.apk
Success

 |Voila! Now you can start using your Android to connect to the Internet.
 |Just follow these steps:
 | 1.)Enable the azilink service on your Android.
 | 2.)Double-click the Droid-Tether-SV desktop icon (then authenticate)
 | 3.)When you are finished using the connection,
 | click into the terminal window, then hit ctrl+c to quit the connection
 | Special Thanks goes out to all who make FOSS possible
 | Also, Thanks to James Perry for azilink
 | Got Feedback? Leave a comment at [http://tinyurl.com/tetherdroid](http://tinyurl.com/tetherdroid)
 | Congratulations on your Freedom! Cheers!
 | Shannon VanWagner - humans-enabled.com
[/INDENT]The problem is (a) I don't know for certain that I know what a "ubuntu desktop" is, and (b) since the launcher app is supposed to be located on the desktop, I have no way to find it.  I did get to the wallpaper area of my ... desktop, but didn't see any apps or links.

Thanks in advance,

smalleeepc

---

### Post by smalleeepc on 2011-10-20
I did it!  I'm on!!  The desktop ... that is the "Ubuntu desktop" is a folder named "desktop" in one's home folder (viewable as "desktop" in the left navigation pane of the "File Manager" app... the path is "/home/<name>/desktop" where <name> is the user name of the (admin?) account the computer was setup on, or the account the current user is logged in as (?))

Anyway I'm smiling now :-)

No more Starbucks security police encounters.  I can grill out on my tailgate and sleep in my truck for forever....

SOLVED

ps... how do I mark my thread [SOLVED]?

---

