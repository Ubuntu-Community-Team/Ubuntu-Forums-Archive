---
title: "Dell E1505 (Broadcom) - need help"
date: 2006-06-18
forum: Networking &amp; Wireless
---

### Post by hedonistic.heathen on 2006-06-18
$ lspci | grep Broadcom
0000:03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (re v 02)
0000:0b:00.0 Network controller: Broadcom Corporation: Unknown device 4311 (rev 01)
____________________________________________________________________________
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.
_____________________________________________________________________________


I've worked through the "How to: Broadcom Wireless cards without Ndiswrapper" and the "How to: Broadcom wireless cards" using ndiswrapper.  Nothing has worked.  I'm fairly new to linux, so I don't know a great deal at this point...I'm savy enoguh to work through the how to's, but thats about it.  I see tons and tons of broadcom related posts, and I've read through a slew of them, but I'm still pretty well where I started.

I would really like to get my wireless connection working because that will give me more time to toy around with ubuntu, work through some tutorials, and become more familiar with linux in general.  

I really don't want to buy a new wireless card, that would be an absolute last resort.  I would consider wiping dapper and tyring my luck with SUSE before messing with a new wirless card, but I prefer dapper and would really like to get things working.  

Has anyone with the E1505 or same Broadcom card gotten it to work successfully in ubuntu?  I would really appreicate it if you could explain how you were able to do so.

Thanks for the help.

---

### Post by tirofiban on 2006-06-18
I just got my E1505 with the Dell 1390 to work with NDISWrapper this weekend.:KS 

Only problem is NDISWRAPPER and Network manager don't work together. I think it might be a bug with one of them. 

But, I can confirm and tell you how to get NDISWRAPPER w/ the Dell 1390 working with unprotected and WEP wifi. I had to uninstall network manager.

Follow the instructions on this link and let me know where you get errors or have problems. I'll respond to your questions.

[http://www.ubuntuforums.org/showthread.php?t=193350](http://www.ubuntuforums.org/showthread.php?t=193350)

The NDISWRAPPER in Synaptic does not WORK with the Dell 1390. You have to download the tarball and compile the latest version.

Also make sure you get good with the sudo command and work from root when you're installing. And make sure gedit doesn't say read only. Use the exact case. It's the small stuff like this that gets you as a beginner. 

I'm going to look into if I can get some driver for the 1390 to work with Ubuntu. I think it might work better than NDISWRAPPER with the network manager.  My ultimate goal is WPA.

Marc

P.S. It REALLY helps to have another computer nearby with high speed internet access so you can do forum searches and download the files, ie ndiswrapper, and driver files. It's even better if you can directly connect your ubuntu computer to the ethernet so you can download and install the compiler dependencies.

---

### Post by hedonistic.heathen on 2006-06-26
Ok, I finally had time to work on this...I followed the directions on the link you provided and to my surprise it worked - to an extent.  Under System > Admin > Networking I can now see my wlan card and the led is now lit as well.  When I run iwconfig, I get this:

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:32 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.




Problem is I can't connect to my wireless network.  Network manager recognizes my wireless card and sees my network, but when I try to connect I just get "waiting for network key for the wireless network" and it doesn't connect.  I tried changing my router settings to WPA, WEP, and unprotected and still couldn't connect.

I tried uninstalling network manager and still couldn't connect through the degault gnome network manager...Which by the way, still only shows eth0 and lo as my only options to connect...I'm not sure how to change that...

---

### Post by MarkSheely on 2006-06-28
You should be able to click on the box displaying eth0 or lo, and enter in wlan0.  

That's if I understand what you are saying correctly.

Keep trying -
Mark

---

### Post by hedonistic.heathen on 2006-06-29
I wasn't aware I could do that.  Once I do though, a signal strength meter appears and reads 0 and I am unable to connect.  I changed the router settings so that there is no security and still nothing.  I'm using the default gnome network manager app btw.

Using network manager, I can see that the signal strength is strong, but it attempts to connect (the swirling icon with the flashing green dots) and eventually stops and reverts back to the 'no connection' icon (I apologize for my lacking the proper vocabulary to explain this better).

I'm not sure what I'm doing wrong...

---

### Post by galaxie on 2006-07-14
I've found a slution with my bcm4311 that could just have to do with order of operations.

All in all, it went like this:
1. install ndiswrapper properly (lots of threads on how to do that)
At that point i could see the network(s) but just not connect
So i through together a shell script that looked like this:

```

#!/bin/bash
# set the key first, wont work if set after essid
iwconfig wlan0 key restricted s:XXXXXXXXXXXXX

# now set the essid
iwconfig wlan0 essid XXXXXXX

# now request an ip
dhclient wlan0

```


and that was it, i gave up using networkmanager or any other crap as it just wouldnt give me an IP address no matter what.

So now, i just boot up, log in, and run:

sudo <script name>

(made one called home and one called work)

Not sure this will work for wpa, i'm just using wep

Hope this helps

---

### Post by hedonistic.heathen on 2006-07-14
First of all, congrats for getting it to work...

I'm new to linux, though, and don't know how to create a script (or really what one is), but from the context of your thread I'm assuming it just feeds the shell (or command line, I'm unsure which is the appropriate term here) a series of commands to be executed...Commands which I could just as well enter into the terminal manually, right?

Going with that assumption I enter the following into the terminal:

```
iwconfig wlan0 key restricted s:<my wep key>
```

...but I get the following error:

```
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.
```

I'm not sure what that means...I tried entering the same command, using the appropriate key, with the network set to WPA and WEP, but I get the same error message either way.

Any suggestions?

---

### Post by loui19 on 2006-07-22
> **hedonistic.heathen said:**
> 

```
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.
```


I ahve the same problem. Followed all the directions and threads. Got the wirless LED lit, wlan card shows in the network manager,. I have played with the properties for the wireless card, zero signal. Router is working have two wireless MS boxes interacting with it. Tried the iwconfig commands and got the same errors. Went to the iwconfig man page to make sure I was using the right commands.

So... I am adding to this thread.. if I get it running I'll will update the how to and post to the forum

Tony

---

### Post by lee_connell on 2006-08-10
off-topic, but does the synaptics touchpad work well for tap to click?  I seem to find myself clicking a couple times to get a tap out of it, I'm playing with the synclient commands but can't find a comfortable spot.  just wondering your experiences since i have an e1505 as well.

---

### Post by loui19 on 2006-11-25
Okay, had some time today and decided I was going to fix my wireless connection. I had tried a number of tips and forum threads and got no wireless access. Took a look at the WiFi docs here at Ubuntu ([https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)) and found a document for the BCM4311 ([https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29))

Very good directions.. I followed them and now have my wireless card running, even have wifi raddr going! Almost gave up hope of having wireless access on this laptop.

---

