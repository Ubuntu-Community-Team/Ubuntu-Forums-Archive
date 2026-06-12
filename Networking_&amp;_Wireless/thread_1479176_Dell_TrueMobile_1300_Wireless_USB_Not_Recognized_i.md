---
title: "Dell TrueMobile 1300 Wireless USB Not Recognized in 10.04"
date: 2010-05-10
forum: Networking &amp; Wireless
---

### Post by Tsu Do Nym on 2010-05-10
Dell TrueMobile 1300 wireless USB adapter is not being recognized by the network manager in 10.04. It seemed to work properly in 9.10. Does anyone know what the problem may be? Should I file a bug report?

---

### Post by Tsu Do Nym on 2010-05-11
Problem solved.  

Reading a thread for a completely different USB Wi-Fi adaptor indicated that a similar problem was solved by including the non-free firmware for Linux kernel drivers package. Although the description for that package describes it as being for DVB cards, it apparently also includes the firmware needed by some Wi-Fi adaptors.  

Two ways to install it.  

1. From the system menu, use the Synaptic Package Manager to install "linux-firmware-nonfree".

-OR-

2. From the command line use apt.
```
sudo apt-get install linux-firmware-nonfree
```Then unplug and replug the adaptor.
It should now appear in Network Manager.
That's it!
I have no idea why this is required in 10.04 but wasn't in 9.10.

---

### Post by cmcneal on 2010-09-10
I have followed the advice last posted in this chain.  It did not seem to work.  I would not discount Tsu Do Nym's experience.  Perhaps one needs to do Tsu Do Nym's advice first and continue with my info (at least that was what I did).

After going through the different packages under synaptic, I noticed there is a separate package called, firmware-addon-dell.  I installed this package then went to System -> Preferences -> Network Connections and added my own wireless router's SSID.  It started to work.

I hope this updated info will help others who face similar issues with Dell TrueMobile 1300 Wireless Adapters and Ubuntu 10.04.

---

### Post by undrline on 2011-12-19
> **cmcneal said:**
> I have followed the advice last posted in this chain.  It did not seem to work.  I would not discount Tsu Do Nym's experience.  Perhaps one needs to do Tsu Do Nym's advice first and continue with my info (at least that was what I did).

After going through the different packages under synaptic, I noticed there is a separate package called, firmware-addon-dell.  I installed this package then went to System -> Preferences -> Network Connections and added my own wireless router's SSID.  It started to work.

I hope this updated info will help others who face similar issues with Dell TrueMobile 1300 Wireless Adapters and Ubuntu 10.04.

I've periodically been looking for this for a few years now.  firmware-addon-dell got my model T2349 Dell TrueMobile 1300 Wireless USB Adapter to work.  Thanks for sharing!

---

