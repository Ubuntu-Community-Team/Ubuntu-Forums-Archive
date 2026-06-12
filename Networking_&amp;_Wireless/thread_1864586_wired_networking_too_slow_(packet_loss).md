---
title: "wired networking too slow (packet loss)"
date: 2011-10-19
forum: Networking &amp; Wireless
---

### Post by prakash_mib on 2011-10-19
Hi,
I am having problem with wired networking. 
Please consider me a linux noob but i know little bit.
server hp proliant n36l microserver
OS : started with ubunto 11.10 desktop. the network was slow 
went on to fedora 15 and it was the same. now it has ubuntu server 11.10 and it is still slow (very high packet loss)

I have configured 
1. disable IPV6 (by adding in /etc/modbprobe.d/aliases - alias word)
2. static ip (by adding in /etc/network/interfaces)
3. added dns (my router) (in /etc/somewhere as i am at office)

simple ping to router (ping -f -i 1 192.168.0.1) returns an astonishing 80% packet loss.
pinging google.com returns with 95% packet loss

the NIC is integrated gigabit NC107i (bcm5723).

Please advise of anything else I have to do.

I can borrow a router from a friend to test if it is the router's fault
(the router working fine with windows 7 laptop wired/wireless)

I am out of options now :(

---

### Post by Jonathan L on 2011-10-19
> **prakash_mib said:**
> Hi,
I am having problem with wired networking. 
Please consider me a linux noob but i know little bit.
server hp proliant n36l microserver
OS : started with ubunto 11.10 desktop. the network was slow 
went on to fedora 15 and it was the same. now it has ubuntu server 11.10 and it is still slow (very high packet loss)

I have configured 
1. disable IPV6 (by adding in /etc/modbprobe.d/aliases - alias word)
2. static ip (by adding in /etc/network/interfaces)
3. added dns (my router) (in /etc/somewhere as i am at office)

simple ping to router (ping -f -i 1 192.168.0.1) returns an astonishing 80% packet loss.
pinging google.com returns with 95% packet loss

the NIC is integrated gigabit NC107i (bcm5723).

Please advise of anything else I have to do.

I can borrow a router from a friend to test if it is the router's fault
(the router working fine with windows 7 laptop wired/wireless)

I am out of options now :(

Hi Prakash

Sounds like you're debugging this the right way.  Ping is the right tool in the first instance.  The fact that the behaviour was the same with different operating systems is suggesting that it's something outside of your computer.  My first guess would be the cable or tiny piece of dirt in the socket.

Here are my suggestions:

1.  Try different cables and sockets on the router.
2.  Try removing things from the network if you can, till it's just the router and the server.
3.  Have you got another switch you can try?
4. Can you try connecting server to another computer, both with static IP addresses, with a simple swap cable? 
5.  Try forcing the speed down with ifconfig

Try seeing if the problem persists with any of those.

Hope that's some use.

Kind regards,
Jonathan.

---

### Post by prakash_mib on 2011-10-19
> **Jonathan L said:**
> Hi Prakash

Sounds like you're debugging this the right way.  Ping is the right tool in the first instance.  The fact that the behaviour was the same with different operating systems is suggesting that it's something outside of your computer.  My first guess would be the cable or tiny piece of dirt in the socket.

Here are my suggestions:

1.  Try different cables and sockets on the router.
2.  Try removing things from the network if you can, till it's just the router and the server.
3.  Have you got another switch you can try?
4. Can you try connecting server to another computer, both with static IP addresses, with a simple swap cable? 
5.  Try forcing the speed down with ifconfig

Try seeing if the problem persists with any of those.

Hope that's some use.

Kind regards,
Jonathan.

spot on!!!
the problem was with router with two ports nearly dead and one port working (didnt bother to check the 4th port) time for new router me thinks. a gigabit one comes to my mind.
Thanks again

---

