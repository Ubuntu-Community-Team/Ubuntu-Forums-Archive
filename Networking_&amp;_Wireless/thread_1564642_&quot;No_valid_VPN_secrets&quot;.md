---
title: "&quot;No valid VPN secrets&quot;"
date: 2010-08-30
forum: Networking &amp; Wireless
---

### Post by 98cwitr on 2010-08-30
Converted my .pcf to a .conf for vpnc and it works great from terminal...does not work from GUI b/c I keep getting this error, I've tried everything that the GUI will allow, what am I missing here? I really like to just use the GUI if it's possible.

---

### Post by 98cwitr on 2010-08-30
nm, reboot fixed it even after trying to restart the network-manager service...whatev im happy :)

---

### Post by frmdstryr on 2010-09-10
restart worked for me, thanks!

---

### Post by deezer on 2010-10-22
Reboot worked for me in Ubuntu 10.10 x64

What is this, Windows?? :)  Surely there must be some service that can be restarted...but since Ubuntu boots so fast, no sense in finding that out :)

---

### Post by 98cwitr on 2010-10-23
> **deezer said:**
> Reboot worked for me in Ubuntu 10.10 x64

What is this, Windows?? :)  Surely there must be some service that can be restarted...but since Ubuntu boots so fast, no sense in finding that out :)

I would assume whatever process runs vpnc or just restart network-manager from init.d

---

### Post by Hidde Boomsma on 2010-11-03
I can confirm that restarting the network-manager it enough to make the gui work.

I installed network-manager-vpnc and put in my credentials for the TU Delft, restarted network-manager with
```
sudo /etc/init.d/network-manager restart
```

Thanks

---

### Post by 98cwitr on 2010-11-03
> **Hidde Boomsma said:**
> I can confirm that restarting the network-manager it enough to make the gui work.

I installed network-manager-vpnc and put in my credentials for the TU Delft, restarted network-manager with
```
sudo /etc/init.d/network-manager restart
```

Thanks

Awesome, thanks for verifying that.

---

### Post by twistdhood on 2010-12-15
> **Hidde Boomsma said:**
> I can confirm that restarting the network-manager is enough to make the gui work.

I installed network-manager-vpnc and put in my credentials for the TU Delft, restarted network-manager with
```
sudo /etc/init.d/network-manager restart
```



I can second the above with 10.10.

My office uses cisco for vpn. I got a netbook recently and just tried getting on my vpn. Installed the network-manager-vpnc and all that jazz, Saved my VPN credentials and got the dreaded:
> The VPN connection 'xxxxx' failed because there were no valid VPN secrets.

After a while of searching I came across this thread.

A jump/jive/wail and ```
sudo service network-manager restart
``` ...and we're good!

I guess they're afraid of restarting the network-manager following the network-manager-vpnc installation. I guess that makes some sense...

---

### Post by recluce on 2011-06-30
> **Hidde Boomsma said:**
> I can confirm that restarting the network-manager it enough to make the gui work.

I installed network-manager-vpnc and put in my credentials for the TU Delft, restarted network-manager with
```
sudo /etc/init.d/network-manager restart
```

Thanks

Restarting the network-manager worked for me (Ubuntu 10.04 64bit with kernel 2.6.38-8)

Thanks for the help!

---

