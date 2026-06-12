---
title: "Ubuntu 9.10 64bit Wireless B43 works with auto DHCP but not WEP security"
date: 2010-02-27
forum: Networking &amp; Wireless
---

### Post by Rayskee80 on 2010-02-27
I have a Funny problem going on with my wireless. I just switched over from Fedora 12 to Ubuntu 9.10. Never had a problem with the Broadcom B43 driver working with a WEP security key enabled in Fedora. 

For some reason if I turn on the WEP security in my router using Ubuntu it will only stay connected for about 10 to 30 seconds then disconnect. Sometimes it will reconnect and sometimes it will ask me for the WEP password again. It's completely random though every time and will never stay connected long enough to be productive. 

If I go back into my router setting and turn off the WEP security and just let DHCP auto assign then I never have a problem, it never disconnects. 

Thanks for any help anybody can give me!

---

### Post by pastalavista on 2010-02-27
You could try setting up the router with WPA or WPA2 security which is stronger anyway or it could be you don't have the right drivers installed for your card.

Check out this page: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")

Another option I've heard works sometimes is to install wicd to replace the gnome network manager. Some say it will work when Ubuntu's default nm-applet won't.

---

### Post by Rayskee80 on 2010-02-27
> **pastalavista said:**
> You could try setting up the router with WPA or WPA2 security which is stronger anyway or it could be you don't have the right drivers installed for your card.

Check out this page: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Another option I've heard works sometimes is to install wicd to replace the gnome network manager. Some say it will work when Ubuntu's default nm-applet won't.

Thanks!!! That was a real easy fix switched to WPA2 and all is perfect!

---

