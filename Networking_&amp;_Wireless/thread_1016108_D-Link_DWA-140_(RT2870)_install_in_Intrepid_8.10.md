---
title: "D-Link DWA-140 (RT2870) install in Intrepid 8.10"
date: 2008-12-19
forum: Networking &amp; Wireless
---

### Post by mpadams on 2008-12-19
The following will get the DWA-140 working here in the US with most routers, using the Network-Manager in GNOME.

1. Check **[http://www.ralinktech.com/ralink/Home/Support/Linux.htm]("http://www.ralinktech.com/ralink/Home/Support/Linux.htm")** for the latest RT2870USB driver.
2. Open up a Terminal and "sudo bash"
3. "apt-get update && apt-get -y install build-essential wpasupplicant"
4. "cd /usr/src"
5. Copy the link for the latest RaLink driver and do a "wget" with it. Example: "wget http://www.ralinktech.com.tw/data/drivers/2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.bz2"
6. Extract the driver. Example: "tar -xvf 2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.bz2"
7. Change to the new directory. Example: "cd 2008_0925_RT2870_Linux_STA_v1.4.0.0"
8. "gedit RT2870STA.DAT &" and change the first 12 lines to the following if you're in the United States...

CountryRegion=0
CountryRegionABand=0
CountryCode=US
ChannelGeography=1
SSID=
NetworkType=Infra
WirelessMode=5
Channel=11
BeaconPeriod=100
TxPower=100
BGProtection=0
TxPreamble=2

9. "gedit os/linux/config.mk &" and change all the "=n" to "=y"
10. "make && make install"
11. "gedit /etc/modules &" and add "rt2870sta" to the list.
12. Close the Terminal, then try plugging in the device and see if its detected: reboot if it doesn't come up.

*. Development source post
**[http://ubuntuforums.org/showthread.php?t=919044&highlight=rt2870&page=3]("http://ubuntuforums.org/showthread.php?t=919044&highlight=rt2870&page=3")**
*. List of wireless channels (used with the README_STA to determine proper channel lists)
**[http://en.wikipedia.org/wiki/List_of_WLAN_channels]("http://en.wikipedia.org/wiki/List_of_WLAN_channels")**

---

### Post by pmow on 2009-03-13
You just saved my day.  Thank you!  I'm using a Rosewill RNX-EasyN1 which is based on this chip, and your instructions have it working perfect (with WPA2).

---

### Post by Sportdeck on 2009-03-19
After trying several other dwa-160 install procedures and solutions, I tried this procedure as it is loading the same RT2870 driver that the 160 uses.  This worked the first time!!!! 

There were NO vague steps where I had to guess what to do, because the original poster was writing from a position of assumed knowledge on my part.  I've used Ubuntu since 5.04, and have grown to love it, but when new/updated software won't install through the package manager, most install instructions leave a lot to be desired and assumed.

Thanks mpadams for a great post.

---

### Post by shuukazedojo on 2009-04-12
Hey all. I was hoping this would be the answer to my problem, but no luck. I noticed that the channel is set to 11 here and on the print out for the router settings it says 4. Would this make a difference? Should I change the RT2870STA.DAT file to reflect the same channel?

Also, is this orange light supposed to come on when the adapter is plugged in to the USB? Mine is not coming on, which may also be the issue :). 

Thanks for the help!

Oh, if it matters, the router is connected to a Vista box and the adapter is connected to a dual boot XP/Intrepid box. Both are desktops. The dual boot with the adapter also has the PCI networking card. Does this make a difference? THANKS AGAIN!!!

EDIT: I just had a thought! (see the smoke?) I'm trying to use the router on the Vista box and the adapter on the Ubuntu box. What if I reversed that? Has anyone used the D-Link DIR-625 wireless router with success through Ubuntu? It may be easier to get the router to work through Linux than the Adapter. Also, D-Link provides *some* documentation for Linux for this router. I wanted to know if anyone has done this before I go purchase a long ethernet cable. Anyone?

---

### Post by shuukazedojo on 2009-04-16
Well, I have to say, this was the first time I posted on here and didn't hear back from anyone. 

It all worked out. I decided I was thinking about this the wrong way. Why in the world would I expect Vista to be able to run the router and have Ubuntu run the USB adapter, especially when the adapter isn't "Linux supported"? Well, I switched it and it works perfectly! I have the router connected to the Ubuntu box and the adapter hooked to the Vista box. I'm not at all surprised that Ubuntu auto detected the connection either! Awesome stuff!!!

---

### Post by lessfield on 2009-04-25
great post, thanks
work for RNX-N1 w/ newest driver 
[http://www.ralinktech.com.tw/data/drivers/2009_0424_RT2870_Linux_STA_V2.1.1.0.tgz]("http://www.ralinktech.com.tw/data/drivers/2009_0424_RT2870_Linux_STA_V2.1.1.0.tgz")

---

### Post by xjjjay on 2009-05-19
I'm running Linux Mint 6 (based off Intrepid) and I can't seem to get my RNX-EasyN1 to work. I've followed the directions step by step and encountered no errors, but it won't detect the adapter. The adapter is functional and the led comes on once plugged in. I used the latest RT2870USB driver.

Please let me know if there is any other information I need to include! Thanks

---

### Post by itsjareds on 2009-08-01
Using a Rosewill RNX-EasyN1. I'm in the same boat as xjjjay, I followed the tut step by step and I didn't get any detection. I rebooted and still no detection. I do get the LED to light up meaning it is plugged in, but I run "iwlist scan" and don't see any wireless interfaces there.

I was using Wicd before and uninstalled that for NetworkManager, but now I don't seem to have the nm-applet installed.

Does anybody know if something has changed? Thanks.

====
edit: Ok, I can get a scan through ra0 with "iwlist scan", but only without restarting after installing the driver. After I restart, I can't get that interface to even start. I did get connected to my router once, but I couldn't access the Internet for some reason on Firefox. I was able to successfully ping google.com. Now I've restarted, uninstalled the driver, then installed the version lessfield posted, and now when I try to connect, I get stuck at "Obtaining IP Address...". I'm using Wicd.

Help?

---

### Post by sdenovan on 2009-08-28
I recently purchased a couple of Rosewill RNX-EasyN1 devices and found that the chipset has changed. If you have followed these instructions unsuccessfully, your device may have the rt3070 chipset. Try the latest RT3070USB drivers:

[http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

---

### Post by one2bet on 2010-02-21
[SIZE=3]:oThese installation instructions worked perfectly in[/SIZE][SIZE=3] [SIZE=3]Ubuntu 9.10 (Karmic Koala) for my Rosewill RNX-N1 Wireless N USB adapter too. And that ain't just a swiss cheese.:o[/SIZE][COLOR=Black][URL="http://www.newegg.com/Product/Product.aspx?Item=N82E16833166025"]
[/URL][/COLOR][/SIZE]

---

### Post by dee27 on 2010-06-28
I just found your Thread on the RT2870 linux driver.  I followed your instructions, and they worked just fine using a RNX-N1 on my two 64 bit ubuntu 10.04 machines, but my 32 bit machine also running Ubuntu 10.04 will not even light the RNX-N1 led's when its plugged in.

Any ideas?

Dee

---

