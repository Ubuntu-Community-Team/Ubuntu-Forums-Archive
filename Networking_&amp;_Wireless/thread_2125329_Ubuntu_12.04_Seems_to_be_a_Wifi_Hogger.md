---
title: "Ubuntu 12.04 Seems to be a Wifi Hogger"
date: 2013-03-13
forum: Networking &amp; Wireless
---

### Post by Windowjunk on 2013-03-13
Hello,

I've been using Ubuntu 12.04 for about nine months or so on my laptop [Dell Inspiron 15R with BCM4313 802.11b/g/n Wireless LAN Controller]. My issue is that my laptop creates a radius of a 'dead' zone whenever I have it connected to the internet, and I've been experiencing this for about a month. For instance, while Ubuntu is wirelessly connected to the internet (home network), my iPhone 3GS won't load anything, even though it shows it's connected to the home network, as nothing will load that requires internet access. However, if I disconnect my laptop from the internet, my iPhone or another laptop around will instantly load anything without issue. The reason I know this is an Ubuntu problem because I also have a Windows 7 partition I can boot into; everything works fine connection wise.
If anyone has any idea what the culprit is, I'll be very pleased! 
Also to note, router isn't the issue (in terms of being faulty, fresh one was just bought today and problem is still present). Also tried loading an earlier kernal, no success there either. 
Hopefully there is a solution that won't require me to reinstall Ubuntu. 

Thanks!

---

### Post by nd456 on 2013-03-13
I'd suspect your router setting conflicting with ubuntu. Id start by getting a live distro disk, booting it up, and see if the problem persists when you connect back to the network.
To get a little more info, what router do you have? Also is there an encription? Id try setting the router up unsecured (tempraraly) and go from there.
One last thing to see is when you're in the "dead zone" go under the phone settings, click the blue arrow next to your network and see if it's assigning a ip to the phone, if so, try to login to the router settings on the phone.

---

### Post by Windowjunk on 2013-03-13
> **nd456 said:**
> I'd suspect your router setting conflicting with ubuntu. Id start by getting a live distro disk, booting it up, and see if the problem persists when you connect back to the network.
To get a little more info, what router do you have? Also is there an encription? Id try setting the router up unsecured (tempraraly) and go from there.
One last thing to see is when you're in the "dead zone" go under the phone settings, click the blue arrow next to your network and see if it's assigning a ip to the phone, if so, try to login to the router settings on the phone.

The router is the **Netgear WNDR3400v2. **I'll have to do live distro boot soon and check if it does it. And, I did try it unsecured before (the router), same issue present. About the phone: I see it does have an IP, but what's the significance of logging into the router settings on my phone? (what are am I trying to accomplish here is what I'm asking basically). Bare in my mind though, any internet capable device that goes in a certain radius within my laptop are also affected, not just my phone.
Still find this odd that my Windows 7 partition (go figure) does not have this problem.

---

### Post by Windowjunk on 2013-06-03
Okay, update:
I tried the live boot CD environment and connected the laptop to the network just fine. My mobile phone (I no longer have an iPhone but instead the Defy XT) did not have an issue loading up web pages.
However, I just recently freshly re-installed Ubuntu 12.04, yet however, when I installed the wifi card (via Additional Drivers), and connected my laptop to the wireless network, my phone replicates the same issue as before.
Again, this is only specific to when I use Ubuntu, however switching over to my Windows 7 partition, the problem is not there.

Any further insight?
Thanks!

---

### Post by ahallubuntu on 2013-06-03
~

---

### Post by chili555 on 2013-06-03
Which driver is being used in the live CD?```
lsmod | grep -e bcma -e wl -e brcmsmac
```And how about the same in the installed version?> when I installed the wifi card (via Additional Drivers)Call me suspicious...

---

### Post by Windowjunk on 2013-06-03
> **chili555 said:**
> Which driver is being used in the live CD?```
lsmod | grep -e bcma -e wl -e brcmsmac
```And how about the same in the installed version?Call me suspicious...
Non-Live CD:
```

wl                   3074856  0 
cfg80211              205544  1 wl
lib80211               14381  2 lib80211_crypt_tkip,wl
```
Live CD without installed driver, but has an active wireless connection:
```

bcma                   26696  0 
brcmsmac              570874  0 
mac80211              506816  1 brcmsmac
brcmutil               15139  1 brcmsmac
cfg80211              205544  2 brcmsmac,mac80211
crc8                   12893  1 brcmsmac
cordic                 12535  1 brcmsmac

```
With installed driver on Live CD:
```

wl                   2568210  0 
lib80211               14381  1 wl
bcma                   26696  0 
brcmsmac              570874  0 
mac80211              506816  1 brcmsmac
brcmutil               15139  1 brcmsmac
cfg80211              205544  2 brcmsmac,mac80211
crc8                   12893  1 brcmsmac
cordic                 12535  1 brcmsmac

```

---

### Post by chili555 on 2013-06-03
> Live CD without installed driver, but has an active wireless connection:A good solid happy connection? If so, I'd suggest you remove the hogger driver and reboot:```
sudo apt-get remove --purge bcmwl-kernel-source
```> wl                   2568210  0 
lib80211               14381  1 [COLOR="#FF0000"]wl[/COLOR]
[COLOR="#FF0000"]bcma[/COLOR]                   26696  0 
brcmsmac              570874  0 
mac80211              506816  1 brcmsmac
brcmutil               15139  1 brcmsmac
cfg80211              205544  2 brcmsmac,mac80211
crc8                   12893  1 brcmsmac
cordic                 12535  1 brcmsmacGreat...two conflicting drivers. The live CD is still not quite perfect.

---

### Post by Windowjunk on 2013-06-03
> **chili555 said:**
> A good solid happy connection? If so, I'd suggest you remove the hogger driver and reboot:```
sudo apt-get remove --purge bcmwl-kernel-source
```

Wow, that did the trick! The dead zone issue is now a thing of the past...
THANK YOU! :D

I do wonder though, what exactly goes on during the installation to make my wifi card to mess up like that...
Nevertheless, I'll keep that command handy the next time I need to re-install Ubuntu!

---

### Post by chili555 on 2013-06-03
You don't really have to remember to remove the wrong driver, you just have to remember not to install it in the first place; e.g.> when I installed the wifi card (via Additional Drivers) The Broadcom 4313 is a bit of a tricky device. The STA driver sort of works but the native suite bcma and brcmsmac work much better. The Additional Driver utility happily installs the wrong driver if you ask for it!

Glad it's working now. This was a fun one for me; I thought I could smell the answer.

---

