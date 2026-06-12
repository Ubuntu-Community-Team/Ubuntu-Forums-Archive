---
title: "&quot;Wireless is disabled&quot; for all wifi with 10.04 on Asus A2500H"
date: 2010-06-16
forum: Networking &amp; Wireless
---

### Post by ssum on 2010-06-16
Hi there,

having problems with wireless on my old Asus A2500H laptop, NetworkManager applet keeps the "enable wireless" greyed out and gives a "Wireless is disabled" for each wirelss network card. The wireless cards in this laptop are:

```

00:0c.0 Network controller: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller (rev 02)
02:00.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)

```It does look like the network interface come up fine as well:

```

wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
wlan1     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off

```Kernel detects the internal as well as the pcmcia card just fine, only gives this error for the internal card:

```

b43legacy-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.

```The rfkill list says something similar as well:

```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```Of course the easy solution would be to just flick that hardware switch on, however there isn't any hardware button only a indicator light, which is off unfortunately.

Any clues to get wifi up? Also tried another pcmcia card but same problem, card is recognized but still "Wireless is disabled". Thanks in advance for any help.

---

### Post by Boompoet on 2010-06-18
Yup, same here. The problem is, out of all the replies, there seems to be the common solution of plugging in and updating drivers. The problem is, I am in a hotel and can't plug in.... nothing to plug in to. 

The Fn key and F key combination seems disabled so I can't turn the wireless card on in the laptop.

If updates are available in a package, that'd be great. I could download with windows 7 and then switch over and run the updates.

---

### Post by prabin-dahal on 2010-11-26
I don't know about you but 
when I tried this command My laptop's wireless was enabled again..

rfkill unblock wlan

---

### Post by pfoff on 2011-03-19
BUMP!
I've this problem here, too!
After rfkill enable all nothing changes, it stays hard blocked. There is no WLAN Switch and all <FN> key combos didn't work neither....
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
Help needed!

---

### Post by nm_geo on 2011-03-19
Try Fn -F2 some asus laptops.

Also see this link>

[http://ubuntuforums.org/showthread.php?p=9795250](http://ubuntuforums.org/showthread.php?p=9795250)

---

