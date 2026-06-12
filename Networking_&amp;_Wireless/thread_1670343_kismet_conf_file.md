---
title: "kismet conf file"
date: 2011-01-18
forum: Networking &amp; Wireless
---

### Post by raac on 2011-01-18
I can't seem to run kismet, but i don't know what to put in source. I have an USB atheros adapter, using the  ath9k_htc driver, and my interface is wlan1. I don't know what to put there. Since I installed it from the repository I don't know how to open the README file

# Sources are defined as:
# source=sourcetype,interface,name[,initialchannel]
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE

[COLOR="Navy"]source =[/COLOR] 

# Comma-separated list of sources to enable.  This is only needed if you defined
# multiple sources and only want to enable some of them.  By default, all defined
# sources are enabled.
# For example:
# enablesources=prismsource,ciscosource
.
.
.
.

---

### Post by chili555 on 2011-01-22
```
I don't know how to open the README file
```In a terminal, do:```
less /usr/share/doc/kismet/README.gz
```Use the arrow keys to review sections 9 and 12.

Reading section 12, I am not at all sure your device will work with Kismet. I suggest you try a few likely looking Atheros settings and see what works. Perhaps something like:```
source=ath5k,wlan1,atheros
```You might also Google for kismet and ath9k_htc.

---

### Post by chili555 on 2011-01-22
Please see:

[http://www.kismetwireless.net/Forum/General/Messages/1231702725.208456](http://www.kismetwireless.net/Forum/General/Messages/1231702725.208456)> ath9k should use the same capture code as ath5k so while I don't generally recommend using the "wrong" source that shouldn't be the problem here. 

---

