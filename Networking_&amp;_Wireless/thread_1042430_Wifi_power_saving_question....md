---
title: "Wifi power saving question..."
date: 2009-01-17
forum: Networking &amp; Wireless
---

### Post by Oranjjje on 2009-01-17
I dual boot XP and Ubuntu on my Acer Aspire One.

I used to get numerous network hangups while playing online poker which drove me crazy. I figured the root cause was the wifi power saving feature as I didn't get any hangups if I kept pinging my router in the background while playing.

On XP, I easily disabled the power saving mode for the wireless interface and never got that problem again.

On Ubuntu, I cannot figure how to do this. I checked [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne) and it claims wifi power saving is now fully functional with the Ibex version but I can't find how to disable it or at least configure it anywhere. I'm using the MadWifi driver.

I'd appreciate it very much if someone could help me with this problem.

---

### Post by pepitux on 2009-04-29
I too would like know how fit out the wifi power saving switch. I've got a Aspire One and Ubuntu 8.10

---

### Post by t0mppa on 2009-04-29
Now that I think about it, I've run into this a few times as well. Might have something to do with:

[QUOTE="MadWifi readme"]The ath_hal module contains the Atheros Hardware Access Layer (HAL).
This code manages much of the chip-specific operation of the driver. 
The HAL is provided in a binary-only form in order to comply with FCC
regulations.  In particular, a radio transmitter can only be operated at
power levels and on frequency channels for which it is approved.  The
FCC requires that a software-defined radio cannot be configured by the
user to operate outside the approved power levels and frequency
channels.  This makes it difficult to open-source code that enforces
limits on the power levels, frequency channels and other parameters of
the radio transmitter.  See
[http://ftp.fcc.gov/Bureaus/Engineering_Technology/Orders/2001/fcc01264.pdf](http://ftp.fcc.gov/Bureaus/Engineering_Technology/Orders/2001/fcc01264.pdf)
for the specific FCC regulation.[/QUOTE]

---

### Post by chili555 on 2009-04-29
> On Ubuntu, I cannot figure how to do this.I think it is disabled by default. Please see *iwconfig*:```
iwconfig wlan0
wlan0     IEEE 802.11abg  ESSID:"mylilrouter"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 99:24:56:2A:XX:YY   
          Bit Rate=54 Mb/s   Tx-Power=14 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          [COLOR="Red"]Power Management:off[/COLOR]
          Link Quality=57/70  Signal level=-53 dBm  Noise level=-127 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```This is from *man iwconfig*:> **power**  Used to manipulate power management scheme parameters and  mode. To  set  the  period between wake ups, enter period ‘value’.  To set the timeout  before  going  back  to  sleep,  enter  timeout ‘value’.  To set the generic level of power saving, enter saving ‘value’.  You can  also  add  the  min  and  max  modifiers.  By default,  those  values are in seconds, append the suffix m or u to specify values in milliseconds  or  microseconds.  Sometimes, those values are without units (number of beacon periods, dwell, percentage or similar). off and on disable and reenable power management.  Finally,  you may  set the power management mode to all (receive all packets), unicast (receive unicast packets  only,  discard  multicast and broadcast)  and multicast receive multicast and broadcast only, discard unicast packets).
              Examples :
                   iwconfig eth0 power period 2
                   iwconfig eth0 power 500m unicast
                   iwconfig eth0 power timeout 300u all
                   iwconfig eth0 power saving 3
                   iwconfig eth0 power off
                   iwconfig eth0 power min period 2 power max period 4I have never fooled with all this, so I can't vouch for its effectiveness. I do assume, however, that not every card will do every function, including power management.

---

