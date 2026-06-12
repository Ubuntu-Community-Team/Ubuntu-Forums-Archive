---
title: "Broadcom BCM4328 802.11a/b/g/n problems"
date: 2009-07-24
forum: Networking &amp; Wireless
---

### Post by Theory5 on 2009-07-24
I have been searching everywhere for a fix to get my wireless card up and running on my TouchSmart tx-2-1270us. HP doesnt even have my model under its list of computers so I cant download any of my models correct broadcom drivers and try to use them with ndiswrapper. I checked [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) but they dont have my model supported. Anyone know how to start this wireless card?

---

### Post by leetkangaroo on 2009-07-24
My broadcom card was automatically loaded after a ubuntu install all i had to do was go into hardware drivers and activate it. I've never succeeded in installing my card drivers any other way but i do know you need the b43-fwcutter package. It should just work :S

---

### Post by Theory5 on 2009-07-24
> **leetkangaroo said:**
> My broadcom card was automatically loaded after a ubuntu install all i had to do was go into hardware drivers and activate it. I've never succeeded in installing my card drivers any other way but i do know you need the b43-fwcutter package. It should just work :S

yes, it is there, and its activated, but for some reason the light on my laptop is not on, the switch does not work, and I dont know how to get it up and running and configure my wireless correctly. It curently says this driver is activated but not currently in use.

---

### Post by leetkangaroo on 2009-07-24
The light and the switch may not work but the card itself should. Have you tried manually connecting to a network? If that doesn't work i don't think i can help you further...

---

### Post by leetkangaroo on 2009-07-24
First of all remove the network-manager package and install wicd it's better anyway. Here's the link [http://cz.archive.ubuntu.com/ubuntu/pool/universe/w/wicd/wicd_1.5.9-2_all.deb](http://cz.archive.ubuntu.com/ubuntu/pool/universe/w/wicd/wicd_1.5.9-2_all.deb)

Once that's installed start it by running wicd-client -n in a terminal. It should find access points near you if not i do not know.

---

### Post by t0mppa on 2009-07-25
To properly install the firmware with fwcutter through the Hardware Drivers, I believe you need to have Internet access (through wired interface) for it to work. See [this page]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx") for more info on that.

However, b43 doesn't support 802.11n, so if you need the full speed, you have to use either ndiswrapper or the Broadcom STA driver. People have reported that they've got b43 to work on a/b/g speeds with this card though. If you're not sure what that means, the theoretical speeds for the different standards are: 1 Mb/s for A, 11 Mb/s for B, 54 Mb/s for G and 600 Mb/s for N. Practically G is capped to 26 Mb/s and N to 450 Mb/s though and even those are under perfect situations, which are rarely encountered in practice.

STA should be shown on the Hardware Drivers as well, but if for some reason it isn't, it can also be installed manually by downloading it from the [Broadcom's website]("http://www.broadcom.com/support/802.11/linux_sta.php") and compiling it yourself.

---

### Post by Theory5 on 2009-07-25
> **leetkangaroo said:**
> The light and the switch may not work but the card itself should. Have you tried manually connecting to a network? If that doesn't work i don't think i can help you further...

I dont know how to set the card up in ubuntu or to see if it is working, could somebody help me with that?

---

### Post by Theory5 on 2009-07-25
installing b43-fwcutter is all it took to get it working.... and the light is on, thanks. AND the switch works!

---

