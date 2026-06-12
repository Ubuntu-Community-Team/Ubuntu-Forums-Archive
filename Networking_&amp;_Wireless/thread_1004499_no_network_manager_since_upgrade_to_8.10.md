---
title: "no network manager since upgrade to 8.10?"
date: 2008-12-07
forum: Networking &amp; Wireless
---

### Post by HarmonicaGoldfish on 2008-12-07
My laptop (Dell Inspiron 1525) is connecting to the Internet. The problem is that once in a while it disconnects and I can not seem to figure out how to reconnect without restarting the computer. 

With 8.04 I just opened up the network manager and was able to reconnect without re-boot. With 8.10 I do not seem to have a network manager, I have a network monitor but all that does is tell me the status.

I had this same issue when I tried the beta version of 8.10. I eventually returned to 8.04 and decided to wait for the stable version. I re-upgraded to 8.10 yesterday (and then blended it with Ubuntu Studio 8.10).

I looked at the 8.10 documentation for wireless and found this:
[https://help.ubuntu.com/8.10/internet/C/wireless-connecting.html](https://help.ubuntu.com/8.10/internet/C/wireless-connecting.html)


> Network Manager (System &#8594; Administration &#8594; Network) supports Roaming mode. This allows you to connect to any available wireless network in range.

   1.

      In the Taskbar click the Network Manager icon.
   2.

      Select your wireless network from the list.
   3.

      Enter your Network Key.
   4.

      Click Connect.

Connecting to a hidden network

   1.

      Left click the Network Manager icon in the system tray.
   2.

      ClickConnect to Hidden Wireless Network
   3.

      In the network name text box enter the ESSID you are connecting to.
   4.

      Select the type of security used from the drop down list.
   5.

      Click Connect.

The thing is, I do not have anything called Network under System --> Administration. I have something called Network Tools, but that doesn't look anything like Network Manager.

Is there a way for me to add Network Manager to my system?

---

### Post by beyboo on 2008-12-07
8.10 has this new nm-applet. Trying running it from a terminal. see the outputl

Also since you have upgraded from 8.04, here is something i did to resolve something very similar. 

nm-applet does not seem to like any changes to the /etc/network/interfaces file other than these default lines 

> auto lo
iface lo inet loopback


Also nm-applet seems much happier without a resolv.conf file defining nameserver entries. 

Apparently since 8.10, you have nm-applet - the new network manager which allows you to create multiple configuration profiles. Then you just click on the profile you want to use and it activates it on the fly. 

So far has worked brilliantly for me.

Try backing up details about ur eth0 and any other interaces you may have configured, note the resolv.conf settings and try giving the nm-applet a try. you will see a default "Auto" setting. Prefer creating a new config profile.

---

### Post by HarmonicaGoldfish on 2008-12-07
thanks for your response. Here is the result:

```
tracy@tracy-laptop:~$ nm-applet

** (nm-applet:13295): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:13295): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
tracy@tracy-laptop:~$ 

```

---

### Post by iponeverything on 2008-12-07
try:

```

sudo killall -v nm-applet
sudo nm-applet

```

---

### Post by HarmonicaGoldfish on 2008-12-07
what will that do?

at the moment, my wireless is connecting. I do not want to stop that. However I would like to figure out how to run the network manager and have an icon in my system tray to easily troubleshoot when need be.

---

### Post by Bronto on 2008-12-07
```
$ sudo service NetworkManager restart
```

---

### Post by beyboo on 2008-12-09
> **HarmonicaGoldfish said:**
> thanks for your response. Here is the result:

```
tracy@tracy-laptop:~$ nm-applet

** (nm-applet:13295): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:13295): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
tracy@tracy-laptop:~$ 

```

This is the same message I used to get with an ifconfig file poulated with entries other than the ones I mention. Once I cleaned up ifconfig and resolv.conf  my problem was solved 

Try running System > Preferences > Network configuration. If you see anything other than Auto eth0, thats the problem. Apparently if nm-applet senses anything other than the default, it loads it as an entry other than auto eth0 and activates it.

Edit : A point I miss here, you have wireless, so obviously there is an entry in the wireless conf files. I have no wireless so cant comment much. Sorry !!

---

### Post by HarmonicaGoldfish on 2008-12-11
I tried the NetworkManager restart command. I got an icon in my system tray that showed it was not connected to the internet (little red x), though the network monitor showed it was (and, the computer was indeed connected).

When I click on the icon I get to the nm-applet and have NO idea what to do with it. There is nothing indicated under wireless, as if nothing has been configured. I have no way of knowing if I am even connected to my own wireless connection or my neighbours! I still get the problem that the internet connection fails and I have to restart the computer in order to get it back.

Kind of sucks, eh? How can I fix this? 

I knew how to configure the old network manager on 8.04. I seem to need a tutorial to figure out this new applet. It is very frustrating.

---

### Post by HarmonicaGoldfish on 2008-12-11
> **beyboo said:**
> This is the same message I used to get with an ifconfig file poulated with entries other than the ones I mention. Once I cleaned up ifconfig and resolv.conf  my problem was solved 

Try running System > Preferences > Network configuration. If you see anything other than Auto eth0, thats the problem. Apparently if nm-applet senses anything other than the default, it loads it as an entry other than auto eth0 and activates it.

Edit : A point I miss here, you have wireless, so obviously there is an entry in the wireless conf files. I have no wireless so cant comment much. Sorry !!

There is no entry in wireless...

---

