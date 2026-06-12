---
title: "Help - WUSB600N and 9.10 32-bit"
date: 2010-03-03
forum: Networking &amp; Wireless
---

### Post by loaba on 2010-03-03
Hola everyone,

I have just installed a fresh copy of 9.10 on an older Compaq nc6000 laptop. I need some help getting my Linksys WUSB600N wireless adapter to function properly.

I have "half-way" connectivity, meaning that I can see (and connect to) my home wireless network but I can't connect to the internet (unless I use the wired connection). I have installed NDIS wrapper - no change

Any help would be much appreciated.

---

### Post by chili555 on 2010-03-03
With the device inserted, please run, in a terminal:```
lsusb
dmesg | grep rt2
```Thanks.

---

### Post by loaba on 2010-03-03
```
ubuntu@ubuntu:~$ lsusb
Bus 001 Device 004: ID 1737:0071 Linksys 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
ubuntu@ubuntu:~$ dmesg | grep rt2
[  236.956261] Registered led device: rt2800usb-phy0::radio
[  236.956290] Registered led device: rt2800usb-phy0::assoc
[  236.956315] Registered led device: rt2800usb-phy0::quality
[  236.957151] usbcore: registered new interface driver rt2800usb
[  237.600311] rt2800usb 1-2:1.0: firmware: requesting rt2870.bin
[  238.282552] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[  238.301559] usbcore: registered new interface driver rt2870
[ 5726.460873] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x1004 with error -19.
[ 5726.460889] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x1004 with error -19.
[ 5726.460902] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0208 with error -19.
[ 5726.460916] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0208 with error -19.
[ 5726.460929] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x1004 with error -19.
[ 5726.460942] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x1204 with error -19.
[ 5726.460955] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x1328 with error -19.
[ 5726.460968] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0208 with error -19.
[ 5726.460982] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0c failed for offset 0x0000 with error -19.
[ 5726.461002] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[ 5726.461115] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[ 5726.461227] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[ 5726.461340] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[ 5726.461452] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[ 5726.461564] phy0 -> rt2x00usb_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xf70ebd84
[ 5726.461579] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[ 5726.461691] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[ 5726.461803] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[ 5726.461916] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[ 5726.462028] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[ 5726.462139] phy0 -> rt2x00usb_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xf70ebd8c
[ 5726.462323] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[ 5726.462436] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[ 5726.462549] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[ 5726.462661] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[ 5726.462774] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[ 5726.462885] phy0 -> rt2x00usb_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xf70ebd94
[ 5726.462969] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[ 5726.463081] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[ 5726.463194] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[ 5726.463306] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[ 5726.463419] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[ 5726.463530] phy0 -> rt2x00usb_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xf70ebd94
[ 5726.463616] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[ 5726.463729] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[ 5726.463842] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[ 5726.463954] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[ 5726.464081] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[ 5726.464192] phy0 -> rt2x00usb_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xf70ebd94
[ 5726.464301] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0220 with error -19.
[ 5726.464315] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0220 with error -19.
[ 5726.464328] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0214 with error -19.
[ 5726.464341] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0214 with error -19.
[ 5726.464354] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0218 with error -19.
[ 5726.464367] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0218 with error -19.
[ 5726.464380] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x021c with error -19.
[ 5726.464393] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x021c with error -19.
[ 5726.464406] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x1300 with error -19.
[ 5726.464420] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x1300 with error -19.
[ 5726.464433] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0220 with error -19.
[ 5726.464446] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0220 with error -19.
[ 5726.464459] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0214 with error -19.
[ 5726.464472] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0214 with error -19.
[ 5726.464485] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0218 with error -19.
[ 5726.464498] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0218 with error -19.
[ 5726.464511] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x021c with error -19.
[ 5726.464524] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x021c with error -19.
[ 5726.464537] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x1304 with error -19.
[ 5726.464550] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x1304 with error -19.
[ 5726.464564] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0224 with error -19.
[ 5726.464577] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0224 with error -19.
[ 5726.464590] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0214 with error -19.
[ 5726.464603] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0214 with error -19.
[ 5726.464616] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0218 with error -19.
[ 5726.464629] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0218 with error -19.
[ 5726.464642] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x021c with error -19.
[ 5726.464655] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x021c with error -19.
[ 5726.464668] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x1308 with error -19.
[ 5726.464681] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x1308 with error -19.
[ 5726.464694] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0224 with error -19.
[ 5726.464708] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0224 with error -19.
[ 5726.464721] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0214 with error -19.
[ 5726.464734] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0214 with error -19.
[ 5726.464747] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0218 with error -19.
[ 5726.464760] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0218 with error -19.
[ 5726.464773] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x021c with error -19.
[ 5726.464786] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x021c with error -19.
[ 5726.464799] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x130c with error -19.
[ 5726.464812] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x130c with error -19.
[ 5987.970141] Registered led device: rt2800usb-phy1::radio
[ 5987.970196] Registered led device: rt2800usb-phy1::assoc
[ 5987.970251] Registered led device: rt2800usb-phy1::quality
[ 5988.032390] rt2800usb 1-2:1.0: firmware: requesting rt2870.bin
```


