---
title: "automatically do 'ifconfig eth1 up' on startup"
date: 2010-01-27
forum: Networking &amp; Wireless
---

### Post by roop_s on 2010-01-27
what i need are interfaces to come up on their own when the system boots, the same as they would when you run "sudo ifconfig ethx up"

some differences are that I don't want DHCP nor static IPs assigned, I want the interfaces to have no IPs. these interfaces are just physical interfaces for vmware server.

i tried putting this into my /etc/network/interfaces file:

auto eth1
auto eth2
auto eth3

but it didn't help. on reboot ifconfig only showed my one DHCP configured interface, eth0. i had to run ifconfig ethx up on eth1-3.

what's the simplest, cleanest way to do this?

---

### Post by Skaperen on 2010-01-27
If it doesn't work via /etc/network/interfaces, then maybe just doing it through /etc/rc.local will do the job.  It may not be pretty, but that's what I'm considering doing for my issue with multiple IP addresses if "the right way" isn't available.

---

### Post by MaindotC on 2010-01-27
> **roop_s said:**
> what i need are interfaces to come up on their own when the system boots, the same as they would when you run "sudo ifconfig ethx up"

some differences are that I don't want DHCP nor static IPs assigned, I want the interfaces to have no IPs. these interfaces are just physical interfaces for vmware server.


Would you mind explaining why you are doing this?  I'm just curious.

---

### Post by roop_s on 2010-01-27
Skaperen - i'm going to leave it in rc.local as a workaround. i wanted to use the interfaces file to keep all my interface configs in one spot. i'm sure in 8 months from now i'll totally forget where i put this setting and spend hours trying to find it. also i figured all user based interface settings should go into the interfaces file only.

strAlan - it's for vmware. the interfaces are internet facing to a vmware guest that's running. i don't want IPs on them and they cannot do DHCP as they will get an IP address.

---

### Post by MaindotC on 2010-01-27
> **roop_s said:**
> strAlan - it's for vmware. the interfaces are internet facing to a vmware guest that's running. i don't want IPs on them and they cannot do DHCP as they will get an IP address.

I understand it's for vmware but that doesn't seem to be relevant to me.  I just don't understand why you would want the interfaces up at all if you don't want them assigned a static or dynamic address.  It's not really my place to try and understand WHY you want to do this, but I can't help but think that I've got a better solution waiting for you if only I knew why you would want the interfaces up but unable to communicate with anything.

I'm going to ask some additional questions - feel free to disregard them if it's not worth your time.  Are these physical interfaces assigned to each vm - like do you have more than one network card installed, and one network card for each vm?  Is this for testing if a driver will properly install and recognise network hardware if you install it?

---

### Post by roop_s on 2010-01-27
Sure, if providing you with why I want to do this will result in a really good answer on how to do this, i'll bite.

This is what's going on:

a) ubuntu 9.10 server is the host OS and has 4 nics in it
b) It's vmware server for guests that are running routing/firewall OSes
c) ISP links are directly connected to ubuntu 9.10, a routing OS handles firewall, not ubuntu 9.10
d) First it's a waste to put my ISP addresses on the ubuntu host. it never needs to be reached directly from the internet
e) Next it won't be firewalled so i think it's a huge security problem, this is why it has no IPs on these interfaces.


I understand it's for vmware but that doesn't seem to be relevant to me.
- it's 100% relevant. normally i would want an ip on an interface otherwise of course you wouldn't be able to reach the system. since it's a VM host, it's not needed.

I just don't understand why you would want the interfaces up at all if you don't want them assigned a static or dynamic address. 
- answered in d) and e)

It's not really my place to try and understand WHY you want to do this, but I can't help but think that I've got a better solution waiting for you if only I knew why you would want the interfaces up but unable to communicate with anything.
- perhaps the question is "what good is an interface without an ip"? the interface is a transparent bridge to the VM host. that's all it's used for. packets go to the interface because there is a virtual host on a virtual bridge with a virtual mac address on the other side.

I'm going to ask some additional questions - feel free to disregard them if it's not worth your time. Are these physical interfaces assigned to each vm - like do you have more than one network card installed, and one network card for each vm? 
- nic question answered in a)
- one vm running a routing/firewall OS that is bridged to all 4 nics. 1 nic is lan, the three others each have an ISP link.

Is this for testing if a driver will properly install and recognise network hardware if you install it?  
- nope, testing its done, everything works great. i just need to remove the requirement of doing an ifconfig up ethx on bootup - if this server reboots all important interfaces are down and i have to go home to type ífconfig up ethx to fix this.

---

### Post by MaindotC on 2010-01-28
I'm still trying to pictures this...have patience

---

