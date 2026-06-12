---
title: "set up ubuntu system as a basic wireless access point"
date: 2010-02-16
forum: Networking &amp; Wireless
---

### Post by Post Monkeh on 2010-02-16
i don't know if wireless access point is the right description.  i don't want to use it as a wireless router, i simply want to be able to connect to my laptop wirelessly without a router.

essentially i want to be able to use my phone to connect to my laptop wirelessly so i can ssh into it even if i don't have a known wireless network near me that both can connect to.

is this possible on a default ubuntu install or would i have to be using the server edition?

---

### Post by puppywhacker on 2010-02-16
With iwconfig you can see that the mode of my wireless interface is in Managed mode. So connected to the access point.

```
sudo iwconfig 
wlan0     IEEE 802.11bg  ESSID:"zyxel"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:02:CF:84:86:1C
```

The mode you are talking about is
- "Ad-Hoc" (network composed of only one cell and without Access Point)

Other options are
- Master (as accesspoint)
- Repeater
- Secondary
- Monitor (not associated but passively monitoring)

you can try to set the wireless card in adhoc mode, but this is dependent on the drivers for the card.

```
sudo iwconfig eth0 mode Ad-Hoc
```

ubunutu desktop and ubuntu server are basically the same, but with different default packages installed and services running. So in this case it doesn't matter which one you are using.

---

### Post by Post Monkeh on 2010-02-16
> **puppywhacker said:**
> With iwconfig you can see that the mode of my wireless interface is in Managed mode. So connected to the access point.

```
sudo iwconfig 
wlan0     IEEE 802.11bg  ESSID:"zyxel"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:02:CF:84:86:1C
```

The mode you are talking about is
- "Ad-Hoc" (network composed of only one cell and without Access Point)

Other options are
- Master (as accesspoint)
- Repeater
- Secondary
- Monitor (not associated but passively monitoring)

you can try to set the wireless card in adhoc mode, but this is dependent on the drivers for the card.

```
sudo iwconfig eth0 mode Ad-Hoc
```

ubunutu desktop and ubuntu server are basically the same, but with different default packages installed and services running. So in this case it doesn't matter which one you are using.

well i'm an idiot. i didn't realise i could just create a new wireless network from network manager.  i can see the network from my phone but as yet haven't got it working the way i want it to but at least i've got a starting point. thanks.

---

