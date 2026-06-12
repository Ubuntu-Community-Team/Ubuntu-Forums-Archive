---
title: "Reset All Network Settings (That's All)"
date: 2011-03-11
forum: Networking &amp; Wireless
---

### Post by driftless on 2011-03-11
Feeling guilty about hijacking, I'm posting here (setting myself up for the dreaded "double-post" chastising...)

The question is simple and was asked in another thread:

> Is there a way of resetting all of the network settings to standard, as if a fresh copy of ubuntu had just been installed?

The resulting discussion trouble-shooting the OP's specific problems were detailed and informative, but failed to answer the fundamental question:

Is there?

Thanks.

---

### Post by chili555 on 2011-03-11
Please see the other thread. I would like you to post separately. Please post your details:```
lspci -nn
lsusb
iwconfig
```Thanks.

---

### Post by driftless on 2011-03-11
Woohooo! And back down the rabbit hole we go... 

Well, if thats the way it must be, here is the simple rundown of what I am experiencing: 

1) Life was good. I was sharing a cable connection to the internet with a windows computer via ad hoc wireless all arranged painlessly though the default network manager. (Elegant, never had a problem)
2) I installed Firstarter not for a firewall, but looking to see what program was pinging the internet without me knowing.
3) Connection Sharing no longer works. Windows box can connect, and registers an IP, but nothing gets through.

Maybe simple, maybe not. But if you're willing to help, Awesome! Here goes:

```
*snipped for modesty's sake*
```

Oh - and I'm on Lucid

Thanks.

---

### Post by chili555 on 2011-03-11
Is this a laptop? What brand and model? Please run and post:```
rfkill list all
dmesg | grep -e ath -e wlan
```Thanks.

---

### Post by driftless on 2011-03-11
Acer AspireOne

```
 rfkill list all
*snipped* I'll try again later -- thanks anyway. 
```

---

### Post by ajgreeny on 2011-03-11
You can flush your iptables which firestarter has changed with ```
sudo iptables -F
```and see if that helps.

Firestarter may not be the best option for the job you are trying to do, as it is now no longer being developed.   However, I'm afraid I have no definitive idea what you could use instead.  Perhaps tcpdump or something similar?

---

### Post by driftless on 2011-03-11
> **ajgreeny said:**
> 
Firestarter may not be the best option for the job you are trying to do, as it is now no longer being developed.

Yeah - I knew there were risks involved when I started this... but I didn't think a re-install of the system would be the only way to solve it...

So far I have tried:
* Flush iptables (sudo iptables -F) but something rebuilds them on reboot any
* Remove / Reinstall Network mananger (all packages network-mana*) to no effect.
* Deleting and re-building my connection profiles in Gnomes Network Manager
* Hopping on one leg and clucking like a chicken.

What might help is to have a definitive list of the config files Firestarter likely changed, along with their default bare-bones settings.

It seems to me when Ubuntu loads for the first time, there must be a script that says: "Hey, check out what equipment is on this computer, and set up the network for minimal functionality." Of course there is - how do we tap into this.

Lots of people I have read are looking for this kind of reset functionality.

Thanks.

---

### Post by driftless on 2011-03-11
Solved it (I think) by myself:

Looks like firestarter modified (created?) a file:

/etc/dhcpd.conf

I have removed that file, and now my ICS works again through Network Manager's simple voodoo.

Do I need a dhcpd.conf file? If so, why, and what should it say?

---

