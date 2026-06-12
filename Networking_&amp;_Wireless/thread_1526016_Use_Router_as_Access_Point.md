---
title: "Use Router as Access Point"
date: 2010-07-07
forum: Networking &amp; Wireless
---

### Post by TheJohlin on 2010-07-07
I have a wireless network in my house through a Zyxel P-320W router, and I've noticing that the signal strength isn't very good in the basement. 
Now I have this old D-Link-624+ router lying around for a long time and I've been hoping to get it to work as an access point, that way I can move freely around the house without changing which router I'm connected to.

Is there some way to make this work?

---

### Post by kfinity on 2010-07-07
If you want multiple wireless access points, and don't want to have to change the network you're connected to, you're probably going to want [WDS]("http://en.wikipedia.org/wiki/Wireless_Distribution_System"). Some routers support this; you'll need to go into the router config page on both routers and look around for a WDS section. You can also try doing a google search for 'dl-624 wds' or 'p-320w wds' and see if you can find guides. 

If you don't mind changing the network or running ethernet wires to the d-link, then it's not hard at all. Just turn off dhcp on the d-link and plug the network cable into one of its LAN ports. And actually, if you set the ssid and key to be the same, they might just show up as the same wireless network that way.

---

### Post by TheJohlin on 2010-07-07
> **kfinity said:**
> If you want multiple wireless access points, and don't want to have to change the network you're connected to, you're probably going to want [WDS]("http://en.wikipedia.org/wiki/Wireless_Distribution_System"). Some routers support this; you'll need to go into the router config page on both routers and look around for a WDS section. You can also try doing a google search for 'dl-624 wds' or 'p-320w wds' and see if you can find guides. 

Well, it seems that none of them supports WDS :(

> **kfinity said:**
> If you don't mind changing the network or running ethernet wires to the d-link, then it's not hard at all. Just turn off dhcp on the d-link and plug the network cable into one of its LAN ports. 

Does it matter? I personally like the Zyxel more, since it's newer and works better for me.

> **kfinity said:**
> And actually, if you set the ssid and key to be the same, they might just show up as the same wireless network that way.

Would this actually work? I've got to try it! I guess you have to set the same security options. :)

---

### Post by TheJohlin on 2010-07-07
Well, set the routers SSID to the same but I still have to disconnect and connect again.
Should they be on the same channel?
Or am I simply trying the impossible, since they don't support WDS?

---

