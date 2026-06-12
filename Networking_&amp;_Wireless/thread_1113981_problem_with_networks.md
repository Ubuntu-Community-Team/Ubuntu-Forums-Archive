---
title: "problem with networks"
date: 2009-04-02
forum: Networking &amp; Wireless
---

### Post by DariusZelvys on 2009-04-02
Hi,
I'm having a real difficulty using the network in ubuntu, this is the last place where i hope to find help. The same thing exists in 8.10 and 9.04 beta. So the situation is... :
there are 3 network connected through the vpn. On the network number 1 where my work place is i can connect to other servers on the same network. 
I mean if i'm on 192.168.110.x i can connect  to 192.168.110.x servers, but if i try to connect ti 192.168.111.x or 192.168.118.x which are the two other networks on vpn connection ussually nothing happens. sometimes i c an sometimes i can't. can't even say on what it depends. Sometimes even ping to the other servers dissapear for no reason. so for 5 minutes i can connect, for other 5 i can't. Can it be something with routes? I left them default. By the way , everything is working without a problem on the same network with windows xp computers. Could someone please help me. I'd be grateful

---

### Post by BkkBonanza on 2009-04-02
What netmask are you using for your network in your router and other configs?

255.255.0.0 is ok for these addresses but 255.255.255.0 is not.

---

### Post by DariusZelvys on 2009-04-02
> **BkkBonaza said:**
> What netmask are you using for your network in your router and other configs?

255.255.0.0 is ok for these addresses but 255.255.255.0 is not.

The gateway we connect to other networks is on the same network i am. He has address of 192.168.110.254 and netmask 255.255.255.0 
How come this is related? Why do windowsxp work? By the way this gw is win2003 server

---

### Post by jigsaws on 2009-04-02
Check on the windows machines:
netmask
gateway
routes
MTU

And then check it on Ubuntu.

Then if the same try to turn off tcp window scaling:
sudo -i
echo "0" > /proc/sys/net/ipv4/tcp_window_scaling

If still not working - trace tcp packets with tcpdump...

---

### Post by BkkBonanza on 2009-04-02
A netmask of 255.255.255.0 means that the network only contains different addresses in the lowest dot value. So if the gateway is 192.168.110.254 netmask 255.255.255.0 then that network will only have valid addresses from 192.168.110.0 to 192.168.110.255. So 192.168.111.* or 192.168.118.* are not valid addresses in that network. It's possible that different configs in various places are causing confusing behaviour, and I wouldn't be surprised if bugs caused some software to work oddly, but that doesn't change what is correct. If you want all those addresses mentioned to be reachable in your network then you need a netmask of 255.255.0.0

---

### Post by coutts99 on 2009-04-02
> **BkkBonaza said:**
> What netmask are you using for your network in your router and other configs?

255.255.0.0 is ok for these addresses but 255.255.255.0 is not.

Yes it is

---

### Post by coutts99 on 2009-04-02
> **DariusZelvys said:**
> Hi,
I'm having a real difficulty using the network in ubuntu, this is the last place where i hope to find help. The same thing exists in 8.10 and 9.04 beta. So the situation is... :
there are 3 network connected through the vpn. On the network number 1 where my work place is i can connect to other servers on the same network. 
I mean if i'm on 192.168.110.x i can connect  to 192.168.110.x servers, but if i try to connect ti 192.168.111.x or 192.168.118.x which are the two other networks on vpn connection ussually nothing happens. sometimes i c an sometimes i can't. can't even say on what it depends. Sometimes even ping to the other servers dissapear for no reason. so for 5 minutes i can connect, for other 5 i can't. Can it be something with routes? I left them default. By the way , everything is working without a problem on the same network with windows xp computers. Could someone please help me. I'd be grateful

Have you got routes to all the networks?

What is the output of 'route'?

And how are all the networks connected?

---

### Post by DariusZelvys on 2009-04-03
> **coutts99 said:**
> Have you got routes to all the networks?

What is the output of 'route'?

And how are all the networks connected?

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.110.0   *               255.255.255.0   U     2      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         192.168.110.254 0.0.0.0         UG    0      0        0 eth1

that's my default route output

What do you mean how are all the networks connected? 
On 192.168.110.254 we have a gw and other two networks 192.168.111.254 and 192.168.118.254 are connected through VPN connection. I work on the first network and no problems if i connect to local servers, but when the job comes to the point of connecting to 118 and 111 networks, everythings goes slow as hell or doesnt connect at all or sometimes for no reason it works good... I;m confused

---

### Post by DariusZelvys on 2009-04-03
> **BkkBonaza said:**
> A netmask of 255.255.255.0 means that the network only contains different addresses in the lowest dot value. So if the gateway is 192.168.110.254 netmask 255.255.255.0 then that network will only have valid addresses from 192.168.110.0 to 192.168.110.255. So 192.168.111.* or 192.168.118.* are not valid addresses in that network. It's possible that different configs in various places are causing confusing behaviour, and I wouldn't be surprised if bugs caused some software to work oddly, but that doesn't change what is correct. If you want all those addresses mentioned to be reachable in your network then you need a netmask of 255.255.0.0

I really doubt that... That's why we use VPN... To make the whole network work like one. 
Everything is going smooth with windows, if your theory would be true then i could never connect to other networks... but sometimes i can... :(

---

### Post by DariusZelvys on 2009-04-03
> **jigsaws said:**
> Check on the windows machines:
netmask
gateway
routes
MTU

And then check it on Ubuntu.

Then if the same try to turn off tcp window scaling:
sudo -i
echo "0" > /proc/sys/net/ipv4/tcp_window_scaling

If still not working - trace tcp packets with tcpdump...

Stil doesn't work... :(
I'm not that skilled, i'm just a begginer , i don't know how to trace packets..

---

### Post by DariusZelvys on 2009-04-03
> **jigsaws said:**
> Check on the windows machines:
netmask
gateway
routes
MTU

And then check it on Ubuntu.

Then if the same try to turn off tcp window scaling:
sudo -i
echo "0" > /proc/sys/net/ipv4/tcp_window_scaling

If still not working - trace tcp packets with tcpdump...

Could you please tell me if this setting is permanent? Does it work after restart? I have a feeling that with this setting it's working better, but i'm not sure if it stays the same after restart. Still need to test it a lot

---

### Post by jigsaws on 2009-04-03
No, it's not permanent, but you can add to config file /etc/sysctl.conf line:

net.ipv4.tcp_window_scaling = 0

Then reboot the system or restart network service to take effect.

---

### Post by DariusZelvys on 2009-04-03
> **jigsaws said:**
> No, it's not permanent, but you can add to config file /etc/sysctl.conf line:

net.ipv4.tcp_window_scaling = 0

Then reboot the system or restart network service to take effect.

still doesn't help...

weird thing is that if i set the ping to the other network and i leave it to ping all the time... connection doesn't drop and i can connect to other network. If i stop any activity like ping or if i'm not doing anything on other servers the connection just falls asleep and i cannot connect

---

