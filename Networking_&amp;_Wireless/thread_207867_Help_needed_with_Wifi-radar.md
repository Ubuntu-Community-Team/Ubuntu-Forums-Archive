---
title: "Help needed with Wifi-radar"
date: 2006-07-02
forum: Networking &amp; Wireless
---

### Post by Oputres on 2006-07-02
Hi.

I really want to keep it simple without a lot of editing in text files etc. I want as much GUI utilities as possible for managing my WLAN connection.

I've got my "hardware present" thanks to ndiswrapper and ndgtk (I think) and I actually got it to work... until reboot.

Now I've downloaded Wifi-radar and I hope this utility can help me find and connect to different WLANS. There are just some problems (remember, I'm a real Linux newbie and I'm not that familiar with Wifi-networking at all):

1. How do I search for available WLANs with Wifi-radar? Or is Wifi-radar "just" a GUI for presetting a specific connection?

2. So I press New, typing in my Network Name (ssid): Monster
What do I put in the different fields under Wifi Options? I guess:
Mode: Auto
Channel: Auto
Key: Have no idea, is this where I put the WPA key for my WLAN?
Security: Open or restricted?

Then there is a menu for "Use WPA" which gives me the field "Driver". What driver? Or is it here I put my WPA key?

Then there is the "Automatic network configuration (DHCP)" which sounds just fine to me. I like the words auto and automatic.

And finally there is the "Connection Commands" Before and After. Do I need to put some information in these fields?

So please anyone, help me to configure my Wifi-radar!

---

### Post by Thund3rstruck on 2006-07-02
I tried both wifi-radar and wlassistant and unfortunatly for me, neither of these detected any of the networks in my range. 

Ultimately I ended up compiling and configuring kismet which really is the best program I have ever used for identifying wifi networks, it detected even more than windows. Unfortunatly it was a little difficult to get up and running. I had to identify the wireless driver being loaded for my card and configure the sources but it was worth the effort.

---

### Post by tturrisi on 2006-07-02
His wifi card won't work w/ kismet, no ndiswrapper driver works w/ kismet.  And because he has to use ndis then his card definitely won't be supported by kismet.

---

### Post by Oputres on 2006-07-03
[QUOTE=tturrisi]His wifi card won't work w/ kismet, no ndiswrapper driver works w/ kismet.  And because he has to use ndis then his card definitely won't be supported by kismet.[/QUOTE]

Aah, so that's why Kismet won't start! So If I manage to find some Linux drivers for my Netgear WG111 Kismet is the utility to use? How do I install drivers on Linux?

But before I start that journey, what kind of utility is Wifi-radar? Is it for detecting Wlans nearby or is it for presetting configurements for my Wlan? And again, what should my settings be?

---

### Post by tturrisi on 2006-07-03
[What Is WiFi Radar?]("http://wifi-radar.systemimager.org/")

---

### Post by lorepansana on 2008-05-08
Hello everyone,

I am looking for some help configuring Wifi-Radar in my Ubuntu Gutsy. I have a USB WiFi adapter, a Sitecom 54g Turbo WL-172. When plugged in, the OS seems not to recognize it.
As suggested here in the forum, I tried Wifi-Radar and yeah, it works: it immediately detects all the wireless networks in range.

Now, the problem is that it can't get any IP address if I just click "connect". I think I need to edit my network, inserting something concerning my WPA protection and so on.:confused:

In other words, the hardware works fine but I can't connect since I am probably missing some initial configuration steps. Any ideas?

Thanks and sorry for my newbieness!

---

