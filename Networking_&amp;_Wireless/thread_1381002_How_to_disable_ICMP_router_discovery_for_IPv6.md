---
title: "How to disable ICMP router discovery for IPv6?"
date: 2010-01-14
forum: Networking &amp; Wireless
---

### Post by sswv on 2010-01-14
I set up a static IPv6 address and a gateway in /etc/network/interfaces.
However, a bad router in my network environment alway send wrong ICMP router discovery messages to me. So I have got extra (wrong) IPv6 address and gateway, and the routing is confused.

On Windows Servers, I can use "netsh interface ipv6 set interface "Local Area Connection" routerdiscovery=disable" to disable ICMP router discovery. But I don't know how to disable it on Ubuntu 9.10.

How could I disable ICMP router discovery for IPv6? Thanks.

---

### Post by KarlIvan on 2010-01-14
i would imagine you would need router discovery, otherwise you wouldnt be able to set up a connection. what i would do is this, but im just going off the top of my head here, so if this is no good, then dont hold it against me, but i figure its a start anyway:

go to /etc/rc.local and insert your own code to remove the route that you don't want. rc.local is a file that is run on startup, after all other startup processes have been run, so its useful if there are other things you want to run, or happen at startup.

for example, use something like the following (excuse me if some of this is psuedocode or some if it is incorrect, just winging this):

```

#!bin/sh -e

touch /home/$someusr/temp
route -A inet6 >> temp
int i = 0
# for loop here to iterate over the contents
# using ping6 on the address that you pull out of the file
#
# if statement to say if ping6 doesnt receive a reply, then remove it from
# the ipv6_route table
# fi
#          sorry, dont have time to write this right now...leaving in a few minutes
#          and id rather give you a little something for the timebeing

rm -rf /home/$someusr/temp
exit 0
```beyond that, I would look at turning off router solicitation/discovery off at the router thats giving you issues, and for the other computers that are hooked up to it, set it up statically if you really want to connect them to that router (and you would have to do that for the computer you are on as well, making the above idea worthless)

sorry i couldnt give more right now, hope this helps though

---

### Post by sswv on 2010-01-15
Thanks. I had tried that. I run:
```

sudo ip -6 route del "2001:XXXX::/64"
sudo ip -6 addr del "2001:XXXX/64" dev eth0

```
The wrong IP and router are deleted. However, it will come back after tens of seconds.
Maybe I did not fully understand ICMP router discovery protocol, But on Windows Server, set "routerdiscovery=disable" by netsh indeed solve the problem. So I want to do it on Linux, too.

Should I filter some ICMP packets?

---

### Post by sswv on 2010-01-15
Uh, It's simpler than I thought. Add these to rc.local, and that's OK! :D

```
/sbin/ip6tables -A INPUT -p icmpv6 --icmpv6-type echo-request -j DROP
```

---

### Post by KarlIvan on 2010-01-15
now how does that work for your other routers? i was worried doing something like that would mean you would have to statically set up all your routers (i dont know how many you have).

EDIT: nm, i see youre just dropping the requests

---

