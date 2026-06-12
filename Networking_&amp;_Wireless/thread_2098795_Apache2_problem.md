---
title: "Apache2 problem"
date: 2012-12-27
forum: Networking &amp; Wireless
---

### Post by maximevhw on 2012-12-27
Well my apache is 100% default.
web root=  /var/www

As local host i can connect to the site but external it doesnt work...
i get my ip from [www.ipchicken.com](www.ipchicken.com)

How can i fix this?

---

### Post by Lars Noodén on 2012-12-27
How is your machine connected to the Internet?  You may have to forward ports 80 and 443 on your router to your machine running Apache.

---

### Post by Cheesemill on 2012-12-27
You need to forward port 80 to your machines internal IP address, this is done by changing the settings on your router.

For instructions for your model of router see [http://portforward.com/](http://portforward.com/).

---

### Post by maximevhw on 2012-12-27
> **Lars Noodén said:**
> How is your machine connected to the Internet?  You may have to forward ports 80 and 443 on your router to your machine running Apache.
It is connected  by wifi.
I tried to portforward my ports but...
Its an router provided by my ips... its a modem/(wireless)router combo.
I did DMZ for my ip so no problem with firewall.
But i cant portforward ports below 1023or something like that...

Should i mail my isp about that?

---

### Post by Cheesemill on 2012-12-27
Some ISP's don't let you run webservers on a residential connection, check with your ISP.

---

### Post by mtreece on 2012-12-27
I've had some routers which won't loopback-route (I'm sure that's not the proper way to say it).

In other words, browsing to localhost works fine, but browsing to my public IP address (even if I have the proper ports forwarded) gives me connection issues. This is usually, I've found, something up with the router. It might be fixable, but I haven't bothered to hack with it.

Try using a proxy and browsing to your public IP address.  If you can see your site, you're experiencing the same situation I'm describing.

---

### Post by Cheesemill on 2012-12-27
If the OP is trying to access his site from an external network then it's just a port-forwarding issue.

If port-forwarding is already set up correctly and the OP is trying to connect from an internal network using the external IP address then it is a NAT loopback issue, for more information on this situation see my posts in these threads:

[http://ubuntuforums.org/showthread.php?t=2030003](http://ubuntuforums.org/showthread.php?t=2030003)
[http://ubuntuforums.org/showthread.php?t=2033584](http://ubuntuforums.org/showthread.php?t=2033584)

---

### Post by maximevhw on 2012-12-27
> **mtreece said:**
> I've had some routers which won't loopback-route (I'm sure that's not the proper way to say it).

In other words, browsing to localhost works fine, but browsing to my public IP address (even if I have the proper ports forwarded) gives me connection issues. This is usually, I've found, something up with the router. It might be fixable, but I haven't bothered to hack with it.

Try using a proxy and browsing to your public IP address.  If you can see your site, you're experiencing the same situation I'm describing.

1)If i connect the pc with cable, will i need port-forwarding(port-forwarding=****)

2) So instead of using proxy can a  connect to a hotspot(different network,don't know if other countries have this...)?
For example i connect server to a and my phone to b
And try to find a with b?


3) Im happy that i decided to wait untill i buy the server, this is a testing rig...
If i sort everything out with your help ill buy the server ;p

Ill try this out, tomorrow... first need some sleep :p
its 2:40am...
Thanks for the help guys!
I love the linux community, the are all "smart" they know the os very good.
But windows users... pfff....
I have a friend that doesnt know wath the programfiles are...
You smartasses ;p

---

### Post by mtreece on 2012-12-27
> **maximevhw said:**
> 1)If i connect the pc with cable, will i need port-forwarding(port-forwarding=****)

If you're behind a NAT then you'll need port-forwarding regardless if you're wired or wireless. For service reliability, I recommend wired.

> **maximevhw said:**
> 
2) So instead of using proxy can a  connect to a hotspot(different network,don't know if other countries have this...)?
For example i connect server to a and my phone to b
And try to find a with b?


Yes, instead of a proxy, you can simply connect to another network with your phone or other device. Sorry - was just reciting what I did back in the day to figure out my own problem :).

Hope it all works out for you!

---

### Post by maximevhw on 2012-12-28
> **mtreece said:**
> If you're behind a NAT then you'll need port-forwarding regardless if you're wired or wireless. For service reliability, I recommend wired.



Yes, instead of a proxy, you can simply connect to another network with your phone or other device. Sorry - was just reciting what I did back in the day to figure out my own problem :).

Hope it all works out for you!



Console(root):

[ATTACH]229249[/ATTACH]

I hope this may help you guys a little bit more...

Configured the /etc/apache2/ports.conf to 8080
/etc/apache2/sites-avaible/default to 8080
/etc/apache2/sites-enabled/000-default to 8080

And now site is accesable from *****:8080

There must be a way to enable that port 80

---

### Post by maximevhw on 2012-12-28
i found out that my isp is just some sons of bitches...
For normal people portforwarding of port 80 is blocked...
You need to buy a bussines class internet... why the **** would i want that...


is this the same in us? or in other countrys?

---

### Post by Cheesemill on 2012-12-28
It's the same in all countries, some ISPs block port 80, others don't.

---

