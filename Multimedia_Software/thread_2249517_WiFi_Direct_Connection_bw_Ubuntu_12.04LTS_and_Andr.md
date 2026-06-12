---
title: "WiFi Direct Connection b/w Ubuntu 12.04LTS and Android Tablet?"
date: 2014-10-22
forum: Multimedia Software
---

### Post by ben115 on 2014-10-22
Has anyone done this?

I can't seem to find any examples on how to.

I have wifi direct working on my Ubuntu 12.04LTS laptop and can issue p2p commands just fine.  I can also connect 2 Android devices via WiFi Direct.  I can see the Android device from my laptop and I can see my laptop from the Android device.  However, I am not able to get a connection setup.  

Does anyone have experience with this?

Thanks,
Ben

---

### Post by Vladlenin5000 on 2014-10-24
What are you trying to achieve exactly?

---

### Post by ben115 on 2014-10-24
I want to be able to setup a connection between the two using just my wifi card (without adding a router or anything in the mix) so I can connect over vnc.  I don't want to use ad-hoc because most Androids require you to root your device to do this.

---

### Post by Vladlenin5000 on 2014-10-24
Well, in my book, that's *ad hoc*. If you're thinking about a different service, please elaborate.

---

### Post by ben115 on 2014-10-24
> **Vladlenin5000 said:**
> Well, in my book, that's *ad hoc*. If you're thinking about a different service, please elaborate.

Here's the wiki definition of WiFi-Direct: [http://en.wikipedia.org/wiki/Wi-Fi_Direct](http://en.wikipedia.org/wiki/Wi-Fi_Direct)

Here's some info on how to configure it with p2p commands: [http://processors.wiki.ti.com/index.php/OMAP_Wireless_Connectivity_NLCP_WiFi_Direct_Configuration_Scripts](http://processors.wiki.ti.com/index.php/OMAP_Wireless_Connectivity_NLCP_WiFi_Direct_Configuration_Scripts)

-Ben

---

### Post by Vladlenin5000 on 2014-10-24
You need a VNC server in the laptop and a VNC client in the Android phone.

---

### Post by ben115 on 2014-10-25
> **Vladlenin5000 said:**
> You need a VNC server in the laptop and a VNC client in the Android phone.

Right.  I'm using x11vnc as the VNC server on the laptop and bVNC as the VNC client on the Android.  And when I have them both connected to the same wifi network, I have no problem.  The only thing is, I want to be able to take this on the go, so I need to be able to connect without a router.  That pretty much leaves me two options (from what I know to be available): ad-hoc and wifi-direct.  Ad-hoc would do the job, but I'd rather not have to root my android.  This leaves me to wifi-direct.  It looks very promising and there is a lot of documentation on how to implement it online.  It's just that I haven't had any success in setting it up.

---

