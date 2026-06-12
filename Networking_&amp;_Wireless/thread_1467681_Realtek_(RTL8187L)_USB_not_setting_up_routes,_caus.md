---
title: "Realtek (RTL8187L) USB not setting up routes, causing DHCP step to fail"
date: 2010-05-01
forum: Networking &amp; Wireless
---

### Post by daboochmeister on 2010-05-01
Hi - I bought an RTL8187L USB wireless adapter, and have had trouble getting it to work.  I have managed to get it to work via manually configuring, one time, but lost that configuration, and now it is once again not working.

The root issue appears to be (if I'm understanding correctly what I'm seeing) that when I connect, routes don't get setup properly, so when network manager (or WICD, which I've also tried) get to the DHCP step, my wireless router can't be reached by dhclient.

This is on Ubuntu 9.10, and I'm using the updated driver from realtek.com, btw, though the in-kernel driver was exhibiting the same behavior.

So, two questions:

- Is anyone familiar with this problem, and is there a fix available?

- I believe I can work around it by setting up routes manually (e.g. with a post-connect script in WICD), but after staring at the "route" manpage, I'm not 100% sure of the commands.  My router (a FIOS MI424WR) is my DHCP server, and is at 192.168.1.1, and route -n on a working PC (wired connection) gives:

```
dave@MinasTirith:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```

What route commands would I script to establish the correct routes?  (I'm not sure what the 169.254 is, btw, but think it's the FIOS network)

And of course, any other thoughts or things to test appreciated!

---

### Post by daboochmeister on 2010-05-01
More info ... it occurred to me to search my terminal command history for the iwconfig commands which had successfully set up the wireless at one point.  The following sequence of commands succeeds -- and after succeeding, then Wicd can disconnect and reconnect successfully.

```
sudo ifconfig wlan1 down
sudo iwconfig wlan1 essid "LothLorien"
sudo iwconfig wlan1 key s:MyKeyPhrase
sudo iwconfig wlan1 key restricted
sudo iwconfig wlan1 mode Managed
sudo dhclient wlan1

```

(Btw, didn't think to mention earlier, my SSID is being broadcast, it's not hidden)

After that, the kernel routing table appears as follows:

```
dave@Giraffe:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan1
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan1

```

BUT ... after some time, the connection fails again, and Wicd can't reconnect, I have to re-execute the series of iwconfig commands above to restore connectivity.  When the failure occurs, the routing table is empty.  It *may* be losing connection on DHCP lease expiration, not sure -- I got a weird lease of 11.4 hours.  I'll watch for that, and report back.

In any case, my theory is still that the routing table gets emptied for some reason, causing the connection issue.  Thoughts?

Tia!

---

