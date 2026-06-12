---
title: "pls help, wifi won't connect"
date: 2010-12-26
forum: Networking &amp; Wireless
---

### Post by attilab on 2010-12-26
Intel 4965agn on AsusC90s notebook, trying to connect through LinksysWRT610n
worked until fresh install ubuntu 10.10
-scanning and listing many wifi networks around, 
-trying to connect my home (windows WORKGROUP with many XPs, Vista's, W7s), typing password, rejects to connect to my WPA-WPA2 personal
- the antenna applet is just running and periodically comes back to enter password? cable running OK. 
- is this some security issue? what is what Im missing? 
Im not planning to do a big-deep study, just to make it work until next major upgrade :)

---

### Post by attilab on 2010-12-26
forgot to say:
same nite 2 default installation:
- Asus EEE 1005PE netbook, installed 10.10 netbook edition and all worked out of box (since I've switched to desktop interface, like it better) 
- Asus C90s laptop, installed 10.10 desktop edition and wireless wont connect (as I sad, scanning and finding surrounding signals), not even after (connected LAN) upgrades;
This gives me an idea that there must be some differences between the default packages, but all these exceedes my understandings.

---

### Post by dcstar on 2010-12-27
> **attilab said:**
> forgot to say:
same nite 2 default installation:
- Asus EEE 1005PE netbook, installed 10.10 netbook edition and all worked out of box (since I've switched to desktop interface, like it better) 
- Asus C90s laptop, installed 10.10 desktop edition and wireless wont connect (as I sad, scanning and finding surrounding signals), not even after (connected LAN) upgrades;
This gives me an idea that there must be some differences between the default packages, but all these exceedes my understandings.

Power cycle the router.

---

### Post by amsterdamharu on 2010-12-28
Is there any output from the command?
```
iwconfig
```

To run the command you can press alt + F2, type gnome-terminal and click run. Then copy and paste the command from the web page to the terminal (use your mouse as control + c control + v doesn't work in terminal)

---

### Post by attilab on 2010-12-28
RE: to dcstar
yes I re-powered the router several times, but no I'm not reversed to hard reset (because I made a range of available IP's between 100-140, I have about 10 static IPs (for TV's, DVDs, game consoles, and the PCs(xp, Vista, W7, linux) are auto IPs.) and it might be a long process assigning back the stats.
RE: to amsterdamharu

attilab@attilab-C90S:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"bibatthun_5"  
          Mode:Managed  Frequency:5.24 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


can you please tell me how to interpret this? the funny faces came out auto :)

---

### Post by kevdog on 2010-12-28
Dumb the situation down

Meaning turn off wpa2 at the router and see if you can connect to an open network.  There are other things you can try also, however need more info.

---

### Post by attilab on 2010-12-28
tomorrow afternoon I will hard reset the router, and will go from there,

---

### Post by attilab on 2010-12-29
Interesting thing:
1. hard reset and built up from scratch the Linksys WRT610N router
2. create one profile 2.4 GHz *_mixed mode_* (abgn) WPA2 and managed the (Asus C90s) Intel 4965 abgn card to connect
3. create one profile 5.0 GHz *_N mode_* only WPA2, couldn't connect ?!
4. previously I had both the wifi profiles locked to N-only for about a year, worked like a charm on all Win and Linux machines untill 10.10 update (fresh install -not update) 
4. the second 5GHz option (N only) would be a perfect for my case, longer range, larger bandwith with faster speed...
anybody?

---

