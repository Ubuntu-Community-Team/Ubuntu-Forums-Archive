---
title: "D link wbr 1310  not getting connected"
date: 2011-04-16
forum: Networking &amp; Wireless
---

### Post by Rakesh_trap on 2011-04-16
Hi,  I trying to connect my linux machine( kernal 2.6)with a D-Link WBR-1310 router (Firmware fully updated).  Internet was working on the computer when it was connected to other network. DLink is DHCP Server enabled. The XP boxes had no problem connecting to the internet automatically. My linux  box was having trouble (absolutely no network detection.) on D link and port of linux lights are green.  for the Wired Connection I set the configuration to Automatic Configuration (DHCP).  I was unable to ping my router at 192.168.0.1 (Destination Host Unreachable).  I'm not sure what to do, but I suspect it may be the DHCP client settings .   Any help would be greatly appreciated!

---

### Post by varunendra on 2011-04-18
Are you sure there is no error in physical connectivity? (bad cable)

What is your current IP and subnet mask? (output of ifconfig)

Try these while connected:
```
sudo ifconfig eth0 down
```

wait 5-10 seconds

```
sudo ifconfig eth0 up
```

```
sudo dhclient
```

You may also try to manually assign IP to your ethernet interface:
```
sudo ifconfig eth0 192.168.0.200
```
(where 200 maybe replaced with any available IP on your network)


If these don't help, please post back results of:
```
ifconfig
```
```
sudo dhclient
```
```
route -n
```

---

