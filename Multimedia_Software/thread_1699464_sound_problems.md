---
title: "sound problems"
date: 2011-03-03
forum: Multimedia Software
---

### Post by Cyclane on 2011-03-03
Hello all,

I've visited this forum quite a few times but never took my time to register. Well this time I took the time and maybe this will be the first of many posts. I registered now because I have a problem, I have a problem with my sound and can't seem to get it right. I've been googling for hours but still I don't have the answer so I'm hoping you can help me.

I'm trying to get my sound working properly, at the moment when i use the volume bar it only changes the level of the subwoofer but not my overall sound. What I can do is use alsamixer and turn PCM down and then the volume level will go down.

I used google and I quickly found out that alsa is pointing at the driver and advises to use a softvol ([http://alsa.opensrc.org/How_to_use_softvol_to_control_the_master_volume](http://alsa.opensrc.org/How_to_use_softvol_to_control_the_master_volume))

at first my /etc/asound.conf:
```
pcm.softvol {
    type softvol
    slave.pcm "swap51"
    control {
        name "MasterVolume"
    }
}

pcm.swap51 {
    type dmix
    ipc_key 2048
    slave {
    pcm "hw:CARD=CMI8762,DEV=1"
    rate 48000
    period_time 0
    period_size 1024
    buffer_size 5120
    channels 6
    }
        bindings {
        0 0
        1 1
        2 2
        3 3
        4 4
        5 5
    }
}
pcm.ch51dup {
    type route
    slave.pcm swap51
    slave.channels 6
    ttable.0.0 1
    ttable.1.1 1
    ttable.0.2 1
    ttable.1.3 1
    ttable.0.4 0.5
    ttable.1.4 0.5
}
pcm.dsnooped {
    ipc_key 1026
    type dsnoop
    slave.pcm "hw:CARD=CMI8762,DEV=1"
}

pcm.asymed {
    type asym
    playback.pcm "softvol"
    capture.pcm "dsnooped"
}

pcm.!default {
    type plug
    slave.pcm "asymed"
}
```OK now when I use the command: speaker-test -Dasymed -c6 -twav
all works well and when I change the level with MasterVolume in alsamixer the volume changes. BUT, I thought the use of this last block was to let the system know to use "asymed" for all sound but apperently it doesn't because all sound acts like it did before.

My question, what do I need to change so that I can use the volume bar to regulate my sound?


BTW: I'm using Ubuntu 10.10

---

### Post by Cyclane on 2011-03-03
I'm double posting because I think I found the solution.

I've added the following to /etc/pulse/default.pa:
```
load-module module-alsa-sink device=asymed sink_name=asymed_source channels=6 control=MasterVolume
```

Sound dit get all garbled up but maybe that was caused by me flipping to many switches.
I will see if it keeps working these 2 days and will get back here  to let you guys know if this is solved or not.

---

### Post by lidex on 2011-03-04
This look any simpler?
[http://ubuntuforums.org/showthread.php?t=1305889](http://ubuntuforums.org/showthread.php?t=1305889)

---

### Post by Cyclane on 2011-03-05
Thanks for the reply, I did try that before but it did not work. Logic tells me that I did something wrong because it tells Ubuntu to control the PCM mixer instead of the master, which should work.

I prefer the configuration I made to the solution offered in the above post because it will 2 channels  to 6 channels and if I wish to make changes later on I can implement them easily.

I've made a few small adjustment to above configuration because I made  some mistakes. one of them causing garbled sound when playing multiple sounds at the same time. I'm on my laptop now and I will post the changes when I'm  on my computer. Meanwhile this problem is solved

---

