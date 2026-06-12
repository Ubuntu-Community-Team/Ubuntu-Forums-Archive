---
title: "NO Ubuntu pc can connect to the internet but windows ca"
date: 2010-04-08
forum: Networking &amp; Wireless
---

### Post by zutronius on 2010-04-08
I'm having an problem I've never before encountered. I've been using ubuntu on my parents network (wireless router, etc) since 2007 and I've always been able to connect fine.

I've been living abroad for the past year and just came home and tried to connect my ubuntu desktop to the internet. Through the router, there is no internet connection detected. The network card doesn't even blink. When I connect directly to the modem, the NIC shows signs of life but is unable to connect. I've tried several network cards and the same problem happens. I also tried another Ubuntu desktop I have. 

The wireless router is a dlink dl 524 and the modem is a Boradmax Linkmax HSa3000a. Im out of ideas and need help.

---

### Post by zutronius on 2010-04-10
Anybody??

---

### Post by oldfred on 2010-04-10
Have you checked system, preferences, network connections? You may have to reset eth0 to use DHCP.

You can also see settings with ifconfig in linux or ipconfig in windows. 

Do not post the part that is your unique mac address. (I spoofied my old computers mac address into my router so my initial setup of the router would connect immediately, I do not want others to be able to spoof yours)

---

### Post by Dogmatix86 on 2010-04-10
Like oldfred says, don't post your mac but paste the results of 'ifconfig' and 'route' here. 

Also try pinging an external IP such as 196.25.1.1. If the ping test is successful, then the problem is dns related. Check your /etc/resolv.conf file and make sure the nameservers specified are valid.

---

