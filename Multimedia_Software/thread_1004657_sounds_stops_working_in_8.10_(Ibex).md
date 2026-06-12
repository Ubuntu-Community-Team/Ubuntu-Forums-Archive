---
title: "sounds stops working in 8.10 (Ibex)"
date: 2008-12-07
forum: Multimedia Software
---

### Post by edwinw on 2008-12-07
When I first start the computer, sound is working fine.  However, the problem is that sound stops working in all applications after a certain amount of time, usually over 12 hours.  Rebooting is a workaround (simply logging in and out is doesn't work) but is an annoyance for obvious reasons.

When I go into sound settings to test them, I get the error message:

```

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

```

Googling this error message comes up with hits for people in which sound is not working at all right off the bat.  Nobody seems to have quite my problem.

I took a look at my system messages log file and this entry seems to be relevant (I'm guessing it's the time my system loses its sound ability):

```

Dec  7 12:22:55 edwin-desktop3 pulseaudio[5419]: protocol-native.c: Failed to push data into queue
Dec  7 12:22:56 edwin-desktop3 last message repeated 1498 times

```

So this appears to be a pulseaudio problem, anybody have any ideas on how to fix it?  Thanks!

---

### Post by tomszyszko on 2008-12-09
Exact same problem
```
Dec  9 11:56:51 tom-laptop2 pulseaudio[6025]: protocol-native.c: Failed to push data into queue
```

Its very annoying. Also found that if you:
```
killall pulseaudio
sudo pulseaudio
```

You get
```
 sudo pulseaudio
W: ltdl-bind-now.c: Failed to find original dlopen loader.
W: main.c: This program is not intended to be run as root (unless --system is specified).
E: alsa-util.c: Error opening PCM device hw:0: Device or resource busy
E: module.c: Failed to load  module "module-alsa-sink" (argument: "device_id=0 sink_name=alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0"): initialization failed.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0

```

---

### Post by tomszyszko on 2008-12-09
Found a workaround.
If sound stops working do :
```
killall pulseaudio
sudo alsa force-reload
```

Sound starts working.

---

### Post by edwinw on 2008-12-09
Thanks tomszyszko, will try it out next time my sound cuts out, I'll keep on looking for a fix as well.

---

### Post by psyke83 on 2008-12-09
> **tomszyszko said:**
> Exact same problem
```
Dec  9 11:56:51 tom-laptop2 pulseaudio[6025]: protocol-native.c: Failed to push data into queue
```

Its very annoying. Also found that if you:
```
killall pulseaudio
sudo pulseaudio
```

The next time this happens, try the following instead:
```
killall pulseaudio
pulseaudio -vv
```

In other words, check the verbose output - and don't run as root. Ubuntu is configured to launch PulseAudio as a user process (spawned from gnome-session-daemon in Intrepid, and via a Gnome Session startup entry for Hardy), so running it as superuser may cause problems.

I've observed users reporting problems with PulseAudio crashing only for certain sound cards, due the tweaked buffering in Ubuntu's PulseAudio.

Edit /etc/pulse/default.pa, and change this:
```
default-fragments = 8
default-fragment-size-msec = 10
```

To this:
```
; default-fragments = 8
; default-fragment-size-msec = 10
```

This will force the internal fragment settings for PulseAudio and may increase stability in your case.

See here for information on PulseAudio (including some recommended troubleshooting steps): [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by Burmuda on 2008-12-23
> **psyke83 said:**
> 
Edit /etc/pulse/default.pa, and change this:
```
default-fragments = 8
default-fragment-size-msec = 10
```

To this:
```
; default-fragments = 8
; default-fragment-size-msec = 10
```


Found this settings in /etc/pulse/daemon.conf and disabled them.

I also added myself to the pulse-rt and pulse group (Administration -> User and Groups). But when I play music over pulseaudio the sound or even the whole X still hangs some times... 

I'm using powernowd - could this be a problem? It shouldn't....

```
lspci | grep Audio
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
01:00.1 Audio device: ATI Technologies Inc RV630/M76 audio device [Radeon HD 2600 Series]
```

> See here for information on PulseAudio (including some recommended troubleshooting steps): [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
I reinstalled pulseaudio like described there - didn't help.

---

### Post by alex1973 on 2008-12-24
Sound stopped working 2-3 days ago. Restarting alsa and pulse fixes the sound until restart.

I'm on Intrepid with "proposed" enabled and [http://ppa.launchpad.net/psyke83/ubuntu](http://ppa.launchpad.net/psyke83/ubuntu).

$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
01:00.1 Audio device: ATI Technologies Inc RV630/M76 audio device [Radeon HD 2600 Series]

---

### Post by caro on 2008-12-24
Thanks psyke83 and tomszyszko!

---

### Post by Subban on 2008-12-25
> **tomszyszko said:**
> Found a workaround.
If sound stops working do :
```
killall pulseaudio
sudo alsa force-reload
```

Sound starts working.

Same problem has been bugging me also, this workaround gets sound back without a reboot, as noted earlier log out/log in isn't enough to fix it.

---

### Post by jsully1 on 2009-01-19
This is now suddenly happening to me on my Thinkpad T60 as well as my Asus M2N desktop all within the last few weeks.  Then today it just started happening out of the blue today to a colleague.  It's strange to me that this would come up out of the blue on three unique machines - is anyone else experiencing this suddenly?

---

### Post by cokeonice on 2009-01-22
This just started happening to me too.

Perhaps an update broke it?

I am going to reload.  It does not take long.

---

### Post by PPPP on 2009-01-28
> **Subban said:**
> Same problem has been bugging me also, this workaround gets sound back without a reboot, as noted earlier log out/log in isn't enough to fix it.

Same here.  The work around works but would like a working solution.

---

### Post by GreatestGravity on 2009-02-10
Based on my google, it seems the PulseAudio folks know this and it's a bug on their end... 

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/288093](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/288093) 

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/219672](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/219672)

They claim it is fixed in PulseAudio 0.9.14, which is a recent version that Intrepid does not have. 

Doesn't seem to be any working solution other than wait for the patch. :(

---

### Post by joaopereira on 2011-07-28
My sound fails precisely 18h15m after the computer starts.

I have an Ubuntu 10.04 that reboots automatically every night at 00:30.
This computer is playing audio and video all day... and at 18:45 each day the sound stops (video doesn't stop).
The sound is interrupted at 18:45 and re-starts at 19:00.

This happens every day.

I found this errors in /var/log/messages


Jul 26 18:44:32 insight-desktop pulseaudio[1950]: ratelimit.c: 9134 events suppressed   
Jul 26 18:44:32 insight-desktop pulseaudio[1950]: protocol-native.c: Failed to push data into queue
Jul 26 18:44:37 insight-desktop pulseaudio[1950]: last message repeated 8 times
Jul 26 18:44:37 insight-desktop pulseaudio[1950]: ratelimit.c: 10623 events suppressed
Jul 26 18:44:37 insight-desktop pulseaudio[1950]: protocol-native.c: Failed to push data into queue
Jul 26 18:44:42 insight-desktop pulseaudio[1950]: last message repeated 10 times
Jul 26 18:44:42 insight-desktop pulseaudio[1950]: ratelimit.c: 7143 events suppressed 
Jul 26 18:44:42 insight-desktop pulseaudio[1950]: protocol-native.c: Failed to push data into queue
Jul 26 18:44:47 insight-desktop pulseaudio[1950]: last message repeated 10 times
Jul 26 18:44:47 insight-desktop pulseaudio[1950]: ratelimit.c: 13099 events suppressed
Jul 26 18:44:47 insight-desktop pulseaudio[1950]: protocol-native.c: Failed to push data into queue
Jul 26 18:45:29 insight-desktop pulseaudio[1950]: last message repeated 10 times
Jul 26 18:45:29 insight-desktop pulseaudio[1950]: ratelimit.c: 5283 events suppressed 


My Pulse Audio version is "pulseaudio 0.9.21-63-gd3efa-dirty"

How can I fix this issue in PulseAudio?

Thanks
Regards
Joao Pereira

---

