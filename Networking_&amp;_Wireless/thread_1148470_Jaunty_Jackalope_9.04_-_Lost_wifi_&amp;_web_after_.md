---
title: "Jaunty Jackalope 9.04 - Lost wifi &amp; web after update - Using Edimax EW-7318USg"
date: 2009-05-04
forum: Networking &amp; Wireless
---

### Post by AnthraxMouthwash on 2009-05-04
This message may be quite long, but it explains my situation in detail.

First of all, I want to say this:

UBUNTU RULES!!!

Now that is out of the way, I'd like to say I am very disappointed with Ubuntu right now.  I have used Hardy for about a year now.  Once I realised I was two releases out of date, I thought it was time to update from Hardy to the new Jaunty.  I discovered this was not possible, but involved updating to Intrepid first.

Updating to Intrepid worked splendidly.  I applaud the awesome Ubuntu at this point.  Nothing broke in the update, and few (if any) settings were messed with.  Everything worked — I briefly tested as much stuff as possible.  Certainly, my wifi and web still worked perfectly.

I then updated to Jaunty.  Oh, dear.  Lots of settings had been messed with and a few things are broken.  Most prominently, I have lost wifi and with it web.  Losing web in Ubuntu makes troubleshooting tricky, since it is relied apon for installing packages etc.

I have spent days troubleshooting this issue.  My conclusion is that it has nothing to do with IPv6 as many people are speculating.  Instead, it seems the RALINK driver (RA72/RA2500) is broken or missing.  My wifi device is a USB stick, the Edimax EW-7318USg.  I have entered all the information to connect to my Thomson combo-router.  Reminder: it all worked perfectly in Intrepid and still works now in Windows.  In Ubuntu Jaunty, I never get any activity on my wifi stick; it makes NO attempt to connect AT ALL; brick-dead and responseless.

If it is at all useful, here is the result of iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"T~~~~~~~A"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

Btw, the ESSID there is not supposed to have the ~~~~~'s, I just deliberately "censored" it.

Some other info relating to the router:
The ESSID is "hidden".  I put the ID in manually in the network manager.
It is using open WEP encryption.  I have set this up in the network manager.

I would really like to see this issue/bug fixed soon.  I love Ubuntu, and can't use it for anything right now because I have no web/wifi.

Thanks.

---

### Post by ugm6hr on 2009-08-01
[http://ubuntuforums.org/showthread.php?p=7716964#post7716964](http://ubuntuforums.org/showthread.php?p=7716964#post7716964)

---

