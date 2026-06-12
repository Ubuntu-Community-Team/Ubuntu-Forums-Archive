---
title: "Unloading PVR-150 before S3 Sleep"
date: 2010-06-12
forum: Mythbuntu
---

### Post by dtaylorl on 2010-06-12
I am using S3 sleep (suspend) to save power on my MythTV frontend/backend machine while it is not in use. Unfortunately, whenever it wakes up my PVR 150 card doesn't want to work. If I understand correctly the way to solve this would be to unload the card before sleep and then reload it on wakeup. Can anyone help me find the correct procedure to do this?  Which modules will I need to unload?

---

### Post by ian dobson on 2010-06-13
Hi,

The pvr150 uses the ivtv modules, so you need to unload them. If your running 10.04 you should be able to create a upstart job that starts on standby, which just unloads the ivtv modules.

Sorry but I can't help you much more than this.

Regards
Ian Dobson

---

### Post by dtaylorl on 2010-06-13
Would you be able to steer me in the right direction as to where I might be able to find the names of these ivtv modules?

I am using a script at "/usr/lib/pm-utils/sleep.d/00mythlirc" to unload/reload lirc and my remote works fine after wakeup.  I added some modules which I think are for ivtv to that script but it doesn't seem to be making a difference.  What am I missing here?
```

#!/bin/bash

. /usr/lib/pm-utils/functions

case "$1" in
	suspend|hibernate)
		/etc/init.d/lirc stop
		
		modunload lirc_mceusb2 lirc_dev ivtv saa7134_dvb saa7134_alsa saa7134
		;;

	resume|thaw)
		modreload lirc_mceusb2 lirc_dev ivtv
		/etc/init.d/lirc start
		irexec -d
		sleep 2
		modreload saa7134_dvb saa7134_alsa saa7134
		sudo -u dustin mythwelcome &
                ;;
esac

```

---

### Post by ian dobson on 2010-06-13
Hi,

Just go to the termnal and do a lsmod. The pvr150 module is called ivtv, so you need to unload it and any other modules that depend on it/uses it.

Regards
Ian Dobson

---

### Post by dtaylorl on 2010-06-14
Thank you, lsmod is exactly what I was looking for.  Looking at my log files it also turned out that my unload/reload script was not executable (which would indicate I don't actually need to unload lirc before sleep).  Oops!  After that it still wasn't working, but I found [another thread](http://www.gossamer-threads.com/lists/mythtv/users/363922) which seemed to indicate that the modules have to be loaded in a very specific order like so:
```

rmmod ivtv saa7134_dvb saa7134_alsa saa7134 tuner --force 
sleep 3 
modprobe saa7134-alsa 
modprobe ivtv 
sleep 3 
rmmod --force tuner 
rmmod --force ivtv 
modprobe tuner 
modprobe ivtv

```
It is working now, although it has created a new problem where the computer wakes itself up as soon as it goes to sleep.  Thanks for the help.

Edit: fixed the problem with the computer waking itself up by only unloading ivtv, saa7134_dvb, saa7134_alsa, saa7134.

---

### Post by dtaylorl on 2010-06-19
I'm having a similar problem now with DVD playback not working after wakeup.  Does something need to be unloaded here as well?

---

