---
title: "Rebooting/Restarting the Wireless Card"
date: 2009-11-27
forum: Networking &amp; Wireless
---

### Post by teward on 2009-11-27
Is there any command(s) I can use to restart the networking devices, including the wifi card?

I found on google a recommendation to use this to restart networking:
```
sudo /etc/init.d/networking restart
```but it returns
```
 * Reconfiguring network iterfaces...
Ignoring unknown interface wlan0=wlan0.

```

wlan0 is the wireless card, and this seems to reload the networking overall.  However, I'm sure that it doesn't reload the wifi card.

---

### Post by iponeverything on 2009-11-28
> **TrekCaptainUSA said:**
> Is there any command(s) I can use to restart the networking devices, including the wifi card?

I found on google a recommendation to use this to restart networking:
```
sudo /etc/init.d/networking restart
```but it returns
```
 * Reconfiguring network iterfaces...
Ignoring unknown interface wlan0=wlan0.

```

wlan0 is the wireless card, and this seems to reload the networking overall.  However, I'm sure that it doesn't reload the wifi card.

sudo /etc/init.d/networking restart

is pretty superficial, in that does not reload the driver or anything. --

If what you trying to do is actually reload the driver, you can write a script that brings down the interface, unloads the modules and then reloads them.

---

### Post by teward on 2009-11-28
I'm trying to refresh the DNS, IP, etc. without having to click the network manager and restart the connection.  Any way to do this through terminal?

---

### Post by teward on 2009-11-29
shameless bump

---

### Post by iponeverything on 2009-11-29
```

ifdown wlan0
ifup wlan0

```

---

### Post by teward on 2009-11-30
And of course it would say the interface is not configured.

This displays:
```
me@myComputer:~$ sudo ifdown wlan0
[sudo] password for me: 
ifdown: interface wlan0 not configured
```

---

### Post by teward on 2009-12-01
bump.

any idea why I can't use the up/down commands?

---

### Post by lucia_engel on 2009-12-11
I've got the same question since my wireless is having difficulties starting up after suspend.

I used to be able to use the following commands to renew the wireless connection:

```
sudo ifup
sudo ifdown
sudo /etc/init.d/networking restart
```

but this only works if the wireless was configured in /etc/network/interfaces. I now use NetworkManager to configure my connection and it'd say it's "disconnected" under Wireless Networks connection.


The error from dmesg after suspend resume is:

```
ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

The only fix so far for me is restarting the computer.

---

