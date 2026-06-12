---
title: "GoDaddy Domain to IP"
date: 2009-09-29
forum: Networking &amp; Wireless
---

### Post by mohabitar on 2009-09-29
I've tried searching for this question everywhere, I just cant find the answer I'm looking for. Its a pretty simple scenario:

I have Xubuntu running **_virtually through Sun VirtualBox_**. I installed apache and everything and localhost, on the virtual machine, works just fine. However on my host computer, my windows machine where the virtual is running from, if I type localhost, nothing comes up. 

**1.That is the first question, how do I fix that?**

Another issue is I have a GoDaddy domain registered, say xyz.com. I understand that in order to have that domain forward to my virtual server, I'll need to have the servers IP address. 

**2.Now which IP address would that be? **Would it be the one where if I go to whatismyipaddress.com? Would I use that one. Remember that I'd like it to connect to the virtual machine, not the host. Right now if I go to whatismyipaddress.com on both machines, both display the same result. 

**3.Is that supposed to happen? If not how do I fix that. **

**4. If that is not the IP address I should be using, where (in detail please) would I find the appropriate IP address, **

**5. And how would I configure that IP address to work with my GoDaddy domain name?** Would I use an A-host. Or is it through CNAMES? Or is it nameservers? Please outline the steps neccessary to complete this task. 

Any help would be greatly appreciated, even if you only have answers to some of the questions above.

---

### Post by redmk2 on 2009-09-30
> **mohabitar said:**
> I've tried searching for this question everywhere, I just cant find the answer I'm looking for. Its a pretty simple scenario:

I have Xubuntu running **_virtually through Sun VirtualBox_**. I installed apache and everything and localhost, on the virtual machine, works just fine. However on my host computer, my windows machine where the virtual is running from, if I type localhost, nothing comes up.

Local host is probably not how you should look at it.  The **host** computer has a NIC and you can refer to the NIC as *localhost*.  This is an internal way of addressing it.  The **guest** OS (the virtual machine) also has a NIC.  You and refer to that NIC as localhost when you are addressing it via the terminal. Both carry an IP address in 127.0.0.n range but they are **not** on the same network.  They have different MAC addresses and live in different worlds.

You should use the IP address of the NIC (**eth*n***) when you want to communicate over the network (LAN or WAN).
> 

**1.That is the first question, how do I fix that?**

As the physical NIC in the host computer and the virtual NIC in the guest OS are NOT on the same subnet (segment) you will need to **bridge** them.  This will allow them to communicate using TCP/IP layer 2 protocols (ARP).  ARP maps the IP address to a MAC address.

At this point you should now be have connectivity between the host and guest OS's. > 

Another issue is I have a GoDaddy domain registered, say xyz.com. I understand that in order to have that domain forward to my virtual server, I'll need to have the servers IP address.

GoDaddy maintains DNS servers that will point (map) the Name to the IP address you supply.> 

**2.Now which IP address would that be? **Would it be the one where if I go to whatismyipaddress.com? 

Would I use that one. Remember that I'd like it to connect to the virtual machine, not the host. Right now if I go to whatismyipaddress.com on both machines, both display the same result. 

**3.Is that supposed to happen? If not how do I fix that. **

**4. If that is not the IP address I should be using, where (in detail please) would I find the appropriate IP address, **

In short DNS should map your domain name (FQDN) to the IP address that either is assigned to the NIC interface by you or the external host providing NAT services (your router) if you are using private addressing.  

To answer this fully we would need to see how you have your network set up (it's IP topology).  Specifically, what addressing scheme you are using for the LAN.  

Are you using private or public IP addresses for your LAN?  What type of broadband connectivity is your ISP providing?  Is the WAN side IP obtained by DHCP or is it a static IP provided?> 



**5. And how would I configure that IP address to work with my GoDaddy domain name?** Would I use an A-host. Or is it through CNAMES? Or is it nameservers? Please outline the steps neccessary to complete this task. 


I would recommend you use GoDaddy's DNS servers.  They will host your DNS information and point (map) all your DNS services to the IP addresses you specify.

---

