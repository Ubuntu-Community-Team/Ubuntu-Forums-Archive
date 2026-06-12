---
title: "dhcp problem"
date: 2010-01-05
forum: Networking &amp; Wireless
---

### Post by isahak on 2010-01-05
Hi Everyone

I have five computers. So, 2 ubuntus, 1 xubuntu, 2 windows. I have set a dhcp pool on a cisco router/switch. Now, whenever I connect the windows machines to the router, they get the ip addresses automatically. **However, the ubuntu machine does not get an ip address.** If I look at the light on the Ethernet port on the router, **For ubuntu it shows nothing. but for the windows the light is always on. **

However, if I manually give an ip address to the ubuntu machine, and try to ping the router it works. So I believe that, **something in my ubuntu box is stopping it to get an ip address automatically**. I am really confused.

Any help would be appreciated.

---

### Post by pedro_orange on 2010-01-05
What does network-manager say? (Top right hand corner)

Do you have eth0 enabled? Is it set to ask for DHCP?

What kind of switch do you have? Does it have a built-in DHCP server? A switch is not a router :)
A switch will provide connectivity providing they are in the same network, but it will not route packets like a router.

If you have another machine acting as a DHCP server that's fine, but you need to tell the Ubuntu box that the machine is the DHCP server.

What IP Addresses are the Windows boxes getting? Are they the 169 addresses? These are given by Windows when they cannot obtain an IP address from the DHCP server.

---

### Post by pedro_orange on 2010-01-05
Right, so it gets an IP address if you plug it directly into the router. That's good. There is nothing wrong with the driver, or the card.

What you need to do is tell eth0 that the DHCP server is your router. You can do this from the network-manager plug-in iirc.

It could well be a firewall issue, but unless you've installed something like Firestarter - I doubt it is.

---

### Post by isahak on 2010-01-05
> **pedro_orange said:**
> what does network-manager say? (top right hand corner)


**do you have eth0 enabled? Is it set to ask for dhcp?**

yup it is set to dhcp. If i connect the ubuntu pc to my d-link router(i have internet on this one), it gets an ip address.


[b]what kind of switch do you have? Does it have a built-in dhcp server? A switch is not a router :)
[/b]
sorry, i should have mentioned, that at first i connected one of the ubuntu pc, and then windows pc to the router. Then i did the same thing to a switch. The switch is connected to a router.

And yes there is a dhcp server in the router, i have a dhcp pool on that.:p



[b]if you have another machine acting as a dhcp server that's fine, but you need to tell the ubuntu box that the machine is the dhcp server.
[/b]
no the router is acting as a dhcp server.


**what ip addresses are the windows boxes getting? Are they the 169 addresses? These are given by windows when they cannot obtain an ip address from the dhcp server.**

nope. They are not those addresses.

The router's  fastethernet0/0 has 10.1.8.1 

and the windows pc automatically gets the ip address 10.1.8.2



i remember, i read somewhere, that i need to disable, some firewall setting on ubuntu. But now i could not find all those instructions. So, can anyone help?


:p:p

---

### Post by isahak on 2010-01-05
> **pedro_orange said:**
> Right, so it gets an IP address if you plug it directly into the router. That's good. There is nothing wrong with the driver, or the card.

What you need to do is tell eth0 that the DHCP server is your router. You can do this from the network-manager plug-in iirc.

**It could well be a firewall issue, but unless you've installed something like Firestarter - I doubt it is.**

I can see that the firestarter is not installed.

---

### Post by pedro_orange on 2010-01-05
Well set your connection's DHCP server to be the router

---

### Post by Iowan on 2010-01-05
[This]("http://ubuntuforums.org/showpost.php?p=8602179&postcount=2") lists a couple of options.

---

