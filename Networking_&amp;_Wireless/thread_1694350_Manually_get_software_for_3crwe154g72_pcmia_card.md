---
title: "Manually get software for 3crwe154g72 pcmia card"
date: 2011-02-24
forum: Networking &amp; Wireless
---

### Post by jjsh on 2011-02-24
I'm in a bit of a pickle. I've installed Xubuntu on an old Compag laptop that doesn't have any ethernet or wireless built in. It does have a 3com pcmia wireless card, however.

lspci lists it as 3crwe154g72, and I'm hoping that enabling the restricted drivers will get the right firmware and driver for this card. However, with no internet access, I can't do this!

Any ideas of how or where I can download the required files on a working machine and stick them on a usb stick, or something, to get this working?

---

### Post by chili555 on 2011-02-24
Please run these commands:```
lspci -nn
```We need the product ID, it will be in the form of 1233:abcd. Also:```
lsmod | grep p54
```Is the module p54pci loaded? If so, then run:```
dmesg | grep p54
```Does it want firmware? Please post the results.

---

### Post by jjsh on 2011-02-24
Thanks for the reply, much appreciated. Here's my outputs; 


**lspci -nn**

03:00.0 Network controller [0280]: 3Com Corporation 3com 3CRWE154G72 [Office Connect Wireless LAN Adapter] [10b7:6001] (rev 01)

**lsmod | grep p54**


p54pci                  7146  0 
p54common              24921  1 p54pci
led_class               2864  1 p54common
mac80211              204922  2 p54pci,p54common
cfg80211              126485  2 p54common,mac80211

**dmesg | grep p54**

[   21.150569] p54pci 0000:03:00.0: enabling device (0000 -> 0002)
[   21.150596] p54pci 0000:03:00.0: PCI INT A -> Link[LNKA] -> GSI 10 (level, low) -> IRQ 10
[   21.150616] p54pci 0000:03:00.0: setting latency timer to 64
[   21.150709] p54pci 0000:03:00.0: firmware: requesting isl3886pci
[   21.194837] p54pci 0000:03:00.0: Cannot find firmware (isl3886pci)
[   21.212119] p54pci 0000:03:00.0: firmware: requesting isl3886
[   21.229810] p54pci 0000:03:00.0: PCI INT A disabled
[   21.229829] p54pci: probe of 0000:03:00.0 failed with error -2


All advice welcome!

---

### Post by chili555 on 2011-02-24
Pretty good guess, eh? Here is a file attached you can get with a USB drive. Drag and drop it to the desktop of the Ubuntu machine. Right-click it and select 'Extract here.' Now in a terminal, do:```
cd Desktop
sudo cp isl3886pci /lib/firmware
```Reboot and let us have your report.

---

### Post by jjsh on 2011-02-24
OK, here's what I get ~ Downloaded zip file onto a usb stick, transferred and extracted to desktop. Switched to the desktop directory as instructed (checked this with an 'ls'), and executed the following, with below results;

sudo cp isl3886pci /lib/firmware

{prompts for password}

cp: cannot stat `isl3886pci': No such file or directory


I've checked, and there is an isl3886pci file in Desktop/lib/firmware.

I take it that isn't what was meant to happen :D

---

### Post by jjsh on 2011-02-24
Hang on, I think I got it, I'm meant to be copying the file in Desktop/lib/firmware into /lib/firmware. Done that, re-booting....

---

### Post by jjsh on 2011-02-24
..... and here I am talking to you on an internet enabled laptop from the stone ages :P

Thanks for your help, chili555, really, really appreciated.

---

### Post by chili555 on 2011-02-24
Good job! I think we have helped a few searchers, too. Have fun!

---

### Post by jjsh on 2011-02-24
How do I mark this topic as solved? It might be the home brew, but I can't find that option anywhere :D

---

### Post by chili555 on 2011-02-24
> **jjsh said:**
> How do I mark this topic as solved? It might be the home brew, but I can't find that option anywhere :DAt the top it says _**[COLOR="Red"]Thread Tools[/COLOR]**_. Drop down and select mark as solved.

---

### Post by gyyug78fg87ogguiioioioioi on 2011-02-26
i also get 
cp: cannot stat `isl3886pci': No such file or directory
what can i do?

[jjsh]("http://ubuntuforums.org/member.php?u=543095") can you tell me how you figured it out?

---

