---
title: "Wireless problems! No ndiswrapper or b43-fwcutter!"
date: 2012-09-03
forum: Networking &amp; Wireless
---

### Post by jkasai on 2012-09-03
Hello!

I'm refurbishing a Dell Inspiron 1501, and have just  changed the orginial harddrive to a Hitachi Travelstar 500GB, and  installed Ubuntu 12.04 LTS onto it.

Unfortunately though, I'm not getting any Network Connections...
Networking is enabled, "Connection information" is unavailable and no connections are given in "Edit Connections".

Thinking  it might be a problem with the PCI card (Card/Model: BCM4311 and  PCI-ID: [14e4:4311] ) I connected a USB Wireless Adapter (which is a  Netgear one... Terminal says: "ID0846:9020 Netgear, Inc. WNA 3100 (v1)  Wireless-N300 [BroadcomBCM43241])...Seems that's not doing anything at  all either... :"(

I've looked at the following links for some help:
[http://ubuntuforums.org/showthread.php?t=889395](http://ubuntuforums.org/showthread.php?t=889395)
[http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/](http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/)
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
but to no avail.
Mind you, I might just be doing it all wrong...Still quite the rookie. :S Sorry.

But the laptop is telling me that both ndiswrapper and b43-fwcutter doesn't exist...
 
So I'm totally stuck on what to do...

I'm very sorry for jabbering on but I would really really truly love it if you could please please please help me!! :)

Thank you very much in advance!

M

---

### Post by chili555 on 2012-09-03
Set that USB aside and let's see if we can get the Broadcom built-in to come to life. Walk over to the router, hook up the ethernet and get a connection. Open a terminal and type:```
sudo apt-get install linux-firmware-nonfree
```Detach the ethernet, reboot and post back to tell us how the wireless is working.

---

### Post by jkasai on 2012-09-03
> **chili555 said:**
> Set that USB aside and let's see if we can get the Broadcom built-in to come to life. Walk over to the router, hook up the ethernet and get a connection. Open a terminal and type:```
sudo apt-get install linux-firmware-nonfree
```Detach the ethernet, reboot and post back to tell us how the wireless is working.

Hello chili555!!

Thank you for your reply!! 
I really really appreciate it! :)

I connected the ethernet cable to the laptop but it seems that the laptop still isn't connecting to the internet... :"(
"Wired network disconnected - you are now offline" keeps popping up too...

---

### Post by chili555 on 2012-09-03
Let's get the wireless going first, then we'll fix the ethernet. Download the file I've attached and transfer it to the desktop of the Ubuntu machine on a USB key or similar. Right-click it and select Extract Here. Now open the terminal and do:```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo modprobe -r b43
sudo modprobe b43
```Your wireless should now be working.

---

### Post by jkasai on 2012-09-03
Hi chili555,

Thank you for your help and support again! :)
Unfortunately, after 

> **chili555 said:**
> 
sudo cp Desktop/b43/*  /lib/firmware/b43 

I get:

cp: cannot stat 'Desktop/b43/*' : No such file or directory

---

### Post by jkasai on 2012-09-03
Put the extracted file onto desktop!
Worked!
Worked!!!

WOOHOOOO!!!
THANK YOU SO SO MUCH CHILI555

You're THE Saint! :D

Thank you so so much again!

Do I need to save anything, etc. to make sure this is permanent?

---

### Post by chili555 on 2012-09-03
> Do I need to save anything, etc. to make sure this is permanent?Nope. You are all set. As long as the wireless is working, do we need to work on ethernet or is it not needed?

Please use thread tools at the top to mark Solved.

---

### Post by jkasai on 2012-09-03
Sorry for bugging you again!
Just a few more questions!

Do I need to keep the b43 extracted file in a specific location?
Will ethernet connection work now too?

Thank you so so very much again! :D

---

### Post by chili555 on 2012-09-03
> Do I need to keep the b43 extracted file in a specific location?Trash it and the zip, too.> Will ethernet connection work now too?Not until we troubleshoot it. If you'd like to proceed, please post:```
lspci -nn | grep 0280
dmesg | grep eth0
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

Just to be sure you always get the latest and greatest firmware, you should do:```
sudo apt-get install linux-firmware-nonfree
```

---

### Post by jkasai on 2012-09-03
Chili555,

Terminal says
"Setting up linux-firmware-nonfree (1.11ubuntu1)...
~$ "

Do I need to type or do anything more to complete set up?

Thank you!

---

### Post by chili555 on 2012-09-03
> **jkasai said:**
> Chili555,

Terminal says
"Setting up linux-firmware-nonfree (1.11ubuntu1)...
~$ "

Do I need to type or do anything more to complete set up?

Thank you!It's all done!

---

### Post by jkasai on 2012-09-03
Chili555,

I just tried the ethernet and it doesn't seem to work...
I unplugged the ethernet, hoping to get back to a wireless environment but now the wifi isn't working anymore either...
Just went through the steps using b43 and it's working now...
Will I need to go through those steps each time I alternate between ethernet and wifi?

I'm really sorry for the trouble caused... >_<

---

### Post by jkasai on 2012-09-03
Seems the Wifi doesn't want to work anymore either... :"(

Edit: seems it now is... :S!

Edit 2: Sorry for the confusion, the ethernet still isn't...

---

### Post by chili555 on 2012-09-03
> **jkasai said:**
> Seems the Wifi doesn't want to work anymore either... :"(

Edit: seems it now is... :S!

Edit 2: Sorry for the confusion, the ethernet still isn't...In post #9 I said:> 
[QUOTE]Will ethernet connection work now too?
Not until we troubleshoot it. If you'd like to proceed, please post:
```
lspci -nn | grep 0280
dmesg | grep eth0

```
[/QUOTE]Please post using your nifty new wireless!

---

### Post by jkasai on 2012-09-03
Hi Chili555,

I'm sorry for the late reply.

By "post" did you mean in Terminal?
Sorry...

The wireless also stops working each time I restart the laptop...

M

---

### Post by jkasai on 2012-09-03
The wireless won't connect to my router anymore either... X"(

Please help!

---

### Post by chili555 on 2012-09-03
When it is not running, please check to see if the driver is actually loaded:```
lsmod | grep b43
```If b43 does not appear, as I suspect, let's load it:```
sudo modprobe b43
```Does your wireless spring to life? If so, we can fix it easily.> By "post" did you mean in Terminal?
Sorry...Yes, I meant run this command in the terminal and copy and paste the result from the terminal to your reply here:```
lspci -nn | grep 02[COLOR="Red"]0[/COLOR]0  [COLOR="Red"]<--I made a typo in my original request; sorry.[/COLOR]
```Then run and post this one, too:```
dmesg | grep eth0
```Thanks.

---

### Post by jkasai on 2012-09-03
The wireless isn't coming to life :"(

after I type lsmod&#65372;grep b43,

I get:

b43           342643    0
mac80322  436455   1 b43
cfg80211    187679   2 b43, mac80211
bcma         25651     1 b43
ssb            50691     2 b43, b44

---

### Post by chili555 on 2012-09-03
Looks perfect! Let's dig deeper. Please run and post:```
dmesg | grep wlan
```Thanks.

---

### Post by jkasai on 2012-09-03
Hello!!


Thank you so much for baring with me chili555!

I really, really appreciate it.


I get the following:



[ 1876.836190] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 3/3)
    [ 1877.036176] wlan0: direct probe to 02:23:4e:a5:86:d2 timed out
    [ 2007.444142] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2007.644093] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2007.844084] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2008.044086] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2014.308137] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2014.508095] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2014.708119] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2014.710662] wlan0: direct probe responded
    [ 2014.710703] wlan0: authenticate with 00:23:4e:a5:86:d1 (try 1)
    [ 2014.721769] wlan0: authenticated
    [ 2014.744165] wlan0: associate with 00:23:4e:a5:86:d1 (try 1)
    [ 2014.944059] wlan0: associate with 00:23:4e:a5:86:d1 (try 2)
    [ 2015.144131] wlan0: associate with 00:23:4e:a5:86:d1 (try 3)
    [ 2015.344112] wlan0: association with 00:23:4e:a5:86:d1 timed out
    [ 2021.620131] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2021.820040] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2022.020069] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2022.220107] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2028.480127] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2028.680099] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2028.880095] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2029.080084] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2035.344137] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2035.544147] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2035.744063] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2035.944070] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2042.204210] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2042.404092] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2042.604093] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2042.804089] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2055.276153] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2055.476122] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2055.676145] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2055.876091] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2062.160164] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2062.360174] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2062.560174] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2062.760085] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2190.288171] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 1/3)
    [ 2190.488091] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 2/3)
    [ 2190.688091] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 3/3)
    [ 2190.888129] wlan0: direct probe to 02:23:4e:a5:86:d2 timed out
    [ 2197.148143] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 1/3)
    [ 2197.150181] wlan0: direct probe responded
    [ 2197.150221] wlan0: authenticate with 02:23:4e:a5:86:d2 (try 1)
    [ 2197.158101] wlan0: authenticated
    [ 2197.180137] wlan0: associate with 02:23:4e:a5:86:d2 (try 1)
    [ 2197.184707] wlan0: RX AssocResp from 02:23:4e:a5:86:d2 (capab=0x401 status=0 aid=1)
    [ 2197.184720] wlan0: associated
    [ 2197.186114] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
    [ 2208.224116] wlan0: no IPv6 routers present
    [ 2255.300298] wlan0: deauthenticated from 02:23:4e:a5:86:d2 (Reason: 7)
    [ 2256.667774] wlan0: authenticate with 02:23:4e:a5:86:d2 (try 1)
    [ 2256.864135] wlan0: authenticate with 02:23:4e:a5:86:d2 (try 2)
    [ 2257.064155] wlan0: authenticate with 02:23:4e:a5:86:d2 (try 3)
    [ 2257.264141] wlan0: authentication with 02:23:4e:a5:86:d2 timed out
    [ 2263.520430] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 1/3)
    [ 2263.720143] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 2/3)
    [ 2263.920132] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 3/3)
    [ 2264.120126] wlan0: direct probe to 02:23:4e:a5:86:d2 timed out
    [ 2270.371665] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 1/3)
    [ 2270.568175] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 2/3)
    [ 2270.768171] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 3/3)
    [ 2270.772889] wlan0: direct probe responded
    [ 2270.772918] wlan0: authenticate with 02:23:4e:a5:86:d2 (try 1)
    [ 2270.972114] wlan0: authenticate with 02:23:4e:a5:86:d2 (try 2)
    [ 2271.060548] ADDRCONF(NETDEV_UP): wlan0: link is not ready
    [ 2271.172142] wlan0: authenticate with 02:23:4e:a5:86:d2 (try 3)
    [ 2271.372058] wlan0: authentication with 02:23:4e:a5:86:d2 timed out
    [ 2273.233210] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 1/3)
    [ 2273.432093] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 2/3)
    [ 2273.632051] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 3/3)
    [ 2273.832146] wlan0: direct probe to 02:23:4e:a5:86:d2 timed out
    [ 2280.099783] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2280.296341] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2280.496102] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2280.696104] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2286.940236] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2287.140127] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2287.340090] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2287.540099] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2293.800443] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2294.000240] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2294.200504] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2294.400136] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2300.656154] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2300.856140] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2301.056137] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2301.256163] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2307.504209] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2307.704149] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2307.904148] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2308.104143] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2314.348447] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2314.548186] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2314.748147] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2314.948180] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2321.196463] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2321.396140] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2321.596189] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2321.796160] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2328.052455] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2328.252180] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2328.452181] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2328.652178] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2334.888405] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2335.088184] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2335.288171] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2335.290683] wlan0: direct probe responded
    [ 2335.290713] wlan0: authenticate with 00:23:4e:a5:86:d1 (try 1)
    [ 2335.488176] wlan0: authenticate with 00:23:4e:a5:86:d1 (try 2)
    [ 2335.688058] wlan0: authenticate with 00:23:4e:a5:86:d1 (try 3)
    [ 2335.888053] wlan0: authentication with 00:23:4e:a5:86:d1 timed out
    [ 2344.224417] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2344.424101] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2344.624156] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2344.824116] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2351.064318] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2351.264061] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2351.464093] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2351.664055] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2357.920315] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2358.120176] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2358.320132] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2358.520168] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2364.780941] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2364.980143] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2365.180172] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2365.380166] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2371.645938] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2371.844099] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2372.044086] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2372.244088] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2378.476631] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2378.676177] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2378.876185] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2379.076179] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2385.312400] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2385.512087] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2385.712075] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2385.912844] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2392.176182] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2392.376097] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2392.576089] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2392.776087] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2399.040157] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2399.240127] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2399.440095] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2399.640124] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2480.316459] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2480.516107] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2480.716068] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2480.916107] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2487.152770] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2487.352172] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2487.552138] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2487.752160] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2494.008940] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2494.208103] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2494.408092] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2494.608328] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2500.889434] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2501.088125] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2501.288054] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2501.488091] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2507.736236] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2507.936097] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2508.136094] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2508.336088] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2514.588185] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2514.788110] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2514.988195] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2515.188090] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2521.436228] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2521.636076] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2521.836080] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2522.036082] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2528.271592] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2528.468059] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2528.668092] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2528.868097] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2535.120399] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2535.320097] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2535.520094] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2535.720108] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2578.552152] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2578.752049] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2578.952091] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2579.152049] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2585.400145] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2585.600063] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2585.800085] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2586.000297] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2592.248163] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2592.448092] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2592.648102] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2592.848094] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2599.096235] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2599.296055] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2599.496053] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2599.696056] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2605.963969] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2606.164099] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2606.364158] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2606.564103] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2612.800380] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2613.000265] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2613.200042] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2613.400087] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2619.648429] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2619.848050] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2620.048119] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2620.248088] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2626.507894] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2626.704112] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2626.904095] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2627.104088] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2633.374339] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2633.572058] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2633.772121] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2633.972125] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2641.295565] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 1/3)
    [ 2641.492104] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 2/3)
    [ 2641.692042] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 3/3)
    [ 2641.892089] wlan0: direct probe to 02:23:4e:a5:86:d2 timed out
    [ 2648.141345] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 1/3)
    [ 2648.340104] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 2/3)
    [ 2648.540042] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 3/3)
    [ 2648.740049] wlan0: direct probe to 02:23:4e:a5:86:d2 timed out
    [ 2654.983925] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 1/3)
    [ 2655.180116] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 2/3)
    [ 2655.380126] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 3/3)
    [ 2655.580064] wlan0: direct probe to 02:23:4e:a5:86:d2 timed out
    [ 2661.841547] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 1/3)
    [ 2662.040157] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 2/3)
    [ 2662.240090] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 3/3)
    [ 2662.440088] wlan0: direct probe to 02:23:4e:a5:86:d2 timed out
    [ 2668.672413] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 1/3)
    [ 2668.872079] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 2/3)
    [ 2669.072080] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 3/3)
    [ 2669.272093] wlan0: direct probe to 02:23:4e:a5:86:d2 timed out
    [ 2675.507052] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 1/3)
    [ 2675.704057] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 2/3)
    [ 2675.904050] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 3/3)
    [ 2676.104051] wlan0: direct probe to 02:23:4e:a5:86:d2 timed out
    [ 2682.350983] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 1/3)
    [ 2682.548053] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 2/3)
    [ 2682.748092] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 3/3)
    [ 2682.949322] wlan0: direct probe to 02:23:4e:a5:86:d2 timed out
    [ 2689.203721] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 1/3)
    [ 2689.400056] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 2/3)
    [ 2689.600055] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 3/3)
    [ 2689.800156] wlan0: direct probe to 02:23:4e:a5:86:d2 timed out
    [ 2696.060168] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 1/3)
    [ 2696.260113] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 2/3)
    [ 2696.460119] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 3/3)
    [ 2696.660068] wlan0: direct probe to 02:23:4e:a5:86:d2 timed out
    [ 2704.275368] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 1/3)
    [ 2704.472055] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 2/3)
    [ 2704.672057] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 3/3)
    [ 2704.872053] wlan0: direct probe to 02:23:4e:a5:86:d2 timed out
    [ 2711.118616] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 1/3)
    [ 2711.316093] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 2/3)
    [ 2711.516104] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 3/3)
    [ 2711.716086] wlan0: direct probe to 02:23:4e:a5:86:d2 timed out
    [ 2717.962329] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 1/3)
    [ 2718.160060] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 2/3)
    [ 2718.360056] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 3/3)
    [ 2718.560096] wlan0: direct probe to 02:23:4e:a5:86:d2 timed out
    [ 2724.788501] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 1/3)
    [ 2724.988142] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 2/3)
    [ 2725.188146] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 3/3)
    [ 2725.388188] wlan0: direct probe to 02:23:4e:a5:86:d2 timed out
    [ 2731.636310] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 1/3)
    [ 2731.837307] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 2/3)
    [ 2732.036141] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 3/3)
    [ 2732.236137] wlan0: direct probe to 02:23:4e:a5:86:d2 timed out
    [ 2738.491444] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 1/3)
    [ 2738.688093] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 2/3)
    [ 2738.888085] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 3/3)
    [ 2739.089507] wlan0: direct probe to 02:23:4e:a5:86:d2 timed out
    [ 2745.333542] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 1/3)
    [ 2745.532052] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 2/3)
    [ 2745.732104] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 3/3)
    [ 2745.932266] wlan0: direct probe to 02:23:4e:a5:86:d2 timed out
    [ 2752.180232] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 1/3)
    [ 2752.380102] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 2/3)
    [ 2752.580170] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 3/3)
    [ 2752.780163] wlan0: direct probe to 02:23:4e:a5:86:d2 timed out
    [ 2759.052548] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 1/3)
    [ 2759.252063] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 2/3)
    [ 2759.452091] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 3/3)
    [ 2759.652168] wlan0: direct probe to 02:23:4e:a5:86:d2 timed out
    [ 2767.264447] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 1/3)
    [ 2767.464059] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 2/3)
    [ 2767.664046] wlan0: direct probe to 02:23:4e:a5:86:d2 (try 3/3)
    [ 2767.864080] wlan0: direct probe to 02:23:4e:a5:86:d2 timed out
    [ 2774.105149] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2774.304059] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2774.504054] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2774.704117] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2780.965932] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2781.164747] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2781.364093] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2781.564052] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2787.803037] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2788.001339] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2788.200354] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2788.400103] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2794.649538] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2794.848092] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2795.048053] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2795.248050] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2801.517761] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2801.716070] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2801.916045] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2802.116092] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2808.396106] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2808.596052] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2808.796493] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2808.996068] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2815.261504] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2815.460071] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2815.660132] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2815.860091] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2822.120255] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2822.320080] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2822.520049] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2822.720142] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2828.973236] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2829.172113] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2829.372071] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2829.572208] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2847.176874] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2847.376074] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2847.576134] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2847.776137] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2854.036147] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2854.236109] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2854.436096] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2854.636088] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2860.888141] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2861.088054] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2861.288101] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2861.488040] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2867.768169] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2867.968125] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2868.168097] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2868.368095] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2874.628178] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2874.828073] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2875.028087] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2875.228105] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2881.484972] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2881.684112] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2881.884107] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2882.084087] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 2888.332332] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 2888.532126] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 2888.732161] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 2888.932170] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out


Thank you!

---

### Post by chili555 on 2012-09-03
Let's try a temporary driver parameter:```
sudo modprobe -r b43
sudo modprobe b43 nohwcrypt=1
```Any improvement?

---

### Post by jkasai on 2012-09-03
Hello! Thank you for your reply!

Still no luck... :"(

---

### Post by jkasai on 2012-09-04
I tried to do the last few steps again because the screen justs crashed an I had to restart... I hope that doesn't muck things up...

But anyhoo, after the lsmod | grep b43 step, I got the following:

 [ 4037.368137] wlan0: direct probe to 02:24:17:f6:09:b9 (try 2/3)
    [ 4037.568186] wlan0: direct probe to 02:24:17:f6:09:b9 (try 3/3)
    [ 4037.768117] wlan0: direct probe to 02:24:17:f6:09:b9 timed out
    [ 4044.016235] wlan0: direct probe to 02:24:17:f6:09:b9 (try 1/3)
    [ 4044.216187] wlan0: direct probe to 02:24:17:f6:09:b9 (try 2/3)
    [ 4044.416186] wlan0: direct probe to 02:24:17:f6:09:b9 (try 3/3)
    [ 4044.616182] wlan0: direct probe to 02:24:17:f6:09:b9 timed out
    [ 4050.884140] wlan0: direct probe to 02:24:17:f6:09:b9 (try 1/3)
    [ 4051.084090] wlan0: direct probe to 02:24:17:f6:09:b9 (try 2/3)
    [ 4051.284072] wlan0: direct probe to 02:24:17:f6:09:b9 (try 3/3)
    [ 4051.485411] wlan0: direct probe to 02:24:17:f6:09:b9 timed out
    [ 4057.728115] wlan0: direct probe to 02:24:17:f6:09:b9 (try 1/3)
    [ 4057.928167] wlan0: direct probe to 02:24:17:f6:09:b9 (try 2/3)
    [ 4058.128142] wlan0: direct probe to 02:24:17:f6:09:b9 (try 3/3)
    [ 4058.328168] wlan0: direct probe to 02:24:17:f6:09:b9 timed out
    [ 4064.584411] wlan0: direct probe to 02:23:4e:a5:86:d3 (try 1/3)
    [ 4064.784145] wlan0: direct probe to 02:23:4e:a5:86:d3 (try 2/3)
    [ 4064.984138] wlan0: direct probe to 02:23:4e:a5:86:d3 (try 3/3)
    [ 4065.184178] wlan0: direct probe to 02:23:4e:a5:86:d3 timed out
    [ 4071.484147] wlan0: direct probe to 02:24:17:f6:09:b9 (try 1/3)
    [ 4071.684090] wlan0: direct probe to 02:24:17:f6:09:b9 (try 2/3)
    [ 4071.884149] wlan0: direct probe to 02:24:17:f6:09:b9 (try 3/3)
    [ 4072.084179] wlan0: direct probe to 02:24:17:f6:09:b9 timed out
    [ 4078.344136] wlan0: direct probe to 02:24:17:f6:09:b9 (try 1/3)
    [ 4078.544096] wlan0: direct probe to 02:24:17:f6:09:b9 (try 2/3)
    [ 4078.744100] wlan0: direct probe to 02:24:17:f6:09:b9 (try 3/3)
    [ 4078.944122] wlan0: direct probe to 02:24:17:f6:09:b9 timed out
    [ 4085.220138] wlan0: direct probe to 02:24:17:f6:09:b9 (try 1/3)
    [ 4085.420452] wlan0: direct probe to 02:24:17:f6:09:b9 (try 2/3)
    [ 4085.620170] wlan0: direct probe to 02:24:17:f6:09:b9 (try 3/3)
    [ 4085.820165] wlan0: direct probe to 02:24:17:f6:09:b9 timed out
    [ 4093.288174] wlan0: direct probe to 02:24:17:f6:09:b9 (try 1/3)
    [ 4093.488092] wlan0: direct probe to 02:24:17:f6:09:b9 (try 2/3)
    [ 4093.688996] wlan0: direct probe to 02:24:17:f6:09:b9 (try 3/3)
    [ 4093.888088] wlan0: direct probe to 02:24:17:f6:09:b9 timed out
    [ 4100.148144] wlan0: direct probe to 02:23:4e:a5:86:d3 (try 1/3)
    [ 4100.348086] wlan0: direct probe to 02:23:4e:a5:86:d3 (try 2/3)
    [ 4100.548096] wlan0: direct probe to 02:23:4e:a5:86:d3 (try 3/3)
    [ 4100.748133] wlan0: direct probe to 02:23:4e:a5:86:d3 timed out
    [ 4115.112330] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 4115.312372] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 4115.512082] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 4115.712082] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 4121.976143] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 4122.176108] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 4122.376152] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 4122.576124] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 4128.832133] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 4129.032116] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 4129.232041] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 4129.432099] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 4135.716123] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 4135.916068] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 4136.116101] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 4136.316095] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 4142.576143] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 4142.776170] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 4142.976061] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 4143.176068] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 4149.436210] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 4149.636183] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 4149.836137] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 4150.036179] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 4546.488119] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 4546.688147] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 4546.888093] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 4547.088091] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 4553.348129] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 4553.548111] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 4553.748172] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 4553.948093] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 4560.216147] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 4560.416062] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 4560.616055] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 4560.816077] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 4579.496324] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 4579.696053] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 4579.896064] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 4580.096110] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 4586.340140] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 4586.540046] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 4586.740050] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 4586.940091] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 4593.220145] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 4593.420103] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 4593.620105] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 4593.820136] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 4600.084118] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 4600.284096] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 4600.484288] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 4600.684071] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 5026.436146] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 5026.636160] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 5026.836077] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 5027.036069] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 5033.292138] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 5033.492905] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 5033.692066] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 5033.892137] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 5040.145902] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 5040.344092] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 5040.544083] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 5040.744138] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 5046.996140] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 5047.196090] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 5047.396223] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 5047.596253] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 5053.844118] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 5054.044092] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 5054.244076] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 5054.444073] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 5060.708180] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 5060.908120] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 5061.108124] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 5061.308039] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 5067.560151] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 5067.760077] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 5067.960089] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 5068.160102] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 5074.432144] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [ 5074.632091] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [ 5074.832074] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [ 5075.032150] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [ 5228.852433] ADDRCONF(NETDEV_UP): wlan0: link is not ready


Thank you!

---

### Post by chili555 on 2012-09-04
Let's try the driver parameters:```
sudo gedit /etc/modprobe.d/b43.conf
```A new empty text document will open. Add a single line:```
options b43 nohwcrypt=1 qos=0
```Proofread carefully, save and close gedit. Reboot. Any improvements?

You'll only need to show a couple of repeats from the logs; after ten or fifteen, we are only flooding the forum.

---

### Post by jkasai on 2012-09-04
Hi chili555,

Sorry about flooding the forum! :S

The Wifi still isn't budging :"(

What can I do next please?

Thank you!

---

### Post by chili555 on 2012-09-04
Are the symptoms the same? It tries and never connects? Any clues here?```
dmesg | grep b43
dmesg | grep wlan
```If there are repeats, just omit them and note 'repeating.'

What are your settings in Network Manager? Ideally, you need *none!* If you've made some changes, please remove them. Be sure the mode is set to Infrastructure. Please see attached.

---

### Post by jkasai on 2012-09-04
Hi chili555,

for dmesg &#65372; grep b43, i get:
[    12.790006] b43-pci-bridge 0000:05:00.0: setting latency timer to 64

after typing dmesg&#65372; grep wlan, I don't get anything...
nothing on Terminal, no pop ups or anything...

I haven't made any changes to the settings...
Just says the connection name, SSID (same as connection name), mode is Infrastructure, and Device MAC address...

---

### Post by jkasai on 2012-09-04
I'm not getting any symptoms either, it doesn't even seem to be trying...

---

### Post by chili555 on 2012-09-04
I'd like to see a complete *dmesg* log. Please do:```
sudo modprobe b43 > jkasai.txt
lsmod >> jkasai.txt
dmesg >> jkasai.txt
zip jkasai.zip jkasai.txt 
```Find the file jkasai.zip in your user directory and attach it to your reply using the paperclip tool at the top of the reply box.

With the proper firmware, which you loaded, this thing ought to take off like a rocket. We are puzzled.

---

### Post by jkasai on 2012-09-04
Hello chili555,


Thank you for your help and support again! :)


Terminal now looks like:

:~$ sudo modprobe b43 > jkasai.txt
    [sudo] password for jkasai: 
    WARNING: All config files need .conf: /etc/modprobe.d/options b43 nohwcrypt=1 qos=0, it will be ignored in a future release.
    :~$ lsmod >> jkasai.txt
    :~$ dmesg >> jkasai.txt
    :~$ zip jkasai.zip jkasai.txt
      adding: jkasai.txt (deflated 73%)
    :~$ 



I then got a pop up saying that wireless networks are available.
Typed in the password for the connection but it won't connect...


Attached is the zip file! I hope this is it!!



Thank you again chili555!

---

### Post by chili555 on 2012-09-04
> WARNING: All config files need .conf: /etc/modprobe.d/options b43 nohwcrypt=1 qos=0, it will be ignored in a future release.Oops! A mistake was made. You need to do:```
sudo rm /etc/modprobe.d/options\ b43\ nohwcrypt=1\ qos=0
```Then go back and repeat your steps. You were supposed to create a file called */etc/modprobe.d/b43.conf* containing a single line:```
options b43 nohwcrypt=1 qos=0
```Please try again and reboot.

---

### Post by jkasai on 2012-09-05
Hi chili555,

Thank you so much for your patience and for helping me!
I don't know what I'd do without you!!

I did the above and it tries to connect but it doesn't :"(

Do you think it'd be best if I re-installed Ubuntu 12.04?

Thank you!

---

### Post by chili555 on 2012-09-05
Please let me see:```
ls /etc/modprobe.d
cat /etc/modprobe.d/b43.conf
cat /sys/module/b43/parameters/qos
cat /sys/module/b43/parameters/nohwcrypt
dmesg | grep -e b43 -e firmware -e ssb
```> Do you think it'd be best if I re-installed Ubuntu 12.04?Not really; not unless you think you've fiddled and adjusted settings too far to work properly..

---

### Post by jkasai on 2012-09-05
Hi chili555,

Here's what I got:

 :~$ ls /etc/modprobe.d
    alsa-base.conf          blacklist.conf              blacklist-rare-network.conf
    b43.conf                blacklist-firewire.conf     blacklist-watchdog.conf
    b43.conf~               blacklist-framebuffer.conf  dkms.conf
    blacklist-ath_pci.conf  blacklist-modem.conf        vmwgfx-fbdev.conf
    blacklist-bcm43.conf    blacklist-oss.conf
    jkasai@Junko-PC:~$ cat /etc/modprobe.d/b43.conf
  
  options b43 nohwcrypt=1 qos=0
  
  :~$ cat /sys/module/b43/parameters/qos
  
  0
  
  :~$ cat /sys/module/b43/parameters/nohwcrypt
  
  1
    :~$ dmesg | grep -e b43 -e firmware -e ssb
    [   13.439584] b43-pci-bridge 0000:05:00.0: setting latency timer to 64
    [   13.457547] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243)
    [   13.457561] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243)
    [   13.457569] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243)
    [   13.457577] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243)
    [   13.544187] ssb: Sonics Silicon Backplane found on PCI device 0000:05:00.0
    [   13.564446] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
    [   13.564457] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
    [   13.564466] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
    [   13.635633] ssb: Sonics Silicon Backplane found on PCI device 0000:08:00.0
    [   13.653128] b44 ssb1:0: eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver 00:15:c5:c7:33:04
    [ 5296.378994] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
    [ 5296.516532] Registered led device: b43-phy0::tx
    [ 5296.516598] Registered led device: b43-phy0::rx
    [ 5296.516661] Registered led device: b43-phy0::radio
    [ 5296.828095] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
    [FONT=&quot]:~$ [/FONT]

---

### Post by chili555 on 2012-09-05
Looks pretty good, actually! Let's have a peek at:```
cat /etc/modprobe.d/blacklist-bcm43.conf
cat /etc/modprobe.d/blacklist.conf 
```We may have a conflict there.

---

### Post by jkasai on 2012-09-05
Hi!

Here's how it's looking:

 :~$ cat /etc/modprobe.d/blacklist-bcm43.conf
    # Warning: This file is autogenerated by bcmwl. All changes to this file will be lost.
    blacklist b43
    blacklist b43legacy
    blacklist ssb
    blacklist bcm43xx
    blacklist brcm80211
    blacklist brcmfmac
    blacklist brcmsmac
    blacklist bcma
    blacklist b44
    install wl modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install wl ; modprobe --ignore-install b44
    :~$ cat /etc/modprobe.d/blacklist.conf
    # This file lists those modules which we don't want to be loaded by
    # alias expansion, usually so some other driver will be loaded for the
    # device instead.
     
   
  # evbug is a debug tool that should be loaded explicitly
    blacklist evbug
     
   
  # these drivers are very simple, the HID drivers are usually preferred
    blacklist usbmouse
    blacklist usbkbd
     
   
  # replaced by e100
    blacklist eepro100
     
   
  # replaced by tulip
    blacklist de4x5
     
   
  # causes no end of confusion by creating unexpected network interfaces
    blacklist eth1394
     
   
  # snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
    # hardware on its own (Ubuntu bug #2011, #6810)
    blacklist snd_intel8x0m
     
   
  # Conflicts with dvb driver (which is better for handling this device)
    blacklist snd_aw2
     
   
  # causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
    blacklist i2c_i801
     
   
  # replaced by p54pci
    blacklist prism54
     
   
  # replaced by b43 and ssb.
    blacklist bcm43xx
     
   
  # most apps now use garmin usb driver directly (Ubuntu: #114565)
    blacklist garmin_gps
     
   
  # replaced by asus-laptop (Ubuntu: #184721)
    blacklist asus_acpi
     
   
  # low-quality, just noise when being used for sound playback, causes
    # hangs at desktop session start (Ubuntu: #246969)
    blacklist snd_pcsp
     
   
  # ugly and loud noise, getting on everyone's nerves; this should be done by a
    # nice pulseaudio bing (Ubuntu: #77010)
    blacklist pcspkr
     
   
  # EDAC driver for amd76x clashes with the agp driver preventing the aperture
    # from being initialised (Ubuntu: #297750). Blacklist so that the driver
    # continues to build and is installable for the few cases where its
    # really needed.
    blacklist amd76x_edac
    
Thank you!

---

### Post by chili555 on 2012-09-05
> :~$ cat /etc/modprobe.d/blacklist-bcm43.conf
# Warning: This file is autogenerated by bcmwl. All changes to this file will be lost.
blacklist b43Hmmm. We still have a bit more work to do.```
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo apt-get remove --purge bcmwl-kernel-source
```Reboot and tell me something good!

---

### Post by jkasai on 2012-09-05
Hey, thank you again!



:~$ sudo rm /etc/modprobe.d/blacklist-bcm43.conf
    [sudo] password for jkasai: 
    :~$ sudo apt-get remove --purge bcmwl-kernel-source
    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    The following packages were automatically installed and are no longer required:
      fakeroot dkms
    Use 'apt-get autoremove' to remove them.
    The following packages will be REMOVED:
      bcmwl-kernel-source*
    0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
    After this operation, 3,252 kB disk space will be freed.
    Do you want to continue [Y/n]? 
    
I'm guessing that I do want to continue...?

---

### Post by chili555 on 2012-09-05
> I'm guessing that I do want to continue...?Yes, please. You may also safely do:```
sudo apt-get autoremove
```

---

### Post by jkasai on 2012-09-05
Just restarted but it still tries to connect and fails... :"(

This is what was Terminal before restarting:

 (Reading database ... 141180 files and directories currently installed.)
   
  Removing bcmwl-kernel-source ...
   
  Removing all DKMS Modules
   
  Done.   
   
  update-initramfs: deferring update (trigger activated)
   
  Purging configuration files for bcmwl-kernel-source ...
   
  update-initramfs: deferring update (trigger activated)
   
  Processing triggers for initramfs-tools ...
   
  update-initramfs: Generating /boot/initrd.img-3.2.0-29-generic-pae
   
   
  :~$ sudo apt-get autoremove
    [sudo] password for jkasai: 
    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    The following packages will be REMOVED:
      dkms fakeroot
    0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
    After this operation, 655 kB disk space will be freed.
    Do you want to continue [Y/n]? Y
    (Reading database ... 141130 files and directories currently installed.)
    Removing dkms ...
    Removing fakeroot ...
    update-alternatives: using /usr/bin/fakeroot-tcp to provide /usr/bin/fakeroot (fakeroot) in auto mode.
    Processing triggers for man-db ...
    :~$ 
     
  Sorry!
Thanks!

---

### Post by chili555 on 2012-09-05
Now that we have the b43.conf file as we wanted and we have bcmwl-kernel-source out of the way, please make me a new log file as in post #29.

I am about to hang my head in shame and suggest a re-install. Let's have a look at your newest jkasai.zip first.

---

### Post by jkasai on 2012-09-05
Hi chili555,

Sorry for the late reply and for causing you trouble >_<

Attached is the most recent jkasai.txt.

Thank you for supporting and helping me!
I really really appreciate it!

M

---

### Post by chili555 on 2012-09-05
I see this:> [   17.256297] cfg80211: Found new beacon on frequency: 2472 MHz ([COLOR="Red"]Ch 13[/COLOR]) on phy0And this:> [   14.794358] cfg80211: World regulatory domain updated:...but it doesn't say to where. My dmesg says:> cfg80211: Regulatory domain changed to country: USI wonder if you router is set to a channel that your card can't or won't recognize. Let's see:```
sudo iwlist wlan0 scan
```Just tell us what channel your router is set to; for example:> Cell 01 - Address: xx:13:10:62:8D:xx
                    [COLOR="Red"]Channel:11[/COLOR]
                    Frequency:2.462 GHz (Channel 11)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"GBR1"
Let's compare to:```
sudo iwlist wlan0 channel
```Again, an example from my machine:> wlan0     32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
<snip>No channel 12 or 13 here.

I wonder if that may be our issue. I also wonder if there is no other way, we can trick cfg80211 to do your channel.> I'm refurbishing a Dell Inspiron 1501Did this laptop come from a country other than your own?

---

### Post by jkasai on 2012-09-05
Hello!

It says Channel 11.
Channel 11: 2.462 GHz.
(The channels run from 01 to 14)

Yep! I got it quite a few years back but I'm pretty certain it's from the UK.
:S

---

### Post by chili555 on 2012-09-05
> Yep! I got it quite a few years back but I'm pretty certain it's from the UK.And I assume you and the router are also in the UK. Let's try this:```
sudo gedit /etc/modprobe.d/cfg80211.conf
```A new empty file will open. Add one single line:```
options cfg80211 ieee80211_regdom=GB
```Proofread carefully, twice. Save and close. Reboot and check to see what wlan0 is doing:```
dmesg | grep -e wlan -e cfg8 | tail -n15
```

Note the code is GB and not UK: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2)

---

### Post by jkasai on 2012-09-06
Does the file need to be saved under a particular name?
I just pressed Save and then closed... 

After restarting, the wifi tried to connect again but didn't manage :"(



:~$ dmesg | grep -e wlan -e cfg8 | tail -n15
    [  365.056176] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3)
    [  365.256168] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 3/3)
    [  365.456177] wlan0: direct probe to 00:23:4e:a5:86:d1 timed out
    [  371.508172] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 1/3)
    [  371.708167] wlan0: direct probe to 00:23:4e:a5:86:d1 (try 2/3) 

... and the above repeats.


Thank you!

[FONT=&quot][/FONT]

---

### Post by chili555 on 2012-09-06
> Does the file need to be saved under a particular name?
I just pressed Save and then closed...Let's double-check:```
ls /etc/modprobe.d
cat /etc/modprobe.d/cfg80211.conf
cat /sys/module/cfg80211/parameters/ieee80211_regdom 
dmesg | grep -i regulatory
```

---

### Post by jkasai on 2012-09-08
Sorry for the late reply!

Weird, the laptop won't even switch on properly...

There are 4 indicators next to the power switch. 3 are padlock symbols with something in the middle (Num lock, Capital letters, and an arrow pointing downwards), the other is a wifi indicator...

the padlock symbol with the arrow pointing downwards keeps flashing and the laptop won't even go to the welcome page...

---

### Post by chili555 on 2012-09-08
> the padlock symbol with the arrow pointing downwards keeps flashing and the laptop won't even go to the welcome page...That usually means you have a kernel panic. You can try to boot into an earlier kernel or into failsafe mode. If you can, you can reinstall the latest kernel.

[http://askubuntu.com/questions/35722/what-is-kernel-panic](http://askubuntu.com/questions/35722/what-is-kernel-panic)

---

### Post by denauldo on 2012-09-28
Thanks this worked for me all i did was put zip file on usb floppy and extract file to desktop and bam thats it :)))))))))

---

