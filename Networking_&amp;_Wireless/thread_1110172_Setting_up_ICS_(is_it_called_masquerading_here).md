---
title: "Setting up ICS (is it called masquerading here?)"
date: 2009-03-29
forum: Networking &amp; Wireless
---

### Post by Ross1234 on 2009-03-29
Hi :)

I have my destop connected to the internet and it is assigned its ip address from DHCP.

I have set up a wireless ad hoc network to my ipod touch and laptop.

I want to share my internet connection with my ipod touch and laptop. Can I do this and not have my desktops IP changed to a static IP on the internet connection like what happens in windows?

Thanks Ross

---

### Post by Ross1234 on 2009-03-29
Any idea how to do this?

---

### Post by BkkBonanza on 2009-03-29
I think what you want is here,

[https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless](https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless)

Just use the search field at the top of this page...

---

### Post by Ross1234 on 2009-03-29
Thanks, that looks right. trying it now. Sorry for not searching properly im new and I didnt see the search and didnt know what to type in.

---

### Post by Iowan on 2009-03-29
[Here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") is a help page.  Near the end is a link for [wireless]("https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless").  I guess I'm not sure if it changes address to static, though.

Looks like my typing is slow, again...

---

### Post by Ross1234 on 2009-03-29
OK, I treied the tutorial and it didnt work. I think its because my eth0 ip is assigned by DHCP and i cant use a static one.

It goes as stuff like 134.36.69.226

Any ideas?

---

### Post by Ross1234 on 2009-03-30
Please help!!!

i finally got it working, but im not sure how!

Can you tell me how I save all my network settings so I can replicate them when I restart my computer?

I think I will lose all these settings when I restart it.

---

### Post by Iowan on 2009-03-30
Network Manager stores its settings in */etc/NetworkManager/nm-system-settings.conf*.  You can see what it has there.

---

