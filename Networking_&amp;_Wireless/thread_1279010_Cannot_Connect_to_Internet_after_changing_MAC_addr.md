---
title: "Cannot Connect to Internet after changing MAC address"
date: 2009-09-30
forum: Networking &amp; Wireless
---

### Post by blurboy on 2009-09-30
Router: Linksys WRT54GS
NIC: D-Link DWA-645 (RangeBooster N 650 NoteBook Adapter)

i have successfully changed my MAC address. By doing:
ifconfig wlan0 down
ifconfig wlan0 hw ether AA:BB:CC:11:22:33
ifconfig wlan0 up

When I do:
ifconfig wlan0, it shows my new MAC address.

After changing, I cannot connect to the Internet. I have already disable mac filtering in my router. What did I miss out?

---

### Post by Krydox on 2009-09-30
Maybe you need to have 00 as the first 2 digits.

---

### Post by doas777 on 2009-09-30
did you reboot your upstream demarc device (cable/dsl modem, etc)?
if you change the mac on the wan, then the upstream device is probably very confused.

---

### Post by blurboy on 2009-09-30
> **doas777 said:**
> did you reboot your upstream demarc device (cable/dsl modem, etc)?
if you change the mac on the wan, then the upstream device is probably very confused.
 
what do you mean by rebooting upstream demarc device? how do i do that? 
 
i am connecting to the router via wireless. So after changing the MAC address of my NIC, I cant connect to the internet

---

### Post by oldfred on 2009-09-30
Before I had a router I built a new computer and switched them. The cable co took at least 45 minutes to recognize the new mac. I then learned to spoof the mac and had no problems switching. My router is still using my old computers mac address as it was quicker to bring it up with that mac address.

---

### Post by blurboy on 2009-10-01
so what did u do to connect to the internet after spoofing your MAC address?

---

### Post by oldfred on 2009-10-01
After I spoofed the mac address with my old computer's address, my new computer was inmediately recognized - not long wait for cable co to see it was a new device and assign a new ip.
I just plugged one or the other computer into the cable modem. I then decided to get the router to avoid the plugging and the entire issue.
ifconfig and my router (on a menu) have settings for hw address.

---

### Post by doas777 on 2009-10-01
you have powercycled the router right?

---

### Post by blurboy on 2009-10-01
powercycled the router ?
 
i did not do that.. neither do i know what it means.. how do i do that?

---

### Post by doas777 on 2009-10-01
> **blurboy said:**
> powercycled the router ?
 
i did not do that.. neither do i know what it means.. how do i do that?

heh. unplug it from the wall for 5 minutes and then plug it back in. powercycle = > "turn it off and then back on".

---

