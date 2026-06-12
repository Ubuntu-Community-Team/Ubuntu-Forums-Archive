---
title: "broadcom wireless stopped working after recent update"
date: 2009-08-26
forum: Networking &amp; Wireless
---

### Post by mastahoffunk on 2009-08-26
Hello, 

I've been using 64-bit Jaunty for a while on my Dell inspiron notebook and have had no problems using my BCM4312 802.11b/g (rev 01)  wireless card with the prepackaged drivers until earlier this week.

Suddenly, I stopped being able to see a list of wireless networks to connect to (list appears empty), and trying to connect to known networks manually always results in more password prompts/timing out. "Enable wireless networking" is checked, but still nothing.

Under Admin -> Hardware drivers I notice that the STA driver is not activated, but when I click the button to activate it, it still says it's not activated.

I've tried a few other solutions such as installing windows drivers via ndiswrapper or re-installing the STA driver and nothing seems to work. I'm stumped.

Here's some output:
lspci
...
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

lspci -n |grep 0c:00.0
0c:00.0 0280: 14e4:4315 (rev 01)


iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

eth1      Failed to read scan data : Invalid argument

At this point I don't care which driver I'm using, as long as I can use my wireless again. Any insights would be greatly appreciated. 

Thanks,
Derek.

---

### Post by Bucky Ball on 2009-08-26
System->Administration->Network

Make sure everything is correct in there. You are not getting served an IP by your router by the looks of it. You can set a static IP in 'Network' if you like, but you need to be connecting to your router (if you set a static IP, depending on your router, you need to make sure the router is not attempting to serve you an IP also).

In 'Network' if it isn't already, set 'Automatic Config (DHCP)', and make sure you have 'Enable Roaming' off for the moment and the correct ESSID (name of router/access point) and WEP or other security key. These must match what you have in the router.

There should be no need to change anything on the router as it was working fine before. 

DO NOT try installing Windows drivers with ndiswrapper. The card was working fine before with the correct drivers, the B43 setup by the sounds of it, so in 'Hardware Drivers' make sure that is enabled. You don't want to create another problem. :)

---

### Post by superprash2003 on 2009-08-26
make sure that the wireless switch is ON

For reference:  [http://www.prash-babu.com/2009/05/how-to-fix-wireless-no-scan-results-in.html](http://www.prash-babu.com/2009/05/how-to-fix-wireless-no-scan-results-in.html)

---

### Post by mastahoffunk on 2009-08-26
Hey,

Thanks for the suggestion! I'm not sure why, but changing network to use a static IP fixed the problem. 

I wish I thought of that myself.

Cheers,
Derek.

---

### Post by Bucky Ball on 2009-08-26
Nice one! Sounds like the router is NOT set up as a DHCP server therefore not serving an IP, you have to give it one. :)

---

