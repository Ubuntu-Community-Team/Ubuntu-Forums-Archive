---
title: "Lenovo IdeaPad Z570-1024D9U - Laptop (Wireless Help)"
date: 2013-05-29
forum: Networking &amp; Wireless
---

### Post by zdeuyo on 2013-05-29
[COLOR=#000000]Hello Forum,

[/COLOR]
I am having intermittent wireless problems with two laptops I own. One is a Lenovo laptop which which was working fine. It is running 12.04. The other laptop is also running the same version of Ubuntu. What is happening is on the Windows 7 Home Premium 64-bit partition on both laptops the wireless connection and Ethernet is fine. On the Ubuntu partition of both laptops wireless works, but only intermittently. If I tether or wireless connect to the connection on my Samsung Galaxy S3 there is no problems, but without it the connection is spotty. What would you suggest?[COLOR=#000000]
[/COLOR]

Here is a reference link:


Link: [http://ubuntuforums.org/showthread.php?t=1959458](http://ubuntuforums.org/showthread.php?t=1959458)


[COLOR=#000000]***

[SIZE=4]_**Here are the specs of the Lenovo Laptop.**_[/SIZE][/COLOR]


[COLOR=#000000]Description:    [/COLOR]

[COLOR=#000000]IdeaPad Z570 Laptop - 1024D9U - Gunmetal Grey: Weekly Deal    [/COLOR]

[COLOR=#000000]Processor:    2nd generation Intel Core i7-2670QM Processor( [/COLOR]
[COLOR=#000000]2.2GHz 1333MHz 6MB)    [/COLOR]

[COLOR=#000000]Operating system:    Genuine Windows 7 Home Premium 64    [/COLOR]

[COLOR=#000000]Graphics:    Intel Integrated HD Graphics 3000    [/COLOR]

[COLOR=#000000]Memory:    8.0GB PC3-10600 DDR3 SDRAM 1333 MHz    [/COLOR]

[COLOR=#000000]Display:    15.6" HD Glare with integrated camera 1366x768    [/COLOR]

[COLOR=#000000]Pointing device:    Industry Standard Touchpad    [/COLOR]

[COLOR=#000000]Hard Drive:    500GB 7200    [/COLOR]

[COLOR=#000000]Optical Drive:    DVD Recordable    [/COLOR]

[COLOR=#000000]Battery:    6 Cell Lithium-Ion    [/COLOR]

[COLOR=#000000]Network Card:    Intel 1000 BGN Wireless    [/COLOR]

[COLOR=#000000]Bluetooth:    Bluetooth Version 2.1 + EDR    [/COLOR]

[COLOR=#000000]Warranty:    One Year    [/COLOR]

[COLOR=#000000]Camera:    Integrated 2.0MP Camera    [/COLOR]

[COLOR=#000000]HDMI:    HDMI (Out)

***

[SIZE=5]_**Here are the specs for the ASUS Laptop**_[/SIZE]

[/COLOR]**ASUS U47A-BGR4**

[COLOR=#4D4D4D][FONT=helvetica]**Model**

BrandASUSModelU47A-BGR4**General**

Operating SystemWindows 7 Home Premium 64-BitCPU TypeIntel Core i7-2640M 2.8GHzScreen14"Memory Size8GB DDR3Hard Disk750GBOptical DriveDVD±R/RWGraphics CardIntel HD Graphics 3000Video MemoryShared memoryCommunicationGigabit LAN and WLANDimensions12.9" x 8.9" x 1.2"Weight4.4 lbs.**CPU**

CPU TypeIntel Core i7CPU Speed2640M(2.80GHz)CPU Support4MB L3 Cache
Max Turbo Frequency 3.5 GHz**Display**

Screen Size14"Wide Screen SupportYesResolution1366 x 768LCD FeaturesHigh-definition LED-backlit open-cell**Operating Systems**

Operating SystemWindows 7 Home Premium 64-Bit**Graphics**

GPU/VPUIntel HD Graphics 3000Video MemoryShared system memoryGraphic TypeIntegrated Card**Hard Drive**

HDD750GBHDD RPM5400rpmHDD InterfaceSATA**Memory**

Memory8GBMemory Type204-Pin DDR3 SO-DIMM**Optical Drive**

Optical Drive TypeDVD±R/RW**Communications**

LAN10/100/1000MbpsWLAN802.11b/g/n Wireless LANBluetoothYes**Ports**

USB2 x USB 3.0
1 x USB 2.0HDMI1 x HDMI**Supplemental Drive**

WebcamYes**General**

StyleThin and Light**Power**

Battery6-cell lithium ion**Physical Specifications**

Dimensions12.9" x 8.9" x 1.2"Weight4.4 lbs.
[/FONT][/COLOR]
Any help to fix this is greatly appreciated. Thank you.

---

### Post by chili555 on 2013-05-29
Let's work on one problem at a time, starting with the Lenovo. Please open a terminal and do:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```Now does it work well? If so, we can make it persistent.

In the meantime, we need more details about the Asus:```
lspci -nn | grep 0280
```Thanks.

---

### Post by zdeuyo on 2013-05-29
Thank you for your reply. I did the sudo terminal commands and the wifi is working right now for the Lenvo. Is there anything else I would need to do to keep it working?? Also what did those commands do?

...

Also, here is the result of the command performed on the ASUS,

""

02:00.0 Network controller [0280]:Intel Corporation Centrino Wireless-N 2230 [8086:0887] (rev c4)

---

### Post by chili555 on 2013-05-29
Funny, or maybe not so funny...the Asus uses the same driver iwlwifi, has the same symptoms and needs the same fix! This command disables N speeds from the driver. This driver has issues with the 802.11N implementation in some wireless routers. The fix, regrettably, is to disable it. In both computers, do:```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
```Add a single line:```
options iwlwifi 11n_disable=1
```Proofread, save and close gedit. Unload and reload the driver:```
sudo modprobe -r iwlwifi && sudo modprobe iwlwifi
```You should be all set.

---

### Post by zdeuyo on 2013-05-29
Thank you. I just performed the tasks on the laptops and it seems a little. When I refresh if a page does not load it brings the page right up. I am not sure if disabling this feature shortened the range, speed and or reliability. What do you think?

---

### Post by chili555 on 2013-05-29
Please try a reboot on both.> I am not sure if disabling this feature shortened the range, speed and or reliability. What do you think? I highly doubt it.

---

### Post by zdeuyo on 2013-05-29
Ok. I did a full reboot, restart on both laptops. Both are having the same issue where I have to hit refresh to open a webpage sometimes. Any idea?

---

### Post by chili555 on 2013-05-30
Let's see at first only on the Lenovo:```
iwconfig
cat /etc/modprobe.d/iwlwifi.conf
nm-tool
ping -c3 www.google.com
ping -c3 173.194.73.106
```Thanks.

---

### Post by zdeuyo on 2013-05-30
zdeuyo@zdeuyo-Ideapad-Z570:~$ iwconfig
lo        no wireless extensions.


wlan0     IEEE 802.11bg  ESSID:"BEAST"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: BLOCKED FOR PRIVACY
          Bit Rate=54 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:42   Missed beacon:0


eth0      no wireless extensions.


zdeuyo@zdeuyo-Ideapad-Z570:~$ cat /etc/modprobe.d/iwlwifi.conf
options iwlwifi 11n_disable=1
zdeuyo@zdeuyo-Ideapad-Z570:~$ nm-tool


NetworkManager Tool


State: connected (global)


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        BLOCKED FOR PRIVACY


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off




- Device: wlan0  [BEAST] -------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:       BLOCKED FOR PRIVACY


  Capabilities:
    Speed:           54 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    HOME-3292:       Infra, 00:1D:D4:05:32:90, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    KatyYan:         Infra, 00:1D:D1:27:96:E0, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    *BEAST:          Infra, BLOCKED FOR PRIVACY, Freq 2462 MHz, Rate 54 Mb/s, Strength 63 WPA WPA2


  IPv4 Settings:
    Address:         BLOCKED FOR PRIVACY
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.1


    DNS:             75.75.75.75
    DNS:             75.75.76.76




zdeuyo@zdeuyo-Ideapad-Z570:~$ ping -c3 [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)
zdeuyo@zdeuyo-Ideapad-Z570:~$ ping -c3 173.194.73.106
PING 173.194.73.106 (173.194.73.106) 56(84) bytes of data.


--- 173.194.73.106 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2015ms


zdeuyo@zdeuyo-Ideapad-Z570:~$

---

### Post by chili555 on 2013-05-30
> wlan0 IEEE 802.11bg ESSID:"BEAST"
Mode:Managed Frequency:2.462 GHz Access Point: BLOCKED FOR PRIVACY
Bit Rate=54 Mb/s Tx-Power=14 dBm
Retry long limit:7 RTS thrff Fragment thrff
Power Managementn
Link Quality=54/70 Signal level=-56 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:42 Missed beacon:0

Looks great!> zdeuyo@zdeuyo-Ideapad-Z570:~$ cat /etc/modprobe.d/iwlwifi.conf
options iwlwifi 11n_disable=1Perfect!> *BEAST: Infra, BLOCKED FOR PRIVACY, Freq 2462 MHz, Rate 54 Mb/s, Strength 63 WPA WPA2

I might suggest WPA2 only and not mixed mode, but it shouldn't produce the symptoms you have.> IPv4 Settings:
Address: BLOCKED FOR PRIVACY
Prefix: 24 (255.255.255.0)
Gateway: 10.0.0.1


DNS: 75.75.75.75
DNS: 75.75.76.76
I assume the address you blocked is a 10.0.0.something address, correct? Did you get this address by DHCP from the router or where?

Where did the DNS nameservers come from? The router as well? I can ping 75.75.75.75 but not x.76. I assume you are with Comcast. Is it possible their DNS nameserver is faulty? Do other computers, iPads, phones, etc. using wifi work as expected?

It is highly unusual to be unable to ping Google even by number:> zdeuyo@zdeuyo-Ideapad-Z570:~$ ping -c3 173.194.73.106
PING 173.194.73.106 (173.194.73.106) 56(84) bytes of data.


--- 173.194.73.106 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2015msHave you entered any settings at all in Network Manager? Generally, no human intervention is needed.

---

### Post by zdeuyo on 2013-05-30
That is correct the blocked address is a 10.0.0 setting and the DNS is Comcast. It is a Comcast provided modem and router. It has a simple interface unlike a manufacture net gear router. We just had comcast come out the other day since users using Linux in the household have had this problem. My phone which is a Samsung Galaxy S3 has no problems nor does the Roku box or Google tv or any computers using Windows as its operating system.

---

### Post by chili555 on 2013-05-30
Let's check the firewall:```
sudo ufw status
```If it shows as active, temporarily disable it:```
sudo ufw disable
```And then ping:```
ping -c3 173.194.73.106
```Are the various settings on the Windows computer similar, especially the DNS nameservers?

---

### Post by zdeuyo on 2013-05-30
I did as you suggested. It was already in active and still cannot ping google directly.

---

### Post by chili555 on 2013-05-30
This just gets crazier by the moment. Can you at least ping the router?```
ping -c3 10.0.0.1
```And also, have you entered any settings at all in Network Manager?

---

### Post by zdeuyo on 2013-05-30
Results of modem ping

```

zdeuyo@zdeuyo-Ideapad-Z570:~$ ping -c3 10.0.0.1
PING 10.0.0.1 (10.0.0.1) 56(84) bytes of data.
64 bytes from 10.0.0.1: icmp_req=1 ttl=64 time=3.74 ms
64 bytes from 10.0.0.1: icmp_req=2 ttl=64 time=3.61 ms
64 bytes from 10.0.0.1: icmp_req=3 ttl=64 time=3.54 ms


--- 10.0.0.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 3.549/3.636/3.749/0.097 ms

```

result of google ping - ip

```

zdeuyo@zdeuyo-Ideapad-Z570:~$ ping -c3 10.0.0.1
PING 10.0.0.1 (10.0.0.1) 56(84) bytes of data.
64 bytes from 10.0.0.1: icmp_req=1 ttl=64 time=3.74 ms
64 bytes from 10.0.0.1: icmp_req=2 ttl=64 time=3.61 ms
64 bytes from 10.0.0.1: icmp_req=3 ttl=64 time=3.54 ms


--- 10.0.0.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 3.549/3.636/3.749/0.097 ms
zdeuyo@zdeuyo-Ideapad-Z570:~$ ping -c3 173.194.73.106
PING 173.194.73.106 (173.194.73.106) 56(84) bytes of data.


--- 173.194.73.106 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 1999ms

```

google ping - dns

```

zdeuyo@zdeuyo-Ideapad-Z570:~$ ping -c3 www.google.com
PING www.google.com (74.125.139.99) 56(84) bytes of data.


--- www.google.com ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2000ms

```

Also this is how the security is set up on the network manager.

First the firewall:
[ATTACH=CONFIG]243290[/ATTACH]

Then Parental Controls:
[ATTACH=CONFIG]243291[/ATTACH]

---

### Post by chili555 on 2013-05-30
I meant Network Manager on your Ubuntu computers. Click the NM icon, select Edit Connections and make sure the settings are like the attached and no more.

---

### Post by zdeuyo on 2013-05-30
Hello.

Ok, I took a look and this is what came up when I opened it for the wireless network I am connected to. I have made no modifications.

---

### Post by chili555 on 2013-05-31
This is a toughy! 

Please compare the settings on any Windows computer to these:```
IPv4 Settings:
Address: BLOCKED FOR PRIVACY
Prefix: 24 (255.255.255.0)
Gateway: 10.0.0.1


DNS: 75.75.75.75
DNS: 75.75.76.76

```The same? Let's have a look at:```
route -n
```Can you confirm there is no MAC address filtering in the router? How big is the DHCP range? In other words, if the DHCP settings in the router are to allow addresses from 10.0.0.10 to 10.0.0.19; that is, 10 addresses and you have 12 devices asking for an address, you will have a conflict.

Can you momentarily and temporarily change the firewall in the router to low and then to off and see if it helps? If it does, I am not suggesting you run without a firewall, just that we may need to tweak a setting or two once we focus in on the fault.

---

