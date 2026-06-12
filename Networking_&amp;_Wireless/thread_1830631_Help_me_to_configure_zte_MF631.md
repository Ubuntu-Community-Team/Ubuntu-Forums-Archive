---
title: "Help me to configure zte MF631"
date: 2011-08-22
forum: Networking &amp; Wireless
---

### Post by Hamerins on 2011-08-22
Hi all,

I am using ubuntu 11.04 64bit and i am finding difficulty in configuring the ZTE MF631 usb modem. I configured the dialer but when ever i connect the device and dial it, it disconnects automatically. 


Please help me.


Thanks in advance

---

### Post by gradinaruvasile on 2011-08-22
Try it with the Sakis3g script:

[http://www.sakis3g.org/](http://www.sakis3g.org/)

Most USB modems work with it. I recommend using it like this:

```

sakis3g --console --interactive

```

In a terminal - this is because the default graphical version is kinda funky and leaves tons of zombie processes behind.

Usage tips:

- You have to kill modem-manager (that is part of network-manager) to allow access to the USB modem (in a terminal):
```

sudo killall modem-manager

```
- You have to enter something (anything, 1 letter or digit is suffice, only dont let them blank) in the fields of user and password when asked (provided that you dont need user and pass of course - by default you dont).
- The PIN code can be preset if you create a blank file in your home dir and enter the modems PIN code:
```

nano $HOME/.3gpin

```
enter your PIN code, save with ctrl-o and exit with ctrl-x.

Example for advanced command line usage - this presets the APN to "internet", user to "user" and password to "pass" so you dont have to deal with them later (change to what you actually need especially the APN).

```

#!/bin/bash
sudo killall modem-manager
FORCE_APN="internet" APN_USER="user" APN_PASS="pass" sakis3g --console --interactive connect

```
This can be saved in a script [COLOR="Red"]that runs in a terminal[/COLOR] so you have just to double click on it after the modem is inserted (this kills the modem manager process to permit the script to access the device).
If you ran sakis3g once, you will find its icon here if you want to add it as the scripts icon:
```

$HOME/.local/share/icons/sakis3g.png

```

---

### Post by praseodym on 2011-08-22
Can you show the outputs of:

```
lsusb
usb-devices
```

---

### Post by Hamerins on 2011-08-23
I am attaching the output of lsusb

---

### Post by lkjoel on 2011-08-23
Could you run the Network Info script (in my signature), and attach the generated file (NETWORK-INFO.txt.gz)?

---

### Post by Hamerins on 2011-08-24
Hi lkjoel,


I am getting the error in line number 31 while running the script.

---

### Post by pdc on 2011-08-24
If we sort of start from the beginning .....

these modems are seen firstly as virtual CD-ROM devices;

and then need to be switched so they are seen as modems

from the ID you gave

> 19d2:2003

this device is switched and is seen as a modem

....... so it should be ready to go ....

> *I configured the dialer* .....

this is interesting;

which country are you in? which network do you want to connect to?

Please tell us

Network Manager should manage the connection for you ........

> *I configured the dialer* ....

makes me thing you want to use wvdial or somesuch programme?

---

### Post by lkjoel on 2011-08-24
What's the error message?

---

### Post by Hamerins on 2011-08-25
Hi all,


Thanks for all your replays and suggestions. 

I have fixed the issue by downgrading ubuntu to 10.04.2 LTS from 11.04. I am able to connect to internet.
Ubuntu 10.04.2 LTS detects my usb modem with out any problem. But in ubuntu 11.04 when i click on connect, it automatically disconnects.

I am from India and My configuration settings are

Dial Number:*99#
APN: tatadocomo3g


I am able to browse the internet with out disconnection also.

Thanks all

---

