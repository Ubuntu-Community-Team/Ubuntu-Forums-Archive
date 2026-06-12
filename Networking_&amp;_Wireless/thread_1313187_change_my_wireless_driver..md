---
title: "change my wireless driver."
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by bolex100 on 2009-11-03
I have a "PRO/Wireless 3945ABG [Golan] Network Connection", which does not work with my Belkin N router.  Belkin suggested changing the driver.
How do I do that?

---

### Post by chili555 on 2009-11-03
My 3945ABG works perfectly. What about yours does not?

---

### Post by bkratz on 2009-11-03
> **chili555 said:**
> My 3945ABG works perfectly. What about yours does not?



Does his (and your) module support wireless N band?

---

### Post by chili555 on 2009-11-03
Nope, but it doesn't matter, because the hardware, that is, the physical card itself doesn't support N technology. Compare Intel's 3945ABG to their 4965AG[COLOR="Red"]N[/COLOR].

---

### Post by bkratz on 2009-11-04
> **chili555 said:**
> Nope, but it doesn't matter, because the hardware, that is, the physical card itself doesn't support N technology. Compare Intel's 3945ABG to their 4965AG[COLOR="Red"]N[/COLOR].



The reason I asked that was because when I looked up his router it says nothing other than N technology, at least that is all I found.

[http://catalog.belkin.com/IWCatProductPage.process?Product_Id=372043](http://catalog.belkin.com/IWCatProductPage.process?Product_Id=372043)

So I think what he was asking was: could he update some driver somewhere to make it work, I think you have answered this now though.

---

### Post by chili555 on 2009-11-04
As far as I know, all 'N' devices are backwards-compatible with, at least, 802.11b and -g. The Belkin is no exception. Please see Specifications. The router will work perfectly with an Intel 3945ABG, although not at -a nor -n speeds.

---

### Post by bkratz on 2009-11-04
> **chili555 said:**
> As far as I know, all 'N' devices are backwards-compatible with, at least, 802.11b and -g. The Belkin is no exception. Please see Specifications. The router will work perfectly with an Intel 3945ABG, although not at -a nor -n speeds.



Thanks I missed that "obviously"

---

### Post by bolex100 on 2009-11-04
The Belkin N will work with G hardware but only at G speeds.  My problem is that it keeps cutting out (while staying connected).  The support at Belkin said that they never heard of this problem and to try changing the driver.  

So the question was:- how do I do that?

---

### Post by chili555 on 2009-11-04
I don't know of another driver that you could change to that wasn't a step backwards. There are a variety of steps you can take, however to fine-tune your current setup.

Go in to the administration pages of the router and see if there is a setting for B and G speeds or for B,G and N speeds. Select B and G only.

Try different MTU settings. My router's configuration page says it's MTU setting is 1492. I, therefor, set my MTU at 1492 instead of it's default of 1500.```
sudo ifconfig wlan0 mtu 1492
```If that helps you, we can make that permanent.

Some routers allow you to increase the signal. If signal strength is an issue, check and increase. Check with:```
iwconfig wlan0
```You will see something like this:> wlan0     IEEE 802.11abg  ESSID:"GBR1"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 99:24:56:29:D7:99   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          [COLOR="Red"]Link Quality=62/70[/COLOR]
---snip---When I get down towards 40/70, I have a hard time staying connected.

---

### Post by bolex100 on 2009-11-12
It made no difference.  My USB adapter works though.  Win7 looms!

---

