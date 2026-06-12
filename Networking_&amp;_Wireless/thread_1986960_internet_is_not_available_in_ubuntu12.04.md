---
title: "internet is not available in ubuntu12.04"
date: 2012-05-25
forum: Networking &amp; Wireless
---

### Post by maheshtatva on 2012-05-25
hello guys, i am going through a bad time now after installing ubuntu 12.04 the wireless is connected but internet browser is not working(server is not responding).thanks in advance waiting for your advice

---

### Post by chili555 on 2012-05-25
What kind of Intel card do you have? Please post:```
lspci -nn | grep 0280
```

---

### Post by bikertappy on 2012-05-25
What browser are you using?

---

### Post by maheshtatva on 2012-05-26
03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6205 [8086:0085] (rev 34)

---

### Post by chili555 on 2012-05-26
Intel chipsets have a known issue with 802.11N. Please do:

```
sudo gedit /etc/modprobe.d/iwlwifi.conf

```
Add a single line:

```
options iwlwifi 11n_disable=1
```

Proofread, save and close gedit. Reboot and let us hear your report.

---

### Post by VdubVidiot on 2012-06-15
Hello ):P

 It's my first post in a Linux forum, thanx in advance for your assistance with noobs such as myself. 8-[

I have the same distro and wireless problem as the OP (ubuntu 12.4 desktop amd x64) and for wireless I have "03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6200 [8086:422c] (rev 35)" my browser is firefox 13.0

I used the code suggested in terminal: "sudo gedit /ect/modprobe.d/iwlwifi.conf" which opened a blank gedit document, I then typed into this document "options iwlwifi 11n_disable=1" I then proofread, saved and close gedit. When saving I received the message "Could not find the file "/ect/modprobe.d/iwlwifi.conf." and "Please check that you typed the location correctly and try again." so I saved the file as "iwlwifi.conf" in "/". I then restarted my computer but my (our) wireless issue is unchanged.

Thank you for your patience regarding this matter :D:D

---

### Post by chili555 on 2012-06-15
> When saving I received the message "Could not find the file "/[COLOR="Red"]ect[/COLOR]/modprobe.d/iwlwifi.conf." and "Please check that you typed the location correctly and try again." It's not ect; it's **etc**. Please try again.

---

### Post by VdubVidiot on 2012-06-15
> **chili555 said:**
> It's not ect; it's **etc**. Please try again.

](*,)](*,)](*,) Thank you for pointing this out. :)

It's saving correctly now, I restarted and it seems that wifi is now completely gone, before I could pick up a signal, log in, but poor firefox 13.0 would just spin around in circles without ever connecting to a website. I've checked my radio button that turns wifi on and off, its still turning bluetooth on and off, but wifi remains off.

---

