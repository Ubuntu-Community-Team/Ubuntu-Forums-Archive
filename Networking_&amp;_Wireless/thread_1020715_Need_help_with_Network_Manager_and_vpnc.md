---
title: "Need help with Network Manager and vpnc"
date: 2008-12-24
forum: Networking &amp; Wireless
---

### Post by speedkreature on 2008-12-24
Followed [this]("http://ubuntuforums.org/showthread.php?t=1014882") thread, and that helped a lot...

This leaves me with 2 questions:
1) how do I get the .conf file that pcf2vpnc generates to work with vpnc through network manager?  Or would it even be necessary if 3DES (see next question) would work with vpnc via network manager?

Here is the tail of syslog when I try to connect to our vpn through vpnc (via network manager) without the generated .conf after importing our .pcf...
```

Dec 24 11:17:01 Turtle43 /USR/SBIN/CRON[12228]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 24 11:17:18 Turtle43 kernel: [ 4881.872071] hub 2-0:1.0: over-current change on port 2
Dec 24 11:17:31 Turtle43 NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.vpnc'... 
Dec 24 11:17:31 Turtle43 NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.vpnc' started (org.freedesktop.NetworkManager.vpnc), PID 12358 
Dec 24 11:17:31 Turtle43 NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.vpnc' just appeared, activating connections 
Dec 24 11:17:31 Turtle43 NetworkManager: <info>  VPN plugin state changed: 1 
Dec 24 11:17:31 Turtle43 NetworkManager: <info>  VPN plugin state changed: 3 
Dec 24 11:17:31 Turtle43 NetworkManager: <info>  VPN connection 'Jackson Supply Co.' (Connect) reply received. 
Dec 24 11:17:31 Turtle43 kernel: [ 4894.546677] tun0: Disabled Privacy Extensions
Dec 24 11:17:34 Turtle43 NetworkManager: <info>  VPN plugin failed: 1 
Dec 24 11:17:34 Turtle43 NetworkManager: <info>  VPN plugin state changed: 6 
Dec 24 11:17:34 Turtle43 NetworkManager: <info>  VPN plugin state change reason: 0 
Dec 24 11:17:34 Turtle43 NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active. 
Dec 24 11:17:34 Turtle43 NetworkManager: <info>  (ppp0): writing resolv.conf to /sbin/resolvconf 
Dec 24 11:17:34 Turtle43 NetworkManager: <info>  Policy set 'AT&T' (ppp0) as default for routing and DNS. 
Dec 24 11:17:46 Turtle43 NetworkManager: <debug> [1230139066.290042] ensure_killed(): waiting for vpn service pid 12358 to exit 
Dec 24 11:17:46 Turtle43 NetworkManager: <debug> [1230139066.290362] ensure_killed(): vpn service pid 12358 cleaned up 

```2) for reasons unknown to me, our outsourced network support uses 3DES on our tunnels.  I've put in a support request to have that changed to AES, but in the mean time, I need to be able to use vpnc with 3DES which I can do at the command line with the --enable-1des swtich using the pcf2vpnc generated .conf..so for example

```
$ sudo vpnc --enable-1des myvpn.conf
```


How can I get this to work through network manager?  Most of the work I do requires a GUI (i.e. RDP to Windows servers and VNC'ing to Windows desktops) so GUI notification of the VPN connection is very useful.

---

### Post by hardke01 on 2009-06-23
I also require the network manager gui to be able to support the converted *.pcf file. 

vpnc-connect <name of conf>.conf
works fine for the vpn connection to my work however a network manager supported version of this would be a lot nicer and convenient to use.

when i try to import the pcf2vpnc converted conf file to network manager i get the following error.

The file 'myvpn.conf' could not be read or does not contain recognized VPN connection information

Error: unknown error.

Adding the values in manually as a new cisco vpn connection also doesn't work.

I am currently running the Network Manager 0.7.1 and network-manager-vpnc 0.7.1 on a Ubuntu jaunty install.

---

