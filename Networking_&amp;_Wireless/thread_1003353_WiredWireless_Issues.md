---
title: "Wired/Wireless Issues"
date: 2008-12-06
forum: Networking &amp; Wireless
---

### Post by stndrdsnz on 2008-12-06
I've been having some troubles and getting things figured out, but I'm kind of stumped at the moment and thought I'd see what kind of feedback I can get here. 

I just installed 8.10 on a brand new Dell Vostro A860. Upon loading the OS I was unable to access the internet. Network Manager showed that I was connected via my wired connection, but I couldn't load any pages. If I looked at my connection information it showed everything like it should, correct IP address as assigned by my router, it even showed my router's IP address as the Default Route. However, if I ran ifconfig it wasn't showing that I had an IP address. Subsequently, unplugging and plugging in the cable would then throw an error that it couldn't connect.

I was finally able to connect via my wired connection by adding the following lines into my /etc/network/interfaces file:

```
auto lo
**iface lo inet loopback**
auto eth0
**iface eth0 inet dhcp**
```

After calling up the eth0 interface using the ifup command my wired connection started working after rebooting. I noticed when I rebooted that my Network Manager icon had disappeared, but my connection was running so I wasn't too worried. Thus began my journey to try and get my Wireless card working. 

The wireless card I'm using is an Atheros ar242x. I ended up getting it to work by using guide I found at [madberry.org]("http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/"). However, I wasn't able to confirm it yet because I needed into the Network Manager to configure my wireless connection. So, I ended up going back into the /etc/network/interfaces file and modified it to look like the following:

```
auto lo inet loopback
auto eth0 inet dhcp
```

Following a reboot of my computer, the Network Manager is back, and indeed my wireless card is working and I can setup wireless connections, but here is where my problem is. I am no longer able to use my wired connection. It appears to be doing the same thing that it was before. After I start up the laptop and plug the cable in it says it's connected. Connection Information looks good, but ifconfig doesn't and if I unplug the cable it then says it can't connect.

I know this was lengthy, but I wanted to make sure I had enough information in it and that maybe I can help other users along the way.

Thanks,

David

---

### Post by Wolfhere on 2008-12-06
Thank you. I had lost my ability to manage my wireless due to an attempt to install synce for my windblows pda. Like you, I lost my network manager icon, although my wired connection was working. By following your change to interfaces, I got my manager icon back on reboot...and to get my wireless going, I did the same thing..auto wlan0 inet dhcp. Reboot and lo and behold. I now have both interfaces working as expected. My wireless has WPA (tkip). Thanks again.):P

---

