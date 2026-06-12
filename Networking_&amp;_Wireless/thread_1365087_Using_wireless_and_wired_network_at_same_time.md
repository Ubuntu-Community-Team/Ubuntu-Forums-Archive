---
title: "Using wireless and wired network at same time"
date: 2009-12-26
forum: Networking &amp; Wireless
---

### Post by Konichiwa on 2009-12-26
Hey all

I want to be able to connect to two networks at once, a wireless network and a wired network.

On windows, I just add a route ex route add 192.168.2.0 mask 255.255.255.0 192.168.2.1

On ubuntu, I tried something simliar, with the following command

route add -net 192.168.2.0 netmask 255.255.255.0 gw 192.168.2.1 dev eth0

However this does not work, I receive an error, 

SIOCADDRT: Operation not permitted

Any help would be appreciated

---

### Post by Konichiwa on 2009-12-27
Bump

Anyone have and ideas? I really need to be on two networks at once.

---

### Post by ram4nd on 2009-12-27
Why do you need 2 connections at the same time, I don't think it's possible.

---

### Post by iponeverything on 2009-12-27
put an "sudo" in front of your command.

---

### Post by iponeverything on 2009-12-27
> **Konichiwa said:**
> Hey all

I want to be able to connect to two networks at once, a wireless network and a wired network.

On windows, I just add a route ex route add 192.168.2.0 mask 255.255.255.0 192.168.2.1

On ubuntu, I tried something simliar, with the following command

route add -net 192.168.2.0 netmask 255.255.255.0 gw 192.168.2.1 dev eth0

However this does not work, I receive an error, 

SIOCADDRT: Operation not permitted

Any help would be appreciated

So you want two default routes? Are the wireless and wired sides connected to the Internet through the same router? If they are not what is your goal?

1) load balance 
2) redundancy

1) load balance -- 
Unless your running BGP with your two upstreams as your neighbours and getting the global routing table, this is not going to work to well.

2) redundancy --
Easy, just put in the second default with a higher metric.

---

### Post by Konichiwa on 2009-12-27
The end goal is to be able to connect to my lab network (wired) and internet (wireless) at the same time.

I am dual booting and on windows this works without any issues at all.

To make it work on windows, all I had to do was install a route for the lab network and then my internet connection is my default root.

I tried the command with sudo and I received a different error

SIOCADDRT: No such process

Thanks for the responses, any further input would be appreciated.

---

### Post by ibrahim.k on 2009-12-27
do it like this for eth0
192.168.2.0
255.255.255.0
0.0.0.0 the gatway

---

### Post by iponeverything on 2009-12-27
> **Konichiwa said:**
> The end goal is to be able to connect to my lab network (wired) and internet (wireless) at the same time.

I am dual booting and on windows this works without any issues at all.

To make it work on windows, all I had to do was install a route for the lab network and then my internet connection is my default root.

I tried the command with sudo and I received a different error

SIOCADDRT: No such process

Thanks for the responses, any further input would be appreciated.

Its pretty easy. You are just going to have one default route, it goes to the device that is going to send your packets out to the Internet. The other route will be a network route and you don't need to add it, as it will be added automatically with you configure the interface with the correct IP address and netmask for your lab network.

---

### Post by Konichiwa on 2009-12-27
When I use the route command to add a default route to my wireless I have two default routes to the same network. Then once I plug in my wired connection another default route is added with a metric of 100.

Once this is done I am unable to reach either of the networks. 

Here is my route command output.

```
192.168.2.0     *               255.255.255.0   U     2      0        0 ra0
172.16.1.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 ra0
default         192.168.2.1     0.0.0.0         UG    0      0        0 ra0
default         192.168.2.1     0.0.0.0         UG    0      0        0 ra0
default         172.16.1.1     0.0.0.0         UG    100    0        0 eth0
```

---

### Post by Iowan on 2009-12-27
Multiple default routes should confuse the machine (sounds like it does).
[This]("http://ubuntuforums.org/showthread.php?p=8565991#post8565991") one claims to be working - though I don't really understand why...

---

### Post by Konichiwa on 2009-12-27
I thought it would.

When I do this in windows, my default route is to the internet (wireless) and then I have a second route pointing to the lab network.

Thats all I am trying to do, but I keep getting that operation not permitted error.

Also, in the second post, what file is he editing?

---

### Post by iponeverything on 2009-12-27
```

192.168.2.0     *               255.255.255.0   U     2      0        0 ra0
172.16.1.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 ra0
default         192.168.2.1     0.0.0.0         UG    0      0        0 ra0
default         192.168.2.1     0.0.0.0         UG    0      0        0 ra0
default         172.16.1.1     0.0.0.0         UG    100    0        0 eth0

```


Messed up. Don't use the route command to add any routes at all. 

All it is doing in this case is messing things up. 

Reboot. bring up your internet connection.
Check your routing table, you should have ONE default route.
Now configure eth0 for lab network. First identify an open IP address on that segment -- for sake of demonstration lets pretend that open IP address is 172.16.1.222. Ok, now lets configure eth0 from the command line just to see how things go, 

we can make the changes permanent once we test it and make sure thing look right and are working.  

```
sudo ifconfig eth0 172.16.1.222 netmask 255.255.255.0 

```

Tada.. you are done. print your routing table. 

You SHOULD see this:

```
192.168.2.0     *               255.255.255.0   U     2      0        0 ra0
172.16.1.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 ra0
default         192.168.2.1     0.0.0.0         UG    0      0        0 ra0

```

Now lets configure your lab network in /etc/network/interface to make it permanent:

add this to your  /etc/network/interface file:

```

iface eth0 inet static
  address 172.16.1.222
  netmask 255.255.255.0

auto eth0


```

---

