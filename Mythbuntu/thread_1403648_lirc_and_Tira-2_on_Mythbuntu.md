---
title: "lirc and Tira-2 on Mythbuntu"
date: 2010-02-10
forum: Mythbuntu
---

### Post by brplut40 on 2010-02-10
Since I had such a hard time finding instructions on how to setup a Homelectronics Tira 2 USB IR receiver in Mythbuntu, I figured I would write up the directions. The tira receiver can be bought from homelectronics at [http://www.home-electro.com/tira2.php](http://www.home-electro.com/tira2.php) The main advantage of this receiver is it uses USB instead of serial. Follow the directions found on the Ubuntu community help site [https://help.ubuntu.com/community/Lirc_USB-UIRT ]("https://help.ubuntu.com/community/Lirc_USB-UIRT")except make these changes to /etc/lirc/hardware.conf
```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="None"
REMOTE_MODULES=""
[COLOR=Red]REMOTE_DRIVER="tira"[/COLOR]
REMOTE_DEVICE=""
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF=""
[COLOR=Red]REMOTE_LIRCD_ARGS="-d /dev/ttyUSB0"[/COLOR]

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
[COLOR=Red]START_LIRCD="true"[/COLOR]

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="false"


```you may also find the following command helpful to generate a lircd.conf file for your remote.```
irrecord -H tira -d /dev/ttyUSB0 remotename
```

---

### Post by dmcg on 2010-02-12
Thanks for this.  I've been trying to do the same setup.  I basically got to the same point you did but I still don't see anything when I run irw.  Are you able to see a response?

---

### Post by one30nav on 2011-07-23
brplut40, thanks for this awesome post. May your beer never run out.

I've wanted to get my Tira-2 working for so long and this did the trick. You definitely have to use "irrecord -H tira -d /dev/ttyUSB0 remotename" to generate a unique lircd.conf file for your remote.

One more gotcha that took me weeks to research: Tira-2 was failing to work after a reboot and I had to plug it in again for it to be recognized (hotplug). I found out that the mythfrontend startup sequence was somehow interrupting with the lirc start.

I resolved this by putting a "sleep 15" delay in the mythfrontend script. After that, things work great!

Tira-2 with my One-For-All URC-8820N remote (as some have said) works like it's wireless - so fast. It's truly a wonderful IR receiver. Hope this helps folks with their MythTV setups.

Again, make this change by: sudo nano /usr/bin/mythfrontend
```
[COLOR="Red"]**sleep 15**[/COLOR]

pidof mythfrontend.real 2>&1 >/dev/null && wmctrl -a "MythTV Frontend" 2>/dev/null && exit 0

```

---

