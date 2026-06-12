---
title: "Help with eth1"
date: 2010-07-26
forum: Networking &amp; Wireless
---

### Post by Trogan87 on 2010-07-26
Hi,

I'm running LTSP with 2 network cards.

**Eth0** is used to boot into the thin client. This is working fine - no problems with this. 

Now I'm trying to configure **eth1** which is to connect to the Internet through my router. However, there is no connection. 

This is the output from etc/network/interfaces:
```
# The primary network interface
auto eth0
iface eth0 inet static
          address 192.168.0.40
          netmask 255.255.255.0
          network 192.168.0.0
          broadcast 192.168.0.255
          gateway 192.168.0.1
          # dns-* options are implemented by the resolvconf package, if installed
          dns-nameservers 192.168.0.1
          dns-search lonwshop

# The secondary network interface
auto eth1
iface eth1 inet static
          address 192.168.0.10
          netmask 255.255.255.0
          network 192.168.0.0
          broadcast 192.168.0.255
          gateway 192.168.0.1
          # dns-* options are implemented by the resolvconf package, if installed
          dns-nameservers 192.168.0.1
```Any help to get **eth1** connected to the Internet would be appreciated.

---

### Post by lloyd_b on 2010-07-26
Here's what I *think* is happening:

1.  eth0 starts up, with a netmask of 255.255.255.0 and a gateway at 192.168.0.1.  This adds a default route via eth0 to the gateway.

2.  eth1 start up, with the same netmask and gateway specified.  This adds a second route to that gateway, using eth1 this time.

3.  When you try to talk to any host outside of the 192.168.0.x range, the computer is using the first route to the gateway at 192.168.0.1 via eth0, and I'm guessing that network segment doesn't actually connect to 192.168.0.1.

I'm not sure I understand what you're using eth0 for.  Is this being used to boot this machine, or to boot other thin client devices from this machine?

Either way, try removing the "gateway" line from the configuration for eth0 - this will prevent the creation of a default route via eth0, and the machine will hopefully then use the route via eth1 to reach the gateway (and thus the internet).

One note - if you have multiple physical network segments, you should really configure them as different logical networks.  For instance, if the network eth0 is attached to is physically separate from the network eth1 attaches to, then you could have one on 192.168.0.x and the other on 192.168.1.x.  This prevents conflicts like this from happening.

Lloyd B.

---

### Post by Trogan87 on 2010-07-26
Hi Lloyd

Thanks for your reply.

> I'm not sure I understand what you're using eth0 for.  Is this being  used to boot this machine, or to boot other thin client devices from  this machine?**eth0** is being used to boot thin clients to the terminal server (where the two network cards are installed). So I connect a thin client from **eth0** which then boots into the terminal server. 


I removed the "gateway" line from the **eth0** configuration but still cannot connect to the Internet from **eth1**. 

> One note - if you have multiple physical network segments, you should  really configure them as different logical networks.  For instance, if  the network eth0 is attached to is physically separate from the network  eth1 attaches to, then you could have one on 192.168.0.x and the other  on 192.168.1.x.  This prevents conflicts like this from happening.
I changed the configuration for **eth0** to be on 192.168.1.x and left **eth1** on 192.168.0.x. Doing this prevented the thin client from booting into the terminal server so had to change back to original settings.

Any other possible solutions?

---

### Post by lloyd_b on 2010-07-26
> **Trogan87 said:**
> Hi Lloyd

Thanks for your reply.

**eth0** is being used to boot thin clients to the terminal server (where the two network cards are installed). So I connect a thin client from **eth0** which then boots into the terminal server. 


I removed the "gateway" line from the **eth0** configuration but still cannot connect to the Internet from **eth1**. 

I changed the configuration for **eth0** to be on 192.168.1.x and left **eth1** on 192.168.0.x. Doing this prevented the thin client from booting into the terminal server so had to change back to original settings.

Any other possible solutions?

I'm guessing that changes are required to the thin clients as well in order to accomplish that network change - since I'm not familiar with them, I can't give you any guidance on that score.

Try a simple test.  In a terminal window:```
sudo ifconfig eth0 down
```This will shut down the eth0 interface completely, removing any possible conflicts.  Then see if you have internet connectivity via eth1.

If not, in a terminal window again:```
ping 192.168.0.1
``` and make sure that the eth1 interface can actually reach the gateway.

Also - with both interfaces active (you can reset everything with the command "sudo /etc/init.d/networking restart"), could you run the commands "ifconfig -a" and "route -n" and post the results?  This will provide a lot of info as to what exactly on how the machine used the info from "/etc/network/interfaces".

Lloyd B.

---

### Post by Trogan87 on 2010-07-27
Hi Lloyd,

> Try a simple test.  In a terminal window:```
sudo ifconfig eth0 down
```This will shut down the eth0 interface completely, removing any possible conflicts.  Then see if you have internet connectivity via eth1.
Yes, this worked. Shutting down **eth0** gave Internet connectivity to **eth1**. Soon as I restarted/made active both interfaces, **eth1** stopped connecting to the Internet.


I don't have the server (a [_Dell PowerEdge 1950_]("http://support.euro.dell.com/support/edocs/systems/pe1950/en/hom/html/install.htm")) with me. I have taken it back to work where I will only be able to work with it maybe once or twice a week.

While I had the server at home I was giving **eht1** an IP address of 192.168.0.x as this is my home network. However, at work the IP address I believe is 192.168.1.x or similar but not 192.168.0.x.

Am I right in assuming that I just change the settings I have for **eth1** to the those of the network settings at work? For example, change the 192.168.0.x to whatever is at work?


Thanks!

---

### Post by lloyd_b on 2010-07-27
> **Trogan87 said:**
> Hi Lloyd,


Yes, this worked. Shutting down **eth0** gave Internet connectivity to **eth1**. Soon as I restarted/made active both interfaces, **eth1** stopped connecting to the Internet.


I don't have the server (a [_Dell PowerEdge 1950_]("http://support.euro.dell.com/support/edocs/systems/pe1950/en/hom/html/install.htm")) with me. I have taken it back to work where I will only be able to work with it maybe once or twice a week.

While I had the server at home I was giving **eht1** an IP address of 192.168.0.x as this is my home network. However, at work the IP address I believe is 192.168.1.x or similar but not 192.168.0.x.

Am I right in assuming that I just change the settings I have for **eth1** to the those of the network settings at work? For example, change the 192.168.0.x to whatever is at work?


Thanks!

You'll need to talk to the network people at work to be sure, but it should just be a matter of changing the IP address, network, and gateway to the 192.168.1.x range.

Assuming your work network supports it, you might want to skip that altogether and just configure it for DHCP instead - that way this information will be automatically configured for you.

Lloyd B.

---

### Post by YesWeCan on 2010-07-27
It may be a problem with the kernel routing table. Post 'route -n'.
You may need to add an explicit route to eth1 like 'sudo route add -net 192.168.0.1/32 dev eth1'
Otherwise the 192.168.0.0/24 via eth0 catchall will route 192.168.0.1 via eth0.

---

