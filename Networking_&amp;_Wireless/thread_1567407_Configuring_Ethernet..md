---
title: "Configuring Ethernet."
date: 2010-09-03
forum: Networking &amp; Wireless
---

### Post by s.v.z on 2010-09-03
Hi everyone! I`ve got a laptop with Ubuntu 10.04 which is with me all the time. There is a number of places where I need to connect to the Ethernet LAN. To do that I must manually specify the ip address and all the stuff and even MAC-address. As you can guess it is a bit of trouble to do ifconfig ether hw xx:yy... all the time. I tried to add new wired connections from the network manager applet, but they do not appear int the network choice list. So, is there a way to save some presets (which must include MAC-address as well as network configuration) and easily switch between them?

---

### Post by Iowan on 2010-09-03
The next step up from remembering the information would be to keep it in a text file on the desktop and copy/paste. On my Jaunty laptop, I kept a "manual" configuration for when my DHCP failed. I'd think (and probably be mistaken) that you should be able to set up multiple connections and activate which one you need...

---

### Post by BkkBonanza on 2010-09-03
Why not just have a small script that lists a menu of locations and when you choose one (enter number) it does the ifconfig for you.

eg. untested, simplistic, could be better, but easy to edit

```
#!/bin/bash

loc[1]="Home"
cmd[1]="ether hw xx:xx: etc etc"
loc[2]="School"
cmd[2]="you get the idea"

for n in {1..2}; do
  echo "$n ${loc[$n]}"
done

echo "Choose network:"
read c

sudo ifconfig ${cmd[$c]}

```

I use Wicd, which has profiles, but I don't think the profiles support different MAC addresses. It does have pre/post scripting though which could do the MAC change.

Another option would be to have several interfaces files and just copy the current choice over the default one, then restart networking.

---

### Post by s.v.z on 2010-09-04
> **BkkBonaza said:**
> ... Why not just have a small script that lists a menu of locations and when you choose one (enter number) it does the ifconfig for you.
I`m quite new to Linux, so I just didn`t think of that. But for now this seems to be the best idea.


> **Iowan said:**
> ... I'd think (and probably be mistaken) that you should be able to set up multiple connections and activate which one you need...

I`ve tried to do that but as I said, after I created new connections I just couldn`t see them in the network choice list. I opened the Network Manager applet, chose "add new connection" or whatever and configured it the way I needed. But after that I could see only the default "Auto eth0" connection in the choice list. Is this some kind of bug, or is it me doing something wrong?

---

