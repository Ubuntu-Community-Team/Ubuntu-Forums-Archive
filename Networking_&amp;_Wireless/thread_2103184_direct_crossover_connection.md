---
title: "direct crossover connection"
date: 2013-01-09
forum: Networking &amp; Wireless
---

### Post by Primefalcon on 2013-01-09
I've connection 2 computers via crossover cable directly

Ip adrress are set up to

10.0.0.1 and 10.0.0.2 respectively

they both have the same netmask 255.0.0.0

and the gateway for each machine I've tried both 0.0.0.0 and their own ips

yet though each computer is saying the eth0 is setup fine... neither are way to connect to each other.. ssh is timing out and ping is just saying.

I've also disabled the firewalls on each computer just in case that was causing an issue..

one machine is 12.10 and the other is 12.04

---

### Post by haqking on 2013-01-09
> **Primefalcon said:**
> I've connection 2 computers via crossover cable directly

Ip adrress are set up to

10.0.0.1 and 10.0.0.2 respectively

they both have the same netmask 255.0.0.0

and the gateway for each machine I've tried both 0.0.0.0 and their own ips

yet though each computer is saying the eth0 is setup fine... neither are way to connect to each other.. ssh is timing out and ping is just saying.

I've also disabled the firewalls on each computer just in case that was causing an issue..

one machine is 12.10 and the other is 12.04

for crossover you dont need a gateway

---

### Post by Primefalcon on 2013-01-09
> **haqking said:**
> for crossover you dont need a gateway
yeah fills it in automatically though for 0.0.0.0 so...

---

### Post by pqwoerituytrueiwoq on 2013-01-09
after setting the options reconnect to the network to apply changes
you can try a different cable, i have had strait through work as a crossover cable

---

### Post by dpurgert on 2013-01-09
If you have a tester you should see it light like this:
(tester) - (remote)
1-3
2-6
4-4
5-5
7-7
8-8

if any of those pairs don't light up like that, something's wrong (broken wire, didn't get the wires seated in the connector, etc)

IP addresses and netmask look OK.  I don't think that the gateway is needed (since you're not getting out to the "real world" ... but you can set it to 10.0.0.1 on both).

---

### Post by Primefalcon on 2013-01-09
> **pqwoerituytrueiwoq said:**
> after setting the options reconnect to the network to apply changes
you can try a different cable, i have had strait through work as a crossover cable
different cable... same deal

---

### Post by Primefalcon on 2013-01-09
also the other thing is its saying ping: sendmsg: Operation not permitted

---

### Post by haqking on 2013-01-09
if you have to configure a GW then put in one of the machines IP but use the same one on both machines

---

### Post by Cheesemill on 2013-01-09
Do the machines know that they're on the same network?
Have you set a subnet mask of 255.255.255.0 (or /24).

---

### Post by Gogsyd on 2013-01-09
Have you tried a standard cable i.e. non crossover?  Some NICs now-a-days will autoconfigure for want of a better word and a crossover is not required.
 
Also, thinking with my Windows head on... Is there a place in Linux you can set NIC negotiation?  Just wondering aloud if this could be causing the OP's problems

---

### Post by Primefalcon on 2013-01-09
> **Cheesemill said:**
> Do the machines know that they're on the same network?
Have you set a subnet mask of 255.255.255.0 (or /24).
subnet mask is the same on both machine which 255.0.0.0

---

### Post by Primefalcon on 2013-01-09
got it working sorta... I think its one of the nic cards

good enough for now

---

### Post by Rsxhawk on 2013-01-16
Usually the way you would do this is by assigning each an IP, give them the same mask like a /24, but for gateway, make each of them the default gateway for the other.  

So in other words if your config is as follows:

PC A - 10.0.0.1 255.0.0.0
Default Gateway - 10.0.0.2

PC B - 10.0.0.2 255.0.0.0
Default Gateway - 10.0.0.1

I do this all the time with my cross-over cable between a windows machine and my Ubuntu box.  The windows machine will bitch and moan about having limited connectivity since it obviously can't get out to the net, but its connected.  You can transfer data crazy fast like this.

---

