---
title: "Help needed with ASUS USB-N13 Wireless Network Adapter"
date: 2011-01-30
forum: Networking &amp; Wireless
---

### Post by emillekorea on 2011-01-30
I refer to the below link 
[http://ubuntuforums.org/showthread.php?t=1419504&page=4](http://ubuntuforums.org/showthread.php?t=1419504&page=4)

I follow what it says. 
-------------------------------------
1.) Download the driver from #17 by chili555 (2009_1110_RT3070_Linux_STA_v2.1.2.0)
2.) Extract it to your Desktop (or anywhere, but I used that one)
Basically if you double-click on it the Archive Manager will start and you need to choose where to Extract.
3.) Go to the folder
code:
Quote:
cd /home/redsultan/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0
4.) code:
Quote:
sudo make
(obviously it will ask for your sudo/administrator password)
5.) code:
Quote:
make install
6.) Create two files in the next steps:
code:
Quote:
gedit /etc/udev/rules.d/network_drivers.rules
then when the text editor opens up
copy and paste the followings exactly as it is. case and all, quotes and all:
Quote:
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0b05", ATTR{idProduct}=="1784", RUN+="/sbin/modprobe -qba rt3070sta"
save and close the text editor.
Quote:
gedit /etc/modprobe.d/network_drivers.conf
the copy and paste as above:
Quote:
install rt3070sta /sbin/modprobe --ignore-install rt3070sta $CMDLINE_OPTS; /bin/echo "0b05 1784" > /sys/bus/usb/drivers/rt2870/new_id
save and close text editor.
7.) plug the USB device in (mine wasn't recognized until I restarted...)
8.) exit terminal window
9.) restart system
10.) configure your wireless
11.) enjoy. 
---------------------------------------

iwconfig 

lo        no wireless extensions.

eth1      no wireless extensions.

ra0       Ralink STA  ESSID:""  
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

=============================
However, when I go to System/preferences/network connector and changed ESSID of wireless setting, no change happen. 

I am a newbie on ubuntu. please give me an advice how to use wireless internet.

---

### Post by chili555 on 2011-01-30
Are you able to click the Network Manager icon at the top right and see your network? Let's do some diagnostics. From a terminal, run and post:```
lsmod | grep -e rt2 -e rt3
dmesg | grep -e rt3 -e ra0
modinfo | grep -e version -e 1784
```Thanks.

---

### Post by emillekorea on 2011-01-31
===============================

emillekorea@ubuntu4kit:~$ lsmod | grep -e rt2 -e rt3
rt3070sta             569703  0 
emillekorea@ubuntu4kit:~$ dmesg | grep -e rt3 -e ra0
[  768.164959] RtmpOSNetDevDetach(): RtmpOSNetDeviceDetach(), dev->name=ra0!
emillekorea@ubuntu4kit:~$ modinfo | grep -e version -e 1784
Usage: modinfo [-0][-F field][-k kernelversion][-b basedir]  module...
 Prints out the information about one or more module(s).
 If a fieldname is given, just print out that field (or nothing if not found).
 Otherwise, print all information out in a readable form
 If -0 is given, separate with nul, not newline.
 If -b is given, use an image of the module tree.


==========================
> **chili555 said:**
> Are you able to click the Network Manager icon at the top right and see your network? Let's do some diagnostics. From a terminal, run and post:```
lsmod | grep -e rt2 -e rt3
dmesg | grep -e rt3 -e ra0
modinfo | grep -e version -e 1784
```Thanks.

---

### Post by chili555 on 2011-01-31
Oops! Sorry about that. I should have asked for:```
modinfo **rt3070sta** | grep -e version -e 1784
```So far, I see no errors to fix; that's a good thing.

---

### Post by emillekorea on 2011-01-31
emillekorea@ubuntu4kit:~$ modinfo rt3070sta | grep -e version -e 1784
version:        2.3.0.2
srcversion:     27760B9B04537BF01DDF9E0
alias:          usb:v0B05p1784d*dc*dsc*dp*ic*isc*ip*
vermagic:       2.6.32-28-generic SMP mod_unload modversions 586 


> **chili555 said:**
> Oops! Sorry about that. I should have asked for:```
modinfo **rt3070sta** | grep -e version -e 1784
```So far, I see no errors to fix; that's a good thing.

---

