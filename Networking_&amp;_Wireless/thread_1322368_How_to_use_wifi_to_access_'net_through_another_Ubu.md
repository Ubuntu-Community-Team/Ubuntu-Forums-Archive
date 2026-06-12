---
title: "How to use wifi to access 'net through another Ubuntu PC?"
date: 2009-11-10
forum: Networking &amp; Wireless
---

### Post by Mawg on 2009-11-10
At work I have a desktop, ethernetted. I occasionally bring my laptop to work and swap the ethernet cable between the two.

The IT department refuse to give me another etehrnet port - this is non-negotiable.

Can I use wifi to somehow piggy-back? That is, the desktop stays permanently ethernetted and I use a spare USB-wifi dongle which I have lying around to allow the laptop to have wifi access through the desktop to the 'net?

Not sure if I explained that clearly enough? The desktop would effectively be a router for the laptop. Can I configure it to eb so? How?

Thanks in advance.

---

### Post by bigb_thedestroyer on 2009-11-10
why don't you connect a personal router (not wireless, if you don't have to) in between the lan and the desktop and make it secure so only you can log in.  Set it to a /30 subnet so only your laptop and your desktop can connect.

If you company doesn't use port security (which they probably don't because you hot swap your Ethernet cable all the time), this should work.

---

### Post by Mawg on 2009-11-11
> **bigb_thedestroyer said:**
> why don't you connect a personal router (not wireless, if you don't have to) in between the lan and the desktop and make it secure so only you can log in.  Set it to a /30 subnet so only your laptop and your desktop can connect.

If you company doesn't use port security (which they probably don't because you hot swap your Ethernet cable all the time), this should work.

Well, I was hoping for a wifi solution, since I have a spare device lying around, and don't have a spare router.

But, well, I guess that routers are cheap enough. Thanks a lot for the advice.

---

### Post by bigb_thedestroyer on 2009-11-12
You could use wifi, but if your concerned about getting caught at work, piggy-backing their network, then dont use wifi.

---

### Post by Iowan on 2009-11-12
[Here]("https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless") is a wireless ICS help page.

---

### Post by Mawg on 2009-11-12
> **bigb_thedestroyer said:**
> You could use wifi, but if your concerned about getting caught at work, piggy-backing their network, then dont use wifi.

No, no, they wouldn't mind that. They are nice enough, but can't physically give me another Ethernet wall jack.

---

### Post by Mawg on 2009-11-12
> **Iowan said:**
> [Here]("https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless") is a wireless ICS help page.

Whoo hoo!  That looks like *exactly* what I was looking for. Thanks muchly!

---

