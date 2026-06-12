---
title: "Weak Wireless Signal"
date: 2013-03-26
forum: Networking &amp; Wireless
---

### Post by the_hawk22 on 2013-03-26
I have a very weak 1 bar wireless signal. The same laptop has a strong wireless signal in Windows 8. Other laptops and phones in the exact same location will also have a strong wireless signal. 

For the above reason, I'm pretty sure it's Ubuntu-related with the wireless driver, but not sure how to proceed. 

Here is the output of iwconfig. Would appreciate any help getting this fixed. Roommates named our network CIA :-)

```
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"CIA"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 30:46:9A:67:E9:D7   
          Bit Rate=18 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=31/70  Signal level=-79 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:18  Invalid misc:855   Missed beacon:0

```

Laptop model: Asus S400CA

---

### Post by ChristianWiles on 2013-03-26
It is probably something to do with the drivers.

---

### Post by the_hawk22 on 2013-03-26
Obviously... 

```
lspci -nn:
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9485 Wireless Network Adapter [168c:0032] (rev 01)

```


168c:0032 is not found on [http://cateee.net/lkddb/web-lkddb/PCI.html](http://cateee.net/lkddb/web-lkddb/PCI.html)

Searching just "[COLOR=#000000][FONT=monospace]168c" at the above link does show ath9k driver supports older versions of this wireless card, if I understand correctly. 
[/FONT][/COLOR]
Can anyone with the expertise confirm that I'm understanding correctly so that I can move on?

---

### Post by ahallubuntu on 2013-03-26
~

---

### Post by kurt18947 on 2013-03-27
In addition to what ahallubuntu suggested, what is the status of your power management?  You can tell by running "iwconfig":
  > 
...........
long limit:7   RTS thr Off   Fragment thr Off
          **Power Management:Off**
          Link Quality=31/70  Signal level=-79 dBm  

If power management is on, some find it can reduce signal strength.  Turning power management off can hurt battery life though.  If your power management is on and you want to turn it off, you can do so via a terminal command:
```
sudo iwconfig wlanx power off
```  where wlanx=wlan number from iwconfig, e.g. wlan0, wlan1 etc.  Be aware that rebooting (logging out? dunno) will reset power state to the default.

---

### Post by the_hawk22 on 2013-03-27
I've read on other threads to try disabling hardware encryption and it hasn't helped. I also have the same issue with power management on and off. 

I think I need to upgrade to the latest version of the ath9k driver. Does anyone know a straight forward way to do that? In windows, I would just download and double-click the driver, but it's not proving to be so simple in Ubuntu.

---

### Post by the_hawk22 on 2013-03-29
So I updated to the latest ath9k driver and still no luck. Based on my conversation in the ath9k mailing list, there is a bug with this driver. I reported it here: [https://bugzilla.kernel.org/show_bug.cgi?id=55901](https://bugzilla.kernel.org/show_bug.cgi?id=55901)

---

### Post by mharv on 2013-03-30
The driver does not support some new feature in the hardware yet which is required for maximum performance. If the Windows drivers gives you full bars then use NDISwrapper to use the Windows driver which apparently has better support for the card (At least until a new Linux version comes out that fixes it). 
[http://en.wikipedia.org/wiki/NDISwrapper](http://en.wikipedia.org/wiki/NDISwrapper)

---

### Post by the_hawk22 on 2013-04-01
This sounds like the right thing to do, but does ndiswrapper only work with Windows XP drivers or should it work for any Windows driver?

---

### Post by kurt18947 on 2013-04-02
XP only.  I think some have gotten other Windows drivers to work but I sure wouldn't count on it.

---

### Post by wildmanne39 on 2013-04-02
I have the same card in my new laptop and I just added that driver parameter and set wireless settings to match the screenshots and it works great.
Using 12.04.2
If you are not sure the parameter is added correctly remove it and run:
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```  if possible.
Also set encryption to just wpa2
Thanks

---

### Post by brucedunn on 2013-10-25
This driver problem behind this issues has been identified.  When I upgraded from Ubuntu 13.04 or 13.10, the problem was solved.

---

