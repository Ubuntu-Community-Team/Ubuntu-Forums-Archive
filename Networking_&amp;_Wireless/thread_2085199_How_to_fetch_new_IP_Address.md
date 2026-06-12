---
title: "How to fetch new IP Address"
date: 2012-11-17
forum: Networking &amp; Wireless
---

### Post by WeAreLinux on 2012-11-17
I recently switched to cable from DSL. With DSL, all I had to do was reset the modem and it would fetch me a different IP address, but that doesn't work with my new ISP. I would like to know how could I force my modem to release my current IP and fetch me a new one on Ubuntu?

In Windows, I would use the ipconfig/release then ipconfig/renew command. Is there an equivalent command in Ubuntu? 

I'm connected through a router. Is there a setting I could change to force getting a new IP?

I'm using Ubuntu 10.04 LTS.

Thank You

---

### Post by jerome1232 on 2012-11-17
If you were behind a router when on DSL you only changed your private ip address when you issued that ipconfig command.

You can right click your networking icon in the top right of your screen and uncheck enable networking, then repeat to enable it again to get the same effect, likely your router will just issue the same private ip to you again though.

If you're actually trying to change your public ip, then you need to log into your router and tell it to release and then renew it's ip address, the method to do this will vary by router.

---

### Post by WeAreLinux on 2012-11-20
Nah, when I used Windows's ipconfig command I was using cable but connected straight to cable modem. That was years ago & I havent used Windows since,lol. Sorry to mention that.

With DSL, all I had to do was turn the modem on/off to fetch a new public address. I would verify this by heading over to ShieldsUp @ grc.com.

With my current cable internet, I noticed I would get a new public IP every week or so when I first subscribed....but for the past month I've been getting the same ip -_-. I guess I have to look into changing something into my router like you've posted.

What about if I connect my modem straight to computer, would there be a command I could use to release then fetch a new ip on Ubuntu?

---

### Post by efflandt on 2012-11-20
If you are asking about your public IP, PPPoE and cable use different protocols.  With PPPoE the IP is negotiated and assigned during PPP login, and if you disconnect and reconnect PPPoE you would typically get a new IP, unless you had a static IP plan or depending upon ISP configuration (some ISP's might give you the same IP even if dynamic).

Cable uses DHCP related to cable modem MAC address and they may assign the same IP to the same cable modem MAC address for an extended period of time (like a year), so it is easier to track anyone doing anything malicious (since there is no login and they would still have same IP address).

When my boss had a problem with his cable where his router still seemed to be connected, but no traffic could get through it, I gave him instructions how to release and renew his public IP address on his router, and that worked.  But instead of following my instructions, he kept tampering with his Netgear WiFi dongle settings instead of connecting to his Netgear router, and would mess up his wireless.  So due to those connections that would die on cable, he eventually went back to DSL.  So maybe you need to look at your router instructions, how to release and renew WAN IP on that.

But your question always begs the question "why?"  Unless you are doing something malicious or got banned from a site, your IP address should not matter, as long as you have a router or firewall that only allows uninitiated connections that you want to allow.

---

### Post by WeAreLinux on 2012-11-21
Thanx for the information.

After a couple more Google searches, I found out how to change my MAC address my router uses....reboot modem and router...and got a new IP assigned. So I guess I'll have to do this everytime I want a new IP.

Why? No its nothing malicious. Its just a personal preference to have a new IP assigned to me every so often. I'm sure people who do malicious activities dont rely on their ISP to be anonymous,lol. They use other methods.

---

