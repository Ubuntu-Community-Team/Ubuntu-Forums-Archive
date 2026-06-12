---
title: "Shared WiFi with ndiswrapper?"
date: 2006-01-20
forum: Networking &amp; Wireless
---

### Post by dtlinker on 2006-01-20
I have Ubuntu breezy on a Dell B130 laptop dual boot, using ndiswrapper and the XP driver. I have WiFi working with an Airport base station if I have encryption turned off. I can't get it to work with WEP.

I had the same problem with Windows XP, but was able to solve it by changing the mode from "open" to "shared". When I did that on XP, I wasl able to use WEP without difficulty.

Is there a way of enabling the same mode for Ubuntu?

---

### Post by Lambert on 2006-01-20
In your /etc/network/interfaces file, the section on your interface for a shared key should look like this


wireless-key restricted ____________

insert key in blank.

I believe this is all that's needed with ndiswrapper and using a shared key

---

### Post by dtlinker on 2006-01-21
Thank you for the reply. I had already added that line to my interfaces file. It still doesn't work.

Ideas welcome.

---

### Post by underthing on 2006-04-13
I'm having the same issue. I too tried the modification of /etc/network/interfaces to no avail. Can anyone help?

---

### Post by sadjack on 2006-04-13
I do not use ndiswrapper, however I do have a wireless connection with shared wep keys. My /etc/network/interfaces looks like

iface ra0 inet static
        pre-up /sbin/iwconfig ra0 essid Untitled key ********************
        broadcast 192.168.1.255
        wireless-essid Untitled
        wireless-key **********************
        address 192.168.1.16
        netmask 255.255.255.0
        gateway 192.168.1.254

In kwifimanager I have settings for a "managed" connection

It may not be ideal but it works for me, it may work for you.....

---

### Post by dtlinker on 2006-04-19
I tried this and many variants, and have made some progress, but it still doesn't work. I am connecting to an apple airport, from a Dell laptop on which WiFi works when I have WEP turned off.

Now, the interface appears to connect. During booting, it connects to the ubuntu time server. If I check System -> Administration -> Networking, the wireless connection is listed as active, and signal strength is 100%. If I check iwconfig, everything looks good as well. 

The problem is that I can't connect. If I try connecting through a browser, it doesn't make a connection, saying that it can't find the site. Ping also doesn't work.

Any ideas about how to get this working?

In interfaces, I have:
iface wlan0 inet dhcp
wireless_keymode restricted
wireless_key *****************************
wireless_mode managed
wireless_essid ********
wireless_ap auto

auto wlan0

---

