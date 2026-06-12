---
title: "Tenda w311u usb dongle problem with natty 11.04"
date: 2011-06-09
forum: Networking &amp; Wireless
---

### Post by michalkajaba on 2011-06-09
Hi there,
sorry for my first post as an error with Tenda W311u usb wifi adapter. 
As I installed ubuntu natty, networkmanager sees my usb wifi adapter, but I couldn't connect to wifi networks (using WPA). I searched this forum and was recommended to blacklist rt2800usb module (worked for ubuntu 10.10) or compile the driver from [http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download). I followed that site, now I can connect to my network, but the connection is terribly slow.

I tried nearly every solution but with no luck.

Please, somebody help me!
Thanks

---

### Post by chili555 on 2011-06-09
Please run and post:```
lsusb
lsmod
```Thanks.

---

### Post by michalkajaba on 2011-06-09
Gladly

lsusb:
```

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

lsmod:
```

rt2800usb              22184  0 
binfmt_misc            13213  1 
rt2800lib              48252  1 rt2800usb
rt2x00usb              19915  1 rt2800usb
rt2x00lib              47468  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              264732  3 rt2800lib,rt2x00usb,rt2x00lib
snd_via82xx            24685  2 
gameport               15027  1 snd_via82xx
snd_ac97_codec        105614  1 snd_via82xx

```Thank you chili (I know you can handle these things)

---

### Post by chili555 on 2011-06-09
> recommended to blacklist rt2800usb moduleIt was very good advice. Please do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add four lines:```
blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib
```Proofread carefully, save and close gedit. Now do:```
sudo su
echo rt2870sta >> /etc/modules
exit
```Reboot and use your wireless to tell us how it's working!

---

### Post by michalkajaba on 2011-06-09
Still no luck,
I tired this solution already. I can't connect to my WPA network (it keeps asking for password)

lsmod after blacklist:
```

shpchp                 32345  0 
rt2870sta             410104  1 
crc_ccitt              12595  1 rt2870sta
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
usbhid                 41704  0 

```

any other tips?

---

### Post by chili555 on 2011-06-09
Have you double- and triple-checked the WPA password? Is your network set to WPA or WPA2 or the difficult mixed mode WPA and WPA2 mode? If the latter, I suggest resetting it to WPA2 only.

---

### Post by michalkajaba on 2011-06-10
Sure I have, other computers works well on my network.
My router is configured as follows:
authentication type: auto
encryption: WPA pre-shared key
cipher suit: WPA (TKIP)

In network meneger, as it asks for  password, it asks password for WPA/WPA2 encryption (there is no other choice)
Do you think it's a router config???

---

### Post by chili555 on 2011-06-10
> In network meneger, as it asks for password, it asks password for WPA/WPA2 encryption (there is no other choice)That's what it asks for whether you have WPA or WPA2. Network Manager is supposed to unravel all the details for you. May we see:```
sudo iwlist wlan0 scan
```Thanks.

---

### Post by michalkajaba on 2011-06-10
Yeaj it finnds many networks. This one is mine:
```

Cell 04 - Address: 00:11:3B:07:79:85
                    Protocol:802.11b/g
                    ESSID:"misoHome"
                    Mode:Managed
                    Channel:8
                    Quality:100/100  Signal level:-45 dBm  Noise level:-115 dBm
                    Encryption key:on
                    Bit Rates:18 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

```

---

### Post by chili555 on 2011-06-10
> Cell 04 - Address: 00:11:3B:07:79:85
                    Protocol:802.11b/g
                    ESSID:"misoHome"
                    Mode:Managed
                    Channel:8
                    Quality:100/100  Signal level:-45 dBm  Noise level:-115 dBm
                    Encryption key:on
                    [COLOR="Red"]Bit Rates:18 Mb/s[/COLOR]
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSKLooks awesome. I'm not sure that this has much to do with the ability to connect, but do you have the router set to 18 Mb/s only? I'd suspect it might work a bit better set to 'Auto' or the highest setting if Auto is not an available setting. If it still won't connect, please post:```
sudo cat /var/log/syslog | grep etwork | tail -n25
```

---

### Post by michalkajaba on 2011-06-10
I don't know why there is only 18Mb/s, but other devices (win7 and iPod) work like a charm and the network speed is great.

As for the command
sudo cat /var/log/syslog | grep etwork | tail -n25
```

