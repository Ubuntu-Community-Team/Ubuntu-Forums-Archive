---
title: "Wireless does not connect on startup"
date: 2010-10-04
forum: Networking &amp; Wireless
---

### Post by EddieJessup on 2010-10-04
My media center is currently running XBMC Live (which is basically a minimal ubuntu install with XBMC on top), and is all running fine apart from an irritating problem on startup. I'm pretty sure the XBMC aspect is irrelevant since the problem appears at the terminal also. The Ubuntu version is Lucid.

I can connect just fine to my wireless network (using a wep key) through my tenda w322u v2.0 network card (which I believe uses the rt3070 chipset) using iwconfig, and with the following settings in /etc/network/interfaces:

```
auto ra0
iface ra0 inet static
address 192.168.1.70
netmask 255.255.255.0
gateway 192.168.1.254
wireless-essid BTHomeHub-BDC4
```

There is also a driver configuration file in /etc/Wireless/RT3070STA/RT3070STA.dat with things like channel, ssid, wep key etc.

If I try iwconfig on startup, as soon as I can get to a tty (no desktop environment) it shows the essid and all other settings as I would expect:

```
ra0       Ralink STA  ESSID:"BTHomeHub-BDC4"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:14:7F:A0:63:4E
          Bit Rate=48 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=97/100  Signal level:-71 dBm  Noise level:-63 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

But I can't ping my router or anything. If I then type:

```
sudo iwconfig ra0 essid xxxxxxxx
```

and try iwconfig again, the exact same settings are shown, but I can now ping my router, local devices, google etc.

I've tried putting the above command into rc.local with no result, I have to manually do it on each boot. I can manage with this but other people using it aren't as computer friendly, and I don't really want them to have to go into the terminal every time they want to watch a film.

I guess the config file and interfaces file might well be conflicting in some way, but I don't really understand what either does well enough to know what to change. Any suggestions?

---