### Post by chili555 on 2012-06-15
Please run and post:```
sudo modprobe iwlwifi
cat /etc/modprobe.d/iwlwifi.conf
dmesg | grep iwl
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by VdubVidiot on 2012-06-15
brandon@brandon-Studio-1569:~$ sudo modprobe iwlwifi
brandon@brandon-Studio-1569:~$ cat /etc/modprobe.d/iwlwifi.conf
options iwlwifi 11n_disable=1
brandon@brandon-Studio-1569:~$ dmesg | grep iwl
[   13.167045] iwlwifi 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.167087] iwlwifi 0000:03:00.0: setting latency timer to 64
[   13.167348] iwlwifi 0000:03:00.0: pci_resource_len = 0x00002000
[   13.167350] iwlwifi 0000:03:00.0: pci_resource_base = ffffc90000664000
[   13.167353] iwlwifi 0000:03:00.0: HW Revision ID = 0x35
[   13.167673] iwlwifi 0000:03:00.0: irq 43 for MSI/MSI-X
[   13.167764] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6200 AGN, REV=0x74
[   13.167949] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   13.208923] iwlwifi 0000:03:00.0: device EEPROM VER=0x43a, CALIB=0x6
[   13.208928] iwlwifi 0000:03:00.0: Device SKU: 0X1f0
[   13.212104] iwlwifi 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   13.295955] iwlwifi 0000:03:00.0: loaded firmware version 9.221.4.1 build 25532
[   13.299615] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   14.294423] iwlwifi 0000:03:00.0: RF_KILL bit toggled to disable radio.
[   44.796665] iwlwifi 0000:03:00.0: RF_KILL bit toggled to enable radio.
[   44.806634] iwlwifi 0000:03:00.0: RF_KILL bit toggled to disable radio.
[   47.408995] iwlwifi 0000:03:00.0: RF_KILL bit toggled to enable radio.
brandon@brandon-Studio-1569:~$ ^C
brandon@brandon-Studio-1569:~$

---

### Post by chili555 on 2012-06-15
> [ 14.294423] iwlwifi 0000:03:00.0: RF_KILL bit toggled to disable radio.
[ 44.796665] iwlwifi 0000:03:00.0: RF_KILL bit toggled to enable radio.
[ 44.806634] iwlwifi 0000:03:00.0: RF_KILL bit toggled to disable radio.
[ 47.408995] iwlwifi 0000:03:00.0: RF_KILL bit toggled to enable radio.All we see is the switch going ON to OFF and back. Where is it now?```
rfkill list all
iwconfig
```Thanks.

---

### Post by VdubVidiot on 2012-06-16
*I turned switch on:*

brandon@brandon-Studio-1569:~$ rfkill list all iwconfig
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

*Now I turned switch off:*

brandon@brandon-Studio-1569:~$ rfkill list all iwconfig
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: dell-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: yes
2: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes

*I can see my wireless router and connect to it, but when I open firefox 13.0 it just spins its wheels.*
*Thank you for your interest in this* =D>

---

### Post by chili555 on 2012-06-16
Let's see if we can track down where it's going wrong. Please post:```
cat /sys/module/iwlwifi/parameters/11n_disable
route -n
ping -c3 192.168.1.1  [COLOR="Red"]<--or whatever the IP address of your router is[/COLOR]
ping -c3 8.8.8.8
```Thanks.

---

### Post by VdubVidiot on 2012-06-16
[COLOR=Blue]*With wifi switch on and my LAN cable disconnected:*[/COLOR]

brandon@brandon-Studio-1569:~$ cat /sys/module/iwlwifi/parameters/11n_disable
1
brandon@brandon-Studio-1569:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
brandon@brandon-Studio-1569:~$ ping -c3 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_req=1 ttl=254 time=6.94 ms
64 bytes from 192.168.0.1: icmp_req=2 ttl=254 time=4.65 ms
64 bytes from 192.168.0.1: icmp_req=3 ttl=254 time=4.72 ms

--- 192.168.0.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 4.653/5.442/6.948/1.065 ms
brandon@brandon-Studio-1569:~$ ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2014ms

brandon@brandon-Studio-1569:~$ 
[I][COLOR=Blue]
With my wifi switch on and LAN cable connected:[/COLOR][/I]

brandon@brandon-Studio-1569:~$ cat /sys/module/iwlwifi/parameters/11n_disable
1
brandon@brandon-Studio-1569:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
brandon@brandon-Studio-1569:~$ ping -c3 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_req=1 ttl=254 time=1.41 ms
64 bytes from 192.168.0.1: icmp_req=2 ttl=254 time=1.40 ms
64 bytes from 192.168.0.1: icmp_req=3 ttl=254 time=1.46 ms

--- 192.168.0.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 1.401/1.427/1.467/0.042 ms
brandon@brandon-Studio-1569:~$ ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_req=1 ttl=49 time=29.5 ms
64 bytes from 8.8.8.8: icmp_req=2 ttl=49 time=30.5 ms
64 bytes from 8.8.8.8: icmp_req=3 ttl=49 time=29.9 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 29.523/29.995/30.558/0.450 ms
brandon@brandon-Studio-1569:~$ 

[COLOR=Blue]*Thanks*[/COLOR]

---

### Post by chili555 on 2012-06-16
> With my wifi switch on and LAN cable connected:
Interesting. I'm sure the traffic is going through the ethernet.

Please click the Network Manager icon, edit connections, select wireless and take a look at the IPv4 tab like the attached. Are there any settings there that you added? If so, remove them all. 

Although my attachment is for wired, your wireless IPv4 tab should look the same: DHCP and the remainder blank. If not, as Picard says, make it so. Save and restart Network Manager:```
sudo service network-manager restart
```

---

### Post by VdubVidiot on 2012-06-16
> **chili555 said:**
> interesting. I'm sure the traffic is going through the ethernet.

Please click the network manager icon, edit connections, select wireless and take a look at the ipv4 tab like the attached. Are there any settings there that you added? If so, remove them all. 

Although my attachment is for wired, your wireless ipv4 tab should look the same: Dhcp and the remainder blank. If not, as picard says, make it so. Save and restart network manager:```
sudo service network-manager restart
```

[COLOR=Navy]*Here is what I had*[/COLOR]


[IMG]http://ubuntuforums.org/attachment.php?attachmentid=219807&stc=1&d=1339876512[/IMG]

---

### Post by chili555 on 2012-06-16
My favorite kind of problem; everything looks perfect except it doesn't work. With the ethernet cable detached, please show us:```
nm-tool
```Thanks.

---

### Post by VdubVidiot on 2012-06-16
> **chili555 said:**
> My favorite kind of problem; everything looks perfect except it doesn't work. With the ethernet cable detached, please show us:```
nm-tool
```Thanks.

[COLOR=Navy]*\\:D/\\:D/\\:D/*[/COLOR]

brandon@brandon-Studio-1569:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        F0:4D:A2:6E:7E:59

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         off


- Device: wlan0  [seitz] -------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        18:3D:A2:3C:6D:94

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    myqwest3899:     Infra, 00:24:7B:20:B6:9C, Freq 2412 MHz, Rate 54 Mb/s, Strength 80 WPA WPA2
    myqwest2485:     Infra, 00:24:7B:BF:13:F6, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    luckymagnolia:   Infra, 68:7F:74:98:42:A0, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA2
    qwest4640:       Infra, 00:24:37:0B:85:A0, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WEP
    *seitz:          Infra, 50:67:F0:F1:4F:9F, Freq 2447 MHz, Rate 54 Mb/s, Strength 75 WPA WPA2
    kendall:         Infra, 1C:7E:E5:3C:FB:3A, Freq 2417 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    hy:              Infra, 00:1B:11:55:BF:B3, Freq 2457 MHz, Rate 54 Mb/s, Strength 30 WEP
    Carrithers Wireless: Infra, 00:22:75:48:E1:E7, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    ChenChen:        Infra, 30:46:9A:67:87:88, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WEP
    NTG_WA2G:        Infra, 30:46:9A:F9:4B:02, Freq 2427 MHz, Rate 54 Mb/s, Strength 25 WPA2

  IPv4 Settings:
    Address:         192.168.0.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1
    DNS:             205.171.3.25

---

### Post by chili555 on 2012-06-16
> *seitz: Infra, 50:67:F0:F1:4F:9F, Freq 2447 MHz, Rate 54 Mb/s, Strength 75 [COLOR="Red"]WPA WPA2[/COLOR]You might have better luck if you set the router to use WPA2 only, not mixed mode WPA and WPA2. Will you please make that change and let us have your report?

Everything else looks perfect.

---

### Post by VdubVidiot on 2012-06-16
> **chili555 said:**
> You might have better luck if you set the router to use WPA2 only, not mixed mode WPA and WPA2. Will you please make that change and let us have your report?

Everything else looks perfect.



[IMG]http://ubuntuforums.org/attachment.php?attachmentid=219822&stc=1&d=1339897013[/IMG]

Made the changes and applied them..

Still seeing this.. 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=219823&stc=1&d=1339897013[/IMG]

:guitar:

---

### Post by VdubVidiot on 2012-06-17
I don't know how to install wireless drivers in Ubantu, but I located this "http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-6000-ucode-9.221.4.1.tgz"
It's a driver for my Centrino 6200 Advanced-N.

Do you advise that I attempt to install it? I have yet to find a description on how to do such a thing.

Thanks

---

### Post by fireandlce on 2012-06-17
> **chili555 said:**
> Intel chipsets have a known issue with 802.11N. Please do:

```
sudo gedit /etc/modprobe.d/iwlwifi.conf

