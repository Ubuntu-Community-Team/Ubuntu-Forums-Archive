---
title: "Firewall setup problems - UFW"
date: 2009-06-09
forum: Networking &amp; Wireless
---

### Post by linuxdanny on 2009-06-09
Hey

Info Ubuntu 9.04 Laptop with Gnome-ppp connecting to Internet via usb modem and a wifi connection started with Wicd also Internet but local as well

History - Tried around 4 GUI firewalls (firestarter ect) with no luck and found Iptables to complex with rule making, Also Hours on forums ect trying to make the rules i would like with no result.

ok after much thought i have landed on UFW to make what i need to happen.... happen

Problem - I am trying to get UFW to - 
1 - Drop all packets not accepted SILENTLY (so my ip address seems to be not used)
2 - Block any hosts that try to connect to a specified service or application listening on a port more then a specified amount of times ( to prevent force attacts ect)
3 - I would also like to find a GUI that will list live Connections with info such as 
     there ip address, port, time, service being used, plus any other usefull info
      
This seems to be a problem that most users have so if you reply to this thread keep in mind i will be trying to make an easy to understand doco with my findings and answers to the questions that arise with screen shots ect as i think most new users will benifit from using a basic firewall like UFW but with some general rules

I'll use this thread to ask questions I encounter doing this and hopefully other new Ubuntu 9.04 users will find it healpful.

So if anyone can help please post
Cheers Danny

---

### Post by iponeverything on 2009-06-10
> Problem - I am trying to get UFW to - 
1 - Drop all packets not accepted SILENTLY (so my ip address seems to be not used)

Having the default policy for the INPUT chain being DROP will do this.

> 
2 - Block any hosts that try to connect to a specified service or application listening on a port more then a specified amount of times ( to prevent force attacts ect)


As far as I know there is not a tool that does this. iptables are passive. You put them place and they don't change themselves. ufw the other tools are just packages to manipulate iptables. This is doable -- like almost anything else. 

- have iptables log.
- write a daemon to monitor the log and to establish who is doing what and modify the iptables according to your specification.

What I would do -- Just setup an iptables rule to limit access to those services to just IP addresses that need to access them.
I will provide an example of this below.

```
3 - I would also like to find a GUI that will list live Connections with info such as 
     there ip address, port, time, service being used, plus any other usefull info
```

There are number of tools out there. ntop is very useful in this regard. Google around for screen shots. I use it all the time and very fast and easy to isolate problems users on my network.

      
> This seems to be a problem that most users have so if you reply to this thread keep in mind i will be trying to make an easy to understand doco with my findings and answers to the questions that arise with screen shots ect as i think most new users will benifit from using a basic firewall like UFW but with some general rules

This is the reason that default install of Ubuntu Desktop has has no externally available services. So that new users don't have worry about firewalls, because there nothing to firewall.

Now for sake of a new user that decides that they want access their home machine from work via ssh and they apt-get the ssh server.  They also decide to limit accesses to ssh on there machine to just their work IP addresses. Lets pretend that the work IP block is 111.111.111.0/24

The default rules:
```


root@mac:~# iptables -L -n
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```

The rules are eval'ed from the top down. So our first rule will be to accept ssh from the work IP block.

```
iptables -A INPUT -p tcp -s 111.111.111.0/24 --destination-port 22 -j ACCEPT

```

A breakdown of the above commmand: 

Append to INPUT chain. ie. Packets coming into the box.
```
-A INPUT
```

ssh is tcp protocol
```
-p tcp
```

Where the packets will be comming from
```
-s 111.111.111.0/24
```

The Port they will be going to. 22 is ssh
```
--destination-port 22
```

And what to do with the packet that matches the rule
```
-j ACCEPT
```

our rules should now look like this:

```
root@rli-laptop:~# iptables -L -n
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  111.111.111.0/24     0.0.0.0/0           tcp dpt:22 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination      
```

The next rule will stop everyone else from getting to our ssh server.

```
iptables -A INPUT -p tcp -s 0/0 --destination-port 22 -j DROP

```

So that now the rules look like this:

```
root@rli-laptop:~# iptables -L -n
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  111.111.111.0/24     0.0.0.0/0           tcp dpt:22 
DROP       tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:22 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```

Ta Daa! You now have ssh installed and not have it open to the world to try to guess your account/password.

To make the rules permanent, just add them to the end of your /etc/rc.local and to clear the rules do:

```
iptables -F
```

Note that if your are clearing your rules remotely and your default policy for the INPUT chain is not accept, you will be locked out.

---

### Post by superprash2003 on 2009-06-10
have you tried gufw?

---

