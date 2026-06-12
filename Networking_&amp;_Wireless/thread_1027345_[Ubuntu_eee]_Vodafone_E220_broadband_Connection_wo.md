---
title: "[Ubuntu eee] Vodafone E220 broadband Connection won't connect"
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by ilago on 2009-01-01
I've installed Ubuntu Eee on my EEE PC 701. Installation, including a massive upgrade, was flawless. The only problem I have is getting an option for mobile broadband in Network Settings. My Huawei E220 USB is recognised because it's been included in the kernel for a while now. The Network Settings console doesn't give me an option for mobile broadband. The default Xandros installation was easy to set up. This is the first time I've used an Ubuntu distro. I usually run Mepis or opensuse on my desktops.

Any help to get this set up would be greatly appreciated. I'm setting it up for a little kid to use as well as me.

I read all of this thread
[http://ubuntuforums.org/showthread.php?t=879683&highlight=mobile+E200](http://ubuntuforums.org/showthread.php?t=879683&highlight=mobile+E200)

As recommended I downloaded the two Vodafone packages for the Netbook remix from [https://forge.betavine.net/frs/?group_id=12](https://forge.betavine.net/frs/?group_id=12) 

The USB Modeswitch package seems relevant to the E220
These are the packages
usb-modeswitch_0.9.4-1_i386.deb	
vodafone-mobile-connect_1.99.17-8_all.deb

This is the install text
```
VODAFONE MOBILE CONNECT INSTALLATION INSTRUCTIONS.

-------------------------------------------------


* You need a previously working internet connection (e.g: your ethernet one)

* Download from this page these two DEB packages:

     - usb-modeswitch
     - vodafone-mobile-connect

* Install them, e.g: in a terminal command line (substitute the version and architecture here for the ones you have downloaded)

     sudo dpkg -i usb-modeswitch_0.9.4-1_i386.deb
     sudo dpkg -i vodafone-mobile-connect_1.99.17-8_all.deb

* After this step, you will possibly have unresolved dependencies problems. To solve them execute:

     sudo apt-get -f install  

* If everything has gone fine you can plug in the modem, and execute the driver with:

     vodafone-mobile-connect-card-driver-for-linux

```

It seems I have to use apt-get from the command line even these are .deb packages and it seems there may be dependencies 

I can't find a way to open wvdial.conf to view the file in the Text Editor. Or even open the nautilus with superuser privileges. I'm just not familiar with Gnome or Ubuntu I'm afraid.

---

### Post by Hobgoblin on 2009-01-01
You should need to do no more than install Ubuntu then plug in the USB modem, you should be prompted for the rest.

After that you just click on the network manager icon and select the relevant connection.

---

### Post by ilago on 2009-01-01
> **Hobgoblin said:**
> You should need to do no more than install Ubuntu then plug in the USB modem, you should be prompted for the rest.

After that you just click on the network manager icon and select the relevant connection.

I've been using mobile broadband with this modem for some time. I'm not new to linux just Ubuntu. The connection works on OS X, XP and the default EEE Xandros installation. The Huawei E220 has been recognised by linux for some time.  

There is no Mobile Broadband option in Network Manager. That may be because Ubuntu eee only includes Network Manager 0.6.? rather than 0.7. I'm not sure which repos I need to enable to install that. The Vodafone software doesn't seem to work either. I'll remove that and reinstall it.

I'm posting in the Ubuntu forum because it seems to be a distro specific problem.

---

### Post by jsenlai on 2009-01-18
Never use Netbook Remix in a netbook. But I'm using E220 as well for my broadband connection.

I think it's better to use the Network Manager to connect to your 3G. I'm using Network Manager 0.7 in Ubuntu 8.10 Intrepid Ibex. The NM will automatically detect the card. 

Note: I've found something odd when I use VMC in firestarter block list. Which I am going to discuss and find out more about it in other forum. :neutral:

J'sen

---

