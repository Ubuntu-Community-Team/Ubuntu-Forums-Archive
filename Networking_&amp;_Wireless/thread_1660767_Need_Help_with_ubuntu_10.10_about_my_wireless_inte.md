---
title: "Need Help with ubuntu 10.10 about my wireless internet"
date: 2011-01-05
forum: Networking &amp; Wireless
---

### Post by Fevacowbell on 2011-01-05
hello, I'm very new to Ubuntu as well as linux. But I recently switched to linux because I was sick of windows ********. My computer ran fine for a week than slowed right down. no matter what protection you have your almost gauranteed to get something nasty. Anyway about my current situation. I installed ubuntu from my USB. I did the correct steps and Ubuntu started up great. I got the ubuntu 10.10 version from Ubuntu website. Anyway, I install it and everything seems to be fine, at this point and time of installation I am directly connected via my cable modem. When all is said and done I plug in my wireless router and plug in my wireless linksys USB into my computer. Awsome! It connects, I'm on mozilla and everything is running fast and fine. "can not load web page" "Wireless disconnected" SOB! Not sure what's going on. I was connected than it seems as if I timed out or something. It wont let me reconnect either. I've tryed everything I could think of. Changed from WPA personal to WPA2 than to WEP. Basically my only options given my router. I tryed 64 bit than 128 for WEP. Still nothing seems to work. So I hard reset my modem back to it's originall setting and restart my computer. Again I am connected. Than disconnected minutes later. My internet works fine on another computer that has windows xp. So i know it's not my internet. And also I am able to connect for a short while. So it leads me to believe that there is nothing wrong with my USB. But who knows. Not sure if something went bad in the install. I tryed installing the correct driver for my usb. Still nothing. Every Time i restart my computer it seems to connect.  Here is my information


USB is a Linksys (cisco) Model # : WUSB54GC Ver. 3 Compact wireless-G USB network Adapter

Serial Number: MLF20J680201


I was running vista before. Not sure if that matters. Any info on this matter would be much appreciated. Thanks, Nick

---

### Post by PatchesTheCaveman on 2011-01-06
You might try installing the official Linux drivers for the RT2500USB chipset that your Linksys wireless USB adapter is built with.

