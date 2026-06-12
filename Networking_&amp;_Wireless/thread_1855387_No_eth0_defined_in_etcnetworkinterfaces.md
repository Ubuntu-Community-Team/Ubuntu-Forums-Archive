---
title: "No eth0 defined in /etc/network/interfaces"
date: 2011-10-06
forum: Networking &amp; Wireless
---

### Post by yotamoo on 2011-10-06
Hi, this is something that bugs me as I am trying to learn linux networking. I read in the manual that most ethernet configuration is located in /etc/network/interfaces. This is my interfaces file:

[PHP]auto lo
iface lo inet loopback
[/PHP]

As you can see no eth connection is defined, even though everything works perfect. Here's my ifconfig eth0 output:

[PHP]
eth0      Link encap:Ethernet  HWaddr 00:19:db:c8:ae:03  
          inet addr:10.0.0.2  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:dbff:fec8:ae03/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10377768 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6162989 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2406411484 (2.4 GB)  TX bytes:443869381 (443.8 MB)
          Interrupt:27 
[/PHP]

So my question is: how come no ethernet interface is defined, and still everything works perfectly fine?
Thanks

---

### Post by SlugSlug on 2011-10-06
you most likely have network-manager installed

---

### Post by yotamoo on 2011-10-06
I do! If so, where can I find the configuration files?
Also, I don't remember installing it, any chance its default on ubuntu? I don't see why, but still

---

### Post by SlugSlug on 2011-10-06
its installed by default, you can remove it to make /etc/network/interfaces  work (I do this on each of my installs) but if you've set it up wrong then you'll be without the net.

If you prefer you can just edit the IP settings through the GUI.

---

### Post by AskTell on 2011-10-06
if your doing static your interfaces file should look something like this

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.105
netmask 255.255.255.0
network 192.168.1.0 
broadcast 192.168.0.255
gateway 192.168.1.1

for dhcp it will look like this

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
#address 192.168.1.105
#netmask 255.255.255.0
#network 192.168.1.0
#broadcast 192.168.0.255
#gateway 192.168.1.1

# is used to comment out code 

for  a static ip you will also need your nameserver ip's which you will enter into /etc/resolv.conf 

you can find nameservers in your router status under dns (at least on my router),  connect to your router using your gateway ip address which you can find by typing ifconfig in terminal. enter the gateway ip in your browser, most  default name/passwords are  admin/admin or admin/password (look up your routers defaults on google or whatever search engine you prefer) once you've done all this you need to set aside a reserved IP so your routers dhcp doesn't assign your static ip to another computer (optional)

if you cant find the nameservers in your router just use dhcp settings in /etc/network/interfaces and type enter the following in terminal

sudo ifdown eth0
sudo ifup eth0

Now resolv.conf should have the name servers and you can change back to static if you wish.

I'm still working for my 50 beans and I'm giving myself a gold star:KS... <--- rofl

---

### Post by jonobr on 2011-10-06
```
address 192.168.1.105
netmask 255.255.255.0
network 192.168.0.0<--- this should be 192.168.1.0
```

---

### Post by MOGuy78 on 2011-10-12
Hi everyone.
I didn't know if I should ask this here since my question is nearly the same or if I should start a new thread.  Anyway, here's my question.

I'm also needing help setting up my IP address.  I'm setting up my computer to use as a file server just for my home intranet, so I don't need
any access going to or from it to the internet.

Also, I'm using Ubuntu Server 10.04 and I'm wanting to use a static ip setup for access to the computer.

In many of the threads that I've read, it says that if your setting up a static ip,
your /etc/network/interfaces file should look something like this, as it is written above:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.105
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.0.255
gateway 192.168.1.1


**********************

Looking at this example, do I still need all of the Ip addresses given to use for my purpose or only somes of them?  If so, which ones?

---

### Post by 11notes on 2011-10-12
> **MOGuy78 said:**
> Hi everyone.
I didn't know if I should ask this here since my question is nearly the same or if I should start a new thread.  Anyway, here's my question.

I'm also needing help setting up my IP address.  I'm setting up my computer to use as a file server just for my home intranet, so I don't need
any access going to or from it to the internet.

Also, I'm using Ubuntu Server 10.04 and I'm wanting to use a static ip setup for access to the computer.

In many of the threads that I've read, it says that if your setting up a static ip,
your /etc/network/interfaces file should look something like this, as it is written above:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.105
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.0.255
gateway 192.168.1.1


**********************

Looking at this example, do I still need all of the Ip addresses given to use for my purpose or only somes of them?  If so, which ones?

```
auto eth0
iface eth0 inet static
address 192.168.1.105
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.0.255
gateway 192.168.1.1
```

should work just fine if the gateway is your router (192.168.1.1) and it should be possible to access the ubuntu box via 192.168.1.105

---

### Post by dineshs on 2011-10-12
> **yotamoo said:**
> I do! If so, where can I find the configuration files?
 In /etc/NetworkManager/system-connections
There will be seperate files for eth0 DSL etc

---

### Post by jonobr on 2011-10-12
Not sure I understand the question, but if your given a static IP the contents of your /etc/network.interfaces lines will change

> auto eth0
iface eth0 inet static
address 192.168.1.105
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.0.255
gateway 192.168.1.1

Each line here has a unique function to tell the machine its ip address, how to talk to the network and to other devices and how to go to the internt.

The above example is useful for a user who needs an IP address (static) on the 192.168.1.x network and if he is using eth0 and if his gateway is .1

If you have been given a static IP address by your ISP or you picking one yourself, the contents of the above file (if you choose to use it this way,) will differ

---

### Post by MOGuy78 on 2011-10-22
I understand that all of this is what would usually be in the /etc/network/interfaces file.  But do I need all of it since all I'm wanting it to do is allow my home network to connect to the server?  I don't have any need for it to access the internet.

Do I need all of this as it's written above?
auto eth0
iface eth0 inet static
address 192.168.1.105
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.0.255
gateway 192.168.1.1

---

