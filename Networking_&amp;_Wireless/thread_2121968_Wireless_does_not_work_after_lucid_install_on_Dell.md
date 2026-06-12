---
title: "Wireless does not work after lucid install on Dell Latitude D610"
date: 2013-03-03
forum: Networking &amp; Wireless
---

### Post by karcat on 2013-03-03
tried many things to get the wifi running again. guess im no good at this as nothing  seems to work. i need help please :)
in terminal i got this tonight.....

                        karen@laptop:~$ sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source  
 [sudo] password for karen:  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 Package bcmwl-kernel-source is not installed, so not removed  
 Package broadcom-sta-common is not installed, so not removed  
 Package broadcom-sta-source is not installed, so not removed  
 The following packages were automatically installed and are no longer required:  
   sdparm  
 Use 'apt-get autoremove' to remove them.  
 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.  
 karen@laptop:~$ sudo apt-get install b43-fwcutter firmware-b43-installer  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 E: Couldn't find package firmware-b43-installer  
 karen@laptop:~$ sudo modprobe -rf ndiswrapper  
 karen@laptop:~$ sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk  
 Reading package lists... Done  
 Building dependency tree         
 Reading state information... Done  
 Package ndiswrapper-common is not installed, so not removed  
 Package ndiswrapper-utils-1.9 is not installed, so not removed  
 Package ndisgtk is not installed, so not removed  
 The following packages were automatically installed and are no longer required:  
   sdparm  
 Use 'apt-get autoremove' to remove them.  
 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.  
 karen@laptop:~$ sudo rm /etc/modprobe.d/ndiswrapper.conf  
 rm: cannot remove `/etc/modprobe.d/ndiswrapper.conf': No such file or directory  
 karen@laptop:~$  
 karen@laptop:~$  
 karen@laptop:~$ sudo rmmod -f dell-laptop  
 karen@laptop:~$ rfkill list all  
 0: phy0: Wireless LAN  
     Soft blocked: no  
     Hard blocked: no  
 karen@laptop:~$ sudo cat /var/log/syslog | grep -e iwl -e firmware -e wlan -e etwork | tail -n45  
 Mar  3 20:43:18 laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...  
 Mar  3 20:43:18 laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.  
 Mar  3 20:43:18 laptop NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit  
 Mar  3 20:43:19 laptop NetworkManager: <info>  (eth0): carrier now OFF (device state 7, deferring action for 4 seconds)  
 Mar  3 20:43:23 laptop NetworkManager: <info>  (eth0): device state change: 7 -> 2 (reason 40)  
 Mar  3 20:43:23 laptop NetworkManager: <info>  (eth0): deactivating device (reason: 40).  
 Mar  3 20:43:23 laptop NetworkManager: <info>  (eth0): canceled DHCP transaction, dhcp client pid 1739 
 Mar  3 20:43:24 laptop NetworkManager: <info>  (eth0): carrier now ON (device state 2)  
 Mar  3 20:43:24 laptop NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)  
 Mar  3 20:43:24 laptop NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'  
 Mar  3 20:43:24 laptop NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)  
 Mar  3 20:43:24 laptop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...  
 Mar  3 20:43:24 laptop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...  
 Mar  3 20:43:24 laptop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...  
 Mar  3 20:43:24 laptop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.  
 Mar  3 20:43:24 laptop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...  
 Mar  3 20:43:24 laptop NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)  
 Mar  3 20:43:24 laptop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.  
 Mar  3 20:43:24 laptop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.  
 Mar  3 20:43:24 laptop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.  
 Mar  3 20:43:24 laptop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...  
 Mar  3 20:43:24 laptop NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)  
 Mar  3 20:43:24 laptop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)  
 Mar  3 20:43:24 laptop NetworkManager: <info>  dhclient started with pid 1742  
 Mar  3 20:43:24 laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...  
 Mar  3 20:43:24 laptop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.  
 Mar  3 20:43:24 laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...  
 Mar  3 20:43:24 laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.  
 Mar  3 20:43:24 laptop NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit  
 Mar  3 20:43:28 laptop NetworkManager: <info>  DHCP: device eth0 state changed preinit -> reboot  
 Mar  3 20:43:28 laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...  
 Mar  3 20:43:28 laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...  
 Mar  3 20:43:28 laptop NetworkManager: <info>    address 192.168.1.7  
 Mar  3 20:43:28 laptop NetworkManager: <info>    prefix 24 (255.255.255.0)  
 Mar  3 20:43:28 laptop NetworkManager: <info>    gateway 192.168.1.1  
 Mar  3 20:43:28 laptop NetworkManager: <info>    nameserver '192.168.1.1'  
 Mar  3 20:43:28 laptop NetworkManager: nm_ip4_config_add_nameserver: assertion `nameserver != s' failed  
 Mar  3 20:43:28 laptop NetworkManager: <info>    nameserver '192.168.1.1'  
 Mar  3 20:43:28 laptop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...  
 Mar  3 20:43:28 laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.  
 Mar  3 20:43:28 laptop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...  
 Mar  3 20:43:29 laptop NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)  
 Mar  3 20:43:29 laptop NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.  
 Mar  3 20:43:29 laptop NetworkManager: <info>  Activation (eth0) successful, device activated.  
 Mar  3 20:43:29 laptop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.  
 karen@laptop:~$

---

### Post by mörgæs on 2013-03-03
10.04 is running out of support. Better to begin with a clean install of X/Lubuntu 12.10.

---

### Post by UltimateCat on 2013-03-03
Hi:

 	[**[COLOR=#C61919][B]mörgæs**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=939075") 	 
 						[IMG]http://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-online.png[/IMG] is right Ubuntu 10.04 Lucid Linux will no longer be supported.
[https://help.ubuntu.com/](https://help.ubuntu.com/)

If you still want to use 10.04 you might have to install NDIS Wrapper.
When I was running Ubuntu 10.04 Ultimate Edition helped me to installe Ndis Wrapper and until I did
my internet connection would not work.  I also had to blacklist the rtl 8169 driver as I had the rtl8168- -

If it were me I would download and install either
12.04   [http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Ubuntu_12.04_LTS_.28Precise_Pangolin.29](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Ubuntu_12.04_LTS_.28Precise_Pangolin.29)

Or 120.10 [https://help.ubuntu.com/12.10/index.html](https://help.ubuntu.com/12.10/index.html)

The current version of Lubuntu is:
12.10
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

Here's an article that a man wrote on How To get wireless working on the exact Dell that you have::KS
Hope it helps-:KS

[http://ofaolain.com/blog/2011/03/26/activating-wireless-on-dell-latitude-d610-with-ubuntu/](http://ofaolain.com/blog/2011/03/26/activating-wireless-on-dell-latitude-d610-with-ubuntu/)

Enjoy the rest of the weekend and enjoy your distro-

---

### Post by mörgæs on 2013-03-03
The text mentioned is overly complicated. Stay away from Ndiswrapper - just do the reinstall using wired internet access and report back.

---

### Post by karcat on 2013-03-04
i choose this one as i have used it before and to be honest the 12:10 does not install on my machine. maybe its too old.

---

### Post by mörgæs on 2013-03-04
Please run 
```
sudo lshw > lshw.txt
```

and post lshw.txt.

---

