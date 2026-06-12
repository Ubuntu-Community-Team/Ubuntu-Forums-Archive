---
title: "How to block access to Internet but allowing only local LAN"
date: 2009-08-28
forum: Networking &amp; Wireless
---

### Post by UranUtan on 2009-08-28
Hi,

I would like to block access to the Internet but allowing traffic to all local subnets 192.168.x.x

Can you please suggest the a simple solution? Is it possible to do this by adding some definitions in the routing table or should a firewall be used?

Thanks very much in advance for any help.

---

### Post by jamest09 on 2009-08-28
You could get rid of the default route and add routes for the subnets you want access to.

But a firewall is probably easier.

---

### Post by UranUtan on 2009-08-28
Thanks but I am not familiar with networking, if possible, can you give a few more detailed hints so I can dig further with documentation?

---

### Post by Iowan on 2009-08-28
Check **man route** for more information.  I'll see if there's a good help page somewhere...

---

### Post by UranUtan on 2009-08-28
Excerpted from route man pages.
> route add -net 10.0.0.0 netmask 255.0.0.0 reject
This installs a rejecting route for the private network "10.x.x.x."

So could the solution to my issue be:

```
route add -net 192.168.0.0 netmask 255.255.0.0 reject
```

For the LAN in question, the subnet is 192.168.N.x, the subnet mask is 255.255.255.0. Could the route instruction above still apply even though the subnet mask is different?

---

### Post by doas777 on 2009-08-28
I think reject is not what you want to do with that line. it looks like you would not allow those routes, and I was under the impression that you wanted to do the oposite. might be wrong though.

---

### Post by UranUtan on 2009-08-28
> **doas777 said:**
> I think reject is not what you want to do with that line. it looks like you would not allow those routes, and I was under the impression that you wanted to do the oposite. might be wrong though.

Oh you right I want to do exactly the opposite. If you know the route instruction handy, I'd appreciate if you can share it. Will read further if there is something like "allow only this route" in route.

---

### Post by shredder12 on 2009-08-28
Ya, I think you wanted to block Internet and allow access to all local subnet 192.168.x.x .. 
if this is true then rejecting is probably not the right thing to do..

---

### Post by surj08 on 2009-08-28
add the route for the subnet you want. then block all subnets. If it reads like a firewall that should work!

---

### Post by dmizer on 2009-08-28
Why not just phsically disconnect the router from the internet connection? All local traffic will still be fine. Most routers also have the ability to disable internet access by changing a few settings.

It would be much easier to manage this by point and click router settings rather than trying to figure out how to do it locally with IP tables.

---

### Post by UranUtan on 2009-08-28
> **dmizer said:**
> Why not just phsically disconnect the router from the internet connection?

There are others machines in the LAN which still need Internet access. Only one of them I would like to confine within the LAN. 

I can may be set a static IP and screw up its default gateway setting. But I am looking for a more elegant solution, which if there is one, would also serve as a learning experience.

So basically, the machine get its IP via DHCP. Then I just need to set something in its networking configuration to say "you can only communicate with the internal subnet". May be route is the solution, or may be firewall, or may be something else. I would like to know the simplest and elegant solution.

This may sounds as a crazy idea to need such a scenario. But I hope that there should be a solution.

---

### Post by dmizer on 2009-08-28
You still should be able to manage it from the router. Block access by IP or MAC.

---

### Post by UranUtan on 2009-08-29
> **dmizer said:**
> You still should be able to manage it from the router. Block access by IP or MAC.

Super cool, just reviewed my router config and it is possible to prevent Internet access by IP or MAC address exactly as you suggested. Thanks.

After reviewing some tutorials on the Internet about the route command. The solution is simply to delete the default route. Which, I think is equivalent to not setting a default gateway in network properties. The route command is:

```
route del -net 0.0.0.0 netmask 0.0.0.0
```

If I want to execute this command at each startup, is **/etc/rc.local** the right place to do so?

---

### Post by dmizer on 2009-08-29
> **UranUtan said:**
> After reviewing some tutorials on the Internet about the route command. The solution is simply to delete the default route. Which, I think is equivalent to not setting a default gateway in network properties. The route command is:

```
route del -net 0.0.0.0 netmask 0.0.0.0
```

If I want to execute this command at each startup, is **/etc/rc.local** the right place to do so?
The problem with doing it this way is that the owner of the computer can easily bypass the restriction. All they have to do is restart networking and they'll be back online. The best way to do what you want to do is at the gateway where the computer owner doesn't have any access.

---

### Post by UranUtan on 2009-08-29
> **dmizer said:**
> The problem with doing it this way is that the owner of the computer can easily bypass the restriction. All they have to do is restart networking and they'll be back online. The best way to do what you want to do is at the gateway where the computer owner doesn't have any access.

That is so true. I have played around a little bit yesterday and the tests confirmed what you said. To achieve this, the easiest and most efficient way is to set the blocking at the router. Thank you for your advices.

---

### Post by w00ly on 2009-08-29
Might want to check if the DD WRT firmware is available for your router. It does a ton of stuff with access restrictions: filter by mac or IP address, time of day/week, site url, protocol, etc. You can also set it to allow all clients on and block a few, or block all and allow only a few. It's quite easy to setup too with a nice graphical web interface

---

