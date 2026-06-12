---
title: "madwifi installing errors"
date: 2009-02-23
forum: Networking &amp; Wireless
---

### Post by CurveBall on 2009-02-23
Hello everybody,

I'm trying to install the madwifi drivers for my atheros ar5211 wireless card. I'm running ubuntu 8.10 and my wireless does work already, but I'm learning how to use aircrack, and therefore I had to re-install my madwifi drivers (am I correct?).
I know that there are already a lot treads are about this, but I couldn't find a solution for my problem. I am using [this](http://madwifi-project.org/wiki/UserDocs/FirstTimeHowTo) guide. I'm having problems with the "make" command:

vincent@SatellitePro:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:00:39:43:28:f3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr 00:02:2d:7f:8e:84  
          inet addr:172.19.3.11  Bcast:172.19.255.255  Mask:255.255.0.0
          inet6 addr: fe80::202:2dff:fe7f:8e84/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2811 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2604 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2848372 (2.8 MB)  TX bytes:646767 (646.7 KB)
          Interrupt:11 Base address:0xd100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vincent@SatellitePro:~$ sudo ifconfig eth0 down
vincent@SatellitePro:~$ sudo ifconfig eth1 down
vincent@SatellitePro:~$ sudo ifconfig lo down
vincent@SatellitePro:~$ cd madwifi-0.9.4
vincent@SatellitePro:~/madwifi-0.9.4$ cd scripts
vincent@SatellitePro:~/madwifi-0.9.4/scripts$ sudo ./madwifi-unload.bash
vincent@SatellitePro:~/madwifi-0.9.4/scripts$ sudo ./find-madwifi-modules.sh $(uname -r)

WARNING:
It seems that there are modules left from previous MadWifi installations.
If you are unistalling the MadWifi modules please press "r" to remove them.
If you are installing new MadWifi modules, you should consider removing those
already installed, or else you may experience problems during operation.
Remove old modules?

[l]ist, [r]emove, [i]gnore or e[x]it (l,r,i,[x]) ? 
r
vincent@SatellitePro:~/madwifi-0.9.4/scripts$ cd ..
vincent@SatellitePro:~/madwifi-0.9.4$ make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.27-11-generic/build SUBDIRS=/home/vincent/madwifi-0.9.4 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
rm: cannot remove `/home/vincent/madwifi-0.9.4/.tmp_versions/ath_hal.mod': Permission denied
rm: cannot remove `/home/vincent/madwifi-0.9.4/.tmp_versions/ath_pci.mod': Permission denied
rm: cannot remove `/home/vincent/madwifi-0.9.4/.tmp_versions/ath_rate_amrr.mod': Permission denied
rm: cannot remove `/home/vincent/madwifi-0.9.4/.tmp_versions/ath_rate_minstrel.mod': Permission denied
rm: cannot remove `/home/vincent/madwifi-0.9.4/.tmp_versions/ath_rate_onoe.mod': Permission denied
rm: cannot remove `/home/vincent/madwifi-0.9.4/.tmp_versions/ath_rate_sample.mod': Permission denied
make[1]: *** [crmodverdir] Error 1
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make: *** [modules] Error 2
vincent@SatellitePro:~/madwifi-0.9.4$ sudo make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.27-11-generic/build SUBDIRS=/home/vincent/madwifi-0.9.4 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /home/vincent/madwifi-0.9.4/net80211/ieee80211_power.o
/home/vincent/madwifi-0.9.4/net80211/ieee80211_power.c: In function 'ieee80211_pwrsave':
/home/vincent/madwifi-0.9.4/net80211/ieee80211_power.c:240: error: implicit declaration of function '__skb_append'
make[3]: *** [/home/vincent/madwifi-0.9.4/net80211/ieee80211_power.o] Error 1
make[2]: *** [/home/vincent/madwifi-0.9.4/net80211] Error 2
make[1]: *** [_module_/home/vincent/madwifi-0.9.4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make: *** [modules] Error 2
vincent@SatellitePro:~/madwifi-0.9.4$ 


At the end it shows the error's. I think I have installed all of the requirements, but since I'm very new at all this, I could have done some things wrong at the installation of it. 
I hope someone can help me with this. I really looked around for this but couldn't find what I'm doing wrong. If there already is, I'm really sorry.

I would be very grateful if someone could help me :) !

Thanks in advance,

Vincent

---

### Post by binbash on 2009-02-23
try this : 

sudo make clean && make

---

### Post by CurveBall on 2009-02-23
> **binbash said:**
> try this : 

sudo make clean && make

No, it doesn't work...

---

### Post by CurveBall on 2009-02-24
I seem to have this with all the "make" commands. Is there something that I have to install to run the "make" command properly?

Thank you.

---

