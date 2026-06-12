---
title: "Ubuntu 12.04 LTS Wireless can't authenticate after last week update"
date: 2012-09-29
forum: Networking &amp; Wireless
---

### Post by jpn2 on 2012-09-29
Hello,

after last week update my wireless authentication doesn't work, and the authentication pop up window is always poping up.

My wireless info is:
$ lspci
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
05:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)

$ iwconfig
lo        no wireless extensions.

wlan0     802.11b/g  ESSID:"p\xE9>\xA1A\xE1\xFCg>\x01~\x97\xEA\xDCk\x96\x8F8\*\xEC\xB0;\xFB2\xAF<T\xEC\x18\xDB\"  
          Mode:Managed  Frequency=2.422 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

$ lsmod
r8187se               177422  0 
eeprom_93cx6           12725  1 r8187se

$ dmesg
[ 5760.509560] r8180: WW:No more TX desc, returning 2d of 2d
[ 5760.625400] r8180: WW:No more TX desc, returning 2d of 2d
[ 5760.625421] r8180: WW:No more TX desc, returning 2d of 2d
[ 5760.741499] r8180: WW:No more TX desc, returning 2d of 2d
[ 5760.741540] r8180: WW:No more TX desc, returning 2d of 2d
[ 5760.857497] r8180: WW:No more TX desc, returning 1e of 1e
[ 5763.360079] Linking with PN2: channel is 11
[ 5763.373491] r8180: WW:No more TX desc, returning 1e of 1e
[ 5765.876090] Linking with PN2: channel is 11
[ 5765.889508] r8180: WW:No more TX desc, returning 1e of 1e
[ 5768.392870] Linking with PN2: channel is 11
[ 5768.406301] r8180: WW:No more TX desc, returning 1e of 1e
[ 5770.909068] Linking with PN2: channel is 11
[ 5770.922516] r8180: WW:No more TX desc, returning 1e of 1e
[ 5773.424442] Linking with PN2: channel is 11
[ 5773.437865] r8180: WW:No more TX desc, returning 1e of 1e

$ sudo lshw -C network
PCI (sysfs) 

$ iwlist scan
wlan0     Scan completed :
          Cell 01 - Address: 58:98:35:59:58:DD
                    ESSID:"PN2"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=46/100  Signal level=-63 dBm  Noise level=-83 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 94ms ago

$ lsb_release -d
Description:    Ubuntu 12.04.1 LTS

$ uname -mr
3.2.0-31-generic x86_64

Thank you very much in advance for your support and cooperation!

r8187se               177422  0

---

### Post by uncaspi on 2012-09-29
Log into the router from windows and see if someting have changed with the authenticate settings. And we take it from there,
Also try other authentication methods.

---

### Post by jpn2 on 2012-09-29
Hello uncaspi,

fist of all thank you very much for your support!

I already have tried what U suggested.

I also have disconnected my security and tried to connect, and nothing happened...

Please note that I have several devices connected to my Wlan and all of then are working without any issue. 

BR,
jpn2

---

### Post by uncaspi on 2012-09-29
Many times I have heard about problems after updating. Maybe you have to wait until 12.10 in October. Could be that the network-manager is corrupted.
If you can connect throu cable you could try wicd. I try to figure out what the best ting to try. I is pitty that it happend after an update. That should indicate that one or several packages are corrupted. Usually with type of errors there is nothing else to do than upgrade or reinstallation.

---

### Post by jpn2 on 2012-09-29
ok, I will wait new instructions from U, and I will keep this thread updated with any new info that I could have about this issue.

---

### Post by uncaspi on 2012-09-29
To determine if something wrong with the network-manager you could try to bring up the interface manually.

Try this and see if it connects.

sudo dhcp

---

### Post by jpn2 on 2012-09-29
I got this:
$ sudo dhcp
sudo: dhcp: command not found

---

### Post by uncaspi on 2012-09-29
In older distros you had dhcp. I think we need help on this from anybody else. I found one similar command from locate. I think this is the right according to the man pages.


sudo /sbin/dhclient

After this have a look in ifconfig if you have beeen assigned an ip address.

---

### Post by jpn2 on 2012-09-29
$ sudo /sbin/dhclient
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service smbd reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the reload(8) utility, e.g. reload smbd
RTNETLINK answers: File exists


$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:4c:68:59:f4  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4cff:fe68:59f4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1957059 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1884350 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1151524357 (1.1 GB)  TX bytes:354586304 (354.5 MB)
          Interrupt:41 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4414 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4414 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:481987 (481.9 KB)  TX bytes:481987 (481.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:18:1a:0f:36:eb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:258 overruns:0 frame:0
          TX packets:5914 errors:5 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1373 (1.3 KB)  TX bytes:264194 (264.1 KB)
          Interrupt:18 Memory:ffffc90000350000-ffffc90000350100

---

### Post by uncaspi on 2012-09-29
Please shut down eth0 before using dhclient.

sudo ifconfig eth0 down

---

### Post by jpn2 on 2012-09-29
$ sudo ifconfig eth0 down
$ sudo /sbin/dhclient
$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4426 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4426 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:482703 (482.7 KB)  TX bytes:482703 (482.7 KB)

---

### Post by jpn2 on 2012-09-29
$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4426 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4426 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:482703 (482.7 KB)  TX bytes:482703 (482.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:18:1a:0f:36:eb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:262 overruns:0 frame:0
          TX packets:6161 errors:5 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1373 (1.3 KB)  TX bytes:280932 (280.9 KB)
          Interrupt:18 Memory:ffffc90000350000-ffffc90000350100

---

### Post by uncaspi on 2012-09-29
So this didnt work out. I have attached a small shell script you could use to bring it up manually. Run it by typing ./wifi.sh

---

### Post by jpn2 on 2012-09-29
$ dir
Desktop    examples.desktop  Templates      xbmc_crashlog-20120909_220242.log
Documents  Music         Ubuntu\ One
Downloads  Pictures         Videos
Dropbox    Public         **wifi.sh**

$ sudo ./wifi.sh
sudo: ./wifi.sh: command not found
$ ./wifi.sh
bash: ./wifi.sh: Permission denied

Please note that my wireless security is wpa2

---

### Post by uncaspi on 2012-09-29
Then I dont think you can use the script.
Then we are back to where we started.
And that is that the error occured after updating of the system. And as I said earliere such errors are difficulty to track down. You must decide yourself if you will try wicd, reinstall or wait until October for a new version and upgrade then.

---

### Post by jpn2 on 2012-09-29
When you say reinstall is from the scratch and loosing my actual ubuntu settings and programs, or I can run a command to quickly reinstall the OS and keep my settings?

---

### Post by uncaspi on 2012-09-29
From scratch. You must backup important files. I would tried wicd first.

---

### Post by BicyclerBoy on 2012-09-29
If it was a kernel update then reboot into grub & pick previous image..

If it was some other package update; run synaptic & roll the package version back & pin it..
(sometimes not possible if dependencies or earlier package is gone)

---

