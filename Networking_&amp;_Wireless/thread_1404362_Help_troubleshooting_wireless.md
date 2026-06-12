---
title: "Help troubleshooting wireless"
date: 2010-02-11
forum: Networking &amp; Wireless
---

### Post by steviefordi on 2010-02-11
I am using Intrepid Ibex 8.10 on my Compaq notebook. lspci reports my builtin wireless card as **Atheros Communications AR242x**.

After initial installation a year or so ago, I had to get the wireless working by installing the '**Backport Modules**' package. This enabled me to use the **ath5K** driver, which has worked perfectly for me.

Last Friday I installed some updates, which both included **updates for the kernel and the backport modules** (not sure if this is relevant or not). Everything continued to work for a coulpe of days until I unplugged my router and rebooted it. Now, when Gnome starts up it doesn't even bother to search for my wireless network - it just shows a little cross over the network manager applet and no wireless networks are shown as available.

I would really like some help troubleshooting this as I'm not sure what the wireless commands (iwconfig etc.) are telling me about what's working and what isn't.

I also know this isn't an issue with the router as my ipod touch happily connects wirelessly to the internet through it.

Thanks in advance...

---

### Post by mörgæs on 2010-02-12
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

### Post by steviefordi on 2010-02-12
Excellent, now why couldn't I find that? I'll give it a go later on and post back how I get on.

---

### Post by steviefordi on 2010-02-14
Ok, I followed the guide but couldn't associate an access point with my wireless card. There were also 'no scan results' shown when I did:

```
iwlist wlan0 scan
```

I decided to reboot the laptop to undo any changes that had actually worked with iwconfig so I could start from scratch. When the PC came back up suddenly the wifi was working (and has been through several reboots since).

The only thing I can think is that the backport-modules update has made my wifi on/off hotkey sort of work. I did press and it did nothing, I thought nothing more of it until I rebooted.

---

