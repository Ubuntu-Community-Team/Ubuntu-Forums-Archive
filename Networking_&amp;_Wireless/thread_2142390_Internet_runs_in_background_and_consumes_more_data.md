---
title: "Internet runs in background and consumes more data"
date: 2013-05-05
forum: Networking &amp; Wireless
---

### Post by Boonleigh on 2013-05-05
Recently i upgraded to Ubuntu 13.04. I've got a serious issue with my internet connection. Whenever I turn on my modem, data starts downloading even before i could open any of my browsers/ chat applications (I realised this using bandwidth monitor- BMON). More than 20Mb gets downloaded everytime I turn on my PC#-o. Since I'm using a limited internet usage plan, I find it annoying to lose more than 60mb everyday. Kindly help me fix this issue. I have changed my settings so as not to check for updates everyday. even then, the data loses somewhere and somehow.:confused: Help me...

---

### Post by Hadaka on 2013-05-05
Hi, if you just want to use the internet when you
want,and not have it connect on boot up.
simply click the connection icon...upper right
next to the enevlope..then uncheck ..Enable _N_etworking
then when you want internet use  check ..Enable _N_etworking
*Remember to uncheck before you shutdown.
good luck !

---

### Post by Boonleigh on 2013-05-05
I tried that too. Even if i enable networking just whenever i needed to browse, the data starts downloading in background while i browse... Help me to stop this background internet usage problem...

---

### Post by papibe on 2013-05-05
Hi Boonleigh.

The 'Software Updater' usually runs in the background to download the recent sources (equivalent of 'sudo apt-get update').

To set your own schedule or disable it, open 'Software Sources', and go to the 'Update' tab.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by varunendra on 2013-05-06
You can use 'nethogs' command to see which process is using the bandwidth. But you'll have to install it first :
```
sudo apt-get install nethogs
```

Once installed, you can run it anytime on a desired interface as root. For example, if your network interface in use is eth0, then-
```
sudo nethogs eth0
```

If it is a USB modem, the interface is usually ppp0, just replace eth0 with that or whatever is the name of the interface in use.

There is a native lightweight program to monitor the app/process consuming the bandwidth, but I don't remember it (saw once in a post of moderator oldos2er).

Once the culprit process is identified, we can suggest more precise ways to control it.

---

