---
title: "More wireless problems"
date: 2006-06-30
forum: Networking &amp; Wireless
---

### Post by hedonistic.heathen on 2006-06-30
I'm banging my head against the wall for over a week trying to get my wirless working...I have a Dell E1505 with the BCM4311 wireless card.

After many unsuccessful attempts, I was directed to the forum post below, and have successfully installed a different version of ndiswrapper than is available through synaptic package manager and it seems to have worked, to a degree.  

[http://www.ubuntuforums.org/showthread.php?t=193350]("http://www.ubuntuforums.org/showthread.php?t=193350")



My wi-fi led is now lit up, wlan0 appears in Sys>Admin>Networking and is activated, iwconfig shows a device under wlan0, I click on the Network Manager icon and I see my network's SSID with a full strength signal next to it, I attempt to connect, the icon changes, I wait, but the connection never materializes.  I have tried changing my router settings to WPA, WEP, and unprotected and I tried using Network Manager initially without success, I removed it and tried using the default gnome network manager (typing in wlan0 in place of eth0 and connecting to my network with no security settings), but that didn't work either.  I am connected without a problem right now through windows, so it isn't an issue with signal strength.

I feel like I might be missing something simple, most of the posts I've read deal with getting the OS to recognize the wireless card and after that has been done, most folks are set, but that's not the case for me.  Any suggestions?

---

### Post by galaxie on 2006-07-04
I'm having the exact same problem on an inspiron 9400 with a BCM4311 (dell truemobile 1390) internal wireless card as well.

I've tried both the bcm43xx modules and ndiswrapper using dells "R115321" driver package.

Any find a solution to this?

---

### Post by hedonistic.heathen on 2006-07-05
I've tried following the recommendations of every forum thread related to the BCM4311 without luck.  I've had a number of sessions with "experts" from qunu.com and I've met a couple of knowledgeable people on irc that tried to help and nothing has worked.

I'm at the point where I'm going to have to give up on ubuntu for a bit until a fix comes along or I'm going to have to buy a new wi-fi card.  

I would be very interested to hear from someone with the same laptop/wireless card and has gotten their wireless connection to function...

---

### Post by galaxie on 2006-07-06
I as well have taken the same route as you have, it's back to slackware untill they get the BCM4311 issues figured out for me as well.

---

### Post by galaxie on 2006-07-14
It could all just be an order of operations issue and i offer no guarantee that this will work for you, but it did for me after banging my head for a while

All in all, it went like this:
1. install ndiswrapper properly (lots of threads on how to do that)
At that point i could see the network(s) but just not connect
So i through together a shell script that looked like this:

Code:

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
Edit/Delete Message

---