```
Add a single line:

```
options iwlwifi 11n_disable=1
```

Proofread, save and close gedit. Reboot and let us hear your report.

I was having this same issue too and now it is fixed using this method. But is this permanent or do I need to add this to a blacklist so this problem doesn't happen again? If so, uuuh, how do I do that? Thanks!

P.S. First post! Only had Ununtu for a couple days now and I hope to stick to it!

---

### Post by wildmanne39 on 2012-06-18
Hi fireandlce, that fix is permanent.
Enjoy

---

### Post by VdubVidiot on 2012-06-22
> **VdubVidiot said:**
> I don't know how to install wireless drivers in Ubantu, but I located this "http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-6000-ucode-9.221.4.1.tgz"
It's a driver for my Centrino 6200 Advanced-N.

Do you advise that I attempt to install it? I have yet to find a description on how to do such a thing.

Thanks

Problem seems to have fixed itself after driver uninstall, reinstall and update on the windows side of my partition.

---

### Post by VdubVidiot on 2012-06-23
> **VdubVidiot said:**
> Problem seems to have fixed itself after driver uninstall, reinstall and update on the windows side of my partition.


Grrrrrrr. Everytime I close the laptop lid and re-open it, i have to reset my wireless router for it to work again. *Sad Panda*

---

### Post by chili555 on 2012-06-23
My pal the Wild Man is going to suggest you look at posts #2 and following here: [http://ubuntuforums.org/showthread.php?t=2004690&highlight=suspend](http://ubuntuforums.org/showthread.php?t=2004690&highlight=suspend)

---

### Post by rossmurray on 2012-07-18
Just wanted to show some love for this thread. I've had wifi at home, on my Samsung NC10 netbook running 12.04 LTS.The home wifi 802.11g from memory and the NC10 uses a Broadcom bcm4313. But when out and about trying to use public wifi (thecloud.net used in many cafes here in the UK - seemingly uses 802.11n) I was getting a connection supposedly but no data through. 

Yes that was me slamming the cover shut in disgust with many a coffee 'experience' ruined by having me staring blankly at a wall unless I brought my usb cable to tether via my Android phone. The following quoted fix sorted it for me and I even did a celebration dance as per requirements \\:D/

> **chili555 said:**
> Intel chipsets have a known issue with 802.11N. Please do:

```
sudo gedit /etc/modprobe.d/iwlwifi.conf

