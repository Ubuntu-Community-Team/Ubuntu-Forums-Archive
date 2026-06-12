---
title: "ICS Vista master Ubuntu slave"
date: 2009-02-28
forum: Networking &amp; Wireless
---

### Post by scottclinton on 2009-02-28
Hello. This is my first experience on the forum and I wondered if anybody could help as I have been trying to get this working for ages.

I have two laptops. Laptop A is running windown vista. Laptop B is running the latest ubuntu version I think 8.10

I have internet access on laptop A through a usb broadband connection. 

I would like to access internet on laptop B using this connection as my router has no usb facility.

I have setup ICS internet connection sharing on laptop A but cant get ubuntu to see the internet.

The wirless router is 192.168.1.1

Laptop A is 192.168.1.100 (windows)
Laptop B is 192.168.1.101 (linux)

I have setup resolv.conf with the dns servers 208.67.222.222 and 208.67.220.220 so I think I have done what I need to in respect to dns.

My laptop A (vista) can ping laptop B (ubuntu) and visa versa.
Both laptops can ping the router 192.168.1.1

So how do I configure ubuntu to use ICS as a slave.

Laptop A and laptop B get the IP's from dhcp on the router I guess.

I think I have to configure the default gateway on the ubuntu as laptop a but could someone help with my ubuntu setup so I can use the internet as a slave through ICS.

Thanks

PS. I have been searching posts for ages and am not getting anywhere. As this is my first experience on the forum could someone take pity and help.

---

### Post by Iowan on 2009-02-28
Welcome to the forum! Hope I don't make your first experience a bad one... take comfort in knowing that there are much better resources around here.
Just my opinion, but if Vista machine has been set up for ICS, and if the router has no internet access, then it should be set to send all "internet" traffic to the Vista machine.  The "how" may have to wait for one of those "better resources" I mentioned.

---

### Post by dmizer on 2009-02-28
With ICS, your Vista computer is performing NAT.

In order for ICS to work correctly, you'll need to disable NAT (essentially you need to turn your router into a hub) in your router (wireless will still work). This way, your internet gateway will be the Vista computer.

If you can't figure out how to disable NAT on your router, it would be helpful if you posted the make and model of your router.

---

### Post by scottclinton on 2009-03-01
Wow you guys are great. Thanks for trying to help.

I was beginneing to think I may need to look at the router.

The router is LinkSys Wireless - G 

What you are saying makes sense just need to apply the correct configs for router linux.

---

### Post by dmizer on 2009-03-01
Under "seccurity", disable everything. Under "Basic setup", you'll have to select "Disable" next to "DHCP Server". After this, you will no longer be able to access your router's configuration page, so make sure you get everything set up correctly.

Then, you'll have to set your Vista's second NIC with a static IP address (192.168.1.100 for example). Plug the ethernet cable from Vista into one of the 4 LAN ports (not the WAN port). Set Ubuntu with a static IP (192.168.1.101 for example), and set the gateway to the Vista's static IP address.

If you've configured Vista correctly for ICS, you should now be able to browse the internet with Ubuntu.

---

### Post by scottclinton on 2009-03-09
I'm still not able to get a solution. Hopefully you can help me a further.

Point of interest both laptops have built in wireless so I wondered if an ad hoc network was possible thus cutting out the complexities of the router.

I've tried with ad hoc but am reverting back to what you helped me with in the first palce.

I think I am almost ok.

Here is where we are.

Vista laptop is setup for ics on usb broadband connection i've enable http and https. The interface is ppp0 the ip is 89.211.17.68 mask is 255.255.255.255 gw is 0.0.0.0 this is set by isp dhcp i guess.

Router. I've done what you asked and disabled everything under security firewall etc. I've disabled nat and dhcp and re-assigned the ip to 192.168.0.1
Like you said I then can't use the web interface to it anymore unless reseting factory.

I have plugged a cable from nic on vista laptop into one of the four available ports on the router.

I have re-configured the nic so that the ip is 192.168.0.2 with subnet 255.255.255.0 gw 192.168.0.1

Now comes the client ie my other laptop running ubuntu.

It has a nic but I have no cable so was hoping to connect to the router wireless as the laptop has built in wireless.

I have setup a wireless connection from ubuntu gui wlan0 and have configured the ip to be 192.168.0.3 subnet 255.255.255.0 gw 192.168.0.2 (which is the ip of the vista nic) I made sure that the mode was infrastructure and not adhoc.

When I go back to the gui the gateway is 0.0.0.0 ?

Now from vista I can ping the ip of the linux 192.168.0.3
I can ping the nic on the vista 192.168.0.2
and I can also ping 192.168.0.1

On the linux I can ping all the internal numbers 192.168.0.3 (wlan0) 192.168.0.2 and 192.168.0.1

But I still cant see the internet from ubuntu laptop.

