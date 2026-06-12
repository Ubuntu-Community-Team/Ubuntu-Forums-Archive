---
title: "dhclient -r followed by dhclient is not releasing and renewing my ip"
date: 2009-06-29
forum: Networking &amp; Wireless
---

### Post by markg85 on 2009-06-29
Hey,

I followed this link: [http://ubuntuforums.org/showthread.php?t=435851](http://ubuntuforums.org/showthread.php?t=435851)
I did all options described there but dhclient would still only give me the wrong ip's in the wrong range. It remembered my lease and somehow dhclient -r wasn't letting it go. No errors where visible.

So, how did i release my ip?

Well, after looking in the dhclient man page i noticed a few lease files described in there. Those files (/var/lib/dhcp3/dhclient.leases and /var/lib/dhcp3/dhclient-eth0.lease) had the ip in there that i did not want to have! So my solution (probably wrong but nothing else worked) first do:

sudo dhclient -r

Then CLEAN those 2 files

Then run sudo dhclient

Now you get a real new ip! (not one based on those 2 files you just cleared)

Now i know this is wrong since dhclient didn't send a message to the dhcp server to actual release the ip thus it will not be usable by any other pc till the lease expires. But HOW do i release the ip the sane way if the known sane way (dhclient -r) is not working?

Hope this others with the same issue as well,
Mark

---

### Post by kevdog on 2009-06-29
Its not running because you are not using the correct syntax.

Its supposed to be something like:

sudo dhclient -r wlan0 (or eth0, eth1, etc)
sudo dhclient wlan0 (or eth0 eth1 ath0, etc)

---

### Post by markg85 on 2009-06-29
> **kevdog said:**
> Its not running because you are not using the correct syntax.

Its supposed to be something like:

sudo dhclient -r wlan0 (or eth0, eth1, etc)
sudo dhclient wlan0 (or eth0 eth1 ath0, etc)

I also tried adding eth0 (that's the one i had the issue with) and the results where the same.

---

### Post by kevdog on 2009-06-29
Can you type the full set of commands you are using to connect from the command line?

---

### Post by markg85 on 2009-06-29
> **kevdog said:**
> Can you type the full set of commands you are using to connect from the command line?

I only use the command line if the gui isn't working or doesn't seem to be working.

The commands i tried to change my ip:

**first attempt (failed)**
```

ifconfig eth0 // to see what it is now lets say i see 192.168.1.123
sudo dhclient -r
sudo dhclient
ifconfig eth0 // to see what it has become (also printed by dhclient) and i say 192.168.1.123

```

**second attempt (failed)**
```

ifconfig eth0 // 192.168.1.123
sudo dhclient -r eth0
sudo dhclient eth0
ifconfig eth0 // 192.168.1.123 (so had no effect)

```

**third attempt (working)**
```

ifconfig eth0 // 192.168.1.123
sudo echo '' > /var/lib/dhcp3/dhclient.leases
sudo echo '' > /var/lib/dhcp3/dhclient-eth0.lease
sudo dhclient -r // also tried with eth0
sudo dhclient // also tried with eth0
ifconfig eth0 // 192.168.1.88 (WORKED)

```

Those are all commands i typed with this issue.
The only issue i have right now is that the command sudo dhclient -r is not releasing the ip in the dhcp server which it should do according to the manual.

---

### Post by kevdog on 2009-06-29
Try this

sudo dhclient -r eth0
sudo ifconfig eth0 down
sudo ifconfig eth0 up
sudo dhclient eth0

Also the way routers work, is that the usually assign you the same ip address unless their cache is flushed.  The usually have a client list they keep and try under most circumstances try to assign the same IP address to the MAC address of the wireless card.  I know you gave the permission to the router to release the IP address, however in most cases the router will keep record of your past connections and only reassign you a different IP address if it needs to.

---