```
Add a single line:

```
options iwlwifi 11n_disable=1
```

Proofread, save and close gedit. Reboot and let us hear your report.

---

### Post by chili555 on 2012-07-18
Awesome! Glad it's working. I have never over-dosed on positive vibes, so thanks!

---

### Post by DJBurgess on 2012-12-20
A big thanks, Chili, for this solution to a little frustration with wireless N connectivity on my Acer 4830TG, with Intel Centrino Advanced-N 6205 Wifi controller.  I'm completely novice with Ubuntu, but impressed with gedit, and plan to learn more...

> **chili555 said:**
> Intel chipsets have a known issue with 802.11N. Please do:

```
sudo gedit /etc/modprobe.d/iwlwifi.conf

```
Add a single line:

```
options iwlwifi 11n_disable=1
```

Proofread, save and close gedit. Reboot and let us hear your report.

---

### Post by secundus12 on 2013-01-15
Hi. I seem to have a problem similar to that of maheshtatva (or, rather, more like that of rossmurray) -- that is, I can connect to public wifi ssid's, like attwifi, but my firefox never loads the login page that asks for my consent before I can then access any other site online. I often get messages to the effect that a server is not responding. However, I think I can ping through the open connection. This problem seems to be isolated to public internet connections because I can use my own home wireless connection without any difficulty. I don't know whether chili555's instructions at the beginning of this thread apply to my situation. If they do, the results to "lspci -nn | grep 0280" are in the following post.

---

### Post by secundus12 on 2013-01-15
Here is the result to "lspci -nn | grep 0280":

04:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)

---

### Post by chili555 on 2013-01-15
> I don't know whether chili555's instructions at the beginning of this thread apply to my situation. If they do, the results to "lspci -nn | grep 0280" are in the following post.No. Therefor, I suggest you start your own new thread.

---

