---
title: "Dell Wireless 4965 AGN sort of"
date: 2009-12-13
forum: Networking &amp; Wireless
---

### Post by sephox on 2009-12-13
Hi all, I am having a problem with my wireless adapter not functioning properly (including not lighting up my LED). My wireless switch is set to ON. The adapter is not present in ifconfig or nm-applet but is present in iwconfig, lspci, iwlist, and lshw. I am running Ubuntu 9.10 Karmic Koala on a DELL XPS M1210 Notebook with an Intel Pro wireless 4965AGN network adapter.

Here are some helpful outputs:

```
lspci | grep Kedron
0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

```

```
lshw -C network | head
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1f:3b:1c:b7:11
       width: 64 bits

```

```
iwconfig
wlan1     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

* ifconfig displays my wlan0 adapter which is a removable USB adapter I have been using in the meantime, but does not display wlan1

```
iwlist scan | grep wlan1
wlan1     Failed to read scan data : Network is down

```

```
sudo rmmod iwl4965
ERROR: Module iwl4965 does not exist in /proc/modules
```

* modprobe iwl4965 does nothing

```
sudo ifconfig wlan1 up
SIOCSIFFLAGS: Input/output error

```

```
dmesg | tail | grep -e iwlagn
[ 3694.739533] iwlagn 0000:0c:00.0: Unable to set up bootstrap uCode: -5
[ 3694.740141] iwlagn 0000:0c:00.0: BSM uCode verification failed at addr 0x00003800+32 (of 788), is 0x0, s/b 0x2069
[ 3694.740147] iwlagn 0000:0c:00.0: Unable to set up bootstrap uCode: -5
[ 3694.740735] iwlagn 0000:0c:00.0: BSM uCode verification failed at addr 0x00003800+32 (of 788), is 0x35fac00, s/b 0x2069
[ 3694.740741] iwlagn 0000:0c:00.0: Unable to set up bootstrap uCode: -5
[ 3694.741350] iwlagn 0000:0c:00.0: BSM uCode verification failed at addr 0x00003800+32 (of 788), is 0x0, s/b 0x2069
[ 3694.741361] iwlagn 0000:0c:00.0: Unable to set up bootstrap uCode: -5
[ 3694.741862] iwlagn 0000:0c:00.0: BSM uCode verification failed at addr 0x00003800+8 (of 788), is 0x0, s/b 0x2069
[ 3694.741873] iwlagn 0000:0c:00.0: Unable to set up bootstrap uCode: -5
[ 3694.752968] iwlagn 0000:0c:00.0: Unable to initialize device after 5 attempts.

```

* I have had no luck with sudo modprobe iwlagn either

Please help! :D

---

### Post by maraja on 2010-01-03
Hi,

same problem here on a Dell XPS 1330. I had not problems since using Ubuntu 32 bit now the wireless is working when she like; meaning sometimes it works right after the boot and sometimes I have to reboot few times before its reckognized (and the led is turned on).

Please see my comments at:
[http://ubuntuforums.org/showthread.php?p=8604718](http://ubuntuforums.org/showthread.php?p=8604718)

and please let me know if you found a stable solution.

---

### Post by zekecl on 2010-01-03
Hey guys, 

Don't know if this will help but I was just having this issue and after about 2 or 3 hours of installing backports trying other workarounds I found this [issue with 8.10]("http://www.ubuntu.com/getubuntu/releasenotes/810#Cannot%20reactivate%20Intel%203945/4965%20wireless%20if%20booting%20with%20killswitch%20enabled").Basically it said if you boot up with the wireless card disabled via the switch then you won't be able to re-enable it. 


I had tried many times to reboot with the switch set to wireless enabled with no luck.

So I actually did the opposite, I set the switch to disabled and then rebooted the system. Once the system was up I renabled the wireless via the switch and the wireless connected fine.

---

### Post by sephox on 2010-01-04
> So I actually did the opposite, I set the switch to disabled and then rebooted the system. Once the system was up I renabled the wireless via the switch and the wireless connected fine.

Hmm. I renabled the wireless switch in BIOS, then I tried turning the laptop off and back on with the wifi switch off, and then switching it on while the laptop was on. Ubuntu did not recognize that there were any wireless networks. It did not seem to notice that the switch had come on either.

---

### Post by gradinaruvasile on 2010-01-04
If you use 9.10, there is a program called rfkill:
Open a terminal, type:

rfkill list

what is the output of that command?

---

### Post by sephox on 2010-01-05
**rfkill list**
> 0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

---

### Post by maraja on 2010-01-23
there is a solution here:
[http://ubuntuforums.org/showpost.php?p=8710493&postcount=30](http://ubuntuforums.org/showpost.php?p=8710493&postcount=30)

---

### Post by Jerazol on 2011-01-11
This might also be relevant: [http://ubuntuforums.org/showthread.php?t=1604190](http://ubuntuforums.org/showthread.php?t=1604190)

---

