---
title: "How to configure wireless and PPPoE at the same time"
date: 2009-10-25
forum: Networking &amp; Wireless
---

### Post by Radissthor on 2009-10-25
I'm using Ubuntu Jaunty in a DELL laptop and I have no problem connecting to wireless. The network manager is up and running in that sense. 

My problem started when I had to configure a PPPoE connection in another house that also has to be connected to a wireless connection in order to work. So each time I turned the computer on it would automatically connect to the wireless and I had to run 

```
sudo pppoeconf
```

It worked fine and I would be connected to both, the wireless and the PPPoE. But when I reboot my computer the wireless would be completely dead and even if I run the pppoeconf, it just wouldn't connect. 

I finally learned, thanks to help provided in the forums, that to restore the wireless I had to edit /etc/network/interfaces to be:

auto lo
iface lo inet loopback


#auto dsl-provider
#iface dsl-provider inet ppp
#pre-up /sbin/ifconfig/eth1 up # line maintained by pppoeconf

#auto eth1
#iface eth1 inet manual

I then had to reboot and the computer and wireless would be working again... 

So the questions is: Is there any way I could configure the laptop to connect to both wireless and PPPoE automatically without having to go through this whole process?
Thanks for reading such a long post, I appreciate any comments or help you may provide. Thanks!

---

### Post by Radissthor on 2009-10-25
Well... It's been 10 hours without a reply, so I'm posting again... any help? :(

---

### Post by Onesimus on 2009-10-28
You need to have a bit more patience with people on the forums.  Everyone is a volunteer.

You might want to explain why you would want to connect to the wireless and the pppoe simultaneously, or perhaps you haven't explained yourself fully.

How about giving you system spec, then people may be able to assist you in a more focussed way.

---

### Post by Radissthor on 2009-10-28
Thanks for the reply Onesimus. 

Well, I didn't give any more system spec because I thought saying what computer I had and what Ubuntu system  I'm running was enough. Excuse my ignorance, but I'm really new in Ubuntu and totally dependent on help provided in the forums (which so far has been really great and I appreciate that! :D)

I'm trying to connect to both because, for some reason, the house in which I do this hired a wireless service and when the company sent a guy to install the router, he said it wouldn't be enough with just the wireless, so he also added a PPPoE connection (I don't know if this makes sense, it's just what I was told they were told :S) so that's why people there have to connect to both. The wireless always connects automatically, and the PPPoE has, in Windows, to be initiated manually by clicking on a connect icon in the desktop. 

I once called the technical service of this house internet provider, but when I told them I was using Linux they said they didn't provided assistance to Linux users... and that was it...

I don't know what else I could say. If anyone feels that with some more information they could be able to help me, please just ask. I'll be checking this thread permanently. 

Many thanks!

---

### Post by Iowan on 2009-10-28
If you need both at the same time, one (or the other) will probably need to be set up via */etc/network/interfaces*. NM can (probably) be set to handle either one... but not both at the same time.

---

### Post by Radissthor on 2009-10-28
> **Iowan said:**
> If you need both at the same time, one (or the other) will probably need to be set up via */etc/network/interfaces*.+

That's precisely what I do, I reconfigure /etc/network/interfaces and reboot every time.

> **Iowan said:**
>  NM can (probably) be set to handle either one... 

What is the NM?


> **Iowan said:**
> but not both at the same time.

So how come it cannot be done. If I'm not mistaken, Windows could.

---

### Post by ant2ne on 2009-10-28
> hired a wireless service and when the company sent a guy to install the router, he said it wouldn't be enough with just the wireless, so he also added a PPPoE connection (I don't know if this makes sense, it's just what I was told they were told :S) so that's why people there have to connect to both. The wireless always connects automatically, and the PPPoE has, in Windows, to be initiated manually by clicking on a connect icon in the desktop. this doesn't make sense. 

From the wiki.> The Point-to-Point Protocol over Ethernet (PPPoE) is a network protocol for encapsulating Point-to-Point Protocol (PPP) frames inside Ethernet frames. It is used mainly with DSL services where individual users connect to the DSL modem over Ethernet and in plain Metro Ethernet networks. It was developed by UUNET, Redback Networks, and RouterWare and is available as an informational RFC 2516.

Unless... the ISP installed their custom (closed) WAP that then limits the number of client devices that can connect.

Otherwise, I'm kind of confused.

---

### Post by Radissthor on 2009-10-28
> **ant2ne said:**
> t
Unless... the ISP installed their custom (closed) WAP that then limits the number of client devices that can connect.

Otherwise, I'm kind of confused.

I think it is very probable that that is the case. I'll check anyway, but if it is (which I think) what could be done?

---

### Post by ant2ne on 2009-10-29
> **Radissthor said:**
> what could be done?scrap the custom closed box for a store bought WAP. You'll have to go through the MAC spoof steps and do a little configuring, but then you'll have a real WAP.

---

### Post by Radissthor on 2009-10-29
> **ant2ne said:**
> scrap the custom closed box for a store bought WAP. You'll have to go through the MAC spoof steps and do a little configuring, but then you'll have a real WAP.

Thanks for the advice, but I'm afraid I do not understand what it is I have to do. Could you be a bit more explicit, keeping in mind my knowledge of Computers is quite limited. 
Thanks
:lol:

---

### Post by Iowan on 2009-10-29
> **Radissthor said:**
> That's precisely what I do, I reconfigure /etc/network/interfaces and reboot every time. 

What is the NM?

So how come it cannot be done. If I'm not mistaken, Windows could.
Dunno why you should need to reconfigure each time - settings *should* stick.

Sorry... NM is short for Network Manager.

This isn't Windows... Surprisingly, last night I booted up my Jaunty laptop and connected to my home network and neighbor's wireless simultaneously - so maybe NM (again, that's Network Manager) CAN handle more than one... traditionally, not.
(For what it's worth - I didn't try to connect to neighbor's wireless - Ubuntu just found the open wireless network and connected.)

---

### Post by ant2ne on 2009-10-29
> **Radissthor said:**
> Could you be a bit more explicit, keeping in mind my knowledge of Computers is quite limitedThat is hard to do without knowing the model of WAP you intend to buy and how it is setup. It SHOULD come with instructions. Be sure to ask the vendor that you purchase it from.

---

### Post by Radissthor on 2009-11-01
Thanks for the replies.

Whenever I run pppoeconf the computer is already connected to the wireless and it then connects to the PPPoE, so it is connected to both. 

When I reboot, /etc/network/interfaces looks like this:

auto lo
iface lo inet loopback


#auto dsl-provider
#iface dsl-provider inet ppp
pre-up /sbin/ifconfig/eth1 up # line maintained by pppoeconf
#pre-up /sbin/ifconfig/eth1 up # line maintained by pppoeconf


#auto eth1
#iface eth1 inet manual

And then part of the code is again repeated, but without the # signs. I have to edit it to remove the repeated 4rd line  (pre-up ...) and remove all the other repeated lines, the reboot and starts again getting wirless correctly. 

By the way, I'm running a Dell Inspiron 1525. The driver manager says I'm using a Broadcom STA Wireless Driver

Hope this information helps to solve the problem...
Thanks for all the replies

---

