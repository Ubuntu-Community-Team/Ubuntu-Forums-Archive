---
title: "Changing IP???"
date: 2010-03-28
forum: Networking &amp; Wireless
---

### Post by volatilepyro on 2010-03-28
So I've been looking for a few days, out of curiosity, to see if there is anyway to setup a static IP on ubuntu 9.10. I haven't found anything yet. Well at least not anything on how to do it for a wireless connection. Does anyone have any idea on how to do this???

---

### Post by chili555 on 2010-03-28
I guess I have an idea. I am posting from it now. I think you can do it in Network Manager by right-clicking the icon and editing wireless and IPv4 settings to specify manual connection as per the attached. Add your details.

If you want to remove Network manager, you can edit /etc/netwrork/interfaces:```
auto lo 
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.101
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid your_router
wireless-key 0123456789
```The details are a bit more complex for WPA, but not bad.

---

### Post by volatilepyro on 2010-03-29
All right well the only problem with just making it automatic and stuff is I'm using a laptop and use it in various places so I need to be able to connect to any network which makes network manager really useful.

---

### Post by Iowan on 2010-03-29
You should be able to build another Network Manager connection with a static address. The trick might be when to connect DHCP, and when to connect static. You can disable (uncheck) the "connect automatically" option for all connections, then pick the one you want.

---

### Post by volatilepyro on 2010-03-31
> **Iowan said:**
> You should be able to build another Network Manager connection with a static address. The trick might be when to connect DHCP, and when to connect static. You can disable (uncheck) the "connect automatically" option for all connections, then pick the one you want.
That sounds perfect!!! ....now then, how do I do that???

---

### Post by Iowan on 2010-03-31
@herry.james:
> # Please refrain from using "leet" speak or slang.
# Please do not shorten your words to acronyms or abbreviations. It is very difficult to read and understand. The MAC address is *supposed* to be fixed (though that can be changed, too), but IP addresses are frequently changed - the D(ynamic) in DHCP.

volatilepyro:
My Karmic box got converted to Lucid last weekend - so I'll try to mix/match between Hardy and Lucid. Check **ifconfig -a** to get MAC address - you'll need it next. Right-click Network Manager Applet and choose Edit Connections. You should have an option to Add... - select that and fill in information - IPv4 Settings tab will let you manually configure IP address, etc. Remember to uncheck the "Connect automatically" box. You'll need to edit "Auto eth0" (or whatever it's called) to uncheck the "Connect automatically" box there, too.

You'll want to restart Network Manager (or reboot to re-sync everything).

---

### Post by volatilepyro on 2010-04-01
> **Iowan said:**
> @herry.james:
 The MAC address is *supposed* to be fixed (though that can be changed, too), but IP addresses are frequently changed - the D(ynamic) in DHCP.

volatilepyro:
My Karmic box got converted to Lucid last weekend - so I'll try to mix/match between Hardy and Lucid. Check **ifconfig -a** to get MAC address - you'll need it next. Right-click Network Manager Applet and choose Edit Connections. You should have an option to Add... - select that and fill in information - IPv4 Settings tab will let you manually configure IP address, etc. Remember to uncheck the "Connect automatically" box. You'll need to edit "Auto eth0" (or whatever it's called) to uncheck the "Connect automatically" box there, too.

You'll want to restart Network Manager (or reboot to re-sync everything).
I don't really understand how that will help me. I don't really understand it I guess.

---

### Post by Iowan on 2010-04-01
Which part? (Maybe I'm the one who's confused...)

---

