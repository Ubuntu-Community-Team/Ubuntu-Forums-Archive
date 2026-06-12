---
title: "how to set bluetooth radio default off (afrer booting)?"
date: 2009-11-21
forum: Networking &amp; Wireless
---

### Post by maiko29 on 2009-11-21
Currently, the bluetooth radio is by default allways  on after booting. How to set bluetooth radio default off?

---

### Post by chili555 on 2009-11-21
You may have to look around in /proc/acpi to find where this is in your system. I suggest:```
sudo gedit /etc/rc.local
```Add a line above 'exit 0' as follows:```
echo "disabled" > /proc/acpi/ibm/bluetooth
```This may or may not be located in /proc/acpi/[COLOR="Red"]ibm[/COLOR] in your system, please look around and customize to suit. On boot, the bluetooth LED blinks off in the last few seconds for me.

---

### Post by Wollombi on 2009-12-01
I've found this to work better:

Still edit the /etc/rc.local file, but instead add this line:
```
rfkill block bluetooth
```

This will keep bluetooth turned off when you boot/login but you can still turn it on at will with the bluetooth applet in the panel.

---

### Post by cyberjar09 on 2011-02-03
> **Wollombi said:**
> I've found this to work better:

Still edit the /etc/rc.local file, but instead add this line:
```
rfkill block bluetooth
```

This will keep bluetooth turned off when you boot/login but you can still turn it on at will with the bluetooth applet in the panel.

Brilliant! it worked like a charm ... thanks!

---

### Post by SilverZero on 2011-02-20
I know this is a very old thread and all, but I had to chime in to say this worked great on my CR-48! Thanks!

---

### Post by mattsloper on 2011-02-25
> **Wollombi said:**
> I've found this to work better:

Still edit the /etc/rc.local file, but instead add this line:
```
rfkill block bluetooth
```This will keep bluetooth turned off when you boot/login but you can still turn it on at will with the bluetooth applet in the panel.


Worked perfectly, bluetooth applet is still running and can turn it back on, but radio is off after boot! :) :) :)

*edit: This turns off the bluetooth LED on my ThinkPad as well, so it actually turns it off, in case others wanted to know...
the only problem is, when I turn bluetooth on, then off again, for some reason the bluetooth-applet icon goes away, but can still use it through System -> Preferences -> Bluetooth
(didn't do this before, but not a real issue)

Thanks for the post!

---

### Post by kwaanens on 2011-11-04
This worked for me on Natty, but I have since upgraded to Oneiric. /etc/rc.local still contains the line, but bluetooth is still on by default. Any advice?

---

### Post by [Knuckles] on 2011-12-08
> **kwaanens said:**
> This worked for me on Natty, but I have since upgraded to Oneiric. /etc/rc.local still contains the line, but bluetooth is still on by default. Any advice?

For me, I noticed that at least on Ubuntu 11.10 (Oneiric), you can run rfkill without any other special permissions, so I just added
```
rfkill block bluetooth
```
to gnome's "Startup Applications..." configuration menu.

If it still doesn't work for you, try running the command in the terminal and see if you get some error back.

---

### Post by kwaanens on 2011-12-09
Thanks [Knuckles], that worked like a charm.
Funnily enough, bluetooth is reenabled after the computer is back from suspend, so if you or anyone know how to deal with that as well, I'd much appreciate it!

---

### Post by [Knuckles] on 2011-12-11
> **kwaanens said:**
> Thanks [Knuckles], that worked like a charm.
Funnily enough, bluetooth is reenabled after the computer is back from suspend, so if you or anyone know how to deal with that as well, I'd much appreciate it!

I haven't tried this, but it should work.

Create a file in /etc/pm/sleep.d/ called 70_disablebluetooth with the following contents.

```

#!/bin/bash
case $1 in
    thaw|resume)
        rfkill block bluetooth
        ;;
    *)
        ;;
esac

exit $?

```

Don't forget to mark it as executable:
sudo chmod +x /etc/pm/sleep.d/70_disablebluetooth

---

### Post by kwaanens on 2011-12-11
Thanks! I'll give it a shot.

---

### Post by kwaanens on 2011-12-12
Sadly that script does not seem to work. Bluetooth is still enabled after waking up from suspended state.

---

### Post by CallsignBaron on 2012-07-28
Thank you Wollombi, works brilliantly in 12.04! Bluetooth is off by default and still usable if needed. =)

Late 2008 13" Macbook (aluminum), Ubuntu 12.04/Unity.

---

