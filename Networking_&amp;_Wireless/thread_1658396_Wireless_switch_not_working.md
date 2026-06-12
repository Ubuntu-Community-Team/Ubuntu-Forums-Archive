---
title: "Wireless switch not working"
date: 2011-01-02
forum: Networking &amp; Wireless
---

### Post by DBS_Paul on 2011-01-02
I just installed 10.10 on my HP dv2700 laptop and I can't get the wireless card to turn on.  Here are some of my results.  I get the same results regardless of which position the wireless switch is in and the indicator light always indicates that the wireless is off. 


paul@paul-HLaptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
paul@paul-HLaptop:~$ sudo ifconfig wlan0 up
[sudo] password for paul: 
Sorry, try again.
[sudo] password for paul: 
SIOCSIFFLAGS: Operation not possible due to RF-kill
paul@paul-HLaptop:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
paul@paul-HLaptop:~$

07:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
    Subsystem: Intel Corporation Vaio VGN-SZ79SN_C
    Physical Slot: 5
    Flags: bus master, fast devsel, latency 0, IRQ 47
    Memory at f4300000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlagn
    Kernel modules: iwlagn

---

### Post by PatchesTheCaveman on 2011-01-02
Hi DBS_Paul!

Download the rfkill package:
```
sudo apt-get install rfkill
```

And use it to check if your wireless card is soft or hard blocked:
```
sudo rfkill list
```

If it's hard-blocked flip your wireless switch and try again.

If it's soft-blocked, unblock it with this command:
```
sudo rfkill unblock 0
```

---