I am guessing there is a driver issue...

---

### Post by chili555 on 2010-03-03
> I am guessing there is a driver issue...Oh, my oh my, yes! Here is your device:> [COLOR="Blue"]1737[/COLOR]:[COLOR="Blue"]0071[/COLOR] Linksys Both rt2800usb and rt2870sta claim this device:> $ modinfo rt2800usb | grep 0071
alias:          usb:v[COLOR="Blue"]1737[/COLOR]p[COLOR="Blue"]0071[/COLOR]d*dc*dsc*dp*ic*isc*ip*
$ modinfo rt2870sta | grep 0071
alias:          usb:v[COLOR="Blue"]1737[/COLOR]p[COLOR="Blue"]0071[/COLOR]d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0071d*dc*dsc*dp*ic*isc*ip*As you can see from your *dmesg*, the only thing worse than having no driver is having two conflicting drivers fighting. Let's try to fix it:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add three lines:```
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
```Proofread carefully, save and close gedit.

Reboot. Is your wireless working?

---

### Post by loaba on 2010-03-03
And it works. :)

Thank you

---

### Post by Gmr Leon on 2010-03-15
```
ubuntu@ubuntu-desktop:~$ lsusb
Bus 001 Device 003: ID 0bc2:3000 Seagate RSS LLC 
Bus 001 Device 002: ID 1737:0071 Linksys 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
ubuntu@ubuntu-desktop:~$ dmesg | grep rt2
[   35.825062] Registered led device: rt2800usb-phy0::radio
[   35.825087] Registered led device: rt2800usb-phy0::assoc
[   35.825111] Registered led device: rt2800usb-phy0::quality
[   35.832214] usbcore: registered new interface driver rt2800usb
[   35.833524] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   35.848191] usbcore: registered new interface driver rt2870
[   37.011897] rt2800usb 1-1:1.0: firmware: requesting rt2870.bin
```

Decided to use this thread since it seemed rather recent, I take it this just means I need the rt2870 driver?

---

### Post by chili555 on 2010-03-15
> I take it this just means I need the rt2870 driver?Correct. However, you do not need all the others. Please complete the fix outlined in post #4 above.

---

### Post by Yondergod22 on 2010-03-15
I have the same problem as the original poster

lsusb:
```
taylor@taylor-desktop:~$ lsusb
Bus 001 Device 005: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)
Bus 001 Device 004: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 046d:c045 Logitech, Inc. Optical Mouse
Bus 002 Device 002: ID 045e:00dd Microsoft Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
(the netgear one is the one I had to use to post this, but it's realllllyyy slow and only works when it wants to)

dmesg | grep rt2 returns nothing

---

### Post by Gmr Leon on 2010-03-15
I gave that a shot, and it still doesn't connect. I think the main solution, which I've looked into, would be to get the driver, but I haven't had any of the methods mentioned [here]("http://ubuntuforums.org/showpost.php?p=6112069&postcount=1") or [here]("http://ubuntuforums.org/showpost.php?p=8898185&postcount=96") work yet. [URL="http://ubuntuforums.org/showpost.php?p=8898185&postcount=96"]
[/URL]

---

### Post by chili555 on 2010-03-16
> **Gmr Leon said:**
> I gave that a shot, and it still doesn't connect. I think the main solution, which I've looked into, would be to get the driver, but I haven't had any of the methods mentioned [here]("http://ubuntuforums.org/showpost.php?p=6112069&postcount=1") or [here]("http://ubuntuforums.org/showpost.php?p=8898185&postcount=96") work yet. [URL="http://ubuntuforums.org/showpost.php?p=8898185&postcount=96"]
[/URL]You *have* the driver, r2870sta. Didi you reboot after you did the blacklisting? What does this say after a reboot?```
dmesg | grep rt2
```Thanks.

---

### Post by chili555 on 2010-03-16
> **Yondergod22 said:**
> I have the same problem as the original poster

lsusb:
```
taylor@taylor-desktop:~$ lsusb
Bus 001 Device 005: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)
Bus 001 Device 004: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
--- snip ---

```
(the netgear one is the one I had to use to post this, but it's realllllyyy slow and only works when it wants to)

dmesg | grep rt2 returns nothingPlease try:```
sudo modprobe rtl8187
iwconfig
dmesg | grep rtl8
```Thanks.

Is your device labelled WUSB660N?

---

### Post by Yondergod22 on 2010-03-16
Thanks for the reply

iwconfig:
```
wlan4     IEEE 802.11bg  ESSID:"2WIRE087"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:95:85:EF:E1   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=48/100  Signal level:-47 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

dmesg | grep rtl8:
```
[   15.897206] phy0: hwaddr 00:18:4d:cf:74:09, RTL8187vB (default) V1 + rtl8225z2
[   15.897240] usbcore: registered new interface driver rtl8187
[  203.522665] rtl8187: 8187B chip detected. Support is EXPERIMENTAL, and could damage your
[  203.527940] phy1: hwaddr 00:14:d1:38:d7:79, RTL8187BvE V0 + rtl8225z2
[  316.957211] phy2: hwaddr 00:18:4d:cf:74:09, RTL8187vB (default) V1 + rtl8225z2
[  419.108675] phy3: hwaddr 00:18:4d:cf:74:09, RTL8187vB (default) V1 + rtl8225z2
[  511.843074] rtl8187: 8187B chip detected. Support is EXPERIMENTAL, and could damage your
[  511.848762] phy4: hwaddr 00:14:d1:38:d7:79, RTL8187BvE V0 + rtl8225z2
```

I should add that it works perfectly in my 8.04 live disk. 

Thank you.

---

### Post by chili555 on 2010-03-16
> wlan4     IEEE 802.11bg  ESSID:"2WIRE087"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:95:85:EF:E1   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=48/100 It looks like it's working; i.e. connected here. The signal strength looks like it's a bit far from the router, however it is still connected, or at least trying, at 54 Mbp/s. Please try:```
sudo iwconfig wlan4 rate auto
```If it is still balky, you might try:```
sudo iwconfig wlan4 rate 36M
```Is the behavior improved?

---

### Post by Gmr Leon on 2010-03-17
Apologies for the delay, here's the output:

```
ubuntu@ubuntu-desktop:~$ dmesg | grep rt2
[   23.785186] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   23.807476] usbcore: registered new interface driver rt2870
```

In case you request it: 

iwconfig:
```
ubuntu@ubuntu-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2870 Wireless  ESSID:"11n-AP"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by chili555 on 2010-03-17
Please do:```
sudo ifconfig ra0 up
```Now check the Network Manager icon, see if your network appears and connect.

---

### Post by dea.leal on 2010-03-18
Hello everyone, 
I am very very new to ubuntu, so please excuse me if I ask for some very basic help. I have a dual boot computer, with Windows XP and UBUNTU 9,1
I have read through 2 threads on the WUSB600N adapter. Some of the tips read like greek to me, though.
I have downloaded the WUSB600N.tar file. I have copied that and then extracted the file to my desktop.
I tried then going into the terminal and navigating to the folder where the files were extracted. I can't get past this: the computer says there is no such folder.
I have typed in "dir" to see a list of the directories, but it just won't work. 
Here is a print screen shot.
I would really appreciate it if anyone could help me.
Andrea.

---

### Post by bkratz on 2010-03-18
> **dea.leal said:**
> Hello everyone, 
I am very very new to ubuntu, so please excuse me if I ask for some very basic help. I have a dual boot computer, with Windows XP and UBUNTU 9,1
I have read through 2 threads on the WUSB600N adapter. Some of the tips read like greek to me, though.
I have downloaded the WUSB600N.tar file. I have copied that and then extracted the file to my desktop.
I tried then going into the terminal and navigating to the folder where the files were extracted. I can't get past this: the computer says there is no such folder.
I have typed in "dir" to see a list of the directories, but it just won't work. 
Here is a print screen shot.
I would really appreciate it if anyone could help me.
Andrea.

Welcome!

Here is a link to show how to get to the desktop from the command line

[http://ubuntuforums.org/showpost.php?p=3339279&postcount=2](http://ubuntuforums.org/showpost.php?p=3339279&postcount=2)

Here is also a link to learning about the command line ( it is a free pdf beginners guide).

[http://www.freesoftwaremagazine.com/articles/command_line_intro](http://www.freesoftwaremagazine.com/articles/command_line_intro)


Try ls   (LS in lowercase ) to see the current contents of the folder you are in (not dir) and cd changes directory. Look up . and .. also.



Also see

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

---

### Post by chili555 on 2010-03-18
Please insert the device, open a terminal and do:```
lsusb
```Do you see the same usb.id code as in post #4 above?> [COLOR="Blue"]1737:0071[/COLOR] Linksys If so, please follow the same steps as in post #4 and I am quite confident your device will work. If you have a different device or get stuck, please post back.

Edit: Before you try to compile a driver from scratch, please try the easy steps.

---

### Post by Yondergod22 on 2010-03-18
> **chili555 said:**
> It looks like it's working; i.e. connected here. The signal strength looks like it's a bit far from the router, however it is still connected, or at least trying, at 54 Mbp/s. Please try:```
sudo iwconfig wlan4 rate auto
```If it is still balky, you might try:```
sudo iwconfig wlan4 rate 36M
```Is the behavior improved?

The second one made it work. Thank you VERY much :D

EDIT: I take that back. It worked for about 15 then stopped :(
Do you have any other magical fixes?
Orr, should I try using ndiswrapper with the windows driver, thats how I used to get it to work. Would I have to blacklist the ubuntu one? How would I do that?

---

### Post by Gmr Leon on 2010-03-20
> **chili555 said:**
> Please do:```
sudo ifconfig ra0 up
```Now check the Network Manager icon, see if your network appears and connect.

The network shows up, and it appears to be connecting, then it subsequently drops. It doesn't even last fifteen minutes, as Yonder said his did.

---

### Post by chili555 on 2010-03-20
> EDIT: I take that back. It worked for about 15 then stopped
Do you have any other magical fixes?Please try:```
sudo iwconfig wlan4 rate 24M
sudo iwconfig wlan4 power on
```Please let us know the outcome.

---

### Post by Yondergod22 on 2010-03-21
It works, for about half an hour so far. But it is very laggy....but it's better than nothing. Thank you :)

---

### Post by Gmr Leon on 2010-03-21
Any clue regarding my situation Chili? Many thanks for your patience.

---

### Post by chili555 on 2010-03-21
> **Gmr Leon said:**
> The network shows up, and it appears to be connecting, then it subsequently drops. It doesn't even last fifteen minutes, as Yonder said his did.Let's take a peek at:```
iwconfig
sudo cat /var/log/syslog | grep -i network
```The last command will produce a lot of output, so try to find the place it gives up and disconnects and post about ten lines up to that point. Thanks.

---

### Post by Gmr Leon on 2010-03-21
Iwconfig:
```
ubuntu@ubuntu-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:"Expanded Probe."  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.447 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=91/100  Signal level:-66 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```This is what I get when I have it attempting to connect:
```
ubuntu@ubuntu-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:"Expanded Probe."  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.447 GHz  Access Point: 00:1E:E5:4F:78:26  
          Bit Rate:104 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=91/100  Signal level:-70 dBm  Noise level:-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```I think this is what you were asking for below, as it reappeared several times in the output:

```

Mar 21 15:52:16 ubuntu-desktop NetworkManager: <info>  Activation (ra0) Stage 4 of 5 (IP4 Configure Get) started...
Mar 21 15:52:16 ubuntu-desktop NetworkManager: <info>    address 192.168.1.101
Mar 21 15:52:16 ubuntu-desktop NetworkManager: <info>    prefix 24 (255.255.255.0)
Mar 21 15:52:16 ubuntu-desktop NetworkManager: <info>    gateway 192.168.1.1
Mar 21 15:52:16 ubuntu-desktop NetworkManager: <info>    nameserver '24.158.96.130'
Mar 21 15:52:16 ubuntu-desktop NetworkManager: <info>    nameserver '24.158.96.131'
Mar 21 15:52:16 ubuntu-desktop NetworkManager: <info>  Activation (ra0) Stage 4 of 5 (IP4 Configure Get) complete.
Mar 21 15:52:22 ubuntu-desktop NetworkManager: <info>  Device 'ra0' IP6 addrconf timed out or failed.
Mar 21 15:52:22 ubuntu-desktop NetworkManager: <info>  Activation (ra0) Stage 4 of 5 (IP6 Configure Timeout) scheduled...
Mar 21 15:52:22 ubuntu-desktop NetworkManager: <info>  Activation (ra0) Stage 4 of 5 (IP6 Configure Timeout) started...
Mar 21 15:52:22 ubuntu-desktop NetworkManager: <info>  (ra0): device state change: 7 -> 9 (reason 5)
Mar 21 15:52:22 ubuntu-desktop NetworkManager: <info>  Activation (ra0) failed for access point (Expanded Probe.)
Mar 21 15:52:22 ubuntu-desktop NetworkManager: <info>  Marking connection 'Auto Expanded Probe.' invalid.
Mar 21 15:52:22 ubuntu-desktop NetworkManager: <info>  Activation (ra0) failed.
```

---

### Post by chili555 on 2010-03-21
If you edit connections by right-clicking the Network Manager icon, select wireless, do you see an IPv6 tab? Is it set to Ignore? Please see attached.

---

### Post by Gmr Leon on 2010-03-21
It's set to automatic. 

Edit: I'll be bloody, I set it to ignore, and now it appears to be working wonderfully. I'll post again if it drops in a few minutes, but if you were going to tell me to set it to ignore then thank you! Actually, thank you for all of your help and patience over the past few days.

---

### Post by chili555 on 2010-03-21
> **Gmr Leon said:**
> It's set to automatic.Erm...could you try it at Ignore, please? That, IPv6, seems to be where it's stumbling:> Activation (ra0) Stage 4 of 5 (IP6 Configure Timeout) started...


---

### Post by Gmr Leon on 2010-03-21
That did the trick, as noted above, and many, many thanks for all of your assistance Chili. Without it, I would have just reverted to 9.04 instead.

---

### Post by Melano Chole on 2010-05-08
Dear friends,

I also try to make D-Link DWA-160 (Ralink 2870 chipset) wireless adapter working on Ubuntu 10.04 LTS. I have read this thread and followed the instructions, but the adapter doesn't work yet: it founds a wireless network (like it did before blacklist.conf was edited), asks a password and can not connect.

The following steps have been made:

1. /etc/modprobe.d/blacklist.conf edited as chili555 advised. After that, lsusb returns the following:

```
chole@chole-ubuntu:~$ lsusb
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0ac8:0328 Z-Star Microelectronics Corp. A4Tech PK-130MG
Bus 001 Device 004: ID 04d9:1400 Holtek Semiconductor, Inc. 
Bus 001 Device 003: ID 07d1:3c11 D-Link System 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

2. And that is what dmesg shows after installing the adapter in USB (modprobe.conf have been already edited):

```
[  521.477770] usb 1-1.2: new high speed USB device using ehci_hcd and address 6
[  521.586608] usb 1-1.2: configuration #1 chosen from 1 choice
[  521.588240] 
[  521.588242] 
[  521.588243] === pAd = fd232000, size = 566748 ===
[  521.588244] 
[  521.588247] <-- RTMPAllocAdapterBlock, Status=0
[  521.871154] <-- RTMPAllocTxRxRingMemory, Status=0
[  521.872943] -->RTUSBVenderReset
[  521.873058] <--RTUSBVenderReset
[  522.149179] --> Error 2 opening /etc/Wireless/RT3070STA/RT3070STA.dat
[  522.149183] 1. Phy Mode = 0
[  522.149185] 2. Phy Mode = 0
[  522.183463] RTMPSetPhyMode: channel is out of range, use first channel=1 
[  522.197315] 3. Phy Mode = 0
[  522.203099] MCS Set = 00 00 00 00 00
[  522.216939] <==== RTMPInitialize, Status=0
[  522.218791] 0x1300 = 00073200
[  527.238929] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 136 
```

3. After I try to rise up the connection, the following next strings appear in dmesg:

```
[  527.238929] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 136
[  532.214262] wlan0: no IPv6 routers present
[  547.786865] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 237
[  577.716627] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 136
[  597.265231] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 270
[  597.265423] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1) 
```

Please, pay attention **IPv6 is mentioned there.** I checked if IPv6 is turned to IGNORE in wlan settings, and it is.

4. iwconfig shows:

```
chole@chole-ubuntu:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RTxx70 Wireless  ESSID:""  Nickname:"RT3070STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: 00:21:91:0A:00:CD   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=10/100  Signal level:-58 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
```

5. And I entered sudo cat /var/log/syslog | grep -i network:

```
May  8 23:51:45 chole-ubuntu NetworkManager: <info>  (wlan0): driver does not support SSID scans (scan_capa 0x00).
May  8 23:51:45 chole-ubuntu NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'usb')
May  8 23:51:45 chole-ubuntu NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/2
May  8 23:51:45 chole-ubuntu NetworkManager: <info>  (wlan0): now managed
May  8 23:51:45 chole-ubuntu NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
May  8 23:51:45 chole-ubuntu NetworkManager: <info>  (wlan0): bringing up device.
May  8 23:51:46 chole-ubuntu NetworkManager: <info>  (wlan0): preparing device.
May  8 23:51:46 chole-ubuntu NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
May  8 23:51:46 chole-ubuntu NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
May  8 23:51:46 chole-ubuntu NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 42)
May  8 23:52:48 chole-ubuntu NetworkManager: <info>  Activation (wlan0) starting connection 'Auto Flavia'
May  8 23:52:48 chole-ubuntu NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
May  8 23:52:48 chole-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
May  8 23:52:48 chole-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
May  8 23:52:48 chole-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
May  8 23:52:48 chole-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
May  8 23:52:48 chole-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
May  8 23:52:48 chole-ubuntu NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
May  8 23:52:48 chole-ubuntu NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto Flavia' has security, but secrets are required.
May  8 23:52:48 chole-ubuntu NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
May  8 23:52:48 chole-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May  8 23:52:56 chole-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
May  8 23:52:56 chole-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
May  8 23:52:56 chole-ubuntu NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
May  8 23:52:56 chole-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
May  8 23:52:56 chole-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
May  8 23:52:56 chole-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
May  8 23:52:56 chole-ubuntu NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
May  8 23:52:56 chole-ubuntu NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto Flavia' has security, and secrets exist.  No new secrets needed.
May  8 23:52:56 chole-ubuntu NetworkManager: <info>  Config: added 'ssid' value 'Flavia'
May  8 23:52:56 chole-ubuntu NetworkManager: <info>  Config: added 'scan_ssid' value '1'
May  8 23:52:56 chole-ubuntu NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
May  8 23:52:56 chole-ubuntu NetworkManager: <info>  Config: added 'psk' value '<omitted>'
May  8 23:52:56 chole-ubuntu NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
May  8 23:52:56 chole-ubuntu NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
May  8 23:52:56 chole-ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May  8 23:52:56 chole-ubuntu NetworkManager: <info>  Config: set interface ap_scan to 1
May  8 23:52:56 chole-ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  inactive -> scanning
May  8 23:53:01 chole-ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
May  8 23:53:06 chole-ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
May  8 23:53:06 chole-ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
May  8 23:53:11 chole-ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
May  8 23:53:16 chole-ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
May  8 23:53:16 chole-ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
May  8 23:53:21 chole-ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
May  8 23:53:26 chole-ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
May  8 23:53:26 chole-ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
May  8 23:53:31 chole-ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
May  8 23:53:36 chole-ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
May  8 23:53:36 chole-ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
May  8 23:53:37 chole-ubuntu NetworkManager: <info>  wlan0: link timed out.
May  8 23:53:41 chole-ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
May  8 23:53:46 chole-ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
May  8 23:53:46 chole-ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
May  8 23:53:51 chole-ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
May  8 23:53:56 chole-ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
May  8 23:53:56 chole-ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
May  8 23:53:57 chole-ubuntu NetworkManager: <info>  Activation (wlan0/wireless): association took too long.
May  8 23:53:57 chole-ubuntu NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
May  8 23:53:57 chole-ubuntu NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets
May  8 23:53:57 chole-ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
May  8 23:54:05 chole-ubuntu NetworkManager: <info>  (wlan0): device state change: 6 -> 9 (reason 7)
May  8 23:54:05 chole-ubuntu NetworkManager: <info>  Activation (wlan0) failed for access point (Flavia)
May  8 23:54:05 chole-ubuntu NetworkManager: <info>  Marking connection 'Auto Flavia' invalid.
May  8 23:54:05 chole-ubuntu NetworkManager: <info>  Activation (wlan0) failed.
May  8 23:54:05 chole-ubuntu NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
May  8 23:54:05 chole-ubuntu NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
```

I suggest the problem in IPv6 here, but have no idea how to fix the problem. Another suggestion is this string in dmesg: 

*[  522.149179] --> Error 2 opening /etc/Wireless/RT3070STA/RT3070STA.dat*

I'll appreciate for any help!

---

### Post by chili555 on 2010-05-08
> [ 522.149179] --> Error 2 opening /etc/Wireless/RT3070STA/RT3070STA.datDo you have any files in /etc/Wireless? If you have a directory called RT2870STA and a file within it called RT2870STA.dat, you can do:```
sudo mkdir /etc/Wireless/RT3070STA
sudo cp /etc/Wireless/RT2870STA/RT2870STA.dat /etc/Wireless/RT3070STA
sudo mv /etc/Wireless/RT3070STA/RT2870STA.dat /etc/Wireless/RT3070STA/RT3070STA.dat
```Now reboot and see if things improve.

You may need to edit /etc/Wireless/RT3070STA/RT3070STA.dat to suit your needs. There are instructions in the readme in the file you used to compile the driver.

---

### Post by Melano Chole on 2010-05-12
Thank you for advice, Chili. Actually, I didn't compile the driver; the logs and messages were obtained with the default driver included in Ubuntu 10.04 LTS. But I found the file (RT2870STA.dat) in the sources downloaded from Ralink, edited it and put in /etc/Wireless/RT3070 directory. Of course, I renamed the file to RT3070STA.dat also. But, anyway it doesn't work. Here are the .dat file and dmesg:

RT3070STA.dat (entire):
```
#The word of "Default" must not be removed
Default
CountryRegion=5
CountryRegionABand=7
CountryCode=
ChannelGeography=1
SSID=Flavia
NetworkType=Infra
WirelessMode=5
Channel=0
BeaconPeriod=100
TxPower=100
BGProtection=0
TxPreamble=0
RTSThreshold=2347
FragThreshold=2346
TxBurst=1
PktAggregate=0
WmmCapable=1
AckPolicy=0;0;0;0
AuthMode=WPA2PSK
EncrypType=AES
WPAPSK=
DefaultKeyID=1
Key1Type=0
Key1Str=
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
PSMode=CAM
AutoRoaming=0
RoamThreshold=70
APSDCapable=0
APSDAC=0;0;0;0
HT_RDG=1
HT_EXTCHA=0
HT_OpMode=0
HT_MpduDensity=4
HT_BW=1
HT_BADecline=0
HT_AutoBA=1
HT_AMSDU=0
HT_BAWinSize=64
HT_GI=1
HT_MCS=33
HT_MIMOPSMode=3
HT_DisallowTKIP=1
IEEE80211H=0
TGnWifiTest=0
WirelessEvent=0
CarrierDetect=0
AntDiversity=0
BeaconLostTime=4
PSP_XLINK_MODE=0 
```

I changed here SSID to my Wireless network's name. In Windows 7 the network's Authentication type is WPA2 and encryption type is AES, so I turned AuthMode to WPA2PSK and EncrypType to AES. This is it.

$: dmesg
```
[  229.367961] usb 1-1.2: new high speed USB device using ehci_hcd and address 6
[  229.476289] usb 1-1.2: configuration #1 chosen from 1 choice
[  229.477897] 
[  229.477899] 
[  229.477900] === pAd = feb32000, size = 566748 ===
[  229.477901] 
[  229.477904] <-- RTMPAllocAdapterBlock, Status=0
[  229.761964] <-- RTMPAllocTxRxRingMemory, Status=0
[  229.763582] -->RTUSBVenderReset
[  229.763703] <--RTUSBVenderReset
[  230.041847] RTMPReadParametersHook::(WPAPSK key-string required 8 ~ 64 characters!)
[  230.041938] I/F(wlan0) Key1Str is Invalid key length! KeyLen = 0!
[  230.041984] I/F(wlan0) Key2Str is Invalid key length! KeyLen = 0!
[  230.042031] I/F(wlan0) Key3Str is Invalid key length! KeyLen = 0!
[  230.042079] I/F(wlan0) Key4Str is Invalid key length! KeyLen = 0!
[  230.043361] 1. Phy Mode = 5
[  230.043363] 2. Phy Mode = 5
[  230.079148] RTMPSetPhyMode: channel is out of range, use first channel=1 
[  230.097090] 3. Phy Mode = 5
[  230.108357] MCS Set = ff ff 00 00 01
[  230.121195] <==== RTMPInitialize, Status=0
[  230.123843] 0x1300 = 00064300
[  235.165027] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 136
[  240.351045] wlan0: no IPv6 routers present 
```

Of course, I restarted the system everytime I changed the system. IPv6 is still turned to "Ignore" in the network configuration...

---

### Post by chili555 on 2010-05-12
Your dmesg says:> WPAPSK key-string required 8 ~ 64 characters!And your dat file says:> WPAPSK=
Please fill in the blank and then reboot. You might also add your country code and channel in the required spaces; US? 6? Does it work as expected?

---

### Post by Melano Chole on 2010-05-12
> **chili555 said:**
> Please fill in the blank and then reboot. You might also add your country code and channel in the required spaces; US? 6? Does it work as expected?
What exactly should I put in the WPAPSK string? My password to the wireless network? My country is Ukraine and I don't know which code fits Ukraine. I suppose, it's not a phone code :) Channel is the same. I have never adjusted these parameters in Windows, so I need an advice. Thank you in advance!

---

### Post by chili555 on 2010-05-12
> What exactly should I put in the WPAPSK string? My password to the wireless network?Yes, exactly. Your country code is UA. It may negotiate the channel by itself. Try these settings and reboot.

---

### Post by Melano Chole on 2010-05-12
I entered CountryCode as you advised along with a Password in WPAPSK line, and nothing changed. Then I payed attention to the following strings in dmesg:
```
[   47.989827] I/F(wlan0) Key4Str is Invalid key length! KeyLen = 0! 
```
So I also typed the Password to one of the lines Key*Str. Now my RT3080STA.dat looks like:
```
#The word of "Default" must not be removed
Default
CountryRegion=5
CountryRegionABand=7
CountryCode=UA
ChannelGeography=1
SSID=Flavia
NetworkType=Infra
WirelessMode=5
Channel=0
BeaconPeriod=100
TxPower=100
BGProtection=0
TxPreamble=0
RTSThreshold=2347
FragThreshold=2346
TxBurst=1
PktAggregate=0
WmmCapable=1
AckPolicy=0;0;0;0
AuthMode=WPA2PSK
EncrypType=AES
WPAPSK=<my_password>
DefaultKeyID=1
Key1Type=0
Key1Str=<my_passwoed>
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
PSMode=CAM
AutoRoaming=0
RoamThreshold=70
APSDCapable=0
APSDAC=0;0;0;0
HT_RDG=1
HT_EXTCHA=0
HT_OpMode=0
HT_MpduDensity=4
HT_BW=1
HT_BADecline=0
HT_AutoBA=1
HT_AMSDU=0
HT_BAWinSize=64
HT_GI=1
HT_MCS=33
HT_MIMOPSMode=3
HT_DisallowTKIP=1
IEEE80211H=0
TGnWifiTest=0
WirelessEvent=0
CarrierDetect=0
AntDiversity=0
BeaconLostTime=4
PSP_XLINK_MODE=0 
```
And after reboot dmesg returnes:
```
[   47.304834] usb 1-1.2: new high speed USB device using ehci_hcd and address 6
[   47.413532] usb 1-1.2: configuration #1 chosen from 1 choice
[   47.415042] 
[   47.415043] 
[   47.415043] === pAd = fd352000, size = 566748 ===
[   47.415044] 
[   47.415045] <-- RTMPAllocAdapterBlock, Status=0
[   47.691375] <-- RTMPAllocTxRxRingMemory, Status=0
[   47.693109] -->RTUSBVenderReset
[   47.693215] <--RTUSBVenderReset
[   47.989769] I/F(wlan0) Key1Str is Invalid key length! KeyLen = 23!
[   47.989788] I/F(wlan0) Key2Str is Invalid key length! KeyLen = 0!
[   47.989807] I/F(wlan0) Key3Str is Invalid key length! KeyLen = 0!
[   47.989827] I/F(wlan0) Key4Str is Invalid key length! KeyLen = 0!
[   47.990668] 1. Phy Mode = 5
[   47.990668] 2. Phy Mode = 5
[   48.027593] RTMPSetPhyMode: channel is out of range, use first channel=1 
[   48.046665] 3. Phy Mode = 5
[   48.058568] MCS Set = ff ff 00 00 01
[   48.072402] <==== RTMPInitialize, Status=0
[   48.074921] 0x1300 = 00064300
[   53.104771] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 136 
```

---

### Post by Melano Chole on 2010-05-18
Hello,

Is there any suggestions?

---

### Post by Melano Chole on 2010-05-18
Hello All,

I just want to say I gave up to make the default driver working and compiled a new one using this great toturial: [http://ubuntuforums.org/showthread.php?t=1342593&highlight=dwa+160](http://ubuntuforums.org/showthread.php?t=1342593&highlight=dwa+160)

Thank you all and, espetially, **chili555** for help and patience!

---

