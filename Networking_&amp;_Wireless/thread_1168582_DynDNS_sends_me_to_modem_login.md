---
title: "DynDNS sends me to modem login"
date: 2009-05-24
forum: Networking &amp; Wireless
---

### Post by torehan7 on 2009-05-24
hey I;ve got a problem,
I set up a DynDNS and installed the ddclient.
When trying to access the DNS i get sent to my modem.

I think my setup may be an issue.

Box1---------
                  |
Box2---------------Wireless AP ---------Modem
                  |
Box3---------

Thanks

---

### Post by torehan7 on 2009-05-24
Hey I just looked at my diagram. It may be misleading.
Let me explain:
3 computers connect to the Wireless AP (which creates the network) and the wireless AP is connected to a modem.

---

### Post by whoop on 2009-05-24
It could be that there is nothing wrong with that... Your modem or router probably is configurable via a web interface. So when you enter your ip or your dyndns domain name you get the web interface, because it is actually just like any other website.. It is possible that this web interface is only accessible via lan. So you can ask somebody outside of you lan to access you dnds domain; they won't/shouldn't get to your modem login, if they do, you need to drop everything an fix that (or at the very least put an extremely good long weird password on there). Your router login, is best if it is a lan only webservice and has a strong password.

So let's say you want to provide a website, sitting on Box2, you need to make the lan ip for Box2 static, then go to your router login, and do some port forwarding so that the router redirects all port 80 traffic from Box2 via router port 80 to the internet.

---

### Post by torehan7 on 2009-05-24
Hey thanks!
Ill try this out.

---

### Post by whoop on 2009-05-24
> **torehan7 said:**
> Hey thanks!
Ill try this out.

It could be that you still have this problem after you configured your lan. This is because your router detects that you are inside your lan when you connect to your network via the dyndns domain. There are several things you can do:
* Put the website you want to show on a different router port (not 80), you probably don't want that.
* Change the default port for the router login.
* Just check your website via accessing the webservice on Box2 directly, and to check outside of the lan use an online http proxy.

---

### Post by torehan7 on 2009-05-24
Hi, I tried creating a static IP but all that did was cut off all networking capabilities. I could not longer browse the internet and all my shares were no longer accesible by the clients.
Is there something else I can do?

---

### Post by whoop on 2009-05-24
> **torehan7 said:**
> Hi, I tried creating a static IP but all that did was cut off all networking capabilities. I could not longer browse the internet and all my shares were no longer accesible by the clients.
Is there something else I can do?
Which machine are you trying to give static ip? I am talking about a static lan ip. So you should configure it on the machine itself. Even misconfiguration of a machines static ip should not (in general) mess up the entire lan.

---

### Post by torehan7 on 2009-05-24
Well one of my boxes is running Ubuntu which I want to act as a server.
I changed the LAN configuration on the wireless network so that its IP was 192.168.1.5 and for some reason all SAMBA connections and internet connections were severed. 
It all works fine when running off DHCP.

Im a total noob at this so thanks for baring with me.

---

### Post by whoop on 2009-05-26
> **torehan7 said:**
> Well one of my boxes is running Ubuntu which I want to act as a server.
I changed the LAN configuration on the wireless network so that its IP was 192.168.1.5 and for some reason all SAMBA connections and internet connections were severed. 
It all works fine when running off DHCP.

Im a total noob at this so thanks for baring with me.

You should make the IP of the ubuntu machine static. Determine what service port(s) your server is running and port forward that through your router.

---

### Post by dmizer on 2009-05-26
What router do you have? It's possible that you have the ability to assign a DHCP address by MAC number.

Also, please post your /etc/ddclient.conf (be sure to sensor your username and password)

---

