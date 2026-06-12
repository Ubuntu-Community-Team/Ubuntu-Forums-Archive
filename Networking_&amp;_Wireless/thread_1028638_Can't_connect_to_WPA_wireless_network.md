---
title: "Can't connect to WPA wireless network"
date: 2009-01-02
forum: Networking &amp; Wireless
---

### Post by Emanuele_Z on 2009-01-02
Hi all, I can't connect on a WPA wireless network (I have password long 10 chars [A-Z][0-9]). In Windows XP it works without any issue.

I'm posting the output of **sudo iwlist scan**
```

...          Cell 03 - Address: 00:1D:68:F0:A9:4F
                    ESSID:"ThomXXXXXXXXX"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=82/100  Signal level:-52 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000074f8f575e3
                    Extra: Last beacon: 1252ms ago

...

```

When I enter the same password (**WPA & WPA2 Personal** is the default dialog) that I enter in Windows XP (10 chars all letters uppercase) it hangs and then disconnects. If I save the password and then I ask to visualize it I see an hash (could be sha1 or md5)? Why?

Can you please help me, please?
I'm using Ubuntu 8.10; the wireless network card is working on other connections (eg. not broken).

Thanks in advance,

Ema! :-)

---

### Post by Emanuele_Z on 2009-01-03
Btw the network controller name is:
```

02:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

```

Has anyone any idea why I can connect with Windows XP but not Ubuntu?

Cheers,
Thanks again,

---

### Post by Kevbert on 2009-01-03
Please enter the following commands and post the result:
```
iwconfig
ifconfig

```

---

### Post by Emanuele_Z on 2009-01-03
**iwconfig**
```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"XXXXXXXXX"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:21:29:7A:1D:E0   
          Bit Rate=48 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=67/100  Signal level:-67 dBm  Noise level=-94 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

**ifconfig**
```

eth0      Link encap:Ethernet  HWaddr 00:1d:60:ae:34:24  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:468 errors:0 dropped:0 overruns:0 frame:0
          TX packets:468 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:24276 (24.2 KB)  TX bytes:24276 (24.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:13:e8:c1:0f:73  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:e8ff:fec1:f73/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12775 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10254 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10192287 (10.1 MB)  TX bytes:2231163 (2.2 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-E8-C1-0F-73-66-37-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

Keep in mind that the iwconfig is when I'm connected to **another (working) wireless network**. In this case it's working.
Want me to post the iwconfig and ifconfig when I try to connect to the not working WPA network?

Thanks in advance,
Ema! :-)

---

### Post by Kevbert on 2009-01-03
Can you connect to the non-working WPA connection if you disable encryption ?  Is the source restricted by walls or clear line of sight ? It may be that the signal is so low and data is being corrupted.
Maybe the wpasupplicant package is corrupted - you could try re-installing/repairing this via Synaptic.

---

### Post by Emanuele_Z on 2009-01-03
Hi,

1) I can't control the router directly.
2) The reception is 95%~100%.
3) It works without any issue in Windows XP.

Anyone has any idea?
Why when I input the password and then I ask to see it, from 10 chars it becomes like the sha1 (or md5)?
How to repair via apt-get?

Cheers,

---

### Post by Kevbert on 2009-01-03
You could try in terminal
```
sudo apt-get install -f
```
which should force a repair on any damaged packages. Another command to try is
```
sudo apt-get check
```
which will check for broken dependencies.

Edit: Just found a bug [[COLOR="Red"]report[/COLOR]]("https://bugs.edge.launchpad.net/ubuntu/intrepid/+source/wpasupplicant/+bug/272185") for Intrepid (which may be your problem).  It may be worth adding a comment.

---

### Post by Emanuele_Z on 2009-01-03
Hey guys, this is my wpa_supplicant.log when I try to connect to that network:
```

CTRL-EVENT-SCAN-RESULTS 
No network configuration found for the current AP
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
No network configuration found for the current AP
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
No network configuration found for the current AP
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
No network configuration found for the current AP
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
No network configuration found for the current AP
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
No network configuration found for the current AP
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
No network configuration found for the current AP
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
No network configuration found for the current AP
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
No network configuration found for the current AP
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys

```
Remeber that in Windows XP it works a treat and actually the reception is 82%~95%.

