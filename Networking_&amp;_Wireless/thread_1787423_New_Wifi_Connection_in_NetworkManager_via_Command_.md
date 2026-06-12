---
title: "New Wifi Connection in NetworkManager via Command Line?"
date: 2011-06-21
forum: Networking &amp; Wireless
---

### Post by cRACKmONKEY421 on 2011-06-21
I would like to be able to use NetworkManager via command line and connect to NEW wifi networks with or without security. GUI works fine and all, but I'd like to make it work with a shell script. I've tried other command line options, but nothing seems as stable as NetworkManager. I think I'll have to use GConf and/or dbus. I found some examples here: [http://www.arachnoid.com/linux/NetworkManager/](http://www.arachnoid.com/linux/NetworkManager/) and I can probably piece together the rest, but it sure would speed things up if someone who's already done this could cut and paste me some info. I'll post info if I solve it on my own, but I'm pretty noobish so it'll take a while. Also found the C and Python examples that were named with exactly what I want to do, but I failed to get them working ( [http://cgit.freedesktop.org/NetworkManager/NetworkManager/tree/examples](http://cgit.freedesktop.org/NetworkManager/NetworkManager/tree/examples) ).

---

### Post by iponeverything on 2011-06-21
See my reference to cnetworkmanger referenced in the below thread:

[http://ubuntuforums.org/showthread.php?p=5908963](http://ubuntuforums.org/showthread.php?p=5908963)

it is a python script to interact with nm dbus hooks.

---

### Post by cRACKmONKEY421 on 2011-06-21
Perfect. Thanks!! That is exactly what I was looking for. Sorry for being too stupid to find it myself :P
 
I'll call this one solved as soon as I get my Netbook back and test it, but it looks like exactly what I need.

---