### Post by chili555 on 2011-02-26
Please post:```
ls Desktop
ls Desktop/lib/firmware
```Thanks.

---

### Post by gyyug78fg87ogguiioioioioi on 2011-02-26
it says 
ls: cannot access Desktop: No such file or directory
:confused:

---

### Post by jjsh on 2011-02-26
in my case, the firmware file was extracted to a /lib/firmware directory on my desktop, and it needs to be transfered into your actual /lib/firmware directory. So what I did was navigate to the directory on the desktop ( cd /Desktop/lib/firmware ) then run the copy command that chili gave from there (sudo cp etc etc)

sorry for the poor punctionation, spelling,etc, I'm typing this from my mobile!

---

### Post by chili555 on 2011-02-26
:confused: indeed!

Please do and post:```
cd ~
ls
cd Desktop
ls
```You did drag and drop the zip file to your desktop and extract it, didn't you?????????????

---

### Post by gyyug78fg87ogguiioioioioi on 2011-02-26
ok that commands worked but what do i do now?
i extracted the folder to the desktop, not the zip

---

### Post by chili555 on 2011-02-26
Go to post #4 above. Grab the zip file I attached. I assume it's on another computer, since the wireless doesn't work on yours. In either case, get it to the desktop of the computer that has the not working wireless. On your desktop, right-click the zip file and select 'Extract Here.' A folder will be created with the strange name of lib. Don't worry, we'll take care of it.

Now, open the terminal and type each command in order and press Enter after each one. At the end reboot and tell us if your wireless is working.

Here we go:```
cd Desktop/lib/firmware
sudo cp isl3886pci /lib/firmware
```Now reboot and give us your report.

We love your user name, by the way.

---

### Post by gyyug78fg87ogguiioioioioi on 2011-02-26
> **chili555 said:**
> Now, open the terminal and type each command in order and press Enter after each one. At the end reboot and tell us if your wireless is working.

Here we go:```
cd Desktop/lib/firmware
sudo cp isl3886pci /lib/firmware
```Now reboot and give us your report.

We love your user name, by the way.
wich commands are u exacly taking about, is there others than those 2?
i just did all this what u said, and wrote those 2 commands and i still getting ```
bash: cd: Desktop/lib/wirmware: No such file or directory
```and yeah it is on a other computer not this i am writing here on..
 
i also have had this "cant find" problems even the files was there before on another computer when i was trying to install drivers for screen, had to give up

---

### Post by chili555 on 2011-02-26
> bash: cd: Desktop/lib/[COLOR="Red"]w[/COLOR]irmware: No such file or directoryIs it also not found if you do:```
cd Desktop/lib/[COLOR="Red"]f[/COLOR]irmware
```> wich commands are u exacly taking about, is there others than those 2?Nope, just these two.

---

### Post by gyyug78fg87ogguiioioioioi on 2011-02-26
yeah still not found..... that one i just wrote wrong because i dident copy that i had to manualy write what i get back from the other computer

---

### Post by chili555 on 2011-02-26
Please check private messages at the top of the forum.

---

