---
title: "Ubuntu 9.10 detect wi-fi but could not connect"
date: 2010-01-15
forum: Networking &amp; Wireless
---

### Post by scoobythedoo on 2010-01-15
Hi everyone!
I'm newbie ubuntu user, so I kindly ask you to help with my problem: I could not connect to any wireless network on my laptop with ubuntu 9.10. Network manager detects all wireless networks avaliable, but could not connect to any of them. When I try to connect, system asks for wpa-key, but typing it gives no result. I tried home and office network, but it is the same.
There is WinXP installed on the other disc partition and no problem with wireless connection at all.
 
I have Acer 3680 with broadcom wireless adapter 4318 (driver was installed via ndiswrapper).

I've already spent hours, browsing the Internet, but it does not help unfortunately, so I'll appreciate any advice of experienced user.

iwconfig:
                          ```
lo        no wireless extensions.  
 

 eth0      no wireless extensions.  
 

 wlan0     IEEE 802.11g  ESSID:"SvoyDom"   
           Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1E:8C:E5:12:BE    
           Bit Rate=54 Mb/s   Tx-Power:25 dBm    
           RTS thr:2347 B   Fragment thr:2346 B    
           Power Management:off  
           Link Quality:71/100  Signal level:-50 dBm  Noise level:-96 dBm  
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0  
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

```

---

### Post by bkratz on 2010-01-15
It may not be good news, but 9.10 with ndiswrapper has a few unresolved issues with encrypted networks, it works for some people not for others ( including me). I did do a prelimenary download of 10.04 and mine returned to working; but for the near term I have returned to 9.04.  You might be be better off with the native b43 drivers for your particular card.

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

or with the new open source versions

[http://ubuntuforums.org/showthread.php?t=1055078&highlight=BCM4318](http://ubuntuforums.org/showthread.php?t=1055078&highlight=BCM4318)

but that would be up to you and would require the removal of ndiswrapper.

---

### Post by scoobythedoo on 2010-01-18
Thanks for help.
I did try both solutions, but not any of them worked. :(:(:( 

I reinstalled ubuntu and tried both variants, but my wlan card does not seem to work with either b43 or opefwwf. It was even better with ndiswrapper - I could see all wireless networks, but could not connect. Now wlan seems to be dead.

Do you have any other suggestions how to make it work? Or maybe it is better to try elder versions of ubuntu?
I really want to switch from windows, but without wireless access it is impossible.

---

### Post by scoobythedoo on 2010-01-20
Is there anyone who could help?
I can not manage with the problem myself! Please help!!!!

---

### Post by scoobythedoo on 2010-01-25
Finally, I installed ndiswrapper back again (as it was the best of what I tried) and removed wpa key from my wireless router.
And that's it! I managed to connect and surf the Internet.

Unfortunately, It is bad solution as it only gives me access to my home network (without wpa). Any protected network is still unavailable for me.

I hope, that better solution exists...:(

---

### Post by jml on 2010-01-25
I would consider bkratz's suggestion.  Download and burn a copy of Ubuntu 9.04.  Run it as a live CD and see if it works any better.

Joe

---

### Post by scoobythedoo on 2010-01-27
Hi Joe,
I tried 9.04. It is exactly the same story. After ndiswrapper installation it detects all the networks, but could not connect, because of wpa encryption, I suppose.

I'll try [**Fixing ndiswrapper invalid cmd 12**]("http://ubuntuforums.org/showthread.php?t=1343847&highlight=1602") and give feedback soon.

---

