---
title: "Kismet"
date: 2006-07-03
forum: Networking &amp; Wireless
---

### Post by tturrisi on 2006-07-03
I have a few cards that work well with Ubuntu Dapper & Kismet:
DLink 630G+
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=706706&CatId=367](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=706706&CatId=367)
Proxim Orinoco G/B (atheros chipset)
[http://www.data-alliance.net/servlet/Detail?no=35](http://www.data-alliance.net/servlet/Detail?no=35)

I ordered the Proxin last Thursday from Data Alliance & it came in the mail today.  Installed the linux-restricted-modules for my 686 kernel, plugged in the card and automatically connected to my wlan.  1-2-3 no trouble at all!

Kismet config for this Proxim card:
```
# User to setid to (should be your normal user)
suiduser=YOUR_UBUNTU_USER_NAME

# Sources are defined as:
# source=sourcetype,interface,name[,initialchannel]
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=madwifi_b,ath0,madwifi

# Do we use sound?
# Not to be confused with GUI sound parameter, this controls wether or not the
# server itself will play sound.  Primarily for headless or automated systems.
sound=true
# Path to sound player
soundplay=/usr/bin/aplay

# Other possibilities:  Sorting by directory
# logtemplate=%l/%n-%d-%i
# Would expand to, for example,
# dump/Pok-Dec-20-01-1
# crypt/Pok-Dec-20-01-1
# and so on.  The "dump", "crypt", etc, dirs must exist before kismet is run
# in this case.
logtemplate=/home/YOUR_UBUNTU_USER_NAME/log/kismet/%n-%d-%i.%l
```

The above logtemplate makes Kismet save the logs in your home dir so you can easily open them without root access from Ethereal.  (Create the /llog/kismet dirs in advance)

Sitting in my office in my home,  a suburban neighborhood w/ lots of trees, I plugged in my Cantenna to the Proxim card and Kismet detected 3 additional wlans that my other cards never detected!  

<spam>I highly recommend Data Alliance.  They deivered what they promised and the shipping was fast.</spam>

---