### Post by chili555 on 2011-02-26
So the answer was that gyyug78fg87ogguiioioioioi's sytem is in Norwegian. When we did:```
cd Skrivebord/lib/firmware
sudo cp isl3886pci /lib/firmware
```and then rebooted, his wireless worked.

The lesson learned is that Desktop may be called something else in your language on your system. Please adapt to my US English instructions.

---

### Post by dsat on 2011-03-04
Hi,

Thank you all for setup with 3crwe154g72!

My WLAN also works now :)

Additional info:
The ziped firmware from chili555 has caused problems. The speed was going up and down, also pings in the local network.
I have searched for isl3886pci and found a maybe newer on:
> 
wget -O isl3886pci [http://daemonizer.de/prism54/prism54-fw/fw-softmac/2.13.25.0.arm](http://daemonizer.de/prism54/prism54-fw/fw-softmac/2.13.25.0.arm)
sudo cp isl3886pci /lib/firmware/.

This firmware is a little bit bigger one, and the WLAN connect is constant now!

======================

Current ubuntu release: This driver doesn't work on ubuntu natty :( May you have some suggestions

---

### Post by dsat on 2011-05-15
This thread isn't solved for Ubuntu 11.04 (Natty).

I haven't seen no chance, to get the 3crwe154g72 pcmia card up in Natty!

What I have been tested for this card:

* Firmwares with p54pci and old prism54 from
   [http://daemonizer.de/prism54/prism54-fw/](http://daemonizer.de/prism54/prism54-fw/)

* I have also extract the firmware from windows original driver with fwextract from
  [http://lekernel.net/prism54/misc.html](http://lekernel.net/prism54/misc.html)

It's possible to run with ndiswrapper, but there is no WPA2 support per default.

3com was also swallowed by HP, which doesn't provide any information for this card.

I have spend a lot of hours, without a possible connect to a WPA(2) based router. 

If there is someone out, who have a 3crwe154g72 ready card with Natty please post!

---

### Post by chili555 on 2011-05-15
Have you tried the firmware in linux-firmware-nonfree?```
sudo apt-get install linux-firmware-nonfree
```

---

### Post by lnappa on 2011-06-05
Hi,

No luck with this adapter after upgrading to Natty. Everything seem Ok, but I am unable to connect to any wireless network I have tried so far. Any ideas?

Code:
$ uname -a
Linux amanda 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux
$ sudo apt-get install linux-firmware-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-firmware-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
$ sudo lspci | grep 3CRWE154G72
03:00.0 Network controller: 3Com Corporation 3com 3CRWE154G72 [Office Connect Wireless LAN Adapter] (rev 01)
$ sudo lsmod | grep p54
p54pci                 17054  0 
p54common              32371  1 p54pci
crc_ccitt              12595  1 p54common
mac80211              257001  2 p54pci,p54common
cfg80211              156212  2 p54common,mac80211
$ sudo dmesg | grep p54
[   31.099670] p54pci 0000:03:00.0: enabling device (0000 -> 0002)
[   31.099694] p54pci 0000:03:00.0: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[   31.099717] p54pci 0000:03:00.0: setting latency timer to 64
[   31.166356] ieee80211 phy0: p54 detected a LM86 firmware
[   31.166365] p54: rx_mtu reduced from 3240 to 2376
[   32.341580] Registered led device: p54-phy0::assoc
[   32.341761] Registered led device: p54-phy0::tx
[   32.341928] Registered led device: p54-phy0::rx
[   32.342107] Registered led device: p54-phy0::radio
[   32.342124] p54pci 0000:03:00.0: is registered as 'phy0'
$ sudo rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:0d:54:a2:50:44  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
$ sudo iwlist wlan0 scanning
wlan0     Scan completed :
          Cell 01 - Address: 00:1C:F0:5F:CC:71
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"Some wlan network in the neighbourhood"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000011fffc835180
                    Extra: Last beacon: 212ms ago
                    IE: Unknown: 001C48616E73652073697474207472E5646CF87365206E6574747665726B
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD070050F202000100
                    IE: Unknown: DD1E00904C334C101FFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340100070000000F000000000000000000000000000000
                    IE: Unknown: 2D1A6C101FFFFF000000000000000000000000000004000000000000
                    IE: Unknown: 3D160100000000000F000000000000000000000000000000
                    IE: Unknown: DD0E0050F204104A0001101044000102

---

### Post by chili555 on 2011-06-05
> $ sudo iwlist wlan0 scanning
wlan0 Scan completed :
Cell 01 - Address: 00:1C:F0:5F:CC:71
Channel:1
Frequency:2.412 GHz (Channel 1)
[COLOR="Red"]Quality=20/70[/COLOR] Signal level=-90 dBm
Encryption keyn
ESSID:"Some wlan network in the neighbourhood"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=000011fffc835180
Extra: Last beacon: 212ms ago
IE: Unknown: 001C48616E73652073697474207472E5646CF87365206E6574 747665726B
IE: Unknown: 010482848B96
IE: Unknown: 030101
IE: Unknown: 050400010000
IE: Unknown: 2A0100
IE: Unknown: 32080C1218243048606C
IE: IEEE 802.11i/[COLOR="Red"]WPA2 Version 1[/COLOR]
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK
IE: [COLOR="Red"]WPA Version 1[/COLOR]
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK
IE: Unknown: DD070050F202000100
IE: Unknown: DD1E00904C334C101FFFFF0000000000000000000000000000 00000000000000
IE: Unknown: DD1A00904C340100070000000F000000000000000000000000 000000
IE: Unknown: 2D1A6C101FFFFF000000000000000000000000000004000000 000000
IE: Unknown: 3D160100000000000F000000000000000000000000000000
IE: Unknown: DD0E0050F204104A0001101044000102This network will be difficult to impossible to connect to because of signal strength. Once networks get down towards 40/70 they are just to weak to get and most importantly, stay connected.

As well, either Network Manager, wpa_supplicant or the driver has trouble with WPA and WPA2 mixed networks. If this is really somewhere in the neighborhood, you probably have no option to change it to WPA2 only.

---

### Post by lnappa on 2011-06-05
Thanks for looking in to the issue, and sorry for providing confusing information. The listed network is not my network, it is just the only one that gets listed. My networks are hidden, at channel 9 and 13 and has shows a strenght of 50-65% when dualbooting with XP. It has worked fine with all releases up to and including Maverick.

---

### Post by chili555 on 2011-06-05
> **lnappa said:**
> Thanks for looking in to the issue, and sorry for providing confusing information. The listed network is not my network, it is just the only one that gets listed. My networks are hidden, at channel 9 and 13 and has shows a strenght of 50-65% when dualbooting with XP. It has worked fine with all releases up to and including Maverick.We might just try:```
sudo ifconfig wlan0 down
sudo rmmod -f p54common
sudo modprobe p54common nohwcrypt=1
sudo ifconfig wlan0 up
```If it works, we can make it permanent by writing one .conf file.

---

### Post by lnappa on 2011-06-05
Still no luck.
```
$ sudo ifconfig wlan0 down
$ sudo rmmod -f p54common
ERROR: Removing 'p54common': Resource temporarily unavailable

