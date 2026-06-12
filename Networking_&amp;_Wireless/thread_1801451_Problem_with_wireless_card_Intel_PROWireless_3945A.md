---
title: "Problem with wireless card Intel PRO/Wireless 3945ABG"
date: 2011-07-10
forum: Networking &amp; Wireless
---

### Post by mwallacesd on 2011-07-10
Hello fellows, I turn off the wireless power button and turn it on but now it is not working. The wireless does not connect. The power led is blue:

Ubuntu 11.04 32 bits, notebook hp dv2000

**mwallacesd@TranHungDao:~$ sudo lshw -C network**
[sudo] password for mwallacesd: 
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 02
       serial: 00:18:de:6e:c6:28
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
        configuration: broadcast=yes driver=iwl3945  driverversion=2.6.38-8-generic firmware=N/A latency=0 link=no  multicast=yes wireless=IEEE 802.11abg
       resources: irq:43 memory:d4000000-d4000fff
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:08:08.0
       logical name: eth0
       version: 02
       serial: 00:16:d3:10:fd:2c
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
        configuration: autonegotiation=on broadcast=yes driver=e100  driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.71  latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII  speed=100Mbit/s
       resources: irq:20 memory:d4100000-d4100fff ioport:3000(size=64)

#########################################

**mwallacesd@TranHungDao:~$ iwconfig wlan0**
wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

#################################

**mwallacesd@TranHungDao:~$ ifconfig -a**
eth0      Link encap:Ethernet  HWaddr 00:16:d3:10:fd:2c  
          inet addr:192.168.1.71  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d3ff:fe10:fd2c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7311 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5291 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5636611 (5.6 MB)  TX bytes:1097180 (1.0 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:18:de:6e:c6:28  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

############################################
[B]
mwallacesd@TranHungDao:~$[/B]** nm-tool**

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            e100
  State:             connected
  Default:           yes
  HW Address:        00:16:D3:10:FD:2C

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.71
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl3945
  State:             unavailable
  Default:           no
  HW Address:        00:18:DE:6E:C6:28

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

#############################

**mwallacesd@TranHungDao:~$ rfkill list wifi**
1: hp-wifi: Wireless LAN
   Soft blocked: yes
   Hard blocked: no
2: phy0: Wireless LAN
   Soft blocked: yes
   Hard blocked: yes

---

### Post by chili555 on 2011-07-10
Please run and post, even if they produce no output:```
sudo rmmod -f hp-wmi
sudo rfkill unblock all
rfkill list all
```

---

### Post by mwallacesd on 2011-07-10
> **chili555 said:**
> Please run and post, even if they produce no output:```
sudo rmmod -f hp-wmi
sudo rfkill unblock all
rfkill list all
```


mwallacesd@TranHungDao:~$ sudo rmmod -f hp-wmi
[sudo] password for mwallacesd: 
mwallacesd@TranHungDao:~$ sudo rfkill unblock all
mwallacesd@TranHungDao:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

---

### Post by chili555 on 2011-07-10
> 2: phy0: Wireless LAN
Soft blocked: no
[COLOR="Red"]Hard blocked: yes[/COLOR]That implies that the switch is off. Can you manipulate the switch and get hard blocked: no when you rerun rfkill list all?

---

### Post by nm_geo on 2011-07-10
Man, Chili I hope he responds back I was thinking about getting one of those Intel 3945ABG mini-cards for my laptop just too see if it works.
It must be cool to have the driver built into the kernel.. well maybe not in his case..

---

### Post by mwallacesd on 2011-07-10
> **chili555 said:**
> That implies that the switch is off. Can you manipulate the switch and get hard blocked: no when you rerun rfkill list all?

No, it is not. It is on and the power led is blue. On the Gnome taskbar it is locked out and I cannot unlock.

Do you know if It is related with this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/796336](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/796336) ???

---

