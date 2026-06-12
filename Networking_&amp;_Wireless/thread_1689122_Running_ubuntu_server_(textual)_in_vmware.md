---
title: "Running ubuntu server (textual) in vmware"
date: 2011-02-16
forum: Networking &amp; Wireless
---

### Post by Sematary on 2011-02-16
So I set up Ubuntu server in Vmware - more as a learning experience than anything else. I also set up apache. I can see the default html file from my local machine but can't seem to figure out how to set it up so that machines on my lan can access it. I'd really appreciate some help on this one.
My gateway is 192.168.1.1
netmask is usual, etc...
I tried setting up a static ip with my lan numbers but apparently that won't work. It must be getting it's info from vm?

---

### Post by Sematary on 2011-02-16
So, to be more specific. I am running Ubuntu 10.10 server in vmware player. I have xubuntu running on another machine and the host for this vm is Windows 7.

I set the static ip to the following:

auto eth0
iface eth0 inet static
       address 192.168.241.138
       netmask 255.255.255.0
       network 192.168.1.0
       gateway 192.168.1.1

The address above was the original ip address given to the vm, I assume by vm player? I tried it with one that would (or should) work in my lan - 192.168.1.101 - the range is 100 - 150 on my gateway. This one was free. After I restarted network services I couldn't ping the gateway so I put the original ip address in and it worked fine. I attempted it with the 101 address and giving resolv.conf the dns of my isp but again, no go. So I set it back to it's original setting (given by vm?) of 192.168.241.2
One last thought. When I ran route -n (with the above settings) I receive the following response:
Destination 192.168.241 Gateway 0.0.0.0 Genmask 255.255.255.0 eth0
Second line
Destination 0.0.0.0     Gateway 192.168.241.2 Genmask 0.0.0.0 eth0

I've also tried the vm with NAT and as a Bridged connection with above settings.
Any thoughts?

---

### Post by Sematary on 2011-02-16
If ANYONE has any thoughts on this, I'd really like to hear them. I can't be the first person to try and do this.

---

