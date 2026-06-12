---
title: "Set up static ip for lucid vbox guest"
date: 2010-08-14
forum: Networking &amp; Wireless
---

### Post by virgil_machine on 2010-08-14
I have virtualbox on a lucid 64 bit host.  I am trying to set up a intranet site on a guest (also lucid 64).  In vbox on the host I went to settings/network for the guest and added a bridged adapter.  When I booted the vm all was well and I got a real ip that I could use to access from other machines (other vms, the host, and other physical machines on teh network). So far, so good.

Now I want a static ip for the vm so I can know how to reference it. I found an article here: [http://www.munkyonline.com/articles/lamp-ubuntu-server-on-virtualbox.html/comment-page-1#comment-114]("http://www.munkyonline.com/articles/lamp-ubuntu-server-on-virtualbox.html/comment-page-1#comment-114") that says to edit /etc/network/adapters on the guest as follows:

auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
address 192.168.1.85
netmask 255.255.255.0
network 192.168.1.255
gateway 192.168.1.25

I'm not sure what the values should be. I'm assuming:
[LIST]
[*]address: is the static ip I want for the guest
[*]netmask: is what I get from netstat -r on the host (or the vm--the only difference between the two is default--which is 10.0.2.2 on the vm and 192.blah.blah.blah on the host.
[*]network: is ip of the host and blah.blah.blah.0 
[*]gateway: ip of the router (blah.blah.blah.1)
[/LIST] 

Where can I find the correct values? [This part is solved...see next post for answer and next question.]

---

### Post by virgil_machine on 2010-08-15
OK, I got this to work. But I am on to the next question.

Here's how I got it to work: I had the right values--my assumptions above were correct.  However, I set it up for eth0 because the bridged adapter in virtualbox settings on the host for the vm says (bridged adapter, eth0).  Then I noticed that when I connected the vm via eth0 I was getting a 10.0.blahblah ip, but when I connected via eth1 I got a valid 192.blahblah ip.

So, I changed /etc/network/interfaces to start off with auto eth1/iface eth1 inet static.  Now, I show only 1 adapter, eth0, and I can get to the vm via the static ip I chose.

Next question: Now I want to give the vm a name so I don't have to reference it by ip. In investigating DNS, I found instructions to edit /etc/resolv.conf.
a) is that right?
b) do that on the host or the guest? 
c) If the guest ip is blah.blah.blah.666 and my proposed name to resolve is satan.com, what would I code in /etc/resolv.conf (or wherever)?

Thanks for your help.

---

### Post by Hero of Time on 2010-08-15
In VirtualBox, you have several networking options to attach your VM to. When your VM gets an IP of 10.0.2.15, with a default gateway of 10.0.2.2, it means that you attached it to NAT. This won't work if you don't want to forward ports or simply let the virtual machine appear as a normal one on the network with it's own IP address. You have to attach it to bridged.

Now for the network configuration. You are correct for how things work in the interfaces file. It would've been a lot easier if you checked the man page for it, just type 'man interfaces' in a terminal and you get all the information you need in how the syntax works.

As for the DNS access part, everything you set in /etc/resolv.conf is considered a DNS server. You don't put your own IP address there or anything if it's not a DNS server.
Let's say you want to connect to your VM from the Host without using the IP address, and don't have access to the DNS server or alter it in any way, you can add the address and name of the machine in a different file, namely /etc/hosts. This file is checked before a request is send to the DNS servers. It's entry would be something like this:
```
192.168.1.85  intranet
```
Now you can access the VM that has the IP address 192.168.1.85 on the name 'intranet'.

---

### Post by virgil_machine on 2010-08-15
Thank you. That works from the host to the vm. 
I figured out that I need to update the hosts file on all computers in the network--that works for my ubuntu machines---I assume for that's windows/system32/drivers/etc/hosts.

Also, why should I not use DNS for this?

---

### Post by Hero of Time on 2010-08-18
You can use DNS for this, but you need to either alter the one you have already, or set one up for the entire network to use. If your router is the DNS server, you usually can't alter it's database, because all it does it forward all requests to the ISP DNS server. Running your own DNS server means that one computer needs to be on 24/7, because all computers will be using that machine for DNS queries. When the machine is offline, so will your internet (or slower if you set the secondary DNS as your router).

---