Jun 10 21:25:44 airport NetworkManager[431]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun 10 21:25:45 airport NetworkManager[431]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 10 21:25:45 airport NetworkManager[431]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun 10 21:25:45 airport NetworkManager[431]: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Jun 10 21:25:45 airport NetworkManager[431]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun 10 21:25:45 airport NetworkManager[431]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun 10 21:25:45 airport NetworkManager[431]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun 10 21:25:45 airport NetworkManager[431]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Jun 10 21:25:45 airport NetworkManager[431]: <info> Activation (wlan0/wireless): connection 'Auto misoHome' has security, and secrets exist.  No new secrets needed.
Jun 10 21:25:45 airport NetworkManager[431]: <info> Config: added 'ssid' value 'misoHome'
Jun 10 21:25:45 airport NetworkManager[431]: <info> Config: added 'scan_ssid' value '1'
Jun 10 21:25:45 airport NetworkManager[431]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jun 10 21:25:45 airport NetworkManager[431]: <info> Config: added 'psk' value '<omitted>'
Jun 10 21:25:45 airport NetworkManager[431]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun 10 21:25:45 airport NetworkManager[431]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun 10 21:25:45 airport NetworkManager[431]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun 10 21:25:45 airport NetworkManager[431]: <info> Config: set interface ap_scan to 1
Jun 10 21:25:45 airport NetworkManager[431]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jun 10 21:26:00 airport NetworkManager[431]: <info> (wlan0): supplicant connection state:  scanning -> associating
Jun 10 21:26:10 airport NetworkManager[431]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Jun 10 21:26:10 airport NetworkManager[431]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jun 10 21:26:25 airport NetworkManager[431]: <info> (wlan0): supplicant connection state:  scanning -> associating
Jun 10 21:26:35 airport NetworkManager[431]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Jun 10 21:26:35 airport NetworkManager[431]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jun 10 21:26:41 airport NetworkManager[431]: <warn> (wlan0): link timed out.

```

---

### Post by chili555 on 2011-06-10
There are a number of bug reports about rt2870sta, for instance: [https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/762987](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/762987)

And this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549801](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549801)

The most interesting comments start at post #17 or so in the first link and deal with the firmware. Let's see which firmware you have, 4096 bytes or 8 Kb.```
ls -al /lib/firmware | grep -e 287 -e 307
```Let's also see if there are any messages about firmware:```
dmesg | grep rt2
```Finally, let's see if the package linux-firmware is installed:```
sudo dpkg -s linux-firmware
```For reference, on my system, it is installed and I see:> $ ls -al /lib/firmware | grep -e 287 -e 307
-rw-r--r--  1 root root    [COLOR="Red"]4096[/COLOR] 2010-11-18 16:20 rt2870.bin
-rw-r--r--  1 root root    4096 2010-11-18 16:20 rt3070.bin
-rw-r--r--  1 root root    4096 2010-11-18 16:20 rt3071.bin


----------

Note to chili: See post #5 here:  [https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/770232](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/770232)

---

### Post by michalkajaba on 2011-06-10
I think we've got the same:

```

airport@airport:~$ ls -al /lib/firmware | grep -e 287 -e 307
-rw-r--r--  1 root root    4096 2010-11-18 22:20 rt2870.bin
-rw-r--r--  1 root root    4096 2010-11-18 22:20 rt3070.bin
-rw-r--r--  1 root root    4096 2010-11-18 22:20 rt3071.bin

```

```

airport@airport:~$ dmesg | grep rt2
[   14.258831] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   14.312159] usbcore: registered new interface driver rt2870
[   17.102885] <==== rt28xx_init, Status=0
[   18.441330] <==== rt28xx_init, Status=0

```

```

