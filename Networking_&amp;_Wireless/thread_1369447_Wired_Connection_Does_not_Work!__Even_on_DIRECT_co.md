---
title: "Wired Connection Does not Work!  Even on DIRECT connection"
date: 2010-01-01
forum: Networking &amp; Wireless
---

### Post by anitrous on 2010-01-01
This can't be a networking problem otherwise I would be able to connect through a direct connection with my cable modem, correct?

My wired connection has ceased working entirely.  I can ping my router but I cannot ping google.com or ubuntu.com.  The ubuntu help guide told me that I may have DNS problems which I do not know how to fix if that's true.

My laptop is x86 and runs windows vista and **ubuntu 9.10** via dualboot.

Vista connects perfectly without any trouble on my part via wireless and wired.  I think I know why my wireless connection won't work in Ubuntu but I can't fix that problem until I fix my wired connection problem.

I've tried the NetworkManager and Network tools but I swear if I do anything more I'm going to explode.  It absolutely refuses to resolve the DNS or even recognize that the router has internet access.

Please help...

---

### Post by focwiz on 2010-01-01
> **anitrous said:**
> This can't be a networking problem otherwise I would be able to connect through a direct connection with my cable modem, correct?

My wired connection has ceased working entirely.  I can ping my router but I cannot ping google.com or ubuntu.com.  The ubuntu help guide told me that I may have DNS problems which I do not know how to fix if that's true.

My laptop is x86 and runs windows vista and **ubuntu 9.10** via dualboot.

Vista connects perfectly without any trouble on my part via wireless and wired.  I think I know why my wireless connection won't work in Ubuntu but I can't fix that problem until I fix my wired connection problem.

I've tried the NetworkManager and Network tools but I swear if I do anything more I'm going to explode.  It absolutely refuses to resolve the DNS or even recognize that the router has internet access.

Please help...