Cheers,

---

### Post by Kevbert on 2009-01-04
The solution should be to install alternative drivers, see [[COLOR="Red"]this[/COLOR]]("http://ubuntuforums.org/archive/index.php/t-963924.html") link.

---

### Post by Emanuele_Z on 2009-01-04
Anyone has any possible solution?

Cheers,

---

### Post by marcellosales on 2009-01-20
Hello everyone,

I've been using Ubuntu since 7.10 and I had never had a problem through the 8.04 and then 8.10 got this wireless problem... I was having this same issue: the 2 green dots kept trying to connect with the WPA wireless network and then hang up... It would not connect to any wireless network... 

After reading the wpasupplicant bug [https://bugs.edge.launchpad.net/ubuntu/intrepid/+source/wpasupplicant/+bug/272185](https://bugs.edge.launchpad.net/ubuntu/intrepid/+source/wpasupplicant/+bug/272185) and decided to reinstall the package "wpasupplicant"...

IT WORKED!!! I can connect to the wireless again!!!!

sudo apt-get install --reinstall wpasupplicant

Thanks!
Marcello

---

### Post by Belin on 2009-02-02
> **marcellosales said:**
> Hello everyone,

I've been using Ubuntu since 7.10 and I had never had a problem through the 8.04 and then 8.10 got this wireless problem... I was having this same issue: the 2 green dots kept trying to connect with the WPA wireless network and then hang up... It would not connect to any wireless network... 

After reading the wpasupplicant bug [https://bugs.edge.launchpad.net/ubuntu/intrepid/+source/wpasupplicant/+bug/272185](https://bugs.edge.launchpad.net/ubuntu/intrepid/+source/wpasupplicant/+bug/272185) and decided to reinstall the package "wpasupplicant"...

IT WORKED!!! I can connect to the wireless again!!!!

sudo apt-get install --reinstall wpasupplicant

Thanks!
Marcello

Thanks for this suggestion!

I'm using a Dell Inspiron 6400 and now It seems works fine (I hope!).

I used this guide to install the driver:

[http://www.ubuntu1501.com/2008/04/ndiswrapper-in-hardy-heron.html](http://www.ubuntu1501.com/2008/04/ndiswrapper-in-hardy-heron.html)

and I finished with the command:

sudo apt-get install --reinstall wpasupplicant


Regards!

- Belin - 

PS: Sorry for my bad English! :P

---

### Post by stevelove on 2009-03-23
I've been experiencing this same problem on a couple different laptops and different networks.

In my case, I found the problem was WPA2 security using TKIP algorithms. Apparently WPA2 is meant to use AES algorithms, but can be used with TKIP for backward compatibility. (Correct me if any of that is wrong.)

I tried all the solutions out there. It was only when I switched my router's security settings to WPA2 using AES algorithms that I was able to connect.

Hope this helps others.

---

### Post by BkkBonanza on 2009-03-23
I have the same wifi card as the original poster, Intel 4965. Have been using Ubuntu and accessing WPA2 router. The regular default drivers should be fine with that. I originally had problems too but likely different reasons. But I can tell you what is working for me.

I use wicd instead of the normal network manager. It can be installed from synaptic package manager and has more options. It also has a log file that enabled me to see what was wrong with my config to get wpa_supplicant to work for WPA2. For this reason you may want to try it out.

What I did in the end was use wpa_supplicant from the command line with the config file that was being used by wicd. I found that there was a problem with the driver being used for encryption and also that I had given it a passphrase incorrectly. Turns out the tutorial on here was wrong about that and I didn't know until I traced it down this way.

The single most useful clue came from running wpa_supplicant like below because it then gave me all the debug messages.

sudo wpa_supplicant -i wlan0 -c "/var/lib/wicd/configurations/001d7e401290" -D wext -d

Note that the numeric filename above was created by wicd. Once I saw the debug messages I was able to edit that config and see it work. Then I figured out what was wrong in wicd gui interface and altered that. After that it worked great. Trying the above command gave me answers. 

You should see it try to associate to the AP, then connect, then authenticate, then retrieve an ip using dhcp. You can see what step it's failing at.

---