### Post by chili555 on 2011-07-10
It is not related, in my opinion. I think it is related to this: [http://ubuntuforums.org/showthread.php?t=1793994](http://ubuntuforums.org/showthread.php?t=1793994)

See posts #8 and following. I suggest you reload hp-wmi:```
sudo modprobe hp-wmi
```Now try variations on the usual key combination, such as Alt+Fwhatever, Ctrl+Fwhatever, etc. See if one gets the wireless working.> I was thinking about getting one of those Intel 3945ABG mini-cards for my laptop just too see if it works.
It must be cool to have the driver built into the kernelI have a Thinkpad with an Intel 3945ABG that works perfectly with everything I've run on it from 8.10 to 11.04. Recently, I've been running Debian on a USB key and, after I installed firmware, it runs perfectly. The problem is not the card or the driver in my opinion, it's the well-known outlaw hp-wmi.

---

### Post by mwallacesd on 2011-07-10
> **chili555 said:**
> It is not related, in my opinion. I think it is related to this: [http://ubuntuforums.org/showthread.php?t=1793994](http://ubuntuforums.org/showthread.php?t=1793994)

See posts #8 and following. I suggest you reload hp-wmi:```
sudo modprobe hp-wmi
```Now try variations on the usual key combination, such as Alt+Fwhatever, Ctrl+Fwhatever, etc. See if one gets the wireless working.I have a Thinkpad with an Intel 3945ABG that works perfectly with everything I've run on it from 8.10 to 11.04. Recently, I've been running Debian on a USB key and, after I installed firmware, it runs perfectly. The problem is not the card or the driver in my opinion, it's the well-known outlaw hp-wmi.


No choice my friend, after sudo modprobe hp-wmi the same error:

mwallacesd@TranHungDao:~$ rfkill list all
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
4: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

I'm cheking the link you post...Thank you.

---

### Post by mwallacesd on 2011-07-11
Any one else?
I don't know but I think that is related with this bug:
[https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/724292](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/724292)

Please, can you help.

---

### Post by chili555 on 2011-07-11
What possible evidence could you possibly have that it's related to microcode? The reason is quite evident and you posted it:> mwallacesd@TranHungDao:~$ rfkill list all
0: hci0: Bluetooth
Soft blocked: no
Hard blocked: no
2: phy0: Wireless LAN
Soft blocked: no
Hard blocked: yes > I turn off the wireless power button and turn it on but now it is not working.Did you read the link I gave you?```
The other problem might be the module hp-wmi. Laptops require a small module to translate key presses, primarily Function keys, to useful information, such as, "Please turn on the wireless, Mr. Kernel." Here is a very interesting post: http://ubuntuforums.org/showpost.php...2&postcount=20 The gist is that hp-wmi does, indeed, translate keypresses to action, but may be mapped to the wrong key. I suggest you try reloading hp-wmi:
Code:

sudo modprobe hp-wmi

Next, try the other Function combinations to see if 'hard blocked' changes to no. You can recall the previous terminal command with the Up arrow; keep trying:
Code:

rfkill list all


```Can you confirm you tried various combinations of keys and *_none_* of them changed the hard blocked?

---

### Post by mwallacesd on 2011-07-11
> **chili555 said:**
> What possible evidence could you possibly have that it's related to microcode? The reason is quite evident and you posted it:Did you read the link I gave you?```
The other problem might be the module hp-wmi. Laptops require a small module to translate key presses, primarily Function keys, to useful information, such as, "Please turn on the wireless, Mr. Kernel." Here is a very interesting post: http://ubuntuforums.org/showpost.php...2&postcount=20 The gist is that hp-wmi does, indeed, translate keypresses to action, but may be mapped to the wrong key. I suggest you try reloading hp-wmi:
Code:

sudo modprobe hp-wmi

Next, try the other Function combinations to see if 'hard blocked' changes to no. You can recall the previous terminal command with the Up arrow; keep trying:
Code:

rfkill list all


```Can you confirm you tried various combinations of keys and *_none_* of them changed the hard blocked?


Hey my friend I already did it. the button is ON and the led light is blue.
after I lot of 
sudo modprobe hp-wmi (I run it like as 8 times and restart then it is working now!!!

THANK VERY MUCH!!!!

---

### Post by chili555 on 2011-07-11
> it is working now!!!
Great job! Glad it's working.

---

