---
title: "Problems with DD-WRT Bridge"
date: 2009-03-28
forum: Networking &amp; Wireless
---

### Post by BuntuFreak on 2009-03-28
I have a WRT54G router with the DD-WRT firmware. I have been using it as a Client Bridge with a couple of windows machines in my bedroom.

The thing is, in Client Bridge mode, DHCP does not work, therefore I had assigned static IPs to both the windows boxes. On of the laptops, I installed Ubuntu 8.0 Hardy, and am having some trouble configuring static IP for it.

Google search yielded the following URL that explains configuring static IP

[http://www.howtogeek.com/howto/ubuntu/change-ubuntu-desktop-from-dhcp-to-a-static-ip-address/](http://www.howtogeek.com/howto/ubuntu/change-ubuntu-desktop-from-dhcp-to-a-static-ip-address/)

There are two problems I'm facing. First I don't see the GUI that is depicted in the above URL. What I see under "Network Configuration" is different, with an IPv4 tab under which I can provide the necessary configuration. However, neither is my configuration working, nor is it accepting it correctly. The NetMask which I specify as 255.255.255.0 becomes 24(?) after I save the configuration.

I even tried manually configuring /etc/network/interfaces to no avail. This is how my setup needs to be

My primary wireless router i.e. Gateway is 192.168.1.1. My Client Bridge is 192.168.1.201 and is configured with 192.168.1.1 as its Gateway.

On my windows machine I used to do this
IP Address: 192.168.1.206 (My static IP for my computer)
Gateway: 192.168.1.201 (address of my Client Bridge)
Subnet Mask: 255.255.255.0

Please note that the Gateway I'm using for my windows computer is my Client Bridge Router IP and NOT the Primary Router IP. That's how I got it to work. When I connected my XBox for to the client bridge, it actually worked with 192.168.1.1 as the Gateway for the XBox. I never understood why the windows box needs my Client Bridge IP as gateway while my XBox needs my Primary Router IP as gateway. This lack of understanding is mostly preventing me from getting my Ubuntu laptop working with my Client Bridge.

Any insights into my problem would be deeply appreciated. I "convinced" a certain family member to give up windows and try Ubuntu like I do for one of my machines. Let's just say I'm in jail right now. Please help !!!

---

### Post by chili555 on 2009-03-28
Well, having tried a few times to get my WRT54G working in client bridge mode, and failing, I can tell you that the process is mysterious.

Since you have conflicting, yet working results; that is, the Windows machine uses the client bridge IP and the Xbox uses the actual gateway, and works, the obvious solution is to try using the gateway address in */etc/network/interfaces.*

If I remember correctly, I also specified the client bridge's MAC address in my file, thus:```
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet static
address 192.168.1.108
netmask 255.255.255.0
gateway 192.168.1.254   <---IP of gateway the bridge repeats
wireless-ap 00:0C:41:19:58:77   <---MAC of bridge
wireless-key 096c7fXXX...
wireless-essid GBR1


#auto eth0
iface eth0 inet dhcp
```Please let us know.

---

### Post by Bucky Ball on 2009-03-28
IP Address: 192.168.1.206
Gateway: 192.168.1.1 
Subnet Mask: 255.255.255.0

Maybe?

---

### Post by BuntuFreak on 2009-03-28
I will try as you say.

One quick question. I noticed you used eth1 instead of eth0 in your example. Are these just logical names? I mean are you saying I should keep eth0 around just comment out the auto line so the DCHP setting ubuntu ships with is a no-op, and then just give logical name eth1 separately and since it is ahead of the eth0 configuration in the file anyways, it will pick it up first?

Or do eth0 and eth1 mean two separate physical network cards?

Thanks.

---

### Post by Bucky Ball on 2009-03-28
IP Address: 192.168.1.206
Gateway: 192.168.1.1 
Subnet Mask: 255.255.255.0

The router with the wan plugged is your gateway, the other is your access point. Everything else looks correct. Your second router should play no part in this except as a through port. If you were using DHCP, you would be getting it served from the wan router, *not* the second router (AP - access point). That is one reason you have DHCP off and a different IP for the second router.

The eth0 or eth1 is not really a concern as it refers to the hard wire ethernet, not the wlan0 which you are trying to get happening.

I'm thinking you have a desktop on a regular router and the wireless router acting as a way for your laptop to get into the network? In that case, access point, not gateway (although it kind of seems like one).

Get into the routers config GUI and go to the wireless properties. Make sure you have an ESSID (a name for the access point) and a WEP key (security key or password it is sometimes called). If not, add them. 

In Ubuntu, open System->Administration->Network, unlock, Wireless properties. Type in the ESSID and WEP key, same as the one you put into the router. Now, I have had some trouble with the static IP and this should be done from the router first, not this setup.

---

### Post by chili555 on 2009-03-28
> **BuntuFreak said:**
> I will try as you say.

One quick question. I noticed you used eth1 instead of eth0 in your example. Are these just logical names? I mean are you saying I should keep eth0 around just comment out the auto line so the DCHP setting ubuntu ships with is a no-op, and then just give logical name eth1 separately and since it is ahead of the eth0 configuration in the file anyways, it will pick it up first?

Or do eth0 and eth1 mean two separate physical network cards?

Thanks.eth0 is my wired ethernet card and eth1 is my wireless. Substitute your interfaces as needed. 

I have *auto eth0* commented out because I don't generally use my wired ethernet and I don't want the boot process slowed down by looking for and failing to connect to ethernet. It simply implies, "Yes, we have an ethernet interface, eth0, but don't start it automatically just now." I just don't DHCP to operate on my not-connected wired ethernet and time out, because there is no wire connected, while I drum my fingers waiting for the machine to boot. If a wire suddenly gets installed at my elbow, I can easily switch with:```
sudo ifdown eth1 && sudo ifup eth0
```

Incidentally, I use static IP's on all my computers so I can easily SSH into them.

---

### Post by Bucky Ball on 2009-03-28
**** Updated ...***

Bucky's easy peasy setup using DHCP (use any IPs that suit):

Setup the routers with one computer plugged in, nothing else (no wan, router, or other computer)

Wired router: 192.168.1.1 (DHCP enabled)
Wireless router (AP): 192.168.1.2 (DHCP disabled)

Plug the routers together using ethernet ports, *not* wan port on the wireless to ethernet port on the wired.

Choose ESSID and WEP key and input with wireless router configuration GUI.

In Ubuntu, open System->Administration->Network, unlock, Wireless properties. Type in the ESSID and WEP key, same as the one you put into the router. Set to 'Configuration' to 'Auto Configuration (DHCP)'.

Done.

---

### Post by BuntuFreak on 2009-03-28
Err, I'm afraid you have it all wrong.

MY WRT54G is wireless. If I wanted to operate it like an Access Point it would be because my primary router was WIRED. This is not the case. Both would also have to be colocated in the same room with my WRT54G serving out DHCP ip's wirelessly.

I'm using my WRT54G as a Client Bridge, i.e. as a glorified wireless card with multiple clients - upto 4 - in another room. My primary router is indeed wireless. This setup works great so I can have computers and or game consoles in my bedrooms connected to the bridge.

---

### Post by BuntuFreak on 2009-03-28
> **Bucky Ball said:**
> **** Updated ...***

Bucky's easy peasy setup using DHCP (use any IPs that suit):

Setup the routers with one computer plugged in, nothing else (no wan, router, or other computer)

Wired router: 192.168.1.1 (DHCP enabled)
Wireless router (AP): 192.168.1.2 (DHCP disabled)

Plug the routers together using ethernet ports, *not* wan port on the wireless to ethernet port on the wired.

Choose ESSID and WEP key and input with wireless router configuration GUI.

In Ubuntu, open System->Administration->Network, unlock, Wireless properties. Type in the ESSID and WEP key, same as the one you put into the router. Set to 'Configuration' to 'Auto Configuration (DHCP)'.

Done.

Again, I'm operating my WRT54G as a bridge. IT has the WEP key and everything set up. Clients of my WRT54G connect using CAT-5 cable. These clients - computers or xbox console - do not need WEP configured. In fact they are not even aware they are hooked up wirelessly to my wireless network. They simply see the WRT54G as the gateway. Of course, why my XBOX "sees" my WRT54G but still needs my Primary Router as the Gateway setting is a mystery for me to solve another day.

Right now, I just need to get my Ubuntu laptop back to working like when it was a Windows laptop, so a certain some one in my household can get me out of the doghouse.

---

### Post by BuntuFreak on 2009-03-28
> **chili555 said:**
> eth0 is my wired ethernet card and eth1 is my wireless. Substitute your interfaces as needed. 

I have *auto eth0* commented out because I don't generally use my wired ethernet and I don't want the boot process slowed down by looking for and failing to connect to ethernet. It simply implies, "Yes, we have an ethernet interface, eth0, but don't start it automatically just now." I just don't DHCP to operate on my not-connected wired ethernet and time out, because there is no wire connected, while I drum my fingers waiting for the machine to boot. If a wire suddenly gets installed at my elbow, I can easily switch with:```
sudo ifdown eth1 && sudo ifup eth0
```

Incidentally, I use static IP's on all my computers so I can easily SSH into them.

Just to clarify, my laptop is old and does not have any wireless card. I used a CAT5 cable to connect to one of the ports of the bridge. I just installed Ubuntu instead of Windows. Should have dual booted in retrospect :-(

In any case, you have given me some good ideas and I'll try them out. Thanks for all your help guys. I'll report back how it goes.

---

### Post by BuntuFreak on 2009-03-28
> **BuntuFreak said:**
> Just to clarify, my laptop is old and does not have any wireless card. I used a CAT5 cable to connect to one of the ports of the bridge. I just installed Ubuntu instead of Windows. Should have dual booted in retrospect :-(

In any case, you have given me some good ideas and I'll try them out. Thanks for all your help guys. I'll report back how it goes.

All right guys. I'm very close to giving up. I don't think this is going to work.

Giving your ubuntu box a static IP is one thing. The problem is, it simply cannot seem to negotiate the bridge. Or maybe it is the XIRCOM PCMCIA adapter that gives me the RJ-45 port? My laptop is so old, it doesn't even have a RJ-45 port. I have to use PCMCIA wireless which I used to at one point, or a XIRCOM Wired adapter which I was using when my computer had windows.

I'm going to go back to windows, then do a dual boot with Ubuntu. This will buy me some time and people in my house will start talking to me again.

Thanks for all of your time and help.

Best Regards.

---

### Post by drewdizzle on 2010-02-13
I also have a DD-WRT with Unbuntu desktop 9.10 behind it.  I found a solution that works from this blog, it worked for me:

[http://www.gersbo.dk/2006/04/dd-wrt-wireless-bridge-update.html](http://www.gersbo.dk/2006/04/dd-wrt-wireless-bridge-update.html)

The short answer is run this command (copy paste it exactly) in telnet on your DD-WRT:

```
# echo 1 >  /proc/sys/net/ipv4/conf/br0/proxy_arp
```

Note that you still have to setup a static ip for your network adapter.

---

