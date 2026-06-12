---
title: "Problem with Cable Internet Router"
date: 2010-05-30
forum: Networking &amp; Wireless
---

### Post by Ulysses on 2010-05-30
Hello,

Ubuntu 9.10.

Problem is like this.

Wired Connection > Cable > Cable Router > Computer
I get internet, no problem.

When I add my wireless router
Wired Connection Cable > Cable Router > Wireless Router > Computer
I do not get internet at all.

And, the other windows laptop (my work one) which is not wireless but hooked up to the cable router works!

I know I'm doing something wrong and I know I'm not the sharpest knife in the drawer, so if someone could point me in the right direction, that would be awesome!

RAR

---

### Post by mikewhatever on 2010-05-30
Let's see the outputs of the following on the computer with wireless:

ifconfig
ping -c4 212.227.93.146 #(google.com)
nm-tool

---

### Post by Ulysses on 2010-05-31
Hello,

Replying from work, so's I can't do any work on my home desktop.
Never figured out the remote login, though this is not the forum for that.

Nevertheless, the machine that does work with wireless is the work computer and it is Windows NT.

RAR

---

### Post by mikewhatever on 2010-05-31
I was under the impression that wired connection worked at home. You should run the commands when wirelessly connected, then connect the cable and post the outputs.

---

### Post by Ulysses on 2010-06-01
Hello,

Thanks for the patience, mikewhatever. So, here goes.

Cable Router + Ubuntu machine = internet connection.
No problem.

Cable Router + Wireless Router + Wired Connection + Ubuntu machine = NO internet connection
Big problem

Cable Router + Wireless Router + Wired Connection + Windows NT laptop (for work - no mess around with ; almost got fired the last time) = NO internet connection.
Which means I can't work from home, which is nice, but unfortunately, it's sometimes required.

The router is new and all the lights are flashing. Never had this problem before. Even went back to the OLD wireless router that DID work and now, it doesn't work. I never had to do no fancy switching.

I know I'm coming off like an idiot, but it's how I feel. 
Can you help me out, mikewhatever?

RAR

---

### Post by Ulysses on 2010-06-01
Hello,

Oh. Whoops.
Outputs when connected:

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:30:67:04:09:6b  
          inet addr:99.251.41.65  Bcast:99.251.41.255  
Mask:255.255.254.0
          inet6 addr: fe80::230:67ff:fe04:96b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1026 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1064 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:924699 (924.6 KB)  TX bytes:194527 (194.5 KB)
          Interrupt:27 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:106 errors:0 dropped:0 overruns:0 frame:0
          TX packets:106 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10979 (10.9 KB)  TX bytes:10979 (10.9 KB)
```

ping -c4 212.227.93.146 #(google.com)
```
PING 212.227.93.146 (212.227.93.146) 56(84) bytes of data.
64 bytes from 212.227.93.146: icmp_seq=1 ttl=52 time=150 ms
64 bytes from 212.227.93.146: icmp_seq=2 ttl=52 time=151 ms
64 bytes from 212.227.93.146: icmp_seq=3 ttl=52 time=147 ms
64 bytes from 212.227.93.146: icmp_seq=4 ttl=52 time=152 ms

--- 212.227.93.146 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3005ms
rtt min/avg/max/mdev = 147.852/150.643/152.387/1.739 ms
```

nm-tool

```
NetworkManager Tool

State: connected


** (process:2143): WARNING **: error: failed to read connections from 
org.freedesktop.NetworkManagerUserSettings:
    The name org.freedesktop.NetworkManagerUserSettings was not provided
 by any .service files
- Device: eth0  [Auto eth0] 
----------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             connected
  Default:           yes
  HW Address:        00:30:67:04:09:6B

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         99.251.41.65
    Prefix:          23 (255.255.254.0)
    Gateway:         99.251.40.1

    DNS:             64.71.255.198
```

Connected wired through router is as follows:

ifconfig

e```
th0      Link encap:Ethernet  HWaddr 00:30:67:04:09:6b  
          inet addr:192.168.1.100  Bcast:192.168.1.255  
Mask:255.255.255.0
          inet6 addr: fe80::230:67ff:fe04:96b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1741 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1614 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1611618 (1.6 MB)  TX bytes:281116 (281.1 KB)
          Interrupt:27 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:106 errors:0 dropped:0 overruns:0 frame:0
          TX packets:106 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10979 (10.9 KB)  TX bytes:10979 (10.9 KB)

```

ping -c4 212.227.93.146 #(google.com)
```

PING 212.227.93.146 (212.227.93.146) 56(84) bytes of data.

--- 212.227.93.146 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3006ms
```

nm-tool
```

NetworkManager Tool

State: connected


** (process:2254): WARNING **: error: failed to read connections from 
org.freedesktop.NetworkManagerUserSettings:
    The name org.freedesktop.NetworkManagerUserSettings was not provided
 by any .service files
- Device: eth0  [Auto eth0] 
----------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             connected
  Default:           yes
  HW Address:        00:30:67:04:09:6B

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1
```

Now, sir, what is it I am doing the wrong?

RAR

---

### Post by david.burlingame on 2010-06-02
I had a similar problem a few years back.  If I plugged in any other computer into my cable modem it would not work without rebooting.  My solution for this was to reboot the cable modem with the new device (router) plugged in.  Some service providers attempt to limit the number of devices on your home network.  Most home wireless routers will let you plug in your laptop and copy it's MAC address to the router's internet port.  I suggest you do this 1st to see if that fixes the problem.

Next - you might have a cabling issue.  Make sure you have known good cables and the link lights are working on both ends.  I had a guy from work who used to put a small piece of clear scotch tape over the copper ends of our laptop cables while we were on break.  Assuming that isn't the problem:

ping your default gateway: 192.168.1.1
If this fails, it is likely a misconfiguration of IP address or subnet mask on either device

If that works I would open a web browser to the same IP address (router) and login to view the device configuration.  Verify the WAN interface (internet) has an IP address that starts with 99.251.X.X.
 Some routers will give you a warning like, "The device is not connected to the internet!"

 Obviously, that would be the problem if you see such a warning.  Assuming the IP address is good on the WAN interface:

From your computer: ping 99.251.40.1 
 - which should be the WAN default gateway

If this works let's check your DNS 
ping 64.71.255.198
 - if it fails try to use your router for DNS forwarding at 192.168.1.1
- if it works

Ping google.com
 - if that does not resolve to an IP address the problem is with your DNS.

---

### Post by mikewhatever on 2010-06-02
It looks like the problem is somewhere between the cable modem and the router. Make sure you plug the cable that connects the two into the correct socket (might say "WAN" next to it).

---

### Post by Ulysses on 2010-06-03
Hey

Thank you, gents.
I haven't done anything yet 
(I work as a scheduler at a factory that makes automotive seats and the 16 hour days are making it hard to motivate myself when the easiest solution is just to plug and unplug from the cable router but damnit, I came home early just to solve this and I will do my level best)
But I will take all of your advice and see what I can't do to make this work.

I will post my results. Thanks again for all the help.

RAR

---

### Post by Ulysses on 2010-06-03
Hey Guys,

SOLVED!
Well, I want to say Holy somethingorother but I'm not sure that is all kosher on the forums, but Holy somethingorother. It works.

Something so simple. Geez.

This is the best thing that has happened to me all day.
I will have a beer, gentlemen and enjoy the rest of my early day at home (well, earlier than usual which is just about getting home on time for everyone else)

Thanks again,
RAR

---

### Post by Iowan on 2010-06-03
Sounds like a good case of [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")! :)

---