See this Post...?...
[http://ubuntuforums.org/showthread.php?t=1361797]("http://ubuntuforums.org/showthread.php?t=1361797")

---

### Post by anitrous on 2010-01-01
The IP trick didn't work like the other guy.  I can not connect to remote hosts, period.  Like I said, it refuses to acknowledge the internet exists.  My problem wasn't progressive like the other user's.  My problem has happened since I've returned home for Winter break.  Ubuntu fails to connect to the internet though it connects to my home network (it did have internet access at school [approx. 3 weeks ago]).

---

### Post by Iowan on 2010-01-01
> **anitrous said:**
> 
I've tried the NetworkManager and Network tools but I swear if I do anything more I'm going to explode. I'm not sure how you're going to fix it if you don't do anything more...
If you're willing, check */etc/resolv.conf* to see that it has valid nameservers. Also check **route -n** - the last line should show your default gateway. That should probably be your router's address.

---

### Post by anitrous on 2010-01-01
> **Iowan said:**
> I'm not sure how you're going to fix it if you don't do anything more...
If you're willing, check */etc/resolv.conf* to see that it has valid nameservers. Also check **route -n** - the last line should show your default gateway. That should probably be your router's address.

Sorry I didn't mean it that way.  Part of that was just frustration.  What I meant was I'm not doing anything else without direction haha.  Because I was fiddling with all the network tools and all the online guides all night.

Anyway,

/etc/resolv.conf comes back as Permission denied

and route -n returns with my gateway.

---

### Post by Bigfootbuilt on 2010-01-01
I had 3 days of both wireless and wired connectivity nightmares and discovered my problem, which I hope solves yours. Open your network manager again and click on the IPv6 tab. Next to "Method", make sure it is set to "ignore". It solved the problem on all 3 of my PC's! Hope this helps.

---

### Post by Iowan on 2010-01-01
> **anitrous said:**
> /etc/resolv.conf comes back as Permission deniedTry it as **cat /etc/resolv.conf**

---

### Post by anitrous on 2010-01-01
> **Iowan said:**
> Try it as **cat /etc/resolv.conf**

Ok I know my nameserver now.  What's next?

> **Bigfootbuilt said:**
> I had 3 days of both wireless and wired connectivity nightmares and discovered my problem, which I hope solves yours. Open your network manager again and click on the IPv6 tab. Next to "Method", make sure it is set to "ignore". It solved the problem on all 3 of my PC's! Hope this helps.

I have done this but it doesn't help.  I still can't ping any remote host.

---

### Post by confusedstingray on 2010-01-01
is your computers and your router on the same subnet eg; computer is 192.168.1.x is your router 192.168.1.x this is on the same subnet if different could cause a problem

also i have a couple of setups where i had to put the ISP's dns server in the /etc/resolv.conf to allow internet access

---

### Post by anitrous on 2010-01-01
> **confusedstingray said:**
> is your computers and your router on the same subnet eg; computer is 192.168.1.x is your router 192.168.1.x this is on the same subnet if different could cause a problem

also i have a couple of setups where i had to put the ISP's dns server in the /etc/resolv.conf to allow internet access

They should be the same.  How do I put the DNS into the etc/resolv.conf?

---

### Post by confusedstingray on 2010-01-01
you can do it through network settings. System-adminstration-network click the DNS tab

or you can edit directly through cmd line 
sudo vim /etc/resolv.conf

---

### Post by Iowan on 2010-01-01
You can manually edit */etc/resolv.conf* via ```
sudo nano /etc/resolv.conf
``` or (if you prefergraphical editor) ```
gksudo gedit /etc/resolv.conf
``` If you get IP address via DHCP, */etc/resolv.conf* may get overwritten. You can check your Windows box for your ISP's DNS address, or use OpenDNS or GoogleDNS.

---

### Post by confusedstingray on 2010-01-01
you should have got dns server ip address from you internet provider
use them

---

### Post by anitrous on 2010-01-01
> **Iowan said:**
> ```
gksudo gedit /etc/resolv.conf
```

Ok so putting this in tells me that my name server is 192.168.1.1

And your wanting me to change it to my results of cat /etc/resolv.conf which is exactly the same?  Is there something else I should change it to?

---

### Post by Iowan on 2010-01-01
You should be able to check your Vista side to see what it uses for DNS. My network was set up like yours seems to be. Although I use a DSL modem instead of a router, it is the DHCP, gateway address and DNS for network. 

You could try using [OpenDNS]("https://store.opendns.com/setup/device/ubuntu/"), or GoogleDNS (8.8.8.8 or 8.8.4.4). It might be worth mentioning that Network Manager has the option to include DNS settings in it's Connection configuration.

---

### Post by anitrous on 2010-01-02
> **Iowan said:**
> You should be able to check your Vista side to see what it uses for DNS. My network was set up like yours seems to be. Although I use a DSL modem instead of a router, it is the DHCP, gateway address and DNS for network. 

You could try using [OpenDNS]("https://store.opendns.com/setup/device/ubuntu/"), or GoogleDNS (8.8.8.8 or 8.8.4.4). It might be worth mentioning that Network Manager has the option to include DNS settings in it's Connection configuration.

Ok so I know my ip address, my subnetmask, my gateway and my DNS.

Do I just manually input all the information into Network manager to get my internet functioning again or should I put in google's free DNS instead?

---

### Post by anitrous on 2010-01-02
I changed my DNS to google's open DNS.  I still cannot access the internet.  I followed open DNS's instructions and just replaced it with google's.

If I'm plugged into a router will that router have to be configured with google's DNS before it functions properly?


EDIT:  Ok get this.  When I plug it directly into a modem it no longer recognizes that I have an "eth0" connection.  It says it doesn't exist while its plugged in but if i unplug it and put it in the router it automatically connects (not to the internet mind you...).

EDIT 2:  I ran Linux Mint from a disc and it won't connect to the internet either.  ???

---

