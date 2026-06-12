---
title: "pulseaudio and jackd in Hardy"
date: 2008-04-29
forum: Multimedia Software
---

### Post by heisters on 2008-04-29
Hi all,

I had ESD and jackd playing nicely: totem and rhythmbox (and anything that used gstreamer) would both automatically detect jack and use it. Then I upgraded to Hardy. 5 hours later, I've installed the Debian sid package pulseaudio-module-jack, tried several pulse configs, tried uninstalling pulseaudio and installing ESD, all to no avail. Here's where things stand at the moment:

```
ian@kasai:~$ uname -a
Linux kasai 2.6.24-16-rt #1 SMP PREEMPT RT Thu Apr 10 15:15:40 UTC 2008 i686 GNU/Linux
ian@kasai:~$ ps ax | grep pulse
 6302 ?        Sl     0:00 /usr/bin/pulseaudio --log-target=syslog
 6305 ?        S      0:00 /usr/lib/pulseaudio/pulse/gconf-helper
 8360 pts/2    R+     0:00 grep pulse
ian@kasai:~$ ps ax | grep jackd
 7911 ?        SLsl   0:46 /usr/bin/jackd -R -P70 -t2000 -dfreebob -r48000 -p102
 8368 pts/2    S+     0:00 grep jackd
ian@kasai:~$ 

```

so pulse is running, jack is running, I've got the RT kernel. I've installed every pulseaudio package I could find. But pulse doesn't seem to be able to connect to jack.

Any ideas?

---

### Post by luctor on 2008-04-30
I followed this guide [http://ubuntuforums.org/showthread.php?p=4795013](http://ubuntuforums.org/showthread.php?p=4795013) and also installed the Debian sid package pulseaudio-module-jack

But i'm not really succesfull at the moment

---

### Post by heisters on 2008-04-30
> **luctor said:**
> I followed this guide [http://ubuntuforums.org/showthread.php?p=4795013](http://ubuntuforums.org/showthread.php?p=4795013) and also installed the Debian sid package pulseaudio-module-jack

But i'm not really succesfull at the moment

Yeah, that's one of the many guides I've tried to follow to no avail.

---

### Post by heisters on 2008-05-04
I seem to have gotten it working with the following pa config:

```

#!/usr/bin/pulseaudio -nF

###
load-module module-jack-sink
load-module module-jack-source
###
#add-autoload-sink output module-jack-sink channels=2
#add-autoload-source input module-jack-source channels=2
#load-module module-esound-protocol-unix
load-module module-native-protocol-unix
load-module module-volume-restore
load-module module-rescue-streams
.nofail

load-module module-x11-publish
load-module module-gconf


```

---

