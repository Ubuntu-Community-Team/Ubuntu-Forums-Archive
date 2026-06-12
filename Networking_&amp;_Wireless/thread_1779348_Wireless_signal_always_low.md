---
title: "Wireless signal always low"
date: 2011-06-10
forum: Networking &amp; Wireless
---

### Post by Haur on 2011-06-10
Hello

My wireless signal is really bad all of the time and the connection drops every now and then. I have been trying to find a solution but no dice. There are three other laptops in the house each with a different operating system, xp, win7 and osx10.6 and they all get good to great signals. So is there anything i can do or do i just have to bite the bullet and connect directly :(

Thanks for any help :)

```
Network controller: Intel Corporation Centrino Advanced-N + WiMAX 6250 (rev 57)
        Subsystem: Intel Corporation Centrino Advanced-N + WiMAX 6250 2x2 AGN
        Flags: bus master, fast devsel, latency 0, IRQ 41
        Memory at f0500000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>
        Kernel driver in use: iwlagn
        Kernel modules: iwlagn
        iwlagn 0000:03:00.0: loaded firmware version 41.28.5.1 build 33926
```

---

### Post by Haur on 2011-06-10
Would more information be helpful?

---

### Post by garvinrick4 on 2011-06-10
That driver does not work in N you have to make a config file and run at G. In your router you
also have to set the 2.4 range at mixed and not just N because you will be using g at 54Mb/s.
Open a terminal and copy and paste.
```
gksudo gedit /etc/modprobe.d/iwlagn.conf
```Now put this iine in below and save and close:
                                 [COLOR=#000000][FONT=Times New Roman][SIZE=3]
[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman][SIZE=3]options iwlagn 11n_disable50=1 11n_disable=1[/SIZE][/FONT][/COLOR]


[COLOR=#000000][FONT=Times New Roman][SIZE=3]Now reboot and will work. 
[/SIZE][/FONT][/COLOR]

---

### Post by garvinrick4 on 2011-06-10
When you run this it should show your card at AG now and should have dropped the N.
```
iwconfig
```

#Mine below is a bgn card notice it is 802.11bg now. Have found nothing to make this driver
work at N and it does not look like it will happen so 54Mb/s gets around pretty good and any machine or install I have will still get to N when using mixed:
rick@rick-HP:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Home"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: C0:C1:C0:C6:0A:EC   
          Bit Rate=54 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=52/70  Signal level=-58 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:875   Missed beacon:0
Router config below: click on thumbnail

---

