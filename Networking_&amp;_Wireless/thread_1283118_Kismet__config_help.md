---
title: "Kismet  config help"
date: 2009-10-05
forum: Networking &amp; Wireless
---

### Post by gabrielshier on 2009-10-05
Hey,
Just recently bought a new wireless network USB card. The chipset of the card is Ralink and it is fully compatible with ubuntu ( didn't even need any driver's installation, just PnP ). 
Now i'm trying to make it work with Kismet and just can't figure out what all the kismet.conf means. Any way, here is the quote of what matters:

```

Kismet config file
# Most of the "static" configs have been moved to here -- the command line
# config was getting way too crowded and cryptic.  We want functionality,
# not continually reading --help!

# Version of Kismet config
version=2007.09.R1

# Name of server (Purely for organizational purposes)
servername=Kismet

# User to setid to (should be your normal user)
#suiduser=gabriels

# Do we try to put networkmanager to sleep?  If you use NM, this is probably
# what you want to do, so that it will leave the interfaces alone while
# Kismet is using them.  This requires DBus support!
networkmanagersleep=true

# Sources are defined as:
# source=sourcetype,interface,name[,initialchannel]
# Source types and required drivers are listed in the README under the

```
Any way, it runs (when i type 'sudo kismet') it brings up kismet with no errors besides the fact it does not discover any network (when i'm sure there is).
Thanks, 
Gab

---

### Post by chili555 on 2009-10-05
This part needs to be un-commented:> #suiduser=gabrielsRemove the leading #.

You have stopped short of showing the capture sources, just after this:> # Sources are defined as:
# source=sourcetype,interface,name[,initialchannel]
# Source types and required drivers are listed in the README under theWhat did you put in there? For an example, here is mine:```
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=ipw2915,eth1,Intel
```Did you read the README, especially sections 9 and 12?```
less /usr/share/doc/kismet/README.gz
```

---

### Post by gabrielshier on 2009-10-06
> **chili555 said:**
> This part needs to be un-commented:Remove the leading #.

You have stopped short of showing the capture sources, just after this:What did you put in there? For an example, here is mine:```
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=ipw2915,eth1,Intel
```Did you read the README, especially sections 9 and 12?```
less /usr/share/doc/kismet/README.gz
```

chili555 - Thanks!
Now working perfectly - all i needed to do was to read the manual :)

---

