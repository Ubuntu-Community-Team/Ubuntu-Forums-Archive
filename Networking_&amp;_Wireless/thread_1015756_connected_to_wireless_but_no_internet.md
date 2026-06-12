---
title: "connected to wireless but no internet"
date: 2008-12-19
forum: Networking &amp; Wireless
---

### Post by Jameshardy88 on 2008-12-19
hi im dual booting windows xp/Ubuntu i use a Netgear WG111v2 wireless usb adapter and this seems to automatically show all available wireless networks within my area. I can connect with it to a network that i use when on windows (which allows me access to the internet) however when connected to it on ubuntu i don't have internet access, why could this be?

---

### Post by blueblob on 2008-12-19
I have the same problem with WiFi. It says its connected and the connection information looks good with a speed of 54Mb/s but when I try to browse on firefox I get page load error.
I have a similar problem with my vpn connection using vpnc and I´m pretty certain everythings configured correctly but when I try to connect it fails.
Both connections work fine in windows.

Edit: My mistake. The wireless was also a vpn connection so the problem is not with wifi. Will find different thread.

---

### Post by ieee488 on 2008-12-19
If you are using Firefox 3 in Ubuntu 8.04, there is a bug.
Firefox always starts up in Offline mode.

It happened to me when I was working on getting my mobile broadband card to work. I had thought I had set Firefox in offline mode, but now realize it is a bug.

---

### Post by Jameshardy88 on 2008-12-19
sorry i should have mentioned i am using intrepid not hardy

---

### Post by usman.patel on 2008-12-19
Hello,

I am also having exactly this problem.  I have also opened a thread - - >  [http://ubuntuforums.org/showthread.php?t=1015323](http://ubuntuforums.org/showthread.php?t=1015323)

My wired connection works perfectly using Firefox, but when using wireless, the WLAN0 connects, acquires IP address, but cannot access internet.  I cannot even ping the default gateway from where the IP address is offered.

My wireless card is Realtek RTL8187B.  As this appears to happen irrespective of hardware, perhaps it is a bug?  Anyone know how report a bug?

usman.

---

### Post by usman.patel on 2008-12-19
oh..forgot to mention i am using Ibex inside Vista (wubi install).

---

