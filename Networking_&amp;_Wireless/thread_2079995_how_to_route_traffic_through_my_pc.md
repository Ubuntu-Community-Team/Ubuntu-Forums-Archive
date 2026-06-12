---
title: "how to route traffic through my pc?"
date: 2012-11-02
forum: Networking &amp; Wireless
---

### Post by jonnyboysmithy on 2012-11-02
I'm trying to route internet traffic through my pc but I'm having little success.
I tried using the "use access point" feature on the setup page  my router but that wasn't much good because the feature allows another access point to connect, not vice versa (as far as I can tell). I want the router to be the access point and my laptop to be the gateway to the internet (the modem plugs into my laptop).

I have the modem plugged into my lan, my wifi connected to my router.
So now I want to share the internet (eth0) with my router (connected on wlan0).
How can I do this?

---

### Post by jonnyboysmithy on 2012-11-04
Bump.

---

### Post by fwre01 on 2012-11-05
You will need to do a few things:

1. Enable IP forwarding, this will allow your PC to route traffic between interfaces. There are a few ways of doing this, but you will likely want to do this permanently. It's quite straight forward, this link will help in doing this.

[http://www.ducea.com/2006/08/01/how-to-enable-ip-forwarding-in-linux/]("http://www.ducea.com/2006/08/01/how-to-enable-ip-forwarding-in-linux/") 

2. You will need to configure your remaining clients on the network to use the wireless interface on your computer as their default gateway, this can be done from the DHCP settings, or simply manually defined on each client.

3. I will need a little more information here, could you confirm if the public IP address issued to you by your service provider is the address of your eth0 interface? If so, you will need to install (if not already) IPTABLES and configure it to perform port address translation (also called masquerading) which is a form of NAT which translates all of your internal hosts IP addresses to this public address when destined for the internet. This link will likely help, but I will see if I can dig up some old examples also:

[http://www.ibiblio.org/pub/linux/docs/howto/other-formats/html_single/Masquerading-Simple-HOWTO.html]("http://www.ibiblio.org/pub/linux/docs/howto/other-formats/html_single/Masquerading-Simple-HOWTO.html")

Let us know how you go.

---

### Post by jonnyboysmithy on 2012-11-07
Thanks for the info. Interesting stuff.
Last time I needed to use my machine as gateway went to >Systems Settings>Network>Wireless>use as hotspot and that worked well.

I asked the question wrong. I'm hoping set it up like: 
Other pcs connect to-> router which connects to ->my laptop which connects to-> modem to ->internet

Or: 
Other pcs  -> router ->my laptop which routes back to ->router which goes to-> modem to ->internet

The thing is I want the router being used . Is there anyway to do this?

---

### Post by fwre01 on 2012-11-07
Hey, yeah I think we're on the same page. 

I have drawn a couple of diagrams (attached to this post) to try and represent it. Let me know if this is what you're after.

---

### Post by jonnyboysmithy on 2012-11-07
Yes this is exactly what I'm after. :)
Edit: I tried googling it but I could never get good search results for what I was trying to do.

---

### Post by fwre01 on 2012-11-07
Cool. The three things I wrote at the top will need to be done to complete this.

The reason IP forwarding needs to be enabled on the laptop connected to the modem is because by default a computer wont route traffic between interfaces (i.e between wlan0 and eth0)

Next, I assume that when your 'other' wired/wireless devices connect to the network that the router gives those devices IP addresses in the form of a DHCP lease? This DHCP scope will need to be changed to issue a default gateway value of the WLAN0 IP address on the laptop. This instructs each client on the network that to reach networks outside of their local subnet (i.e the internet) they must send their traffic to their default gateway (this traffic will go through the router)

Lastly, when the traffic reaches the laptop and is sent on towards the internet the source address of the client will need to be changed to be the IP address of eth0. This is because only this public address is able to be routed by your upstream ISP routers. 

EDIT: I have found another good thread detailing the NAT section a little simpler:

[http://ubuntuforums.org/showthread.php?t=2081172]("http://ubuntuforums.org/showthread.php?t=2081172")

If your internal subnet is 192.168.1.0/24, the piece of code that you're after would be:

> echo "IP Forwarding and Routing for gateway use..."
iptables -A FORWARD -o eth0 -i wlan0 -s 192.168.1.0/24 -m conntrack --ctstate NEW -j ACCEPT
iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

echo "Enable Packet Forwarding..."
echo 1 > /proc/sys/net/ipv4/ip_forward


Any other questions or problems let me know.

---

### Post by jonnyboysmithy on 2012-11-11
I've been away from my computer for a few days.. I'm back!! :D

 1. I've got ipforwarding done. I had to use sudo -i then I did
  ```
echo 1 > /proc/sys/net/ipv4/ip_forward
  
``` then I did ```
exit
``` I heard its bad practice to use sudo -i? I used it because putting sudo in front of the command left me with :permission denied.

2. Changing the default gateway: So I need to change the gateway to my laptops ip so that traffic gets directed to my laptops wlan0 right? How to do this? There is a page on my routers setup page titled LAN>Static routing. See attached picture.

I have DHCP setup so it automatically addresses ip addresses.

---

### Post by fwre01 on 2012-11-12
sudo -i is fine, but you may want to check if this setting is still applied after a reboot.

Yes, changing the default gateway is what you will need to do. It's unusual, but your router doesn't appear to let you change this value, try the 'more info' link on the LAN > LAN SETTINGS page, under DHCP sever, there may be more settings in there.

What's the model of router you are using?

If it won't let you change this, you really only have three options:

1. Get a router that does allow you to make these kinds of advanced changes
2. Disable the DHCP server on your router and install a DHCP server on the laptop connected to the modem.
3. Statically assign a unique IP address on each device connected to the network.

---

### Post by jonnyboysmithy on 2012-11-12
The router is a belkin F5D8235-4 v1000
I'll rerun the command after reboot, later I'll make it permanent.
I could statically assign all the ips gateways from 192.168.2.2 to say 20? That should work.
Also I have reserved the address for my wlan0 so its always the same ip (its 192.168.2.12)

I'm not sure if I'll need masquerading.. We have a radio link to a tower on a mountain. Attached is a screen shot of connection info screen when the modem is plugged in. I think it does the translating? I see the default route is 192.168.0.1

---

### Post by Doug S on 2012-11-12
> I'm not sure if I'll need masqueradingYes, you will need the network address translation (NAT).
Your gateway will perform NAT to/from 192.168.2.XXX - 192.168.0.100 and then further upstream there will be another NAT to internet

---

### Post by fwre01 on 2012-11-15
It sounds as though you're on the right track.

I'm not convinced you will need masquerading considering your eth0 interface is on private address space. One would assume your upstream gateway will NAT all internal address space? Maybe?

See how you go without it.

---

### Post by Doug S on 2012-11-15
> I'm not convinced you will need masquerading considering your eth0 interface is on private address space. One would assume your upstream gateway will NAT all internal address space? Maybe?
Yes, but how it know how to route the traffic? I think you still need to NAT from the one private network to the other private network. Then, yes, the upstream gateway will NAT again to/from the WAN. Perhaps there is a way to do it without the 192.168.2.XXX to/from 192.168.0.100 NAT, via adding in specific routing on the 192.168.0 sub-net, I don't know as I wouldn't do it that way.

---

### Post by jonnyboysmithy on 2012-12-05
Thank you very much for the information, I should be able to research the rest (although I may have to ask :) ). Before starting this thread I hadn't a clue how to go about doing this. Right now I'm quite busy, I'll get back to this later, maybe in a few weeks. Thanks again.:popcorn::KS

---

