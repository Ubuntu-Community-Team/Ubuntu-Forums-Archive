---
title: "ppp0, wlan, shared internet"
date: 2009-07-19
forum: Networking &amp; Wireless
---

### Post by jacobdk on 2009-07-19
Hi All..

I have this crasy setup, and i wonder how i can make it work.

My network is like this: PPP0 on ubuntu. A cable from my ubuntu box to a wireless router, and then 2 windows client, whish connect to the router via wireless lan..

ppp0 ->>ubuntu "server" ->> eth0 on the server->>router->>win1->>win2

ppp0 is a usb modem.
router is a wireless one from SMC
win1+2 windows xp sp 2 and 3

my main problem is how too share ppp0 whit my router, so win* can get inet from the router..

Info mising? 

Jacob

---

### Post by apkent on 2009-07-19
This is EXACTLY what I am also trying to do.

I have a Xubuntu server with USB modem on PPP0 and then a wireless network card on wlan0, which connects to my wireless router, and will hopefully share its internet to my Vista laptop.

I read through this tutorial - [http://www.freesoftwaremagazine.com/columns/howto_share_mobile_broadband_ubuntu_using_only_gui](http://www.freesoftwaremagazine.com/columns/howto_share_mobile_broadband_ubuntu_using_only_gui) - but after setting up Firestarter as suggested, I still don't have any network connection on the laptop, and the wireless router status page says 'Internet : No Connection'.

Would be most grateful for any advice on this one!

Andy

---

### Post by apkent on 2009-07-20
Anyone got any ideas?

---

### Post by apkent on 2009-07-20
Ok, so I think I'm nearly there.......just missing a few final steps I think.

I have my home network set up (called APKNet).

Router is on 192.168.2.1 assigning IPs upwards starting at 192.168.2.2 which is fine and works perfectly

Even managed to get my PS3 connected to it access mediatomb - spot on.

Back on Xubuntu I've got the 3G internet running (through the mobile broadband tab in NetworkManager) and set the wireless network up so that it doesn't look for the internet through the wireless lan, put rather pulls it from the 3G - again, not a problem.

But using Firestarter I told it to route from the PPP device to wlan0 (the wireless connection back to the wireless network) and it doesn't seem to want to play ball.

Bearing in mind I haven't done any changes on the Vista laptop, should I? If so, what should I change?

---

### Post by superprash2003 on 2009-07-21
you would need to disable the DHCP server of the router as it is the ubuntu machine which is providing the internet and the eth0 of the ubuntu box should be the gateway ip. whereas if you enable DHCP server on the router , then the machines connected to it will automatically be assigned the router's ip as the gateway ip.. for ICS , if firestarter's ICS feature didnt work , you could try this [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

