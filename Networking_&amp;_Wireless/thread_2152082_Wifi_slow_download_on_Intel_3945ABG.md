---
title: "Wifi slow download on Intel 3945ABG"
date: 2013-06-06
forum: Networking &amp; Wireless
---

### Post by franz_bieberkopf on 2013-06-06
Dear forum,

For the past few days i'm having trouble with my wifi connection, specifically with the download speed which barely tops off 50 kb/s, while the upload speed remains normal (over 2 Mb/s).

I've gone through countless forum posts trying to decipher the solution to the problem, but to no avail.

So far i've tried:

1.) Upgrading Ubuntu (now 12.10)
2.) Removing gnome wireless manager, and installing Wicd
3.) Using module iwl3945 with the options disable_hw_scan=0 and 11n_disable=1
4.) Using (at least trying) ndiswrapper,  but always getting "invalid driver" error
5.) Using an older kernel

I am really at a loss here, as i am not experienced in this matter.
Any insight would be much appreciated.

Regards,
Marko

PS - I apologize as i know there have been countless posts before, but believe me when i say i've been through every single one of them

I've included output of several commands 

```


marko@:~$ ifconfig

wlan0     Link encap:Ethernet  HWaddr 00:13:02:72:97:a2  
          inet addr:10.188.246.11  Bcast:10.188.255.255  Mask:255.255.0.0
          inet6 addr: fe80::213:2ff:fe72:97a2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9996 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7530 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10466713 (10.4 MB)  TX bytes:893999 (893.9 KB)

marko@:~$ lspci | grep -e "ABG"
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

marko@:~$ lsmod | grep "iwl"
iwl3945                63666  0 
iwlegacy               87773  1 iwl3945
mac80211              470383  2 iwl3945,iwlegacy
cfg80211              183967  3 iwl3945,iwlegacy,mac80211
compat                 14558  6 iwl3945,mac80211,cfg80211,rfcomm,bnep,bluetooth


```

---

### Post by ahallubuntu on 2013-06-06
~

---

### Post by franz_bieberkopf on 2013-06-07
Sorry for the late response, different time zone i guess :)

The laptop is an oldie, Toshiba Satellite Pro L100.

I'm in a bit of a predicament, since i have only one wireless operator where i currently reside.
Another annoying thing is, when i inquired them about help, they told me "We have no support for linux. Have a nice day!"

There are two points available, and the result is the same through both of them.
They both usually hover at 30% signal strength.

It's weird, because the wireless connection was working totally fine until a few days ago(albeit with a hiccup here and there).

---

