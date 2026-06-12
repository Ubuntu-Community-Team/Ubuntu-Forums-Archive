---
title: "what am i doing wrong? FATAL: Error inserting ndiswrapper..."
date: 2006-05-04
forum: Networking &amp; Wireless
---

### Post by 0okami on 2006-05-04
i have been trying to follow instructions found eveywhere on the forums and im at the point where im stuck now... if anyone has any sugestions to try next please inform me. 

basicly, im trying to get my dwl-g510 working. 

```

ookami@navi:~$ lspci | grep 802.11
0000:01:06.0 Network controller: Broadcom Corporation BCM4301 802.11b (rev 02)
0000:01:08.0 Ethernet controller: Marvell Technology Group Ltd. Marvell W8300 802.11 Adapter (rev 07)
ookami@navi:~$


' this shows DWL-g510 card info
ookami@navi:~$ lspci -n | grep 0000:01:08.0
0000:01:08.0 0200: 11ab:1fa6 (rev 07)
ookami@navi:~$

' this shows Linksys wmp11 wifi card info 
ookami@navi:~$ lspci -n | grep 0000:01:06.0
0000:01:06.0 0280: 14e4:4301 (rev 02)
ookami@navi:~$


' this shows ndiswrapper being installed
ookami@navi:~/Desktop$ sudo dpkg -i ndiswrapper-utils_1.8-0ubuntu2_i386.deb
Password: ***************
Selecting previously deselected package ndiswrapper-utils.
(Reading database ... 68056 files and directories currently installed.)
Unpacking ndiswrapper-utils (from ndiswrapper-utils_1.8-0ubuntu2_i386.deb) ...
Setting up ndiswrapper-utils (1.8-0ubuntu2) ...
ookami@navi:~/Desktop$


' this shows windows XP driver for the DWL-g510
ookami@navi:~/Desktop/WinXP$ ls
mrv8k51.inf  MRV8K51.sys
ookami@navi:~/Desktop/WinXP$


' this shows installation of driver report odd error
ookami@navi:~/Desktop/WinXP$ sudo ndiswrapper -i mrv8k51.inf
Installing mrv8k51
Parse error in inf. Unable to find section W8100PCI.zerocfg
Parse error in inf. Unable to find section W8100PCI.zerocfg
Parse error in inf. Unable to find section W8100PCI.zerocfg


' checking to see if it actually installed... looks "ok"
ookami@navi:~/Desktop/WinXP$ ndiswrapper -l
Installed ndis drivers:
mrv8k51         driver present, hardware present
ookami@navi:~/Desktop/WinXP$


' so I proceed to follow more steps found online... 
ookami@navi:~/Desktop/WinXP$ sudo ndiswrapper -m
Adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper
ookami@navi:~/Desktop/WinXP$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-10-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted
ookami@navi:~/Desktop/WinXP$

' this is me trying some guess work...
ookami@navi:~/Desktop/WinXP$ sudo ndiswrapper -d 11ab:1fa6 mrv8k51
Driver 'mrv8k51' is used for '11AB:1FA6'
ookami@navi:~/Desktop/WinXP$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-10-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted
ookami@navi:~/Desktop/WinXP$


'this is me frustrated
...wtf?... *puzzled* now what? 

```

---

### Post by 0okami on 2006-05-04
ok, looks like i got it sorted out. I removed ndiswrapper which was aparently a newer version? Or maybe i was doing it wrong by using the XP driver? 

Anyway, I removed: 
ndiswrapper-utils_1.8-0ubuntu2_i386.deb

```

ookami@navi:~/Desktop/dwlg510_driver_100/Driver/manual/Win98$ sudo apt-get remove ndiswrapper-utils
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  ndiswrapper-utils
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 139kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 68068 files and directories currently installed.)
Removing ndiswrapper-utils ...

```

And then,  I added the ndiswrapper which was found in the pool on the original ubintu 5.10 CD: 
ndiswrapper-utils_1.1-4ubuntu2_i386.deb

```

ookami@navi:~/Desktop$ sudo dpkg -i ndiswrapper-utils_1.1-4ubuntu2_i386.deb
Selecting previously deselected package ndiswrapper-utils.
(Reading database ... 68056 files and directories currently installed.)
Unpacking ndiswrapper-utils (from ndiswrapper-utils_1.1-4ubuntu2_i386.deb) ...
Setting up ndiswrapper-utils (1.1-4ubuntu2) ...

```


And then from there, I browsed into the win98 folder of the drivers from a zip pack called: dwlg510_driver_100.zip
and installed the win98 driver which did not spit out any errors. 

```

ookami@navi:~/Desktop/dwlg510_driver_100/Driver/manual/Win98$ sudo ndiswrapper -i mrv8k51.inf Installing mrv8k51

```


I verified that it was in fact installed and proceeded to modprobe it. No more fatal error! ^_^

```
ookami@navi:~/Desktop/dwlg510_driver_100/Driver/manual/Win98$ ndiswrapper -l
Installed ndis drivers:
mrv8k51 driver present, hardware present
ookami@navi:~/Desktop/dwlg510_driver_100/Driver/manual/Win98$ sudo modprobe ndiswrapper
```

I ussed the command iwconfig and behold!!! its working. 
```

ookami@navi:~/Desktop/dwlg510_driver_100/Driver/manual/Win98$ iwconfig
lo        no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"ookami_1"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:10:77:ED:CB
          Bit Rate:54 Mb/s   Sensitivity=-200 dBm
          RTS thr:2346 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-68 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:36  Invalid misc:11   Missed beacon:0

ookami@navi:~/Desktop/dwlg510_driver_100/Driver/manual/Win98$

```
 
I looked into the GUI ... 
system->administration->networking.
and the interface is now listed.

---

### Post by DavidFourer on 2006-05-12
I

---

