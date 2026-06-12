---
title: "I got a new router, now can't see the NAS"
date: 2012-12-21
forum: Networking &amp; Wireless
---

### Post by jessel on 2012-12-21
Hi,

I just got a new router (the Asus RT-N56U) and now my Diskstation NAS does not mount automatically. I was able to mount the NAS using NFS before, so I assume that some setting in the router is preventing me from seeing the NAS. If I try to mount at the command line I get:

mount.nfs: access denied by server while mounting 192.168.1.105:/volume1/Photo

Thanks

---

### Post by ahallubuntu on 2012-12-21
To ask the obvious question: did you configure your new router's LAN in exactly the same way as the old one?  How was the NAS set to an IP of 192.168.1.105 by the old router?  Static IP?  Does the new router also use the subnet 192.168.1.1/24 ?

Can you PING the NAS?

```
ping 192.168.1.105
```

?

---

### Post by jessel on 2012-12-21
ahallubuntu:

Thanks for the response.

I most likely haven't set up the new router like the old one. The setup looks the same to me, but franlkly I'm a bit confused about the meaning of a lot of the settings. Until recently I've never set up any network other than wireless access. I don't think I ever did much in the way of configuring the old router, I put a password on the wireless and thats about it. So the default settings were different.

I can see that the new router is set up with an IP address of 192.168.1.1, which is the same as before. I don't see where I'd specify the subnet 192.168.1.1/24.

In the Diskstation control panel the gateway is 192.168.1.1, and I have it set up so that the address is a static address of 192.168.1.105 for the NAS.

ping works:
64 bytes from 192.168.1.105: icmp_req=30 ttl=64 time=0.119 ms
^C
--- 192.168.1.105 ping statistics ---
30 packets transmitted, 30 received, 0% packet loss, time 28997ms

---

### Post by ahallubuntu on 2012-12-21
> **jessel said:**
> I can see that the new router is set up with an IP address of 192.168.1.1, which is the same as before. I don't see where I'd specify the subnet 192.168.1.1/24.

That's not a setting you'd actually type in.  192.168.1.1/24 is just shorthand for saying your network subnet mask is 255.255.255.0 and your local network would have a range of IP addresses from 192.168.1.1-192.168.1.255 .  The 24 means (in a sense) "how many bits are the same?" (An IPv4 IP address has 32 bits total, 8 bits in each number between the periods.)  An address of say 192.168.2.5 in this case would NOT be on your local network - it would be on some other network.

You could say 192.168.1 is the "area code" and the remaining number at the end is the individual phone number.  You could make the "area code" bigger or smaller.  You could make it "192.168" (16 bits instead of 24) and then the last two digits in the IP address are the "phone number."  Such a network would be designated as 192.168.1.1/16 - and your subnet mask would be 255.255.0.0 .  (And you would have 65536 unique addresses on your local network, instead of only 256!)
 
> **jessel said:**
> In the Diskstation control panel the gateway is 192.168.1.1, and I have it set up so that the address is a static address of 192.168.1.105 for the NAS.

ping works:
64 bytes from 192.168.1.105: icmp_req=30 ttl=64 time=0.119 ms

I meant, can you ping the IP 192.168.1.105 from the place you were trying to connect?  That is, if you are trying to access the NAS from your laptop, on your laptop see if you can ping 192.168.1.105 .  That's a way of seeing if your laptop can see the NAS at all.

Or from the NAS, see if you can ping 192.168.1.1, the router's gateway.

Did you make sure on your new router that it doesn't assign an IP of 192.168.1.105 to some other computer on the network?  This is why you need to configure the router.  It (probably) uses something called DHCP to assign IP addresses automatically to computers on the network that say "Just give me an IP, I don't care what it is."  The router can't tell that your NAS already has an IP of 192.168.1.105 - unless you reserve that IP in your router, so no other computer gets it.  Or, just tell the router to choose a different range for DHCP.  Maybe it can assign IP addresses from 192.168.1.110 to 192.168.1.199 and nothing lower or higher.  That way, 192.168.1.105 is safe.

---

### Post by jessel on 2012-12-21
OK, my subnet mask is 255.255.255.0

I did issue the ping command from the place where I want to connect. I can't find where on the diskstation I would ping the router, but when I click on the ddns icon in the control panel it opens a dialog in which there the gateway address 192.168.1.1 lights up green (I believe to indicate that the network connection exists).

I can see on the router control panel that there are four connections, only one is at 192.168.1.105 and it is the NAS (because the MAC address is shown).

I came across something about port forwarding:

[http://forum.synology.com/enu/viewtopic.php?f=145&t=45933](http://forum.synology.com/enu/viewtopic.php?f=145&t=45933)

but it did not work for me, though I'm not sure if I followed it.

---

### Post by ahallubuntu on 2012-12-21
Port forwarding is only needed if you are trying to access something through a firewall.  If you are on the same local network as your NAS (sounds like you are) you should not need to worry about it, because you aren't going through your firewall; all your devices on your local network are behind it.  If you were trying to get to your NAS from the internet, you'd probably need to forward a port through your router's firewall (but that doesn't sound like what you're trying to do).

This may not solve your immediate problem, but after you do, you STILL need to make sure no other device gets an IP of 192.168.1.105 on your network.  That's very important - otherwise you could have two devices with the same IP, not good!

---

### Post by jessel on 2012-12-22
ahallubuntu,

thanks for the explanation of port forwarding. I've disabled it, as it is inappropriate for me. I will keep your advice in mind in the future but right now I'm focused on the issue of mounting the NAS. I don't want to make too many changes. I've got inquiries to asus about the router and synology about the issue. I'll post it once there is a solution.

Back to the network configuration, are you recommending static assigned ip addresses?

Also, what is a decent book or other reference for someone looking for a really high level explanation of basic networking? Like probably anyone I'm busy and I don't want to spend my life studying networking for a little home network, and so when the introduction is like 200 pages its tough to swallow a ton of low level information. I have no intent on setting up computer networks for a living.

---

### Post by steeldriver on 2012-12-22
If this is an NFS mount, then the first thing I would check is that you can actually see the exports from the NAS using [FONT=Courier New]showmount [/FONT]e.g.

```
$ showmount -e 192.168.1.127
Export list for 192.168.1.127:
/c/home    *
/c/media   *
/c/public  *
/c/backup  *
/USB_HDD_1 *
```(replace 192.168.1.127 with the LAN IP of your NAS obviously)

It shouldn't be necessary for the client(s) to be statically addressed - mine are all DHCP (in fact my NAS is DHCP as well - but with address reservation on the router)

---

### Post by jessel on 2012-12-22
jesse@aardvark:~$ showmount -e 192.168.1.105
Export list for 192.168.1.105:
/volume1/Photo 192.168.1.103
/volume1/Music 192.168.1.108

above is my output from the showmount command

---

### Post by steeldriver on 2012-12-22
OK so it looks like you have a very restrictive exports list on your NAS - if I understand it correctly, it only allows host 192.168.1.103 to mount the Photo share - you either need to ensure your client has that IP (either by static IP or DHCP address reservation) or change your NAS's /etc/exports file to open it up to other client IPs - if you're on a home LAN behind a NATed router, then afaik '*' is safe, but if you're uncomfortable with that then you could set it to allow any hosts on the subnet i.e. 192.168.1.0/24

---

### Post by jessel on 2012-12-22
you are awesome. i just need to modify the nfs privilidges in the NAS control panel.

Thanks!

---

