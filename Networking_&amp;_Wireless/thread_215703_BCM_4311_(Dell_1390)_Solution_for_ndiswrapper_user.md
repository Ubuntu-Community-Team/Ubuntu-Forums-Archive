---
title: "BCM 4311 (Dell 1390) Solution for ndiswrapper users who can SEE but _NOT_ CONNECT"
date: 2006-07-14
forum: Networking &amp; Wireless
---

### Post by galaxie on 2006-07-14
If your one of those people who has ndiswrapper installed properly, and network manager sees all the wireless networks around you but just cannot for the life of you get an ip address when you try to connect, the solution below just might help you out.

It could all just be an order of operations issue and i offer no guarantee that this will work for you, but it did for me after banging my head for a few days.

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

### Post by lifeempowered.com on 2006-09-13
Getting error:

Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.

Do I need to enclose anything in quotes?

---

### Post by lifeempowered.com on 2006-09-13
Ok, got rid of the error by changing the script to read:

#!/bin/bash
# set the key first, wont work if set after essid (i removed the s:)
iwconfig wlan0 key restricted XXXXXXXXXXXXX

# now set the essid
iwconfig wlan0 essid XXXXXXX

# now request an ip
dhclient wlan0

However, not sure that this helped at all as the interface still does not configure correctly.  when I do iwconfig it has no essid.  weird!  Any help?

---

### Post by collern2 on 2006-09-19
Do you have an nvidia graphics card? If so in your Xorg.conf - what do you have your graphics card set at:
vesa
nv
nvidia

If i have it set at nvidia it enables the 3d acceleration, but won't pick up any wireless networks. When I set to nv, I can see, but not connect. So I either get access to wireless networks but no 3d, or vice versa. Anyone else have this problem or any solutions?

---

### Post by tobirius on 2006-10-25
I've got another solution. Once you have connected install wifi-radar and create a new profile. This will connect you after boot and you won't need any script.

---

