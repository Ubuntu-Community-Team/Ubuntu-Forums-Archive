---
title: "wicd not working, need info on connecting manually?"
date: 2013-01-27
forum: Networking &amp; Wireless
---

### Post by LT83 on 2013-01-27
Continue having difficulty with WICD not finding any wireless networks.  I've reviewed many forums and posts looking for answers.

Ran sudo ifconfig -a ; sudo ifconfig wlan0 up; iwconfig wlan0 essid Eagle1; iwlist wlan0 scan essid Eagle1; and so on. All indications thru terminal window reflected a wireless signal being detected by my laptop, but WICD wasn't finding any wireless. My ssid is not broadcasted, but WICD allows you to 'find a hidden network'. Entering my ssid info, wicd still found nothing.

Reviewing other threads i saw that i could purge WICD thru the apt-get purge wicd* ; but when i attempted to do an apt-get install wicd, no luck. Looking at another post, i saw reference to synaptic package mgr. I found the wicd pkg, but of course i couldn't install because--I HAVE NO INTERNET CONNECTION. Yes, it was a bonehead moment. 

I restarted my box and ethernet connection found. I used synaptic package mgr to install wicd. Still no wireless.

When i do an IWLIST SCAN i see my router with it's hidden beacon: ESSID: "\x00\x00\x00……"
I then executed SUDO IWCONFIG WLAN0 SCAN ESSID EAGLE1, and i see my ssid and associated parameters: encryption key on, bit rates, freq, etc.
But when i go to the wicd n/w mgr, it tells me there no wireless networks found. 

I ran DMESG |GREP WLAN0 and saw the following: ADDRCONF (NETDEV_UP), wlan0: link is not ready. Then DMESG |GREP IWL3945, and got this: detected intel wireless wifi link 3945abg.
Reviewing some other threads, i ran LSHW -C NETWORK and saw my PRO/Wireless 3945G info, then i ran RFKILL LIST ALL and saw nothing is blocked. 

I'm at a loss and need help? I'm using Backtrack 5 (Ubunto 10.04).

---

### Post by LT83 on 2013-01-27
Not getting a lot of help thru a variety of forums; I was given this link
[http://wireless.kernel.org/en/users/Drivers/iwlwifi](http://wireless.kernel.org/en/users/Drivers/iwlwifi)

When I run this cmd I get:
root@bt:~# lsmod |grep iwl3945
iwl3945                72170  0 
iwl_legacy             65230  1 iwl3945
mac80211              410313  2 iwl3945,iwl_legacy
cfg80211              160399  3 iwl3945,iwl_legacy,mac80211

So I don't see how the above link can help.  Can someone provide some instruction for connecting a wireless connection thru cmd line?
Would really appreciate some assistance, thanks.

---

### Post by Cheesehead on 2013-01-27
Please post the contents of your /etc/networking/interfaces file.

Make sure to enclose the rely in CODE or QUOTE tags.
```
Like this
```

---

### Post by m3n3chm0 on 2013-01-31
Hello,

I'm using ubuntu 12.10 i would like to use WICD on gnome shell, is it possible ¿? May i have to uninstall network-manager ¿?

In the past i've use wicd on 11.04 and 11.10 :)

---

