---
title: "Wireless/Wired Network Bridge oddity"
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by ff8jake on 2009-11-02
Hi Guys,

After about 4 hours of playing around and scouring the net for info on creating a bridge between a wireless and wired adapter - I finally gave up. My wireless adapter drops the connection soon after becoming part of a bridge. I have installed bridge-utils and I am running the following commands.

Step 1, create the bridge:
```
ff8jake@machine:~$ sudo brctl addbr br0
```

Step 2, add the wireless interface 'ra0' to said bridge:
```
ff8jake@machine:~$ sudo brctl addif br0 ra0
```

Step 3, add the wired interface 'eth0' to said bridge:
```
ff8jake@machine:~$ sudo brctl addif br0 eth0
```

Step 4, have the bridge get address via DHCP:
```
ff8jake@machine:~$ sudo dhclient br0
```

This is where the oddity begins. It immediately manages to talk to my router at 192.168.1.1 and negotiate an IP address without issues. I logged into the router and I can see both the lease 'ra0' has as well as 'br0'. I have no DHCP reservations based on mac address or anything that would really lock this wireless adapter to a particular IP or prevent it from negotiating more than one IP. At this point, it seems like all is great!

Then 'ra0' disconnects.

The icon in the top right for the built in ubuntu wireless tool begins to attempt a reconnect, and it asks for the WPA key repeatedly without ever making a successful connection. Does anyone have any idea on a fix? About to go crazy. :popcorn:

---