airport@airport:~$ sudo dpkg -s linux-firmware
[sudo] password for airport: 
Package: linux-firmware
Status: install ok installed
Priority: optional
Section: misc
Installed-Size: 32908
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>

```

I really don't know what is the prob

---

### Post by chili555 on 2011-06-10
> I really don't know what is the probLOL! Well, neither do I...yet. I hope we find out and solve it soon. 

I assume you have an ethernet connection. Let's try the 8 Kb firmware. We'll make a backup of the 4096 byte file first:```
sudo mv /lib/firmware/rt2870.bin /lib/firmware/rt2870.bak
```Now, we'll download the later package:```
wget https://launchpad.net/ubuntu/oneiric/+source/linux-firmware/1.53/+files/linux-firmware_1.53.tar.gz
```And now we extract it:```
tar -xzf linux
```Press the Tab key and the remainder will fill in. Now do:```
cd linux-firmware 
cp rt2870.bin /lib/firmware
```Now we unload the module and reload with, hopefully, better firmware.```
sudo ifconfig wlan0 down
sudo rmmod -f rt2870sta
sudo modprobe rt2870sta
sudo ifconfig wlan0 up
```

Now can you connect?

---

### Post by michalkajaba on 2011-06-10
No luck, still asking for WPA/WPA2 password, but still I can't connect:(
It can connect to free networks (but the connection is very slow)

---

### Post by chili555 on 2011-06-10
Can you try WPA**2** on your home network? I'm running low on ideas/talent/mojo.

---

### Post by michalkajaba on 2011-06-10
It connects, but the net is terribly slow and sometimes it disconnects me from my network...

---

### Post by chili555 on 2011-06-10
> **michalkajaba said:**
> It connects, but the net is terribly slow and sometimes it disconnects me from my network...Hey, we're making *some* progress. Let's have a look at:```
dmesg | grep rt2
iwconfig
```Have you tried a reboot?

---

### Post by michalkajaba on 2011-06-10
Now it suddenly works, I chenged something in my router (authentication-type:Open system, encryption:pre-shared key WPA2), and fullspeed

But my ipod is not working with my network..damn thing :D:D

But as for the driver, Thank you chilli. I'll be testing it

---

### Post by chili555 on 2011-06-10
Post back if we can help you further. Glad it's working.

---

### Post by michalkajaba on 2011-06-14
Now there is the problem again, but i didn't change a thing.

---

### Post by chili555 on 2011-06-14
> **michalkajaba said:**
> Now there is the problem again, but i didn't change a thing.The problem that the wireless won't connect or what? Are there any clues in the message logs?```
dmesg | grep -e rt2 -e wlan
```

---

### Post by michalkajaba on 2011-06-14
Exactly, it won't connect. So I tried to figure it out
I downloaded latest firmware (as you described) but still no luck
```

airport@airport:~$ dmesg | grep -e rt2 -e wlan
[   14.353903] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   14.455146] usbcore: registered new interface driver rt2870
[   17.250412] <==== rt28xx_init, Status=0
[   18.243121] <==== rt28xx_init, Status=0
[   29.160028] wlan0: no IPv6 routers present

```

---

### Post by michalkajaba on 2011-06-16
Do you have some recommendation on this?

---

### Post by michalkajaba on 2011-09-01
Now I have different problem. I reinstalled ubuntu. And rightaway I installed wifi driver from ralink source, upgraded firmware. Everything went OK, but after that, I can't see wlan0 in ifconfig.
The module is loaded:
lsmod:
```
rt2870sta             570769  0
```

ls -al /lib/firmware | grep -e 287 -e 307
```

-rw-r--r--  1 root root    4096 2010-11-18 22:20 rt2870.bak
-rw-r--r--  1 root root    8192 2011-09-01 12:07 rt2870.bin
-rw-r--r--  1 root root    8192 2011-09-01 12:02 rt2870_NEW.bak
-rw-r--r--  1 root root    4096 2010-11-18 22:20 rt3070.bin
-rw-r--r--  1 root root    4096 2010-11-18 22:20 rt3071.bin

```
Any ideas what might be wrong???
Thank you for your help

---

