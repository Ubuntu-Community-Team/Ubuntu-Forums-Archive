---
title: "how do you get your ip address?"
date: 2009-03-30
forum: Networking &amp; Wireless
---

### Post by andyklaj on 2009-03-30
hey guys

id like to connect to my computer over the internet using ssh, but im allocated my ip address via DHCP from my ISP. am i going to have to try and get a static address from my ISP if i want to use ssh?

any help would be appreciated
thanks

---

### Post by jbrevik on 2009-03-30
You can find out your external ip by going to whatismyip.com.
If you are behind a router you will need to forward port 22 to allow an ssh connection to the internal address of the machine behing your router. You can find this address by doing:
```
ifconfig
```

---

### Post by rglover on 2009-03-30
If you'd like to access your machine via SSH from elsewhere, you could also use a dynamic DNS Service like DynDNS - that way you can SSH using the domain name, and the DNS service is updated with your dynamic IP address from your ISP.  It's a little tricky to get it working just right, but it's really a pretty handy tool.

---

### Post by Iowan on 2009-03-30
Just my opinion... If you plan frequent access from Internet, the Dynamic DNS service would be better solution.  Short term solution (whatsmyip.com) means finding ip from local net, then using it before lease expires and another ip address is acquired.

---

### Post by hovzio on 2009-03-30
Digit this in a terminal and it will give you your current lan's ip;

```
wget -q -O - checkip.dyndns.org | sed 's/[^[:digit:]|.]//g'
```

EDIT: I got this off some thread in the ubuntuforums.org about a year and a half ago. I do not remember whom's post it was.Sorry I cannot give credit to the author.

---

### Post by dranockcir on 2009-03-30
> **andyklaj said:**
> hey guys

id like to connect to my computer over the internet using ssh, but im allocated my ip address via DHCP from my ISP. am i going to have to try and get a static address from my ISP if i want to use ssh?

any help would be appreciated
thanks


You can browse to [http://www.whatismyip.com](http://www.whatismyip.com) to get the external IP address assigned to you by your provider. This is usually assigned to your router/modem. Assuming you are using some sort of router/modem or both, in which case the modem has the external address, you would then need to make sure that port 22 is forwarded to the internal IP address of the computer you are trying to connect to.

You can use the ifconfig command to get the internal address of the computer you are trying to connect to.

Rick

---

### Post by BkkBonanza on 2009-03-30
If your router/modem has an option for dynamic ip then configure that to work with a service like dyndns.org. If it doesn't then you can still do this but you run a client daemon on your server like ddclient. It does the same thing which is to get out and get your ip every few minutes and update the dynamic dns at a service like dyndns.org. As long as dyndns.org is updated then you can use the name you chose there to access your server. It will follow the dhcp assigned ip (with possible brief downtimes as the ip changes).

---

### Post by andyklaj on 2009-04-05
hey guys

I got ssh working over the internet, thanks a lot for your input.

p.s. do you have any links for good networking guides or books? (the best i could find was at the ubunut community doc's and aboutdebian.com)

thanks

---

