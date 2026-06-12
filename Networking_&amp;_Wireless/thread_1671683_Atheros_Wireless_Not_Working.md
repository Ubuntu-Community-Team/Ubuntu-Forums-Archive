---
title: "Atheros Wireless Not Working"
date: 2011-01-20
forum: Networking &amp; Wireless
---

### Post by dostumai on 2011-01-20
Does exactly what it says on the tin...
I upgraded to Maverick Meerkat on my Compaq Presario CQ60 and the installation bugged killing all the documents and settings. I'm not a total n00by to Linux as I've been using it for years, but neither am I an advanced user.

Any halp you can give with this as I've tried everything I can think of to get the wireless card to work.
Which basically boils down to trawling Google for the drivers and attempting to install them.

Results of iwconfig:
```
dostumai@dostumai-Compaq-Presario-CQ60-Notebook-PC:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
ppp0      no wireless extensions.
```
Xiexie.

---

### Post by dBuster on 2011-01-20
I know when I first installed 9.04 Jaunty I had to use the MADWIFI drivers to get the wifi working on my CQ60.  Ever since every time I would get a kernel update, no more since Jaunty isn't supported any more, but each time I would have to install it again with the old fashioned make/clean/install....

Not sure with your case if the wifi worked out of the box with 10.10 but I would think you could always look to the madwifi way to get the wifi to work.

I know when I tried the 10.10 cd live I had wifi out of the box.  Maybe a recent update hosed it?  Although it looks like your wifi is actually WLan0 from the results you posted.  

Too bad Compaq doesn't have an upgrade for the wireless cards in the CQ60's!  I sure would love to have N internally and not have to try and get the recent airlink101 to work.  But then again maybe when I clean install 10.04 it will work out of the box.

---

### Post by dostumai on 2011-01-20
Thanks, I'll try out MADWIFI and see if that works then post the results. [=

---

### Post by dostumai on 2011-01-20
Either going blonde has killed what's left of my brain, or I've done things wrong...
I either get:
```
ERROR: You must be root to run this script
```
Or:
```
FATAL ERROR: No hal directory ../hal
```
Meh, I'm going out to do something else before I throw my laptop against a wall.

---

