---
title: "Call shell script on network change"
date: 2011-01-21
forum: Networking &amp; Wireless
---

### Post by b0wter on 2011-01-21
Hi,
I have a script that I would like to run when my laptops connects to a new network (e.g. changes to another SSID). I've done some searching on the net but could not find any suitable solution (but I bet there is). Can anyone give me a hint please?

---

### Post by ripat on 2011-01-21
What have you done so far?

---

### Post by b0wter on 2011-01-21
Basically all I've done was searching on google as I am not a really experienced Linux user :>
What I found is e.g. that the NetworkManager sends a message on dBus but that would requite a programm to run permanently to check for them!?

Maybe I have not searched for the right keywords.

---

### Post by b0wter on 2011-01-21
Ok, I finally found something that looks like it could help.
(searching for 'interface' gave much better results)

[http://www.cyberciti.biz/tips/how-do-i-run-firewall-script-as-soon-as-eth0-interface-brings-up.html](http://www.cyberciti.biz/tips/how-do-i-run-firewall-script-as-soon-as-eth0-interface-brings-up.html)

It says that I have to copy the script to 
```
# /etc/network/if-up.d/
```
and then edit
```
/etc/network/interfaces
```
and append
```

post-up /etc/network/if-up.d/my_script.sh

```
und the eth0 configuration section (I hope for wlan0 to work too) but the problem is that the file does not contain anything abouth eth0 :[
It just looks like:
```

auto lo
iface lo inet loopback

```
So is the information on that webpage outdated? Or should I simply add auto eth0 and/or auto wlan0 ?

---

### Post by ripat on 2011-01-21
If your interfaces file only contains these two lines, it means that network-manager is in charge of bringing your interfaces up. Why don't you use NM for the other interfaces (right click on the NM icon) ?

---

### Post by b0wter on 2011-01-21
With the Network Manager I cannot setup any script to be run if the interface goes up (or at least I was not able to find it).

---

### Post by gmargo on 2011-01-21
The Network Manager still runs the scripts under **/etc/network/if-*.d/**.  You don't need to specify it in the /etc/network/interfaces file.  (See /etc/NetworkManager/dispatcher.d/01ifupdown, which invokes run-parts.)

BTW, I just spent a bunch of time figuring out that a script named "my_script.sh" will not run - it must conform to a naming convention without a suffix and so must be called only "my_script".

Here's a sample script, which I call "iface_changed" (formerly iface_changed.sh).  Put this somewhere and point symbolic links at it from all of the /etc/network/if-*.d/ directories.  It just logs info into a temp file, so that you can see what happens during network state transitions.

```

#!/bin/sh
# Do something for an interface state change.

# From interfaces(5) man page:
# All  of  these  commands have access to the following environment vari&#8208;
# ables.
#
# IFACE  physical name of the interface being processed
#
# LOGICAL
#        logical name of the interface being processed
#
# ADDRFAM
#        address family of the interface
#
# METHOD method of the interface (e.g., static)
#
# MODE   start if run from ifup, stop if run from ifdown
#
# PHASE  as per MODE, but with finer granularity, distinguishing the pre-
#        up, post-up, pre-down and post-down phases.
#
# VERBOSITY
#        indicates whether --verbose was used; set to 1 if so, 0 if not.
#
# PATH   the   command   search   path:  /usr/local/sbin:/usr/local/bin:&#8208;
#        /usr/sbin:/usr/bin:/sbin:/bin


OUT=/tmp/iface-state.txt

echo "------------------"          >> $OUT
date                               >> $OUT
echo "Physical Interface: $IFACE"  >> $OUT
echo "Logical Interface: $LOGICAL" >> $OUT
echo "Phase: $PHASE"               >> $OUT
echo "Mode: $MODE"                 >> $OUT
echo "------------------"          >> $OUT

exit 0

```

---

