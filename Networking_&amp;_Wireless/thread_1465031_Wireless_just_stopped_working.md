---
title: "Wireless just stopped working"
date: 2010-04-29
forum: Networking &amp; Wireless
---

### Post by bkwoods on 2010-04-29
I have had ubuntu about a month now and everything has worked great up until now, I was surfing the web and all the sudden I lost connection. I tried to connect to the signal but got nothing so I did a reboot. After the reboot my wireless signal didn't show up. i right clicked the connection icon on the top taskbar and the enable wireless is blacked out to where i cant click it. 

Any help would be great, thank you in advance!

---

### Post by bkwoods on 2010-04-29
when i do a /sbin/iwconfig

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

It looks like wlan0 is up and running so im not sure why it says wireless is off and i cant connect?

---

### Post by bkratz on 2010-04-29
> **bkwoods said:**
> when i do a /sbin/iwconfig

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

It looks like wlan0 is up and running so im not sure why it says wireless is off and i cant connect?




I notice that it says "Tx-Power=off" you might try  

sudo iwconfig wlan0 txpower 15

and see what happens, report any errors, or try a smaller number if needed (say 10 or 5 )

---

### Post by bkwoods on 2010-04-29
I tried the command with 5, 10, and 15 and the output for /sbin/iwconfig still reads tx-Power= off

---

### Post by bkratz on 2010-04-29
> **bkwoods said:**
> I tried the command with 5, 10, and 15 and the output for /sbin/iwconfig still reads tx-Power= off

How about the output of 

```
rfkill list
```

---

### Post by NichoTL on 2010-04-29
Is it a laptop you are using?

I know it sounds silly but I mention it because quite a few people have had similar issues: if it is a laptop, is there a button to enable wi-fi?

---

### Post by rudiger_wolf on 2010-04-29
I had the same problem.  My Dell has touch sensitive multifunction keys and I bumped the on/off button for the wireless card.

Until finding this post I was wondering what was wrong. Thanks for the tip. Its so obvious when you know what the problem is.

---

### Post by bkwoods on 2010-04-29
The output for rfkill list is:

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

Yes it is a laptop and yes it has a a wireless button and i have tried to press it and nothing changes. (not silly at all i really appreciate the help!)

---

