---
title: "Permanent routing (Ubuntu 13.04)"
date: 2013-09-02
forum: Networking &amp; Wireless
---

### Post by azamat2 on 2013-09-02
I have 2 connections: *wlan0* (gw: 192.168.1.1) and *eth0* (gw: 192.168.2.1).  
My default connection is *wlan0*, but I wanted some websites load through my *eth0*, so I set up routing for those websites/IPs like this:

    ```
route add -net 31.135.208.0/21 gw 192.168.2.1 dev eth0
```
This works, however **is not permanent** (disappears after reboot). I tried to put this code in _/etc/network/interfaces_ like this:

    ```
up route add -net 31.135.208.0/21 gw 192.168.2.1 dev eth0
```
but when I restart Ubuntu, it starts without networking (it crashes). I also put these lines into that file:

```
auto eth0
address 192.168.2.125
gateway 192.168.2.1
netmask 255.255.255.0
```
but still system boots without networking.

Currently I have put _route_ command into _/etc/rc.local_, it works, but it is not permanent, because when I restart/re-connect my *eth0* (for some reason), routing disappears.

Some notes:  
I have long list of IPs to route.  
My router, which I connected *eth0* is set to DHCP.  
I tried to connect *eth0* both static and DHCP way.  

So, how do I set permanent routing?

Thanks for you help!

---

### Post by ian-weisser on 2013-09-02
One way to do it it using Upstart to detect when eth0 is connected

Create a file /etc/init/custom-routes
```
# Document your need here so you remember it in six months.
# The script runs each time the eth0 network device comes up.
# WARNING: This script does not check which network you are connecting to. It's easy to add to the script if you wish.

description "My custom routes for eth0 connections"

start on net-device-up IFACE!=eth0

script

# Section 1 - If you want to test which network eth0 is connected to, do it here

# Section 2 - Routing changes
route add -net 31.135.208.0/21 gw 192.168.2.1 dev eth0
# add more routes here
# add even more routes here

# Section 3 - Do something else, if desired

end script


```

You do not need to reboot to test the new Upstart job. Upstart monitors changes and loads them automatically. Merely plug in your ethernet cable.

---

### Post by azamat2 on 2013-09-19
Hey [**[COLOR=#000000]ian-weisser[/COLOR]**]("http://ubuntuforums.org/member.php?u=1841707"),  sorry for late reply, for some reason gmail marked message from  ubuntuforums as spam. Thanks very much for help, however, it is not  working. I read about upstart jobs from their cookbook, it makes sense,  but this simple script is not working. After some research, I changed  script to following, but still no luck:

```

description "My custom routes for eth0 connections"

start on (local-filesystems and net-device-up IFACE=eth0)

script
    # Routing changes
    route add -net 31.135.208.0/21 gw 192.168.2.1 dev eth0

    # Just for test
    mkdir /home/azamat/Desktop/test

end script

```

Is there something wrong with script?
Thanks!

---

### Post by ian-weisser on 2013-09-19
Well, my syntax is slightly different (indenting, parentheses around the AND condition), probably due to age...
 but your syntax seems fine. For example, /etc/init/usplash.conf does it your way.

What command are you using to test your upstart job?

---

### Post by azamat2 on 2013-09-19
> **ian-weisser said:**
> Well, my syntax is slightly different (indenting, parentheses around the AND condition), probably due to age...
 but your syntax seems fine. For example, /etc/init/usplash.conf does it your way.

What command are you using to test your upstart job?

I have just saved that file in /etc/init and plugging in-out my ethernet cable to check if script runs. I also tried to reboot computer, but it does not work..

---

### Post by azamat2 on 2013-09-19
If you are on askubuntu.com, you can submit your answer to the same question of mine: [http://askubuntu.com/questions/339973/set-up-permanent-routing-ubuntu-13-04](http://askubuntu.com/questions/339973/set-up-permanent-routing-ubuntu-13-04)
and earn some votes from the people of askubuntu ;)

---

### Post by ian-weisser on 2013-09-19
Suggestion: Simplify a bit to get the test working. Then we can complicate it again

This should work on *any* network device coming up.
```

description "My custom routes for eth0 connections"
start on net-device-up

script     
    mkdir /home/azamat/Desktop/test
end script

```

You can also force it using **sudo service <servicename> start**

---

### Post by azamat2 on 2013-09-19
Tried, here is output from terminal:

```

[COLOR=#808080]/etc/init$[/COLOR] **ls -l | grep custom-routes**
-rw-rw-rw- 1 root root  134 Sep 19 17:09 [COLOR=#ff0000]custom-routes[/COLOR]

[COLOR=#808080]/etc/init$[/COLOR] **sudo service custom-routes start**
custom-routes: unrecognized service

```

Also tried to reconnect network cable, nothing happened..

---

