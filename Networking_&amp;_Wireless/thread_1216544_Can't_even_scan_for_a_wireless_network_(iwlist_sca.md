---
title: "Can't even scan for a wireless network (iwlist scan error)"
date: 2009-07-18
forum: Networking &amp; Wireless
---

### Post by StateOfMind140 on 2009-07-18
Problem:
Wireless doesn't even appear to be a connection option.
(Cannot scan for wireless networks)

_Info _
I'm running Ubuntu 8.0.4 and on a laptop using a "Intel Corporation PRO/Wireless 3945ABG Network Connection" as the wireless network controller. (common card)

My kernel version is "2.6.24-24-generic"

I have reason to believe this is a hardware problem and I might need to buy a new card, but I guess it can't hurt to ask for help on the software level first.

_Terminal output_

DMESG: [B]The physical device is detected.

[/B]john@john-laptop:~$ dmesg | grep 3945
[   26.685111] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   26.685114] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   26.685279] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   27.390947] iwl3945: Radio Frequency Kill Switch is On:
[   27.396106] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   27.406156] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   27.426124] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   27.453652] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   27.473596] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels

IWLIST: **Notice the interface doesn't even seem to exist**.

john@john-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

IFCONFIG: **Again where is wlan0??**

john@john-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:a8:9f:9d  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:fea8:9f9d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:73484 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44213 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:73241207 (69.8 MB)  TX bytes:4006579 (3.8 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2094 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2094 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:104700 (102.2 KB)  TX bytes:104700 (102.2 KB)

IWCONFIG: **wlan0 does NOT exist???**

john@john-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

john@john-laptop:~$ iwconfig wlan0
wlan0     No such device



Anyway, the main problem is that the card exists and the network exists (it's called netgear)

Thanks in Advance!

---

### Post by wojox on 2009-07-18
Try:

```
iwlist wlan0 scan
```

---

### Post by StateOfMind140 on 2009-07-18
Wow thanks for the fast reply, here the terminal output

[I]john@john-laptop:~$ iwlist wlan0 scan
wlan0     Interface doesn't support scanning.



[/I]

---

### Post by wojox on 2009-07-18
Don't know if you have been here:

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#check](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#check)

---

### Post by StateOfMind140 on 2009-07-18
Ok, I tried "sudo pccardctl ident", and i recieve no output, does that mean my card isn't recognized (it's physically broken)?

---

### Post by shamwow on 2009-07-18
Stateofmind140, I'm getting the same messages you are, so it's probably not your hardware. 

I'm an arrant newbie looking for a solution to my problem (version 9.04). My wireless worked right out of installation, but I suspect Ubuntu is connecting to a neighbor's network,  because it is unusably slow and  keeps crapping out. 

I just want to know how I can find out what wireless network I'm on and how I can make it automatically try to connect to my network. The 4 vertical bars at the top of my screen, I've been told, are supposed to provide me with what I need, but I have a red x on them and the drop down is grayed out. 

If there are possible troubleshooting scenarios, can someone please at a high level what they may be, or are there instructions on how to set up connectivity to a specific wireless router through the terminal interface?

Thanks, 
Shamwow

---

### Post by StateOfMind140 on 2009-07-18
Aha! i think i found the REAL source of the problem, if i do

john@john-laptop:/sys/bus/pci/drivers/iwl3945/0000:0c:00.0$ ls
antenna               enable        rate        subsystem_device
broken_parity_status  filter_flags  resource    subsystem_vendor
channels              flags         resource0   temperature
class                 irq           retry_rate  tune
config                local_cpus    rf_kill     tx_power
device                modalias      rs_window   uevent
driver                msi_bus       statistics  vendor
dump_errors           power         status
dump_events           power_level   subsystem
john@john-laptop:/sys/bus/pci/drivers/iwl3945/0000:0c:00.0$ cat rf_kill
2

See the Radio Frequency kill value is set to 2 THAT MEANS ENABLED, but i can't seem to change it...

Anyone know how?

---

### Post by StateOfMind140 on 2009-07-18
Wow i'm so stupid, i accidently turned off the switch on the side of my laptop that turns it on and off, wow... I feel like such an idiot now, 

EVERYONE ELSE:

Look around the side of your laptop, there should be a switch that turns on your radio from the hardware level.

---

