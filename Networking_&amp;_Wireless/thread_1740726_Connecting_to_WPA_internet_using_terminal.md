---
title: "Connecting to WPA internet using terminal"
date: 2011-04-27
forum: Networking &amp; Wireless
---

### Post by slgtheindividual on 2011-04-27
I need to reinstall my GUI but all I can access currently is a terminal, I have the encryption key and SSID but have found all the how to's I've read really confusing since following certain steps on them give me error messages, I'm connecting wirelessly to wlan0. Thank you in advance.

---

### Post by Buntumatic on 2011-04-27
Well, you have to tell us:

0. what HOWTO you are following, 
1. at which step you get stuck
2. and what error messages you get.

---

### Post by slgtheindividual on 2011-04-27
Ok well the one I was following (I lost the page now) said to try 

"sudo ifup wlan0" which I did and gave me "Ignoring unknown interface wlan0=wlan0"

I don't want to set up anything new either which some of them seem to show, just connect to the connection I usually use via the gui

---

### Post by Buntumatic on 2011-04-27
Is your wireless card seen if you do ```
ifconfig -a
```

---

### Post by slgtheindividual on 2011-04-27
Yes it comes up with 

"wlan0 Link encap:Ethernet HWaddr..."

---

### Post by chili555 on 2011-04-27
You might try:```
sudo iwconfig wlan0 wpa-ssid mynetworkname
sudo iwconfig wlan0 wpa-psk mypassphrase
sudo dhclient wlan0
```If that doesn't work, try editing /etc/network/interfaces to:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-ssid mynetworkname
wpa-psk mypassphrase
```Then do:```
sudo ifdown wlan0 && sudo ifup wlan0
```You will either connect or get some instructive messages about why not.

---

### Post by slgtheindividual on 2011-04-27
ok I got an "unkown command wpa-ssid" also I edited the file interfaces and when I ran "sudo ifdown..." I got out "ifdown: interface wlan0 not configured"

---

### Post by chili555 on 2011-04-27
And when you did 'sudo ifup wlan0' and the system re-read the interfaces file, what happened? Any interesting messages?

---

### Post by slgtheindividual on 2011-04-27
it gives me "ifup: interface wlan0 already configured"

---

### Post by chili555 on 2011-04-27
Well; it went from not configured to already configured in a few moments. Did it connect? Any interesting messages?```
sudo cat /var/log/syslog | grep wlan0 
iwconfig wlan0
```

---

### Post by Joe of loath on 2011-04-27
To connect in the terminal you'll need to use wpa_supplicant or wicd-curses. wpa_supplicant is more flexible, but wicd-curses is easier.

---

### Post by slgtheindividual on 2011-04-27
ok well I rebooted and ran those last two commands and it worked, I'm online and it's currently downloading. I have no idea how but thank you very much for your help =]

to clarify I ran

sudo cat /var/log/syslog | grep wlan0 
iwconfig wlan0

---

### Post by slgtheindividual on 2011-04-27
ok one last thing, so I have my gui back and everything is working fine except at the top the little applet that tells you what network you are connected to says I'm not connected to any but I can still get on the internet and ping myself etc. Any ideas? I'm thinking maybe if I change that file back to how it was and restart it'll be fine?

---

### Post by chili555 on 2011-04-27
> **slgtheindividual said:**
> ok one last thing, so I have my gui back and everything is working fine except at the top the little applet that tells you what network you are connected to says I'm not connected to any but I can still get on the internet and ping myself etc. Any ideas? I'm thinking maybe if I change that file back to how it was and restart it'll be fine?Yes you will, although it will probably take a reboot.

However, if you have a stay-at-home computer that will not be taken down to the library or coffee shop to connect, you could remove Network Manager and leave the interfaces file as is. You will connect on boot to your network automatically.

---

### Post by slgtheindividual on 2011-04-27
Thank You so much for all of your help, everything is as it was =]

---

