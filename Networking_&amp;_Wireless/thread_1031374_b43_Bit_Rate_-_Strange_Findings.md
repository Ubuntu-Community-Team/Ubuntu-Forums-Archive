---
title: "b43 Bit Rate - Strange Findings"
date: 2009-01-05
forum: Networking &amp; Wireless
---

### Post by kevdog on 2009-01-05
I used to run ndiswrapper and theoretically achieve a rate control of 54 Mb/sec.  At least this setting was specified in the iwconfig statement and I could set the card similar to
sudo iwconfig wlan0 rate 54M

I switched back to the b43 driver beginning in Ibex since I could no longer get the ndiswrapper solution to work with my bcm4306 rev 03 card with WPA2.  I noticed by default the bit rate is set at 2 Mb/sec.  This can be manually changed to 11 Mb/sec and still successfully run.  If I change to 54 Mb/sec however, the card no longer functions.

This is quite disappointing to me.  I'm not sure if it makes any practical difference however, but nonetheless I'm disappointed.

Reading through [http://linuxwireless.org](http://linuxwireless.org), I see that other open source drivers such as ath5k, ath9k are also by default set at a rate control or 2Mb/sec, and the documentation states 11 Mb/sec can be set safely for operation.  I think this is really disappointing for 2 reasons:
1. Why limit the default setting to 2 Mb/sec?
2. Why can't the card function at a rate control of 54 Mb/sec?


For others not aware of this, you can check your card statistics with 
iwconfig

and change your rate control with

sudo iwconfig <interface> rate xxx  (where I am using 11M or 54M)

---

### Post by kevdog on 2009-01-06
Going to try to bump my own thread

---

### Post by Ayuthia on 2009-01-06
As far as I know, I thought that the rate auto-adjusts to the speed it needs.  My laptop was sitting idle at 1Mb but as soon as I ran an update, it jumped to 54Mb.  This is on my 4311 rev 01 card using 2.6.28 on Gentoo.  It also was able to set at 54Mb.

I did also try this on my other laptop and I set it to 54Mb and it had no problems.  It is on a 4306 rev 03 also using a nubuntu 8.10 live USB.

Is it possible that the issue is on the current kernel update?  I will try to test it out later today if I can get my laptop back from my child...

---

### Post by kevdog on 2009-01-06
Is there a way to test the bit rate -- mine was idling at 2 Mb/sec.  I didn't see what it became when downloading a package.

Are you just checking the results of iwconfig?

---

### Post by Ayuthia on 2009-01-06
> **kevdog said:**
> Is there a way to test the bit rate -- mine was idling at 2 Mb/sec.  I didn't see what it became when downloading a package.

Are you just checking the results of iwconfig?

That is all that I am doing.  You might try using iperf to test the network speed if you have two computers.  Does it look like you are topping out at 2 Mb/sec?  I am curious (more hoping than curious) if your chipset is not registering the Mb info correctly.

---

### Post by kevdog on 2009-01-06
You stated your changes -- can you post examples and tell me what you are specifically doing when it changes?

---

### Post by Ayuthia on 2009-01-06
I first started out with the iwconfig command:
```
sudo iwconfig
Password: 
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 44:55:66:77:88:99   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality=90/100  Signal level:-40 dBm  Noise level=-70 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
Then I ran sudo emerge --sync (the package manager update--gentoo's version of sudo aptitude update) and then ran iwconfig while it was updating:
```
sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 44:55:66:77:88:99   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality=90/100  Signal level:-40 dBm  Noise level=-70 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I just tested the adjusting of rates again (but when the wireless was idle) and found the following:
```
sudo iwconfig rate 54M
sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 44:55:66:77:88:99   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality=90/100  Signal level:-40 dBm  Noise level=-70 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```Apparently, the system does not seem to care about the rate or else I am not doing it properly.  However, as soon as I do anything (even a ping), it just right back to 54 Mb/sec.

---

### Post by kevdog on 2009-01-06
Ok, I guess I was totally wrong on this one.  I saw my bit rate jump anywhere from 1 mb/sec to 48 mb/sec.  The funny part in addition was that I also saw the link quality go over 100 also (as high as 121).

Interesting to say the least.

---

