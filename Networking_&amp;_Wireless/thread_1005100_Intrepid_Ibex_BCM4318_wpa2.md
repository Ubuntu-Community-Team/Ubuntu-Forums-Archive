---
title: "Intrepid Ibex BCM4318 wpa2"
date: 2008-12-07
forum: Networking &amp; Wireless
---

### Post by theweakend on 2008-12-07
Got this wireless card working with [this]("http://www.sampbar.com/2008/11/broadcom-bcm4318-ubuntu-intrepid.html") tutorial. But now lies the problem with wpa2. i seen a lot of issues with BCM4328 and BCM4306, so basically i am trying to find some one with the same wireless card i have (BCM4318) and if they are having the same issues.

---

### Post by kevdog on 2008-12-08
What was wrong with the built in b43 driver?

---

### Post by theweakend on 2008-12-08
They didn't even scan the network. Unless i missed something.

---

### Post by kevdog on 2008-12-08
What does sudo iwlist auth show?  I'm not sure if this generated list is accurate.

---

### Post by theweakend on 2008-12-08
Usage: iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower 
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation

---

### Post by theweakend on 2008-12-08
Sorry to double post but i found this odd that i just connected to my network? I'll post here if something happens, very odd this is.

---

### Post by kevdog on 2008-12-08
Well I guess the point was mute but the command was

sudo iwlist wlan0 auth

---

### Post by ookboo on 2008-12-24
Hey Kevdog,

see note below

---

### Post by ookboo on 2008-12-24
Hey Kevdog,

Hoping you can be of help here.  Same card BCM4318.  iwlist wlan0 auth returns:  wlan0     no authentication information

sudo iwlist auth
returns
no authentication information for eth0, pan0, wmaster0

eth0    Authentication capabilities::
        WPA, WPA2, CIPHER-TKIP, CIPHER-CCMP

        Current Authentication algorithm
        open, shared key

I just upgraded to Ibex after many happy months in hardy.  This wireless card gave me grief on the initial install of gutsy as well, but no issues on the upgrade to hardy...


any help would be appreciated.

---

### Post by ookboo on 2008-12-24
Hey Kevdog,

Hoping you can be of help here.  Same card BCM4318.  iwlist wlan0 auth returns:  wlan0     no authentication information

sudo iwlist auth
returns
no authentication information for eth0, pan0, wmaster0

eth0    Authentication capabilities::
        WPA, WPA2, CIPHER-TKIP, CIPHER-CCMP

        Current Authentication algorithm
        open, shared key

I just upgraded to Ibex after many happy months in hardy.  This wireless card gave me grief on the initial install of gutsy as well, but no issues on the upgrade to hardy...


any help would be appreciated.

---

