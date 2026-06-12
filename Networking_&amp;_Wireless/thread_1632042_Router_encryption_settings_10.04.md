---
title: "Router encryption settings 10.04"
date: 2010-11-27
forum: Networking &amp; Wireless
---

### Post by hodad on 2010-11-27
Using a D-Link wireless router, trying to get it through the authentication process with the client through a D-Link DWA-125 USB wireless.  When I set encryption to "none" on both ends, the router links up OK, but when I enter matching encryption settings on the router, and then in the driver data file (RT2870STA.dat) on the client side, I can't get it to authenticate.   I've tried all possible combinations in the .dat file with no luck.  I'm fairly well convinced that there is a bug in the .dat file settings, and that the wireless port setting need to be forced at startup through the /etc/networking/interfces file, or some such procedure, to override the settings in the .dat file.


Router wireless encryption settings:
WPA Personal
WPA2
TKIP
<password>

.dat file settings:
AuthMode=WPA2PSK 
EncrypType=TKIP
WPAPSK=<password> 

**********************************************************
Present readings:
desktop:~$ ping 192.168.0.1
connect: Network is unreachable

desktop:~$ iwlist ra0 scan
ra0       Scan completed :
          Cell 01 - Address: 00:1E:58:E8:F5:DB
                    Protocol:802.11b/g/n
                    ESSID:"axmey"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:100/100  Signal level:-29 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:""  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.437 GHz  Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:-33 dBm  Noise level:-33 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: 20:cf:30:56:26:ae
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
       resources: irq:26 ioport:e800(size=256) memory:fdfff000-fdffffff(prefetchable) memory:fdff8000-fdffbfff(prefetchable) memory:febf0000-febfffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: ra0
       serial: 1c:bd:b9:80:71:a6
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN driverversion=2.4.0.1 multicast=yes wireless=Ralink STA

********************************************************

Any idea how I can set client settings through a shell file, or some other way, to get it to match the router settings?

Thanks!

---

### Post by chili555 on 2010-11-27
> IE: [COLOR="Red"]WPA Version 1[/COLOR]
Group Cipher : TKIP
Pairwise Ciphers (1) : TKIP
Authentication Suites (1) : PSK
IE: IEEE 802.11i/[COLOR="Red"]WPA2 Version 1[/COLOR]
Group Cipher : TKIP
Pairwise Ciphers (1) : TKIP
Authentication Suites (1) : PSK
It appears the router is set for mixed WPA and WPA2. Something in the system, either the driver, Network Manager or wpa_supplicant doesn't like that method. Try WPA *OR* WPA2, not mixed.

---

### Post by hodad on 2010-11-27
Hi, Chili!

Thanks again for your help solving my earlier connection problem.

Hopefully this thread will be alot shorter than that one!!!

Anyway, I tried doing  WPA,, WPA2, and Mixed, and tried all possible combinations of the 3 lines in question in the .dat file,   It felt a lot like when we were working with the older driver on the DWA-125; i.e., nothing that I tried made any difference at all.  The router setup clearly offers both WPA and WPA2, and lists TKIP and PSK algorithms.

I did subsequently try working from outside of the .dat file using  iwconfig and other commands.  I was trying to force the encryption settings on the ra0 port; that  didn't accomplish anything either.  

ra0 is happy as a clam with no encryption, but don't want to run it that way,even if I am in the boonies. 

My best guess is that it's still something in the Ralink driver "C" source code files, because it seems to make no difference what I put into the three lines in RT2870STA.dat (though it does work when I put in "NONE" for encryption on both ends...)

---

### Post by hodad on 2010-11-28
I'vee tried several hours of playing around with the RT2870STA.dat file settings to no avail (except for NONE (no encryption)).

Started reading aboput wpa_supplicant and WPA, and I saw a suggestion that Update (Synaptic) might help, so I did that - Result - wiped out ra0 wireless port. Now it doesn't show up on ifconfig anymore.  Lots of posts on this problem, it seems to be very commonplace,  but I haven't seen any solutions that work in my case.

Any idea what got hosed with update?  Gotta figure out what happened to ra0 before I can play around with encryption settings.

THanks!

---

### Post by hodad on 2010-11-28
Chili, see PM for documentation of DWA-125 problem - its a rough draft, will continue working on it...

---

### Post by hodad on 2010-11-28
file attached

---

### Post by hodad on 2010-11-28
Got it back online.

I used lsmod | grep -e rt2 rt3, and found that somehow the pc had reverted to rt2870sta.   I did a recompile of rt3370sta (along with the other neessary steps), and the DWA-125 came back on port ra0.

Still have the encryption problem, though.  I'm operating wireless in clear mode for now...

---

### Post by hodad on 2010-11-28
Got it back online.

I used lsmod | grep -e rt2 rt3, and found that somehow the pc had reverted to rt2870sta.   I did a recompile of rt3370sta (along with the other neessary steps), and the DWA-125 came back on port ra0.

Still have the encryption problem, though.  I'm operating wireless in clear mode for now...

---

### Post by hodad on 2010-11-28
I got the little bugger back up by recompiling the rt3370sta driver. I noticed that the rt2870sta driver was back, for some reason, and that the config.mk file had the "wpa_supplicant..." values changed back to "N"  (don't ask me how?!)

I changed the values, recompiled, copied the .dat file, made some minor changes in it (as before), reloaded rt3370sta driver, and it worked upon reboot. (go figure!).

Encryption still doesn't work, though.

---