There are download and installation instructions in this thread:  [http://ubuntuforums.org/showthread.php?t=960642&page=24](http://ubuntuforums.org/showthread.php?t=960642&page=24)

---

### Post by Project84 on 2011-01-06
^ That looks like it should work.  If not, try this link.  Same driver with a bit more detailed instructions for installing and testing out your system.  Leave your router settings alone if its been working with your other machines.  Linux and your wifi adapter card are more than capable of handling 128 bit encrypted WPA2.

[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

---

### Post by Fevacowbell on 2011-01-06
I followed that thread I think. I'm new to linux so I'm not sure if I'm doing the right steps. This is what I found in my terminal, 

lo: No wireless Extension

eth0 no wireless extension

wlan: IEEE 802.11bg  ESSID "NETGEAR"

Mode: Manged Frequency: 2.412 GHz Access Point: Not Associated

Tx-power : 11 dBm

Retry   Long Limit: 7   RTS thr: off   Fragment thr: off

Power Managment: On


Ethernet Controller: Intel Corporation 82562v 10/100  (Rev 2)

Than when I typed in "ping -n 4.2.2.2 -c 4

Connect: Network is unreachable



Not sure what to do. You had mentioned installing the correct network driver. 

Do I have Ralink rt2870 chipset. or do I have the 2500 version? 

Also not sure where to go about downloading that and installing it. 

Also about using the network-admin GUI network Tool not sure how to get to that in Ubuntu 10.10 because I have instructions here of going to "System" "Administration" "Networking" But there is no networking. Just network Tools. 

And when you said the driver download and install instructions are in this thread were they they first link?

[http://www.smachado.com/2010/11/how-to-make-ralink-rt2870-driver-work-on-ubuntu-10-10/]("http://www.smachado.com/2010/11/how-to-make-ralink-rt2870-driver-work-on-ubuntu-10-10/")


Please help

---

### Post by Fevacowbell on 2011-01-06
I'm also wondering if I should just go out and buy a new wireless usb. Would this be easier? haha

---

### Post by bodhi.zazen on 2011-01-06
Sounds as if the network card is working, you need to configure the connection.

The easy way to do this is with network manager, it is a little graphical tool on your menu.

[https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7)

If you can not connect, what security are you using (if any)? WPA ?

See also :

[https://wiki.ubuntu.com/NetworkManager/Hardware/3G/Probing](https://wiki.ubuntu.com/NetworkManager/Hardware/3G/Probing) 

Although that page is fairly technical.

---

### Post by Fevacowbell on 2011-01-06
My connections are open. I've been trying to do everything I know with the configuration. Nothings working.

---

### Post by bodhi.zazen on 2011-01-06
> **Fevacowbell said:**
> My connections are open. I've been trying to do everything I know with the configuration. Nothings working.

Could be your wireless card is incompatible then. Try another.

---

### Post by Fevacowbell on 2011-01-06
No my usb is compatible. If you look at my first post I said that I am able to connect and actually use the internet at each start up of my pc. But it doesn't last long. Kind of seems like im lagging out or something. But my internet works fine on other computers. So its got something to do with ubuntu and it's settings or something

---

### Post by MarcW10 on 2011-01-06
I have no idea what's wrong but I have the same problem and just posted about it. Does it only happen when you're using the connection heavily (i.e downloading) because that's what seems to happen to me? Hope we find some kind of a solution soon, it's annoying.

---

### Post by Fevacowbell on 2011-01-06
Haha, it's nice to know that i'm not alone, and yes, it seems that whenever I start up my world of warcraft it shuts down, but it's because i'm downloading a 12g file lol. But I have another computer that is using windows xp that works fine on the same internet so I know it's not my connection. If you find a solution please let me know. If I can't find one my saturday I'm going to buy another USB.

---

### Post by MarcW10 on 2011-01-06
I'd recommend you don't buy another USB adapter as I'm pretty sure that's not the issue. I have a built in wireless adapter and get the same issue. Also since it's only been happening on this computer since I installed 10.10 (10-04 worked perfectly), I'm pretty sure it's a Ubuntu issue rather then anything hardware related.

---

### Post by Fevacowbell on 2011-01-06
yea i was also thinking of installing 10.04...everyone says thats better

---

### Post by bodhi.zazen on 2011-01-06
> **MarcW10 said:**
> I'd recommend you don't buy another USB adapter as I'm pretty sure that's not the issue. I have a built in wireless adapter and get the same issue. Also since it's only been happening on this computer since I installed 10.10 (10-04 worked perfectly), I'm pretty sure it's a Ubuntu issue rather then anything hardware related.

Well, on technical grounds, it is not likely to be "ubuntu related", it would either be network manager related (try wicd) or kernel or wireless driver related.

---

### Post by Fevacowbell on 2011-01-06
We'll I know That my wireless USB adapter is compatible with ubuntu 10.10, I looked it up. Also I reset my router to factory settings a.k.a everything is open, Also my network manager has the same settings as my router. So What's next? If it's not my usb, and it's not the router. My usb worked with my windows vista, than I formatted and installed ubuntu. So theres no returning lol. I was either planning on reinstalling or installing ubuntu 10.04. I'd like to install the correct driver for my usb. I don't have a clue on where or how to do that.

---

### Post by bodhi.zazen on 2011-01-06
Boot the 10.10 live CD and try that. If it seems better install it.

The only other option would be to try wicd

[http://wicd.net/](http://wicd.net/)

I had a wireless card in 8.04 that did not work with NM , but was good to go with wicd.

Installing wicd is probably a faster test then 10.10

---

### Post by MarcW10 on 2011-01-07
Hi there. I just got a reply on my thread advising me that it's a known issue with the latest linux kernel and pointing me to this post to sort it out, hope it helps.

[http://ubuntuforums.org/showpost.php?p=10312711&postcount=5](http://ubuntuforums.org/showpost.php?p=10312711&postcount=5)

---

### Post by Fevacowbell on 2011-01-07
We'll I hope this is going to work. I just types uname -n and i've got the bad bug or update of kernal. I hope that's the only problem. going to check it out now....

---

### Post by Fevacowbell on 2011-01-07
I dont seem able to bring up any sort of "GRUB" menu. Not sure what i'm doing wrong. Not sure what the default key is or how to figure out what mine is set at. Please help me :'(

---

### Post by Fevacowbell on 2011-01-07
Nevermind. I was able to get the GRUB menu by using Shift. Anyway. It gave me four options. 

2.6.35-24-generic
2.6.35-24-generic (recovery Mode)
2.6.35-22-generic
2.6.35-22-generic (recovery Mode)

I'm chosing -22 because I was using 24 which wasnt working. So now I'm deleting 2.6.35-24-generic and reinstalling -23? Hope that's right

---

### Post by Fevacowbell on 2011-01-07
Yea it didn't work for me. Not sure what the deal is but I'm on -23 now and it's still connecting than when i load a couple webpages it disconnects. Thanks anyway. I'm just going to reformat and to a clean install of 10.04 ubuntu. I just want to play my world of warcraft :'(

---

