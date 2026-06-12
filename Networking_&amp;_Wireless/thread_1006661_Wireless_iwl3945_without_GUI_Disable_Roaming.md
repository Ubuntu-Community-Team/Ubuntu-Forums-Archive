---
title: "Wireless iwl3945 without GUI? Disable Roaming?"
date: 2008-12-09
forum: Networking &amp; Wireless
---

### Post by Magneto on 2008-12-09
Wireless with iwl3945 works in gnome but has issues. I can't disable roaming and it automatically connects to available wireless networks and disabling those networks isn't something I have found a way to do in searching here and google. I installed the gnome networking manager but it apparently only supports wep- but does offer to kill roaming. Now as it is, Ubuntu is automatically connecting to various neighborhood wireless nets before connecting to my home wireless net. I hate this. I'm surprised any linux distro would be setup to do something like this.  

That is one issue. Another is I dont want to use gnome and when trying to use iwl3945 with wpa_supplicant I get errors. I'm looking for some instructions on how to get this going. I've seen the howto with 51 pages and it isnt a solution to my problem.

I tried using the "system setting" option also to get the network settings to apply prior to login or for all users and ticking the box is undone after closing and reloading the networking app( yes it was unlocked - run as sudo - networking permissions set in the user manager etc).

so im looking for

1. way to setup wireless with wpa and hidden essid that is NOT tied to gui
2.way to kill roaming by default
3. a solution to have network settings system wide that wouldnt make it cumbersome to connect to various networks while at other locations- aka editing wpa_supplicant.conf to connect in a coffeeshop etc


{should i be trying ipw3945? it isnt available in the current kernel}

thanks for any help on this

---

### Post by Magneto on 2008-12-09
trying this for general commandline wifi configuration
[http://ubuntuforums.org/showpost.php?p=1176169&postcount=1](http://ubuntuforums.org/showpost.php?p=1176169&postcount=1)

still interested in any advice

---

### Post by Magneto on 2008-12-09
that link I posted above gave me most of what i needed except no hidden essid support but thats not a biggie

now I need to find out how to disable NetworkManager

---

### Post by Magneto on 2008-12-09
Disabled NetworkManager via

```
mv /etc/rc2.d/S28NetworkManager /etc/rc2.d/D28NetworkManager
```

that takes care of roaming and switching to another net is just a matter of switching /etc/network/interfaces after examining the results of 
```
iwlist scan
```

not too bad. it took me a minute and some patience after not using Ubuntu for awhile
I hope this will help someone else.

---

