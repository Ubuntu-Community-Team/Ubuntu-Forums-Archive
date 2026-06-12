---
title: "Dell Inspiron 640m WPA problems"
date: 2009-06-02
forum: Networking &amp; Wireless
---

### Post by nodger on 2009-06-02
Hello everybody. I'm having TERRIBLE problems getting WPA2-Personal to work on my Dell Inspiron 640m Laptop.

I was using 8.04, I upgraded to 9.04 Jaunty hoping this would solve the porblem...no joy

I then tried to reinstall the ipw 2200 drivers according to this HOWTO: [http://ubuntuforums.org/showthread.php?t=12270](http://ubuntuforums.org/showthread.php?t=12270)

.. but I couldn't install it due to a compilation error.

I also installed just about any other software I could find in the synaptic Package Manager that matched the term "wpa"

Heres as much info on my system as possible:
Dell inspiron 640m
Wireless chipset:Intel PRO/Wireless 3945ABG
Security Type: WPA Personal
Encryption Type:TKIP

The WPA connections work fine in Windows and my WEP 128bit key network works fine aswell. Could this be a firmware issue? I'm going to try setting up my WEP router to WPA and see if I can get it working that way , that way I'll rule out the laptop (or ubuntu) as the issue, but I have a hunch it's a driver issue.

Using a ps command I found the following program is running:
```
/sbin/wpa_supplicant -u -f /var/log/wpa_supplicant.log
```


I also created a new **/etc/wpa_supplicant.conf** file in the hope that this would work.

Heres the contents of that file:
```

ctrl_interface=/var/run/wpa_supplicant

network={
	ssid="UPC 14"
	key_mgmt=WPA-EAP
	eap=TTLS
	password=XXXXXX
}


```

The password is in fact an 8-digit code.

I appreciate any help or clues on this issue. I usually never post on forums looking for help and prefer to figure out the solution myself but I have to admit this problem has me stumped.

---

### Post by nodger on 2009-06-03
Once again I fixed the problem myself. Seems to be an issue with my router (Netgear WNR2000). Just enabled static IP (instead of DHCP) and it finally (after 18 hours trying) worked.

---

