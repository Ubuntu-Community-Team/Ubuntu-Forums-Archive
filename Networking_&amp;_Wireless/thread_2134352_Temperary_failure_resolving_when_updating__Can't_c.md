---
title: "Temperary failure resolving when updating : Can't connect wireless"
date: 2013-04-10
forum: Networking &amp; Wireless
---

### Post by wmidtbo on 2013-04-10
I was able to connect wireless when installing Ubuntu server.  Now when I try to update it says "Temporary failure resolving"

When I type in: lspci -v
I can see my Wireless Network Adapter.... 

Capabilities: <access denied>
Kernel driver in use: ath5k
Kernel modules: ath5k

When I type in: sudo lspci -v
Capabilities: [44] Power Management version 2
Kernel driver in use: ath5k
Kernel modules: ath5k

I think this has something to do with my problem.  Any help would be greatly appreciated!

---

### Post by wmidtbo on 2013-04-12
[INDENT]                     I was able to connect wireless when installing Ubuntu server.  Now  when I try to update it says "Temporary failure resolving"

When I type in: lspci -v
I can see my Wireless Network Adapter.... 

Capabilities: <access denied>
Kernel driver in use: ath5k
Kernel modules: ath5k

When I type in: sudo lspci -v
Capabilities: [44] Power Management version 2
Kernel driver in use: ath5k
Kernel modules: ath5k

I think this has something to do with my problem.  Any help would be greatly appreciated!                 
[/INDENT]

---

### Post by mörgæs on 2013-04-12
Please stop multiposting.
Threads merged.

---

### Post by wmidtbo on 2013-04-12
Thanks mörgæs.  Where in this forum should I post this question to try and get an answer?

---

### Post by mörgæs on 2013-04-12
Most important is that you post once and show patience.

---

### Post by wmidtbo on 2013-04-12
I did a clean install and installed 
[h=3]Ubuntu Server 12.04.2 LTS[/h]Is there another version I should try installing?  Strange that wireless internet worked when I was going through the install process.

---

### Post by steeldriver on 2013-04-12
Can you post the outputs of the following commands please?

```

ifconfig
ping -c4 74.125.226.78
dig google.com
service resolvconf status

```

---

### Post by wmidtbo on 2013-04-12
[IMG]http://www.schlesingerlawoffices.com/ub.JPG[/IMG]

---

### Post by wmidtbo on 2013-04-15
I should add that I'm trying to connect with my wireless card that is manufactured by D-link.

---

### Post by gorkypah on 2013-04-15
...

---

### Post by wmidtbo on 2013-04-16
Not really sure if I'm doing something wrong but those commands are not working.  Sorry I'm new to Linux..[IMG]http://www.schlesingerlawoffices.com/screenshot1.JPG[/IMG]

---

### Post by wmidtbo on 2013-04-16
I took a shot of iwconfig as well.  Hope this helps.[IMG]http://www.schlesingerlawoffices.com/screenshot2.JPG[/IMG]

---

### Post by steeldriver on 2013-04-16
You need to add the lines that gorkypah gave you to your /etc/network/interfaces file - NOT just type them at the command prompt

Also the wpa-ssid and wpa-psk are supposed to be your wireless network's name and passphrase - which doesn't seem to be what you are using

---

### Post by wmidtbo on 2013-04-16
Thank you steeldriver.  When I went to edit this it looks like all my info was already in there.  My essid and pass are correct.
[IMG]http://www.schlesingerlawoffices.com/photo3.JPG[/IMG]

---

### Post by wmidtbo on 2013-04-16
Thank you steeldriver.  When I went to edit this it looks like all my info was already in there.  My essid and pass are correct.

---

### Post by steeldriver on 2013-04-16
OK so that's a WEP setup not WPA but that should be OK (you should consider moving to WPA for security reasons though) provided the info is correct - are you sure about that wireless-key1 value? iirc WEP keys must be either 10 or 26 hexadecimal digits long - yours seems to be 8 digits

If the values are corect but ifconfig is still not showing a DHCP-supplied IPv4 address then the next step would be to try to debug that e.g. look for relevant messages in dmesg

```
dmesg | grep wlan0
```

---

### Post by wmidtbo on 2013-04-16
I logged into my wireless router and its set up for WPA-PSK + WPA2-PSK and my Pre-Shared Key (PSK) is what was listed as my wireless-key1 which is fe244fae the 8 characters.  So it's my understanding that I am in fact using WPA and not WEP.  Do I need to change the Ubuntu set up to WPA somehow?

---

### Post by steeldriver on 2013-04-16
Yes if it's WPA then you need to use the wpa-xxxx field names that gorkypah mentioned in a previous post i.e.

```
auto wlan0
iface wlan0 inet dhcp
    [COLOR=#0000ff]wpa-ssid[/COLOR] *yourssid*
    [COLOR=#0000ff]wpa-psk[/COLOR] *yourkey*
```

If your router/DHCP server doesn't provide a DNS server address you may need to add a dns-nameservers line as well in order to resolve names

---