```No change otherwise.

---

### Post by chili555 on 2011-06-05
> **lnappa said:**
> Still no luck.
```
$ sudo ifconfig wlan0 down
$ sudo rmmod -f p54common
ERROR: Removing 'p54common': Resource temporarily unavailable

```No change otherwise.Let's write the .conf file anyway, reboot and see if there is improvement:```
sudo gedit /etc/modprobe.d/p54common.conf
```Add one line:```
options p54common nohwcrypt=1
```Proofread carefully, save and close gedit. Reboot and tell us if there is any improvement.

---

### Post by lnappa on 2011-06-05
I am afraid I am still out of luck. No change.
```
$ ls -l /etc/modprobe.d/p54common.conf 
-rw-r--r-- 1 root root 31 2011-06-05 18:15 /etc/modprobe.d/p54common.conf
$ cat /etc/modprobe.d/p54common.conf 
options p54common nohwcrypt=1

```

---

### Post by chili555 on 2011-06-05
I am very sorry; I'm out of ideas.

---

### Post by lnappa on 2011-06-05
Thanks for your help. Do you think a bug report somewhere would help?

Did some more testing if this would give any hints.

Took a spare WRT54G with DD-WRT v24-sp2 and configured an unencrypted AP which got detected:

```
$ sudo iwlist wlan0 scanning
  ...
          Cell 02 - Address: 00:16:B6:3E:51:06
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:off
                    ESSID:"amanda"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000212f5183
                    Extra: Last beacon: 128ms ago
                    IE: Unknown: 0006616D616E6461
                    IE: Unknown: 010882848B9624B0486C
                    IE: Unknown: 030103
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32048C129860
                    IE: Unknown: DD090010180200F0000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

