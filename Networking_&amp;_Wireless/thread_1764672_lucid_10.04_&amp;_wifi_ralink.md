---
title: "lucid 10.04 &amp; wifi ralink"
date: 2011-05-22
forum: Networking &amp; Wireless
---

### Post by jrev on 2011-05-22
Hi,
can you tell me where can I download the proper driver for my wifi module :
Ralink RT3090 ?

Ubuntu 10.04 propose the rt3090sta which is no good 

Thanks for your help :P

---

### Post by chili555 on 2011-05-22
Please open a terminal and run and post these two commands:```
lspci -nn
lsmod | grep -e rt2 -e rt3
```> Ubuntu 10.04 propose the rt3090sta which is no good "No good" doesn't tell us much; in what way is it no good? What does it not perform as expected?

---

### Post by jrev on 2011-05-22
sagnes@PC-IVENTIVE:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             connected
  Default:           yes
  HW Address:        40:61:86:1B:D2:72

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.14
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.254

    DNS:             212.27.40.240
    DNS:             212.27.40.241


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt3090
  State:             disconnected
  Default:           no
  HW Address:        40:61:86:3C:E3:92

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points

---

### Post by jrev on 2011-05-22
sagnes@PC-IVENTIVE:~$ lspci -nn
00:00.0 Host bridge [0600]: nVidia Corporation MCP79 Host Bridge [10de:0a83] (rev b1)
00:00.1 RAM memory [0500]: nVidia Corporation MCP79 Memory Controller [10de:0a88] (rev b1)
00:03.0 ISA bridge [0601]: nVidia Corporation MCP79 LPC Bridge [10de:0aae] (rev b3)
00:03.1 RAM memory [0500]: nVidia Corporation MCP79 Memory Controller [10de:0aa4] (rev b1)
00:03.2 SMBus [0c05]: nVidia Corporation MCP79 SMBus [10de:0aa2] (rev b1)
00:03.3 RAM memory [0500]: nVidia Corporation MCP79 Memory Controller [10de:0a89] (rev b1)
00:03.5 Co-processor [0b40]: nVidia Corporation MCP79 Co-processor [10de:0aa3] (rev b1)
00:04.0 USB Controller [0c03]: nVidia Corporation MCP79 OHCI USB 1.1 Controller [10de:0aa5] (rev b1)
00:04.1 USB Controller [0c03]: nVidia Corporation MCP79 EHCI USB 2.0 Controller [10de:0aa6] (rev b1)
00:08.0 Audio device [0403]: nVidia Corporation MCP79 High Definition Audio [10de:0ac0] (rev b1)
00:09.0 PCI bridge [0604]: nVidia Corporation MCP79 PCI Bridge [10de:0aab] (rev b1)
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP79 Ethernet [10de:0ab0] (rev b1)
00:0b.0 SATA controller [0106]: nVidia Corporation MCP79 AHCI Controller [10de:0ab9] (rev b1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP79 PCI Express Bridge [10de:0aa0] (rev b1)
00:15.0 PCI bridge [0604]: nVidia Corporation MCP79 PCI Express Bridge [10de:0ac6] (rev b1)
00:17.0 PCI bridge [0604]: nVidia Corporation MCP79 PCI Express Bridge [10de:0ac7] (rev b1)
02:00.0 VGA compatible controller [0300]: nVidia Corporation C79 [GeForce 9200M G] [10de:086f] (rev b1)
[B]06:00.0 Network controller [0280]: RaLink RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]
 [/B]

/sagnes@PC-IVENTIVE:~$ lsmod | grep -e rt2 -e rt3
rt3090sta             674536  1 
   
:P

---

### Post by chili555 on 2011-05-22
That's it??

I'm about 209 years old and my ability to guess or reach through the screen and see what's wrong by omniscience is pretty well shot. Would you care to just tell me what's wrong?

---

### Post by jrev on 2011-05-23
> **chili555 said:**
> That's it??

I'm about 209 years old and my ability to guess or reach through the screen and see what's wrong by omniscience is pretty well shot. Would you care to just tell me what's wrong?

My computer cannot connect to the Net through the wifi :P
connection OK with eth0

I tried this ;

sudo add-apt-repository ppa:markus-tisoft/rt3090
sudo apt-get update
sudo apt-get install rt3090-dkms

without success
for more details :
[http://forum.ubuntu-fr.org/viewtopic.php?id=505031](http://forum.ubuntu-fr.org/viewtopic.php?id=505031)
Thanks

---

### Post by chili555 on 2011-05-23
Post #3 shows you are connected with wired but not wireless. Network Manager is designed to disallow a wireless connection if wired is available. Please detach the ethernet cable, wait a few moments for NM to notice the change in state and click the NM icon. Do you see networks? What happens when you click yours and try to connect? May we see:```
dmesg | grep -e ra0 -e wlan
```Thanks.

[https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)> The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, **when the user plugs the computer back in, the computer should switch back to the wired connection**. The user should, most times, not even notice that their connection has been managed for them;

---

### Post by jrev on 2011-05-23
> **chili555 said:**
>  May we see:```
dmesg | grep -e ra0 -e wlan
```Thanks.


there is no answer to the above command line

---

### Post by chili555 on 2011-05-23
That can't be good. Let's see:```
sudo modprobe rt3090sta
dmesg | grep -e rt3 -e wlan
```Thanks.

---

### Post by jrev on 2011-05-24
> **chili555 said:**
> That can't be good. Let's see:```
sudo modprobe rt3090sta
dmesg | grep -e rt3 -e wlan
```Thanks.

There is no answer to any of those commands :

sagnes@PC-IVENTIVE:~$ dmesg | grep -e rt3 -e wlan
sagnes@PC-IVENTIVE:~$ sudo modprobe rt3090sta
[sudo] password for sagnes: 
sagnes@PC-IVENTIVE:~$ sudo modprobe rt3090sta
sagnes@PC-IVENTIVE:~$ 
sagnes@PC-IVENTIVE:~$ dmesg | grep -e rt3 -e wlan
sagnes@PC-IVENTIVE:~$

---

### Post by chili555 on 2011-05-24
Let's see:```
modinfo rt3090sta | grep 3090
modinfo rt2860sta | grep 3090
```Thanks.

---

### Post by jrev on 2011-05-25
The solution was to upgrade to Ubuntu 10.10 
the Wifi works fine   :P

---

### Post by jrev on 2011-05-25
Thanks to everybody who tried to help me

---

