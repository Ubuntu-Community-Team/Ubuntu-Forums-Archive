---
title: "Slower wireless link rate / speed in Ubuntu vs Windows XP"
date: 2013-04-26
forum: Networking &amp; Wireless
---

### Post by fizikz on 2013-04-26
On the same system with the same wireless adapter (Intel 5100) in Windows I see up to 300Mbps link rate reported, while in Ubuntu I see a maximum of 150Mbps. Same system, same wireless adapter, same network access point, same location. The only difference is Windows vs Ubuntu.

I'm using the iwlwifi drivers. 

The access point is on the 2.4Mhz band with 2T2R, and 40Mhz channel width. 

Why is there a difference between Windows and Ubuntu in the link rate, and what can I do to get full use of the wireless adapter in Ubuntu?

======

Separately, I upgraded a different system (System2) to Ubuntu 13.04, and while that system was getting the 150Mbps max link rate in Ubuntu previously, with 13.04 it only gets about half of that! So, now my System2 only reports a link rate around 65-72Mbps after the upgrade. Why?

---

### Post by ahallubuntu on 2013-04-26
~

---

### Post by praseodym on 2013-04-26
Disable the N-mode of the driver:
```

echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
BTW: 300M in the 2,4 GHz region is physically impossible (marketing aspects), this only works in the 5 GHz region theoretically without disturbing other networks.

150M is theoretically possible in the 2,4 GHz region

---

### Post by fizikz on 2013-04-26
ahallubuntu, you're right the 5100 is 1T2R, but the link rate reported is usually the receive rate, I believe, so 300Mbps link rate should be possible. I know the link rate and actual throughput will be vastly different, maybe 1/2 to 1/3  of the link rate at best.

The access point is a TP-Link WR841N. I can see the client's MAC address in the list of connected clients but the access point does not report link rates. I used the wireless connection status in Windows XP to see the reported link rate, and in Ubuntu I used the connection information from nm-applet as well as the output from iwconfig. 

praseodym, why would I want to disable n-mode? My understanding is that in the 2.4Ghz band 150Mbps is the limit for 2 antennas and 20Mhz channel width. With 40Mhz channel widths, it should be possible to get the 300Mbps link rate. In any case, that's how Windows reports it as well. When I force 20Mhz channel width on the access point, the link rate goes to 150Mbps, and when I set it to Auto or 40Mhz, I see 300Mbps reported. The question is why Ubuntu is showing a different maximum link rate compared to Windows.

Furthermore, I noticed that in Ubuntu, the link rate sometimes suddenly drops to 1Mbps and then back up to the typical values of 100-150Mbps. This does not happen in Windows, where it stays around 200-300Mbps.

=====

As for 13.04, I like to test the latest releases on my experimental machine, but my main system is still on 12.04 and may remain so. The above is about the main system on 12.04, but it would be nice to solve the even slower link rate problem with the 13.04 machine too.

---

### Post by praseodym on 2013-04-26
> praseodym, why would I want to disable n-mode?
Because it a driver bug ;)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1034740](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1034740)

---

### Post by ahallubuntu on 2013-04-26
~

---

### Post by ahallubuntu on 2013-04-26
~

---

### Post by fizikz on 2013-04-26
That iwlwifi bug was dated from 2012. It's quite unsettling that it hasn't been sorted out yet.

I did not have issues with dropped connections, except for the link rate occasionally being reported as 1Mbps. I did not notice any drops or issues during actual network/internet use. I definitely do not want to disable n since the whole point of getting the 5100 was to upgrade my remaining g devices so I could switch my network from wireless g to n.

DD-WRT is something I would consider in the long term, however, I just got the router and I'm currently evaluating its performance, and may return it if things don't work out, so I do not want to put custom firmware just yet.

---

