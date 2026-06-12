---
title: "How to turn dynamic to static IP"
date: 2012-12-03
forum: Networking &amp; Wireless
---

### Post by igodspeed on 2012-12-03
Hello all,

I have a IP address that is changing all the time and my service provider cannot give me a static IP address. The problem is that i am not able log on to my Ubuntu as the IP address is changing every 24 hours. Is there a way i can know what my IP address is when it changes. Any help would be very appreciated. 

Thanks

---

### Post by lisati on 2012-12-03
I'm not sure I understand your problem. Under normal circumstances, a change of *public* ip address (i.e. the one assigned by your provider) should not affect your ability to log in to your ubuntu machine, unless you are trying to do so remotely.

If you are trying to access your machine from another location, there are options. A little more information about what you are trying to do might be useful when we try to narrow down what to suggest. For starters, are you trying to access your machine remotely? Are you running a website or similar service?

---

### Post by ahallubuntu on 2012-12-03
> **igodspeed said:**
> Hello all,

I have a IP address that is changing all the time and my service provider cannot give me a static IP address. The problem is that i am not able log on to my Ubuntu as the IP address is changing every 24 hours. Is there a way i can know what my IP address is when it changes. Any help would be very appreciated. 

Thanks

Look into a "Dynamic DNS" service.  That is, you can register a domain name somewhere and it can automatically track your changing IP address.  Then you don't have to worry about the IP anymore - just use the name to get to your Ubuntu server at home.

Some of the formerly free Dynamic DNS services are no longer free or as free as before.  Google around.

You can run the service to update the IP to your DDNS name on your server or in your router, if your router supports it.  (like DD-WRT)

---

### Post by igodspeed on 2012-12-04
Well, i have my files in my home computer and since i travel a lot i would like to log in to my computer to retrieve files. That is where the problem is, since my ip address is changing, there is no way i can log on after 12 hours unless i know the new ipaddress. I would like a free service like dynamic DNS. The services that i would like to use is remote desktop and Ssh connection. 

Thanks

---

### Post by oldfred on 2012-12-04
Similar discussion with script to email IP.

[http://ubuntuforums.org/showthread.php?t=1863666](http://ubuntuforums.org/showthread.php?t=1863666)

---

### Post by igodspeed on 2013-07-31
I there no software that does this? Is there a way i can link it to a we URL and i just put the url insted of IP address? I think i heard about something like this a while back.

---

### Post by igodspeed on 2013-07-31
Mostly SSH connection and remote desktops sometimes. But my ip is changing so I cannot log in after 12 or 20 hours since the ip will reset again and i will have to know the new IP.

---

### Post by oldfred on 2013-07-31
Then use the script to have the system email you its new IP. Or better pay your ISP for a fixed IP address, it may cost a little more but then totally avoids the issue.

---

### Post by Thee on 2013-07-31
You can use a Free DNS service like [http://freedns.afraid.org/](http://freedns.afraid.org/)

Just make a free account, choose a domain name and use some of the scripts provided here [http://freedns.afraid.org/scripts/freedns.clients.php](http://freedns.afraid.org/scripts/freedns.clients.php) and run it on your computer to automatically update IP whenever it changes. You can even set it up on your router in case you got a router with some open source firmware. Also, you will need to forward whichever port you need on your router for you to be able to connect.

I use it and it works perfectly.

---

### Post by igodspeed on 2013-08-01
i have a linksys router. Would it be possible for me to flash this router with an open source firmware?

---

### Post by oldfred on 2013-08-01
Open source firmware will not change your issue.

Some Linuxsys can be done and I think some did not have enough RAM to store the new system.

---

