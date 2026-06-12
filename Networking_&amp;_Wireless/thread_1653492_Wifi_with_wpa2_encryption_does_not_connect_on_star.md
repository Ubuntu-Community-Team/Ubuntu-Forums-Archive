---
title: "Wifi with wpa2 encryption does not connect on startup"
date: 2010-12-26
forum: Networking &amp; Wireless
---

### Post by Alex.onub on 2010-12-26
Hi! I have xbmc, a media center shell that runs on ubuntu. I am trying to set up a laptop to run it and be a full time media center. so far it works great, I installed xbmc live, but the only issue is I have a wep2 protected wireless router and the wifi does not connect automatically.  I have it set up and am using wpa_supplicant. every time I reboot I have to exit the shell to the command line and run    ```
 sudo wpa_supplicant -B -Dwext -iwlan0 -c /etc/wpa_supplicant.conf 
```    the conf file has the essid and key for my network, as per the specifications. after that I must reset the network adapter with:    ```
 sudo /etc/init.d/networking restart 
```    once those commands are run the wifi works great.    I am a novice in linux in general, and can not seem to get this to work on startup,  can anyone point me in the right direction on this?  I haven't been able to find the xbmc start up script if one exists, I figured adding those lines to it might work,does this sound like a reasonable approach? if anyone knows where that is and how it is defined to be launched on start-up i would appreciate it(I guess this is getting into the general Linux knowledge but still good info)    thanks very much

---

### Post by grahammechanical on 2010-12-27
Is there an XBMC web site? Does it have a frequently asked questions (FAQ) section?

I am running Gnome. I do not know what menus and options you get with XBMC. Do you get any indication that networking is activated? Is there some kind of network icon as in Gnome?  If so, and clicking left and right gives you options, then select Edit Connections. Choose your wireless connection and set it to Automatically Connect.

If, on the other hand, there is the menu option such as System, then go to Administration and select Network tools. Select your network device and click Configure and you will get the same choices as under Edit connections in the previous paragraph.

Not knowing what the desktop looks like in XBMC makes it difficult to direct you.

Regards.

---

### Post by Alex.onub on 2010-12-27
I was actually a little annoyed with XBMC options, it is very limited in terms of hardware setup.   On the bright side, it really gave me a good opportunity to learn some command line linux hardware setup. so no loss, its more for my own purposes now. xbmc is just a shell on top of ubuntu, which to my understanding so is the gnome desktop so their should be a way to set it up to automatically set this up on startup.

---

