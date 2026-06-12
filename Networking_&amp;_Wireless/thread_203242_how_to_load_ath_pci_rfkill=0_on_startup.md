---
title: "how to load ath_pci rfkill=0 on startup?"
date: 2006-06-24
forum: Networking &amp; Wireless
---

### Post by Eversmann on 2006-06-24
Hello.

I have a fujitsu amilo l1310g. To make wireless to work (because the wireless button to enable it on the laptop doesn't work) the only way to make it to work is replacing the madwifi driver bundled with the linux-restricted package with the one compile from madwifi.org

That way, you can run modprobe ath_pci rfkill=0 that makes the laptop to bypass the radio state and always turn it on.

The thing is: when i reboot, i have later to run: rmmod ath_pci and then modprobe ath_pci rfkill=0.

I have added the line ath_pci rfkill=0 on the /etc/module file, and tried to disable the module from linux-restricted on /etc/default/linux-restricted-modules-common on the disabled modules ("madwifi madwifi-ng ath_pci ath_hal")

Nothing. 

Do you know guys what i'm doing wrong? i need the restricted package for the fglrx driver. I can always install it from the original ati one... but i would like to let that solution at the bottom of the list (run it before to deal with compiz with not very good results).

Thanks a lot in advance.

---

### Post by adwait on 2006-06-24
You could automatically run these commands. Try this post: [http://ubuntuforums.org/showthread.php?t=78425&highlight=running+startup](http://ubuntuforums.org/showthread.php?t=78425&highlight=running+startup)

Check my post there, which is about 4th in line....

---

### Post by Eversmann on 2006-06-24
Thanks a lot adwait, that resolved the problem !

I tried with sessions in gnome with no luck, but i didn't know about the rcconf tool.

Just created a file named: atheros_activate at /etc/init.d with this simple content:

#!/bin/sh
rmmod ath_pci
wait
modprobe ath_pci rfkill=0
wait

then

chmod 755 atheros_activate

and then with rcconf i enable it on the list.

Hope it helps.

---

### Post by Eversmann on 2006-06-25
Sadly, this doesn't work, or just randomnly. Sometimes causes gnome to hang on gdm start (or maybe just another problem with fglrx module).

I'll have to try with ndiswrapper to see....

---

### Post by Eversmann on 2006-06-25
As usual, it's easier, just you have to know what to do.

I've removed linux-restricted-modules completly (i'll install ati from propietary driver) and just compile madwifi and installed.

Then at /etc/modules added ath_hal and ath_pci

after that, edited /etc/modprobe.d/options and added the line

options ath_pci rfkill=0

voila! working on startup.

---

