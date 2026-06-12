---
title: "iwconfig settings on boot?"
date: 2013-02-25
forum: Networking &amp; Wireless
---

### Post by jbuczek on 2013-02-25
I have 5 workstations, usually close together, sharing my internet connection via an Edimax Wireless router and cheap USB dongles where WIFI is not built in. All run either Ubuntu 12.04 or Lubunty 12.04.
My ISP connection is via a 7 km WIFI link on a 100' tower.

I replaced the hard wired connections after a nearby lightning strike apparently affected the long ethernet cable and cooked one expensive motherboard and the router.

Since doing this my download speed is often way down and the wifi often locks up requiring booting the router and/or the long link transmitter.  After noticing that the more machines in use the worse the problem seemed to be, the ISP suggests that all the units may be putting out too much power and drowning each other.

After research I used iwconfig to find out that all but one had txpower=20 and the oddball had txpower=37.

I used: (for example)

 >sudo iwconfig wlan0 txpower 5

on all units and still got link qualities > 55/70 and the quality seemed to improve but I could not test extensively because the setting reverts to full power on boot.

Where can I put this command so it will be executed on every boot at an appropriate point in the booting process?

I've found instructions for start up scripts during logon but I have no idea what the wifi system does when no one is logged on.  For all I know it may still be checking updates, etc. and affecting other workstations.
Without that knowledge it seems more appropriate to put the setting in the boot sequence

TIA

---

### Post by chili555 on 2013-02-25
I suggest you try it in /etc/rc.local:```
<snip>

# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

iwconfig wlan0 txpower 5

exit 0

```Reboot and check:```
iwconfig
```> wlan0     IEEE 802.11abgn  ESSID:"my_router"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 99:13:10:62:8D:77   
          Bit Rate=54 Mb/s   [COLOR="Red"]Tx-Power=5 dBm  [/COLOR] 
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


---

### Post by jbuczek on 2013-02-25
Thank You.  That appears to do the job!

---