```But, still no connection:

```
$ tail -f /var/log/syslog
Jun  5 20:03:44 amanda NetworkManager[439]: <info> (wlan0): device state change: 3 -> 2 (reason 0)
Jun  5 20:03:44 amanda NetworkManager[439]: <info> (wlan0): deactivating device (reason: 0).
Jun  5 20:03:45 amanda NetworkManager[439]: <info> (wlan0): taking down device.
Jun  5 20:03:45 amanda kernel: [ 6342.634650] wlan0: direct probe to 00:16:b6:3e:51:06 (try 1/3)
Jun  5 20:04:11 amanda NetworkManager[439]: <info> (wlan0): bringing up device.
Jun  5 20:04:12 amanda kernel: [ 6369.658707] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  5 20:04:12 amanda NetworkManager[439]: <info> (wlan0): supplicant interface state:  starting -> ready
Jun  5 20:04:12 amanda NetworkManager[439]: <info> (wlan0): device state change: 2 -> 3 (reason 42)
Jun  5 20:04:12 amanda wpa_supplicant[475]: Failed to initiate AP scan.
Jun  5 20:04:23 amanda NetworkManager[439]: user_connection_updated_cb: assertion `old_connection != NULL' failed
Jun  5 20:04:23 amanda NetworkManager[439]: <info> Activation (wlan0) starting connection 'Auto amanda'
Jun  5 20:04:23 amanda NetworkManager[439]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Jun  5 20:04:23 amanda NetworkManager[439]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  5 20:04:23 amanda NetworkManager[439]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun  5 20:04:23 amanda NetworkManager[439]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun  5 20:04:23 amanda NetworkManager[439]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun  5 20:04:23 amanda NetworkManager[439]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun  5 20:04:23 amanda NetworkManager[439]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Jun  5 20:04:23 amanda NetworkManager[439]: <info> Activation (wlan0/wireless): connection 'Auto amanda' requires no security.  No secrets needed.
Jun  5 20:04:23 amanda NetworkManager[439]: <info> Config: added 'ssid' value 'amanda'
Jun  5 20:04:23 amanda NetworkManager[439]: <info> Config: added 'scan_ssid' value '1'
Jun  5 20:04:23 amanda NetworkManager[439]: <info> Config: added 'key_mgmt' value 'NONE'
Jun  5 20:04:23 amanda NetworkManager[439]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun  5 20:04:23 amanda NetworkManager[439]: <info> Config: set interface ap_scan to 1
Jun  5 20:04:23 amanda NetworkManager[439]: <info> (wlan0): supplicant connection state:  inactive -> scanning
Jun  5 20:04:23 amanda NetworkManager[439]: <info> (wlan0): device state change: 5 -> 3 (reason 0)
Jun  5 20:04:23 amanda NetworkManager[439]: <info> (wlan0): deactivating device (reason: 0).
Jun  5 20:04:23 amanda NetworkManager[439]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Jun  5 20:04:23 amanda NetworkManager[439]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Jun  5 20:04:23 amanda NetworkManager[439]: <info> Activation (wlan0) starting connection 'Auto amanda'
Jun  5 20:04:23 amanda NetworkManager[439]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Jun  5 20:04:23 amanda NetworkManager[439]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  5 20:04:23 amanda NetworkManager[439]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun  5 20:04:23 amanda NetworkManager[439]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun  5 20:04:23 amanda NetworkManager[439]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun  5 20:04:23 amanda NetworkManager[439]: <info> (wlan0): supplicant connection state:  scanning -> disconnected
Jun  5 20:04:23 amanda NetworkManager[439]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun  5 20:04:23 amanda NetworkManager[439]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Jun  5 20:04:23 amanda NetworkManager[439]: <info> Activation (wlan0/wireless): connection 'Auto amanda' requires no security.  No secrets needed.
Jun  5 20:04:23 amanda NetworkManager[439]: <info> Config: added 'ssid' value 'amanda'
Jun  5 20:04:23 amanda NetworkManager[439]: <info> Config: added 'scan_ssid' value '1'
Jun  5 20:04:23 amanda NetworkManager[439]: <info> Config: added 'key_mgmt' value 'NONE'
Jun  5 20:04:23 amanda NetworkManager[439]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun  5 20:04:23 amanda NetworkManager[439]: <info> Config: set interface ap_scan to 1
Jun  5 20:04:23 amanda wpa_supplicant[475]: Failed to initiate AP scan.
Jun  5 20:04:23 amanda NetworkManager[439]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jun  5 20:04:23 amanda NetworkManager[439]: <info> (wlan0): supplicant connection state:  scanning -> disconnected
Jun  5 20:04:24 amanda wpa_supplicant[475]: Trying to associate with 00:16:b6:3e:51:06 (SSID='amanda' freq=2422 MHz)
Jun  5 20:04:24 amanda kernel: [ 6382.269397] wlan0: direct probe to 00:16:b6:3e:51:06 (try 1/3)
Jun  5 20:04:24 amanda NetworkManager[439]: <info> (wlan0): supplicant connection state:  disconnected -> associating
Jun  5 20:04:24 amanda kernel: [ 6382.468099] wlan0: direct probe to 00:16:b6:3e:51:06 (try 2/3)
Jun  5 20:04:25 amanda kernel: [ 6382.668113] wlan0: direct probe to 00:16:b6:3e:51:06 (try 3/3)
Jun  5 20:04:25 amanda kernel: [ 6382.868114] wlan0: direct probe to 00:16:b6:3e:51:06 timed out
Jun  5 20:04:34 amanda wpa_supplicant[475]: Authentication with 00:16:b6:3e:51:06 timed out.
Jun  5 20:04:34 amanda NetworkManager[439]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Jun  5 20:04:34 amanda NetworkManager[439]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jun  5 20:04:34 amanda wpa_supplicant[475]: Trying to associate with 00:16:b6:3e:51:06 (SSID='amanda' freq=2422 MHz)
Jun  5 20:04:34 amanda kernel: [ 6392.513509] wlan0: direct probe to 00:16:b6:3e:51:06 (try 1/3)
Jun  5 20:04:34 amanda NetworkManager[439]: <info> (wlan0): supplicant connection state:  scanning -> associating
Jun  5 20:04:35 amanda kernel: [ 6392.712743] wlan0: direct probe to 00:16:b6:3e:51:06 (try 2/3)
Jun  5 20:04:35 amanda kernel: [ 6392.912109] wlan0: direct probe to 00:16:b6:3e:51:06 (try 3/3)
Jun  5 20:04:35 amanda kernel: [ 6393.112115] wlan0: direct probe to 00:16:b6:3e:51:06 timed out
Jun  5 20:04:39 amanda NetworkManager[439]: <warn> (wlan0): link timed out.
Jun  5 20:04:44 amanda wpa_supplicant[475]: Authentication with 00:16:b6:3e:51:06 timed out.
Jun  5 20:04:44 amanda NetworkManager[439]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Jun  5 20:04:44 amanda NetworkManager[439]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jun  5 20:04:45 amanda wpa_supplicant[475]: Trying to associate with 00:16:b6:3e:51:06 (SSID='amanda' freq=2422 MHz)
Jun  5 20:04:45 amanda kernel: [ 6402.646100] wlan0: direct probe to 00:16:b6:3e:51:06 (try 1/3)
Jun  5 20:04:45 amanda NetworkManager[439]: <info> (wlan0): supplicant connection state:  scanning -> associating
Jun  5 20:04:45 amanda kernel: [ 6402.844096] wlan0: direct probe to 00:16:b6:3e:51:06 (try 2/3)
Jun  5 20:04:45 amanda kernel: [ 6403.044110] wlan0: direct probe to 00:16:b6:3e:51:06 (try 3/3)
Jun  5 20:04:45 amanda kernel: [ 6403.244063] wlan0: direct probe to 00:16:b6:3e:51:06 timed out
Jun  5 20:04:52 amanda NetworkManager[439]: <info> (wlan0): device state change: 5 -> 3 (reason 39)
Jun  5 20:04:52 amanda NetworkManager[439]: <info> (wlan0): deactivating device (reason: 39).
Jun  5 20:04:52 amanda NetworkManager[439]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.

```Concurrent iwevent log:

```
$ sudo iwevent
Waiting for Wireless Events from interfaces...
20:03:45.007854   wlan0    New Access Point/Cell address:Not-Associated
20:03:45.008051   wlan0    Set ESSID:off/any
20:04:12.036200   wlan0    Set Mode:Managed
20:04:12.036472   wlan0    Set ESSID:off/any
20:04:13.175334   wlan0    Scan request completed
20:04:24.641647   wlan0    Scan request completed
20:04:24.642383   wlan0    Set ESSID:off/any
20:04:24.642428   wlan0    Set Mode:Managed
20:04:24.642453   wlan0    Set Frequency:2.422 GHz (Channel 3)
20:04:24.642629   wlan0    Set ESSID:"amanda"
20:04:34.885769   wlan0    Scan request completed
20:04:34.886492   wlan0    Set ESSID:off/any
20:04:34.886537   wlan0    Set Mode:Managed
20:04:34.886562   wlan0    Set Frequency:2.422 GHz (Channel 3)
20:04:34.886610   wlan0    Set ESSID:"amanda"
20:04:45.018363   wlan0    Scan request completed
20:04:45.019082   wlan0    Set ESSID:off/any
20:04:45.019127   wlan0    Set Mode:Managed
20:04:45.019151   wlan0    Set Frequency:2.422 GHz (Channel 3)
20:04:45.019199   wlan0    Set ESSID:"amanda"
20:05:02.501506   wlan0    Scan request completed

```

---

