---
title: "Run startup script as root"
date: 2011-08-10
forum: Mythbuntu
---

### Post by zagor on 2011-08-10
Hi all,

I have mythbuntu 10.04 64bit on my mythbox.
It's a frontend/backend system, mostly off. It wakes up and shuts down via mythwelcome.

Now I need to run a script as root after the backend and wythwelcome has started.
How can I do it?

All through sudo.

Thanks

---

### Post by ian dobson on 2011-08-10
Hi,

Why not just add the required commands to te mythbackend startup script (/etc/init.d/mythtv-backend or /etc/init/mythbackend.conf depending on wether 10.04 uses upstart for myth).

The modules you need could also be loaded by adding them to /etc/modules and setting the required options in /etc/modprobe.d/CONFIG_FILE

Regards
Ian Dobson

---

### Post by ajgreeny on 2011-08-10
Ian Dobson has given the right answer, I think, but for future reference, you can add commands that are run as root to the /etc/rc.local script, and they will then be run at boot-up.

You need to edit that script as root, of course, with ```
gksudo gedit /etc/rc.local
```assuming mythbuntu uses gedit, or use ```
sudo nano /etc/rc.local
``` if you prefer a cli editor.

---

### Post by zagor on 2011-08-10
Thanks for your quick answer.
I'll give it a try this evening and let you know tomorrow.

I was aware of the /etc/rc.local approach, but I'm not sure on how to set the right timing for the script to start, i.e. after mythwelcome.

Ian's suggestion is probably better.
As for the modprobe, instead, I guess it would be better to run it in the mythtv-backend script, for I don't want to risk odd device number inversion for my 3 TV adapters....

Thanks!

---

### Post by ian dobson on 2011-08-10
> **zagor said:**
> Thanks for your quick answer.
I'll give it a try this evening and let you know tomorrow.

I was aware of the /etc/rc.local approach, but I'm not sure on how to set the right timing for the script to start, i.e. after mythwelcome.

Ian's suggestion is probably better.
As for the modprobe, instead, I guess it would be better to run it in the mythtv-backend script, for I don't want to risk odd device number inversion for my 3 TV adapters....

Thanks!

You can deal with the " odd device number inversion " by creating udev rules that create a symbolic link that always points to the same card (/dev/hdpvr -> /dev/videoX)

Regards
Ian Dobson

---

### Post by tgm4883 on 2011-08-10
Please do not bring up banned topics on our forum. Thanks.

*Thread closed*

---

### Post by tgm4883 on 2011-08-11
Reopened as I've removed the banned topic

---

### Post by zagor on 2011-08-11
Thanks for reopening and sorry for missing the netiquette.

I'd just like to report that adding the script to the /etc/rc.local file worked flawlessly.

Now the backend starts, then mythwelcome and frontend.
My script starts and backend restarts as part of the script.
I see it restarting, for I see the message of lost connection during restart.

I've probably been lucky in ending up with the right timing, still it works and I'm glad....:D

I've also received a suggestion on how to edit properly the init file in the presence of upstart: [http://upstart.ubuntu.com/getting-started.html](http://upstart.ubuntu.com/getting-started.html).
I might try that solution as well, but in the meantime I'll stick to rc.local.

Thanks for your precious help!!

Thread marked [solved]


-------------------
My /etc/rc.local file for reference:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
sh /usr/local/bin/my_script.sh
exit 0
```

---

