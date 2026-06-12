---
title: "Ubuntu Studio 8.04 JACK in realtime problem"
date: 2008-05-07
forum: Multimedia Software
---

### Post by nlz on 2008-05-07
I've installed Ubuntu studio 8.04, and it is really nice and stable. Also really sweet software and enhancements since studio 7.10.

But JACK & realtime seem to be ill configured.

I tried editing limits.conf but whatever I did, (adding my user to limits.conf) I didn't result in getting Jack to work in RT, it keeps on giving

```

cannot use real-time scheduling (FIFO at priority 99) [for thread -1228596336, from thread -1228596336] (1: Operation not permitted)
```
or
```
cannot lock down memory for RT thread (Cannot allocate memory)
```

on startup.

What can I do? I also couldn't add the group AUDIO.

---

### Post by MetalMusicAddict on 2008-05-07
If you didn't install Studio from disk then you did not really install studio. There are settings your current user wont get if you simply installed the packages. Please post your limits.conf file.

As for the second memory error. Use "System->Admin->Ubuntu Studio Controls" to allocate the amount of memory you want to lock.

---

### Post by nlz on 2008-05-08
PC 1:


```
@audio          -       rtprio          99

@audio - memlock 177794
```

and still:

```
configuring for 44100Hz, period = 512 frames (11.6 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 2 periods for playback
JACK: unable to mlock() port buffers: Cannot allocate memory
JACK: unable to mlock() port buffers: Cannot allocate memory
10:25:50.921 Server configuration saved to "/home/brezjnev/.jackdrc".
10:25:50.925 Statistics reset.
10:25:50.990 Client activated.
10:25:51.005 JACK connection change.
10:25:51.016 JACK connection graph change.
cannot lock down memory for RT thread (Cannot allocate memory)
```

PC 2:

```

# rtprio
@audio - rtprio 90
@audio - nice -5
@audio - memlock 1113495

trotski - rtprio 90
trotski - nice -5
trotski - memlock 500000

```

and gives:
```

ALSA: final selected sample format for capture: 32bit little-endian
ALSA: use 8 periods for capture
ALSA: final selected sample format for playback: 32bit little-endian
ALSA: use 8 periods for playback
cannot use real-time scheduling (FIFO at priority 99) [for thread -1227936880, from thread -1227936880] (1: Operation not permitted)
```


Indeed i installed with the normal version and then selected all the studio packages in synaptic. But this went well in 7.10...

thanks..

BTW when i run sudo qjackctl, there is no problem.

---

### Post by warbread on 2008-05-08
I have never put my user into the limits.conf file.  I would delete or comment out the lines with your user name and change the '90' for rtprio to '99'.  Log out, log back in and then try it.

---

### Post by nlz on 2008-05-12
on one computer i go it working now, but my laptop still gives me problem. I got Ubuntu Studio controls set at 50% memlock (which should be OK with 2 gb of RAM)

I posted my info underneath. Any ideas?

Limits.conf
```

# rtprio
@audio - rtprio 90
@audio - nice -5
@audio - memlock 1031014

# End of file
trotski@wolga:~$ 

```

Jack message output```

creating alsa driver ... hw:0|hw:0|64|6|32000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 32000Hz, period = 64 frames (2.0 ms), buffer = 6 periods
ALSA: final selected sample format for capture: 32bit little-endian
ALSA: use 6 periods for capture
ALSA: final selected sample format for playback: 32bit little-endian
ALSA: use 6 periods for playback
cannot use real-time scheduling (FIFO at priority 99) [for thread -1228907632, from thread -1228907632] (1: Operation not permitted)
16:32:09.582 Server configuration saved to "/home/trotski/.jackdrc".
16:32:09.584 Statistics reset.
16:32:09.888 Client activated.
16:32:09.890 JACK connection change.
16:32:09.892 JACK connection graph change.
16:32:11.132 Client deactivated.
16:32:11.134 JACK is stopping...
jack main caught signal 15
no message buffer overruns
16:32:11.154 JACK was stopped successfully.
16:32:11.154 Post-shutdown script...
16:32:11.155 killall jackd
jackd: no process killed
16:32:11.564 Post-shutdown script terminated with exit status=256.
```

---

### Post by nlz on 2008-05-12
I found it! Just put the priority up and the nice down..
```

@audio - rtprio 99
@audio - nice -10
@audio - memlock 1031014
```

but latency sucks big time in hardy. Where i had <10 msecs in Gutsy i have 20> in Hardy and still Xruns! But that problem is discussed here: [http://ubuntuforums.org/showthread.php?t=781104&highlight=xruns&page=1](http://ubuntuforums.org/showthread.php?t=781104&highlight=xruns&page=1)

---

### Post by CheShA on 2008-05-12
> **MetalMusicAddict said:**
> If you didn't install Studio from disk then you did not really install studio. There are settings your current user wont get if you simply installed the packages. Please post your limits.conf file.


:( I can only install from packages because I need to install on top of dmraid array :(

---

### Post by nlz on 2008-05-12
> **CheShA said:**
> :( I can only install from packages because I need to install on top of dmraid array :(

if you install the packages and alter the limits.conf you'll have the same effect, so no worries..

---

### Post by CheShA on 2008-05-13
> **nlz said:**
> if you install the packages and alter the limits.conf you'll have the same effect, so no worries..

Cheers for that. Also obviously minor edits to users and groups (i.e. adding my user to admin, audio groups) which I have done. I had an unanswered  post from a couple of weeks ago asking just that - what will it take to completely install Studio from apt - I guess I will go and answer it now for posterity.

Ubu Studio is niiice. I last tried it at v1.0 (before Canonical took it under its wing) and it's really come on now it's an official derivative, but they definitely need to get the live CD installer working if there are things which can't be done with the package installation.

---

### Post by nlz on 2008-05-14
I didn't need to add any groups/users. I just installed 8.04 with liveCD and then selected all the ubuntu studio packages in synaptic (system> administration > synaptic package manager). 
The one thing is that you have to edit the limits.conf and the menu.lst as described here: [http://ubuntuforums.org/showthread.php?t=781104&page=3](http://ubuntuforums.org/showthread.php?t=781104&page=3)

---

### Post by CheShA on 2008-05-14
> **nlz said:**
> I didn't need to add any groups/users. I just installed 8.04 with liveCD and then selected all the ubuntu studio packages in synaptic (system> administration > synaptic package manager). 
The one thing is that you have to edit the limits.conf and the menu.lst as described here: [http://ubuntuforums.org/showthread.php?t=781104&page=3](http://ubuntuforums.org/showthread.php?t=781104&page=3)

I see. I installed entirely via apt-get by manually bootstrapping my disks and then installing linux-image-rt, ubuntu-standard, ubuntustudio-desktop, etc  into chroot environment so I also had to add my user account to the admin and audio groups but thats about it. Worth the small amount of extra effort to have a fully clean system without extra ubuntu-desktop cruft ;)

---

### Post by n00rt on 2008-09-09
hi - i have the message unable to lock down realtime memory but my user name is in the audio group and my limits.conf file is as described in this thread - when i run sudo qjackctl the message doesn't come up - any ideas on what to check? also using my usb soundcard works without xruns but the internal intel one gets hundreds in seconds -again - any ideas as i need to use that internal soundcard when not at my desk.

thanks
btw running hardy.

---

