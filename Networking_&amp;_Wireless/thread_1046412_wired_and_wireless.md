---
title: "wired and wireless?"
date: 2009-01-21
forum: Networking &amp; Wireless
---

### Post by wasutton3 on 2009-01-21
i recieve free wireless from my apartment complex (probably tacked into my bill somewhere) but i am trying to set up a private home network. i would like my computers to connect to the wireless network but communicate with each other over a wired network. is there a way to do that?

---

### Post by Kebabman on 2009-01-21
You could use a PC (or something like a linksys WRT54G flashed with linux) to connect to the wireless network and then act as the router/gateway for your home network. This could just be one of the PC's lying on your home network but you will probably want to connect the ethernet port to a switch to feed the other machines.

---

### Post by timcredible on 2009-01-21
there are wireless routers with 4 ports that will do that.  i think the term you're going to look for is 'client mode' on the wireless router.  probably $50US

---

### Post by wasutton3 on 2009-01-21
yes, but they do not allow wireless routers. and it uses 802.1x authentication. plus i already have a wired router and would prefer not to buy anything else.

the setup i would like is

wireless network -> laptop
                       |
                   ethernet cable
                       |
                    wired router
                       |
                   ethernet cable
                       |
wireless network -> desktop

i dont know if this is possible. the entire purpose for this is so that when i am downloading stuff off my friends server, i can reboot my actual computer (the desktop) without interrupting the download itself
the wireless restrictions are such that i can only pull about 55kb/s from the server so the downloads take a while

---

### Post by Kebabman on 2009-01-21
The wireless network between the wired router and the desktop is a bit confusing, I'm going to make a judgment call and say that that is a mistake and you just want an ethernet cable between the wired router and the desktop.

Yes this setup is possible. You will need to enable ipv4 forwarding on the laptop and set it up as normal to connect to the wireless network. You will also probably want to setup a dhcp server on it to dish out the IP address to the Router.

The easiest way is to ensure you use different IP address ranges for the DHCP server on the laptop and the router (say 192.168.0.0/24 on the laptop DHCP server and 10.0.0.0/24 on the wired router).

Once that is set up you should be able to connect on the desktop via the router and laptop.

---

