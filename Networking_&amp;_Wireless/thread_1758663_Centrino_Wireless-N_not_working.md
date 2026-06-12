---
title: "Centrino Wireless-N not working"
date: 2011-05-14
forum: Networking &amp; Wireless
---

### Post by pee_gee_l on 2011-05-14
Hi,
I've just updated my HP Pavilion laptop to 11.04, and my wireless has stopped working. I don't appear to be able to detect any wireless networks. The wireless card switch is a touch-type lighted button - when I press it, nothing happens whereas in Windows it changes colour to show it is on/off. It used to blink in the previous Ubuntu installation when it was working. The output of lspci-v for my wireless card is:

> 02:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
	Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN
	Flags: bus master, fast devsel, latency 0, IRQ 48
	Memory at d9000000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn


I'm no linux expert, so please let me know what other info/outputs you might need to help. I appreciate it!

---

### Post by thelight68 on 2011-05-15
Same problem to my laptop (lenovo y560)!
Anyone please help?

---

### Post by pee_gee_l on 2011-05-15
Update: my card seems to be working fine now. I can turn it on and off in Ubuntu and it acts as it should. I have no idea why...

I had logged in to Windows and turned the card on, then rebooted and logged back in to Ubuntu and now everything seems to be working properly.

---

### Post by garvinrick4 on 2011-05-15
> 02:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
    Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN
    Flags: bus master, fast devsel, latency 0, IRQ 48
    Memory at d9000000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlagn
    Kernel modules: iwlagn
The wireless driver iwlagn for that intel card works fine in G but will not work if you
as an N card. If you try to use N it will slowly lose connection or just go real slow.
You can check in /etc/modprobe.d  for a config file if having connection problems. If
need a config file to make card usable see below: intell 5300 will work if already there also.
This is a must for 11.04 with Intel  Centrino wireless N 1000 if router set to work
at N speeds at mixed 20 and 40 mhz or just 40 mhz. If no other installs can just set router at G speeds and 20 mhz and will work fine without config file.

Fix is to make a config file and put this in.
```
gksudo gedit /etc/modprobe.d/iwlagn.conf
```Now put this line in and close and reboot.
                     ```
options iwlagn 11n_disable50=1 11n_disable=1
``` Makes the card just use the G capabilities in Linux.
If you dual boot can still run at 144 mb/s or N in windows.
Can run at 54 mb/s in linux (still plenty fast enough)
If anyone wants to know if they have N running in this card run
```
iwconfig 
```and N should not show up. Such as:
 IEEE 802.11[COLOR=Red]bg[/COLOR]  ESSID:"Home"  (notice no n just bg)
          Mode:Managed  Frequency:2.412 GHz  Access Point: C0:C1:C0:C6:0A:EC   
          Bit Rate=1 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr off   Fragment thr off
          Power Management off
          Link Quality=52/70  Signal level=-58 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid f rag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by smirarab on 2011-06-12
.

---

### Post by smirarab on 2011-06-12
Thanks for the reply. I was facing the same problem and your suggested solution of turning N mode off solved my problem. 

Just wondering though, when you say
"If no other installs can just set router at G speeds ..." what do you mean by "no other installs"? 

Basically, I am wondering if there is a way to keep the wireless card running in the N mode and still make it compatible with 11.04?

---