### Post by carrotts on 2011-06-18
Hi
I've tried all in this post with no luck on an isl 3886 card I pulled from an old router. Last night I enabled some extra tick boxes on the update tab in repositories menu.  I think the important one was proposed updates (backports). Ran an update and selected kernel update and firmware rebooted and now it connects fine. Hope this helps and thanks to all the above posts for the help. 
Cheers
Carrotts

---

### Post by klinteback on 2011-07-07
Thanks Chili555 and Carrotts

I now have a working 3CRWE154g72 card on my old Dell Latitude C400 with Ubuntu 11.04 Natty.
I first followed Chili555 instruction and installed the posted ZIP drive into the instructed lib firmware folder. The outcome showed some improvement since the card was being used and blinked but did not function properly.
Then as Carrot instructed I used 
System - Administration - Update Manager 
Clicked lower left corner button "Settings"
selected the tab called "Updates"
and selected the box "Pre-released updates"
I installed all of the suggested updates. Todays date is July 7th 2011 for admin version control.
Rebooted
:-) Works!

So I cant easily tell if this would work without the installed ZIP file on page 1, by Chili555 or if you need to do what i did, first install the ZIP'd hardware driver and then Update kernel? Maybe someone who has not installed the ZIP can try and report back.

Cheers

---

### Post by chili555 on 2011-07-07
> So I cant easily tell if this would work without the installed ZIP file on page 1, by Chili555 or if you need to do what i did, first install the ZIP'd hardware driver The zipped file is the _firmware_ which is required by the driver:```
$ modinfo p54pci
filename:       /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/p54/p54pci.ko
[COLOR="Red"]firmware:       isl3886pci[/COLOR]
alias:          prism54pci
license:        GPL
description:    Prism54 PCI wireless driver
<snip>
```So, what did it? A newer kernel version ... or?

---

### Post by Cadders on 2011-07-07
I can confirm I didnt install the zip file I just went into update manager and ticked all four of the ubuntu updates tabs... Updates installed, rebooted laptop and wireless is now working as designed.



Kind Regards,



Cadders

---

### Post by dsat on 2011-07-09
Thank you chili555 and carrotts for your tip!

My 3crwe154g72 also works on hp compaq nx9105 now :)

The firmwares still plays a role in network connectivity, 
which I have post on [http://ubuntuforums.org/showpost.php?p=10522042&postcount=23]("http://ubuntuforums.org/showpost.php?p=10522042&postcount=23")

Greets

---

### Post by chili555 on 2011-07-09
Awesome. Thanks for the firmware tip, too.

---

### Post by kemes on 2011-11-29
Thanks for the tips in this thread. It helped me with a L1300 Amilo..

---

### Post by grrrb on 2012-01-19
Thanks for the firmware file, it works on Ubuntu 11.10 32-bit on a old Fujitsu-Siemens Lifebook E-6560 with the 3com pcmcia card.

---

### Post by batcat on 2012-03-25
Fantastic! Solved the same issue I just had resurrecting an old laptop that had been working happily with an older version of Ubuntu, but the 3COM WiFi card driver disappeared upgrading to 10.04.

---

### Post by fazzaxp on 2012-07-13
Thank you very much. You just save my time fixing the wireless issue. This commands work for Fujitsu Amilo L1300 wireless (isl3886). 

Keep up the good work! :popcorn:

---

### Post by santzi on 2013-01-05
> **chili555 said:**
> Pretty good guess, eh? Here is a file attached you can get with a USB drive. Drag and drop it to the desktop of the Ubuntu machine. Right-click it and select 'Extract here.' Now in a terminal, do:```
cd Desktop
sudo cp isl3886pci /lib/firmware
```Reboot and let us have your report.

Thank for this. I had a wlan problem with Fujitsu Siemens L1300 laptop (Lubuntu 12.04). I used this trick and wlan works fine now. I googled about 4 hours to solve my problem. I tried to use ndiswrapper with WinXp wlan driver, but I couldn't find correct driver anymore. Finally I found this page and problem is now solved. Thank you!

---

### Post by vic_curtis on 2013-01-18
Clearly a very helpful thread - just helped me get Ubuntu talking on an ancient Dell Laptop.

As always with *nix, I just knew it would be a small thing missing or mis-configured - the trick is
finding the needle in the haystack!

Thanks to all.... I may yet be back with other problems!

Regards,
Vic

---

### Post by avsdep on 2013-06-03
Still working on IBM R40e, thx a lot

---

