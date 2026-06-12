---
title: "wifi connection problem"
date: 2008-12-04
forum: Networking &amp; Wireless
---

### Post by Frantic225 on 2008-12-04
I have a wifi USB card and a WEP-enabled APN.

I can connect from gnome's network manager, however I want to run fluxbox and I don't know why I can't get it to connect from the console.

What I've tried is:

ifconfig wlan0 down
iwconfig wlan0 essid <essid-name>
iwconfig wlan0 channel <chan>
iwconfig wlan0 key <wep key>
ifconfig wlan0 up
dhclient wlan0

So what happens is that dhclient doesn't get any response to the DHCPDISCOVER and DHCPREQUESTs.

I've also tried using wifi-radar, no luck either.

What does gnome network manager do extra?

Thanks

---

### Post by gabril on 2008-12-04
what happens if you want to start gnome nwm in fluxbox from terminal? Doesnt that work?

---

### Post by halovivek on 2008-12-04
did you checked whether you have to give the wep key for the wireless router?

---

### Post by gabril on 2008-12-04
I rather think that he doesn't see any wifinetworks to connect to at all! Or am I incorrect in this assumption?

---

### Post by Frantic225 on 2008-12-04
> **gabril said:**
> what happens if you want to start gnome nwm in fluxbox from terminal? Doesnt that work?

if I run NetworkManager from the terminal it starts in the background and I haven't managed to get the NWM window to show (like when clicking the network icon in gnome). Also, my NWM doesn't autoconnect to the saved network for some reason it doesn't show it until I do "connect to hidden wireless network" even tho I have another machine running WinXP that can see it listed.

> **gabril said:**
> I rather think that he doesn't see any wifinetworks to connect to at all! Or am I incorrect in this assumption?
I see others, just not mine, don't know why.

> **halovivek said:**
> did you checked whether you have to give the wep key for the wireless router?
I'm not sure what you mean, I set the wep key with "iwconfig wlan0 key <key>", I'm 100% the key is correct, it works from the WinXP machine and from gnome NWM.

---

### Post by Frantic225 on 2008-12-04
I still have no idea why connecting from console doesn't work, but I found out that I must run nm-applet to show the network manager icon under fluxbox, and I can connect using nwm.

---