Have you any ideas. Do I need further config on ubuntu. Could you explain what I need to do with dns on ubuntu laptop if anything.

I've been trying for weeks now to get this to work and would be ever so gratefull if you could help.

I feel I am so close now.

Thanks

PS ad hoc may be an option but I read that you need more that one client and also im not sure how ics on windows operates with wlan0 as apposed to eth0. I'm not a network guy.

---

### Post by dmizer on 2009-03-09
I don't think Ad-hoc will work.

If you can ping from your Ubuntu client to your Vista, then Ubuntu is configured correctly. Can you ping any external addresses from Ubuntu like
```
ping 6.249.89.104
```

If so, then you just need to configure DNS servers according to the step under "note" here: [https://www.opendns.com/start/device/ubuntu#step8](https://www.opendns.com/start/device/ubuntu#step8)

---

### Post by scottclinton on 2009-03-09
Hi thanks for responding quick. I cant ping any external IP's from ubuntu.

I notice that when I run route -n no default gw exists. Do I need to add one and if so is it 192.168.0.2 (vista nic ip) or 89.211.22.189 (vista ppp)

When I follow the link you suggested it mentions for dns dhclient.conf is this not applicable to dhcp as I have that disabled

---

### Post by scottclinton on 2009-03-09
also the output to route -n shows

192.168.0.0
169.254.0.0

not sure what the second ip is all about

---

### Post by GWBouge on 2009-03-09
I'm having a similar issue ... maybe my problems can help figure out yours ...

Computer A 
     -> Vista, Direct Internet via Sierra Wireless 881u
     -> Static: 192.168.0.1


Computer B
     -> Dual Boot: Vista/Ubuntu 8.10
     -> Static: 192.168.0.2
     -> Netmask: 255.255.255.0
     -> Gateway: 192.168.0.1

Computers connected through a 5-port Hub

I know ICS is set up right on A, because the Vista partition on B has internet access.  the Ubuntu partition can't get internet, however I can see the network and all shared files and folders.  both the Vista and Ubuntu partitions have the same network IP, mask, and gateway.

The kicker ... I've got Windows XP set up in VirtualBox on the Ubuntu partition, and it gets internet access ... I'm using it to post this right now.  does Vista ICS kick back a non-windows networked system?

---

### Post by dmizer on 2009-03-09
GWBouge, can you ping external IP addresses as outlined in [post 7]("http://ubuntuforums.org/showpost.php?p=6864441&postcount=7")?

> **scottclinton said:**
> Hi thanks for responding quick. I cant ping any external IP's from ubuntu.

I notice that when I run route -n no default gw exists. Do I need to add one and if so is it 192.168.0.2 (vista nic ip) or 89.211.22.189 (vista ppp)

When I follow the link you suggested it mentions for dns dhclient.conf is this not applicable to dhcp as I have that disabled
That file still handles DNS, so yes even though the file is related to DHCP, you still need to edit it.

Yes, you'll also have to add Vista's static internal IP address as your gateway.

---

### Post by GWBouge on 2009-03-09
> **dmizer said:**
> GWBouge, can you ping external IP addresses as outlined in [URL="http://ubuntuforums.org/showpost.php?p=6864441&postcount=7"]post 7

Yes, actually.  pinging 209.191.93.52 (yahoo.com) in the terminal worked, but I can't seem to use anything except ping.  Firefox, synaptec ... even apt-get update from the terminal won't go through.

---

### Post by dmizer on 2009-03-09
> **GWBouge said:**
> Yes, actually.  pinging 209.191.93.52 (yahoo.com) in the terminal worked, but I can't seem to use anything except ping.  Firefox, synaptec ... even apt-get update from the terminal won't go through.

Your only problem then is DNS resolution. You should be able to solve that by following the link I posted in post 7.

---

### Post by GWBouge on 2009-03-10
> **dmizer said:**
> You should be able to solve that by following the link I posted in post 7.

Nope    =o(

I can still ping 206.190.60.37, but not yahoo.com

---

### Post by GWBouge on 2009-03-15
Just an update ...

while adding the command to dhclient.conf from your link didn't work for me, manually adding the nameservers to resolv.conf fixed it, as outlined in post #7 here:

[http://ubuntuforums.org/archive/index.php/t-905909.html](http://ubuntuforums.org/archive/index.php/t-905909.html)

"
Check your "/etc/resolv.conf" file. It should have the name servers mentioned


nameserver 208.67.222.222
nameserver 208.67.220.220
"

I'm not sure the difference, but I probably just messed something up or misspelled something.  I'm such a n00b!    =oX

---

### Post by dmizer on 2009-03-15
Does that edit survive a reboot?

---

### Post by GWBouge on 2009-03-16
Yeah.  it seems to be working fine now, even after reboot and kernel upgrades.

---

