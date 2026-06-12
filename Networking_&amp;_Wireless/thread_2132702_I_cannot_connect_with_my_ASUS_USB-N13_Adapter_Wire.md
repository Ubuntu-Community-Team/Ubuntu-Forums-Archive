---
title: "I cannot connect with my ASUS USB-N13 Adapter Wireless-N300"
date: 2013-04-05
forum: Networking &amp; Wireless
---

### Post by SUPERFITTER on 2013-04-05
I cannot connect with my ASUS USB-N13 Adapter Wireless-N300. I am running Ubuntu 12.10. This is a home built computer, with a Gigibit motherboard.
I ran the following:

dennis@dennis:~$ Get it from your product information.
No command 'Get' found, did you mean:
 Command 'eet' from package 'libeet-bin' (universe)
 Command 'net' from package 'samba-common-bin' (main)
 Command 'fet' from package 'fet' (universe)
Get: command not found
dennis@dennis:~$ $ lspci
$: command not found
dennis@dennis:~$ $ lsusb
$: command not found
dennis@dennis:~$ $ lspci -nn | grep 'Wireless Brand'
$: command not found
dennis@dennis:~$ $ ifconfig
$: command not found
dennis@dennis:~$ $ iwconfig
$: command not found
dennis@dennis:~$ $ iwconfig wlan0
$: command not found
dennis@dennis:~$ $ lsmod
$: command not found
dennis@dennis:~$ $ lsmod | grep "wlan_module_name"
$: command not found
dennis@dennis:~$ $ dmesg
$: command not found
dennis@dennis:~$ $ sudo lshw -C network
$: command not found
dennis@dennis:~$ $ iwlist scan
$: command not found
dennis@dennis:~$ $ iwlist scan wlan0
$: command not found
dennis@dennis:~$ $ uname -mr
$: command not found
dennis@dennis:~$ $ sudo /etc/init.d/networking restart
$: command not found
dennis@dennis:~$ ndiswrapper -l
The program 'ndiswrapper' is currently not installed. You can install it by typing:
sudo apt-get install ndiswrapper-common
dennis@dennis:~$ sudo apt-get install ndiswrapper-common
[sudo] password for dennis: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  linux-headers-3.5.0-17
Use 'apt-get autoremove' to remove it.
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed:
  ndiswrapper-common
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 5,988 B of archives.
After this operation, 72.7 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/main ndiswrapper-common all 1.57-1ubuntu1 [5,988 B]
Fetched 5,988 B in 0s (39.3 kB/s)             
Selecting previously unselected package ndiswrapper-common.
(Reading database ... 157848 files and directories currently installed.)
Unpacking ndiswrapper-common (from .../ndiswrapper-common_1.57-1ubuntu1_all.deb) ...
Processing triggers for man-db ...
Setting up ndiswrapper-common (1.57-1ubuntu1) ...
dennis@dennis:~$

---

### Post by SUPERFITTER on 2013-04-05
dennis@dennis:~$ wget -N -t 5 -T 10 [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) && chmod +x wireless_script && ./wireless_script
--2013-04-05 16:50:30--  [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script)
Resolving dl.dropbox.com (dl.dropbox.com)... 23.23.132.169
Connecting to dl.dropbox.com (dl.dropbox.com)|23.23.132.169|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1555 (1.5K) [text/plain]
Last-modified header missing -- time-stamps turned off.
--2013-04-05 16:50:30--  [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script)
Reusing existing connection to dl.dropbox.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 1555 (1.5K) [text/plain]
Saving to: `wireless_script'

100%[======================================>] 1,555       --.-K/s   in 0s      

2013-04-05 16:50:31 (195 MB/s) - `wireless_script' saved [1555/1555]

[sudo] password for dennis: 
dennis@dennis:~$

---

### Post by SUPERFITTER on 2013-04-13
chili555, has found the answer: [http://ubuntuforums.org/showthread.php?t=2133710&page=3](http://ubuntuforums.org/showthread.php?t=2133710&page=3)

Thank you chili555

---

