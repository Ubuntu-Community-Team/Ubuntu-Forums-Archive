---
title: "ipw2200 + NM on Dapper - some information"
date: 2006-06-13
forum: Networking &amp; Wireless
---

### Post by mcbane on 2006-06-13
Hello all,

Just to share my experience, as I finally got my ipw2200 working under Dapper with NetworkManager (router DI-624, in case you're wondering).

Several initial steps for the router before testing:
- Go to your router's manufacturer's website and upgrade the firmware to the latest.
- Unsecure your wireless AP completely (ie. turn of WEP or WPA).
- If your SSID is hidden, unhide it!
- Erase any stored static IP info for your Ubuntu box.
- Turn off, then turn on DHCP server on your router.
- Unplug the router (that's electric plug, not network plug), wait 5 minutes, plug it back in, wait 5 minutes.

On your Ubuntu box:

- Using your wired connection (or any connection that works), use Synaptic and install networkmanager and networkmanager-gnome(sp?). Also install wpasupplicant if you don't have it (you probably have it already).

- Comment out **ALL** interfaces except "lo" from your /etc/network/interfaces:

```
sudo nano /etc/network/interfaces
```

Afterwards, it should look like:

```

auto lo
iface lo inet loopback

```

All other lines should have "#" in front of them!

- Create "/etc/default/wpasupplicant"

```
sudo nano /etc/default/wpasupplicant
```

And add a single line

```
ENABLED=0
```

- Add module options:

```
sudo nano /etc/modprobe.d/options
```

Add a line

```
options ipw2200 hwcrypto=0 associate=0
```

- Reboot.

Once you're back up and running, click on the NM icon in your panel (unfortunately, it looks exactly the same as the standard network icon). If you see no networks, your wireless interface may be turned off at the hardware level. Click on your laptop wireless key combo (Fn-F2 on my Inspiron, for example), wait a sec, and check again. Your wireless indicator light on your laptop will likely not work anyways, so don't count on it to tell you whether it's up or not.

Click on your network and wait. If it works, great! If not, click on any other unsecured networks you may be picking up and see whether they work. Or click on the secured ones and see if you're asked for a passphrase.

**NOTE:** Once you're up, please secure your network!!!! (preferably with WPA for two reasons: better security, and see #1 below)

Some issues about NetWorkManager 0.6.x you need to know about:

1. If you use WEP, NM may not accept your passphrase and ask you repeatedly for it. This is a known bug. The workaround is to use a hex key, rather than a passphrase. Or better yet, use WPA.

2. For people who have upgraded their ipw2200 driver in desperation: this was not a good idea. Version 1.1.2 includes a handshake signal protocol NM does not implement (yet), so it may not conect no matter what you do, leading you to bang your head against the keyboard repeatedly. I use the stock driver included in the original install (1.1.1, I think). No kernel/driver upgrades are necessary.


BTW, my problem ended up being the router. After days of frustration, simply unplugging it and replugging it worked like a charm. And now it consistently works. I just wish I did it earlier. :( 

I hope this helps someone. I'm not a (too) frequent visitor to these forums, so apologies in advance if I do not answer promptly. But I'm sure there will be people who do. :)

---

### Post by scifan on 2006-08-06
Btw, make sure your DI-624 is running firmware 2.75... 2.70 (what shipped on my router) wouldn't give out DHCP assignments once WPA was enabled...  worked great without WPA... didn't work with WPA until I installed 2.75 and re-configured everything.

---

