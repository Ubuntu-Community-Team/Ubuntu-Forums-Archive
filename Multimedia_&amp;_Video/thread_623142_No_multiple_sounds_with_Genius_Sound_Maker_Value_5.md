---
title: "No multiple sounds with Genius Sound Maker Value 5.1!!"
date: 2007-11-25
forum: Multimedia &amp; Video
---

### Post by saz on 2007-11-25
Hi there!

so here is the problem, just bought this sound card (Genius Sound Maker Value 5.1) but it wouldn't play 5.1 channels only on 4... then i found this thread:

[http://ubuntuforums.org/showthread.php?t=251380&highlight=genius+soundcard](http://ubuntuforums.org/showthread.php?t=251380&highlight=genius+soundcard)

and got all the 6 channels to work (fully tested with "speaker-test -c 6 -D surround51")

after getting that one solved i'm up with another problem, no multiple sounds... -.-'..

so here is my ".asoundrc" file that got me full 5.1 support:

```

# 6 channel dmix:
pcm.dmix6 {
type dmix
ipc_key 1024
ipc_key_add_uid false
ipc_perm 0660
slave {
pcm "hw:0,1"
rate 48000
channels 6
period_time 0
period_size 1024
buffer_time 0
buffer_size 5120
}
}

# upmixing:
pcm.ch51dup {
type route
slave.pcm dmix6
slave.channels 6
ttable.0.0 1
ttable.1.1 1
ttable.0.2 1
ttable.1.3 1
ttable.0.4 0.5
ttable.1.4 0.5
ttable.0.5 0.5
ttable.1.5 0.5
}
#this is what i added which gaved my surround in ac3 movies
pcm.!default {
type plug
slave.pcm "surround51"
slave.channels 6
route_policy duplicate
}
```

and here is my "/etc/asound.conf":

```
pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"

}


pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:0,0"
period_time 0
period_size 2048	#1024
buffer_size 32768	#4096
			#periods 128
rate 48000		#44100
}
bindings {
0 0
1 1
}
}
```

don't know if it will be useful but here is my "/etc/esound/esd.conf" file:

```
[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=
```

anyone can help me with this??

---

### Post by saz on 2007-11-26
c'mon guys... i really need to solve this one out... pls help...

---

### Post by saz on 2007-11-26
anyone pls....

---

### Post by saz on 2007-11-28
pls guys... someone at least try to help me with this...  i'm in a dead end here..

---

### Post by saz on 2007-11-29
always the same problem on the multimedia section... so many threads that people can't see all...

---

### Post by saz on 2007-12-01
...

---

### Post by sygin on 2008-03-04
Hi,

It would be good if you could explain your problem better. Is it a midi problem? 

To get help it is always a good idea to explain your problem in detail. This will increase your chances of getting  a solution.
Cheers
Sygin

---

### Post by saz on 2008-03-27
SOLVED!

to anyone with the same problem:

[http://alsa.opensrc.org/index.php/Cmipci](http://alsa.opensrc.org/index.php/Cmipci)


if you are to lazy to read that just substitute your asoundrc for this one:

```
# 6 channel dmix:
pcm.dmix6 {
    type dmix
    ipc_key 1024
    ipc_key_add_uid false
    ipc_perm 0660
    slave {
        pcm "hw:0,1"
        rate 48000
        channels 6
        period_time 0
        period_size 1024
        buffer_time 0
        buffer_size 5120
    }
}

# upmixing: 
pcm.ch51dup {
    type route
    slave.pcm dmix6
    slave.channels 6
    ttable.0.0 1
    ttable.1.1 1
    ttable.0.2 1
    ttable.1.3 1
    ttable.0.4 0.5
    ttable.1.4 0.5
    ttable.0.5 0.5
    ttable.1.5 0.5
}

pcm.duplex {
    type asym
    playback.pcm "ch51dup" # upmix first
    capture.pcm "hw:0"
}

# change default device:
pcm.!default {
    type softvol 
    slave.pcm "duplex"
    control {
        name "Software Master"
        card 0
    }
}

# for aoss
pcm.dsp "duplex"

pcm.dsp1 "duplex"
```

works like a charm!

---

### Post by saz on 2008-04-13
[QUOTE=saz]

works like a charm![/QUOTE]

yes it does but i get no sound on flash player... :confused::confused: 

take a look in [http://ubuntuforums.org/showthread.php?t=753438](http://ubuntuforums.org/showthread.php?t=753438)

---

