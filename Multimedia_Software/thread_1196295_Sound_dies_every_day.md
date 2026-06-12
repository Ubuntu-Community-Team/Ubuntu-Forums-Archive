---
title: "Sound dies every day"
date: 2009-06-24
forum: Multimedia Software
---

### Post by Volt9000 on 2009-06-24
I've got a Sound Blaster Audigy 2 and I'm really getting sick of this. In the past my sound would konk out after a few days, forcing me to restart. Now it happens EVERY DAMN DAY. I have to restart Ubuntu to get my sound back. It's really frustrating.

I've tried manually restarting ALSA using

```

sudo /etc/init.d/alsa-utils restart

```

But this is what I get:

```

 * Shutting down ALSA...                                                 [ OK ] 
 * Setting up ALSA...                                                            * warning: 'alsactl restore' failed with error message 'alsactl: set_control:1407: Cannot write control '3:0:0:EMU10K1 PCM Send Routing:0' : Operation not permitted
alsactl: set_control:1407: Cannot write control '3:0:0:EMU10K1 PCM Send Volume:0' : Operation not permitted'...                                                 Invalid card number.
Usage: amixer <options> [command]
Available options:
  -h,--help       this help
  -c,--card N     select the card
  -D,--device N   select the device, default 'default'
  -d,--debug      debug mode
  -n,--nocheck    do not perform range checking
  -v,--version    print version of this program
  -q,--quiet      be quiet
  -i,--inactive   show also inactive controls
  -a,--abstract L select abstraction level (none or basic)
  -s,--stdin      Read and execute commands from stdin sequentially
Available commands:
  scontrols       show all mixer simple controls
  scontents	  show contents of all mixer simple controls (default command)
  sset sID P      set contents for one mixer simple control
  sget sID        get contents for one mixer simple control
  controls        show all controls for given card
  contents        show contents of all controls for given card
  cset cID P      set control contents for one control
  cget cID        get control contents for one control
Invalid card number.
Usage: amixer <options> [command]
Available options:
  -h,--help       this help
  -c,--card N     select the card
  -D,--device N   select the device, default 'default'
  -d,--debug      debug mode
  -n,--nocheck    do not perform range checking
  -v,--version    print version of this program
  -q,--quiet      be quiet
  -i,--inactive   show also inactive controls
  -a,--abstract L select abstraction level (none or basic)
  -s,--stdin      Read and execute commands from stdin sequentially
Available commands:
  scontrols       show all mixer simple controls
  scontents	  show contents of all mixer simple controls (default command)
  sset sID P      set contents for one mixer simple control
  sget sID        get contents for one mixer simple control
  controls        show all controls for given card
  contents        show contents of all controls for given card
  cset cID P      set control contents for one control
  cget cID        get control contents for one control
Invalid card number.
Usage: amixer <options> [command]
Available options:
  -h,--help       this help
  -c,--card N     select the card
  -D,--device N   select the device, default 'default'
  -d,--debug      debug mode
  -n,--nocheck    do not perform range checking
  -v,--version    print version of this program
  -q,--quiet      be quiet
  -i,--inactive   show also inactive controls
  -a,--abstract L select abstraction level (none or basic)
  -s,--stdin      Read and execute commands from stdin sequentially
Available commands:
  scontrols       show all mixer simple controls
  scontents	  show contents of all mixer simple controls (default command)
  sset sID P      set contents for one mixer simple control
  sget sID        get contents for one mixer simple control
  controls        show all controls for given card
  contents        show contents of all controls for given card
  cset cID P      set control contents for one control
  cget cID        get control contents for one control
Invalid card number.
Usage: amixer <options> [command]
Available options:
  -h,--help       this help
  -c,--card N     select the card
  -D,--device N   select the device, default 'default'
  -d,--debug      debug mode
  -n,--nocheck    do not perform range checking
  -v,--version    print version of this program
  -q,--quiet      be quiet
  -i,--inactive   show also inactive controls
  -a,--abstract L select abstraction level (none or basic)
  -s,--stdin      Read and execute commands from stdin sequentially
Available commands:
  scontrols       show all mixer simple controls
  scontents	  show contents of all mixer simple controls (default command)
  sset sID P      set contents for one mixer simple control
  sget sID        get contents for one mixer simple control
  controls        show all controls for given card
  contents        show contents of all controls for given card
  cset cID P      set control contents for one control
  cget cID        get control contents for one control
Invalid card number.
Usage: amixer <options> [command]
Available options:
  -h,--help       this help
  -c,--card N     select the card
  -D,--device N   select the device, default 'default'
  -d,--debug      debug mode
  -n,--nocheck    do not perform range checking
  -v,--version    print version of this program
  -q,--quiet      be quiet
  -i,--inactive   show also inactive controls
  -a,--abstract L select abstraction level (none or basic)
  -s,--stdin      Read and execute commands from stdin sequentially
Available commands:
  scontrols       show all mixer simple controls
  scontents	  show contents of all mixer simple controls (default command)
  sset sID P      set contents for one mixer simple control
  sget sID        get contents for one mixer simple control
  controls        show all controls for given card
  contents        show contents of all controls for given card
  cset cID P      set control contents for one control
  cget cID        get control contents for one control
Invalid card number.
Usage: amixer <options> [command]
Available options:
  -h,--help       this help
  -c,--card N     select the card
  -D,--device N   select the device, default 'default'
  -d,--debug      debug mode
  -n,--nocheck    do not perform range checking
  -v,--version    print version of this program
  -q,--quiet      be quiet
  -i,--inactive   show also inactive controls
  -a,--abstract L select abstraction level (none or basic)
  -s,--stdin      Read and execute commands from stdin sequentially
Available commands:
  scontrols       show all mixer simple controls
  scontents	  show contents of all mixer simple controls (default command)
  sset sID P      set contents for one mixer simple control
  sget sID        get contents for one mixer simple control
  controls        show all controls for given card
  contents        show contents of all controls for given card
  cset cID P      set control contents for one control
  cget cID        get control contents for one control
Invalid card number.
Usage: amixer <options> [command]
Available options:
  -h,--help       this help
  -c,--card N     select the card
  -D,--device N   select the device, default 'default'
  -d,--debug      debug mode
  -n,--nocheck    do not perform range checking
  -v,--version    print version of this program
  -q,--quiet      be quiet
  -i,--inactive   show also inactive controls
  -a,--abstract L select abstraction level (none or basic)
  -s,--stdin      Read and execute commands from stdin sequentially
Available commands:
  scontrols       show all mixer simple controls
  scontents	  show contents of all mixer simple controls (default command)
  sset sID P      set contents for one mixer simple control
  sget sID        get contents for one mixer simple control
  controls        show all controls for given card
  contents        show contents of all controls for given card
  cset cID P      set control contents for one control
  cget cID        get control contents for one control
Invalid card number.
Usage: amixer <options> [command]
Available options:
  -h,--help       this help
  -c,--card N     select the card
  -D,--device N   select the device, default 'default'
  -d,--debug      debug mode
  -n,--nocheck    do not perform range checking
  -v,--version    print version of this program
  -q,--quiet      be quiet
  -i,--inactive   show also inactive controls
  -a,--abstract L select abstraction level (none or basic)
  -s,--stdin      Read and execute commands from stdin sequentially
Available commands:
  scontrols       show all mixer simple controls
  scontents	  show contents of all mixer simple controls (default command)
  sset sID P      set contents for one mixer simple control
  sget sID        get contents for one mixer simple control
  controls        show all controls for given card
  contents        show contents of all controls for given card
  cset cID P      set control contents for one control
  cget cID        get control contents for one control
Invalid card number.
Usage: amixer <options> [command]
Available options:
  -h,--help       this help
  -c,--card N     select the card
  -D,--device N   select the device, default 'default'
  -d,--debug      debug mode
  -n,--nocheck    do not perform range checking
  -v,--version    print version of this program
  -q,--quiet      be quiet
  -i,--inactive   show also inactive controls
  -a,--abstract L select abstraction level (none or basic)
  -s,--stdin      Read and execute commands from stdin sequentially
Available commands:
  scontrols       show all mixer simple controls
  scontents	  show contents of all mixer simple controls (default command)
  sset sID P      set contents for one mixer simple control
  sget sID        get contents for one mixer simple control
  controls        show all controls for given card
  contents        show contents of all controls for given card
  cset cID P      set control contents for one control
  cget cID        get control contents for one control
Invalid card number.
Usage: amixer <options> [command]
Available options:
  -h,--help       this help
  -c,--card N     select the card
  -D,--device N   select the device, default 'default'
  -d,--debug      debug mode
  -n,--nocheck    do not perform range checking
  -v,--version    print version of this program
  -q,--quiet      be quiet
  -i,--inactive   show also inactive controls
  -a,--abstract L select abstraction level (none or basic)
  -s,--stdin      Read and execute commands from stdin sequentially
Available commands:
  scontrols       show all mixer simple controls
  scontents	  show contents of all mixer simple controls (default command)
  sset sID P      set contents for one mixer simple control
  sget sID        get contents for one mixer simple control
  controls        show all controls for given card
  contents        show contents of all controls for given card
  cset cID P      set control contents for one control
  cget cID        get control contents for one control
Invalid card number.
Usage: amixer <options> [command]
Available options:
  -h,--help       this help
  -c,--card N     select the card
  -D,--device N   select the device, default 'default'
  -d,--debug      debug mode
  -n,--nocheck    do not perform range checking
  -v,--version    print version of this program
  -q,--quiet      be quiet
  -i,--inactive   show also inactive controls
  -a,--abstract L select abstraction level (none or basic)
  -s,--stdin      Read and execute commands from stdin sequentially
Available commands:
  scontrols       show all mixer simple controls
  scontents	  show contents of all mixer simple controls (default command)
  sset sID P      set contents for one mixer simple control
  sget sID        get contents for one mixer simple control
  controls        show all controls for given card
  contents        show contents of all controls for given card
  cset cID P      set control contents for one control
  cget cID        get control contents for one control
Invalid card number.
Usage: amixer <options> [command]
Available options:
  -h,--help       this help
  -c,--card N     select the card
  -D,--device N   select the device, default 'default'
  -d,--debug      debug mode
  -n,--nocheck    do not perform range checking
  -v,--version    print version of this program
  -q,--quiet      be quiet
  -i,--inactive   show also inactive controls
  -a,--abstract L select abstraction level (none or basic)
  -s,--stdin      Read and execute commands from stdin sequentially
Available commands:
  scontrols       show all mixer simple controls
  scontents	  show contents of all mixer simple controls (default command)
  sset sID P      set contents for one mixer simple control
  sget sID        get contents for one mixer simple control
  controls        show all controls for given card
  contents        show contents of all controls for given card
  cset cID P      set control contents for one control
  cget cID        get control contents for one control
Invalid card number.
Usage: amixer <options> [command]
Available options:
  -h,--help       this help
  -c,--card N     select the card
  -D,--device N   select the device, default 'default'
  -d,--debug      debug mode
  -n,--nocheck    do not perform range checking
  -v,--version    print version of this program
  -q,--quiet      be quiet
  -i,--inactive   show also inactive controls
  -a,--abstract L select abstraction level (none or basic)
  -s,--stdin      Read and execute commands from stdin sequentially
Available commands:
  scontrols       show all mixer simple controls
  scontents	  show contents of all mixer simple controls (default command)
  sset sID P      set contents for one mixer simple control
  sget sID        get contents for one mixer simple control
  controls        show all controls for given card
  contents        show contents of all controls for given card
  cset cID P      set control contents for one control
  cget cID        get control contents for one control
Invalid card number.
Usage: amixer <options> [command]
Available options:
  -h,--help       this help
  -c,--card N     select the card
  -D,--device N   select the device, default 'default'
  -d,--debug      debug mode
  -n,--nocheck    do not perform range checking
  -v,--version    print version of this program
  -q,--quiet      be quiet
  -i,--inactive   show also inactive controls
  -a,--abstract L select abstraction level (none or basic)
  -s,--stdin      Read and execute commands from stdin sequentially
Available commands:
  scontrols       show all mixer simple controls
  scontents	  show contents of all mixer simple controls (default command)
  sset sID P      set contents for one mixer simple control
  sget sID        get contents for one mixer simple control
  controls        show all controls for given card
  contents        show contents of all controls for given card
  cset cID P      set control contents for one control
  cget cID        get control contents for one control
Invalid card number.
Usage: amixer <options> [command]
Available options:
  -h,--help       this help
  -c,--card N     select the card
  -D,--device N   select the device, default 'default'
  -d,--debug      debug mode
  -n,--nocheck    do not perform range checking
  -v,--version    print version of this program
  -q,--quiet      be quiet
  -i,--inactive   show also inactive controls
  -a,--abstract L select abstraction level (none or basic)
  -s,--stdin      Read and execute commands from stdin sequentially
Available commands:
  scontrols       show all mixer simple controls
  scontents	  show contents of all mixer simple controls (default command)
  sset sID P      set contents for one mixer simple control
  sget sID        get contents for one mixer simple control
  controls        show all controls for given card
  contents        show contents of all controls for given card
  cset cID P      set control contents for one control
  cget cID        get control contents for one control
Invalid card number.
Usage: amixer <options> [command]
Available options:
  -h,--help       this help
  -c,--card N     select the card
  -D,--device N   select the device, default 'default'
  -d,--debug      debug mode
  -n,--nocheck    do not perform range checking
  -v,--version    print version of this program
  -q,--quiet      be quiet
  -i,--inactive   show also inactive controls
  -a,--abstract L select abstraction level (none or basic)
  -s,--stdin      Read and execute commands from stdin sequentially
Available commands:
  scontrols       show all mixer simple controls
  scontents	  show contents of all mixer simple controls (default command)
  sset sID P      set contents for one mixer simple control
  sget sID        get contents for one mixer simple control
  controls        show all controls for given card
  contents        show contents of all controls for given card
  cset cID P      set control contents for one control
  cget cID        get control contents for one control
Invalid card number.
Usage: amixer <options> [command]
Available options:
  -h,--help       this help
  -c,--card N     select the card
  -D,--device N   select the device, default 'default'
  -d,--debug      debug mode
  -n,--nocheck    do not perform range checking
  -v,--version    print version of this program
  -q,--quiet      be quiet
  -i,--inactive   show also inactive controls
  -a,--abstract L select abstraction level (none or basic)
  -s,--stdin      Read and execute commands from stdin sequentially
Available commands:
  scontrols       show all mixer simple controls
  scontents	  show contents of all mixer simple controls (default command)
  sset sID P      set contents for one mixer simple control
  sget sID        get contents for one mixer simple control
  controls        show all controls for given card
  contents        show contents of all controls for given card
  cset cID P      set control contents for one control
  cget cID        get control contents for one control
   ...done.

```

I've tried substituting restart with reset, but that doesn't help either.

I've already checked if anything's using the sound manager with

```

lsof | grep pcm

```

But this always returns nothing.

Is there something I can do to manually restart my sound without having to restart Ubuntu?

---

### Post by Volt9000 on 2009-06-25
*bump*
Any help here?

---

### Post by Volt9000 on 2009-06-27
*bump*

Please, I need help!

---

### Post by gatecrasher on 2009-07-21
Im getting the same **** and it is starting to piss me the off. Everytime I update my system something ***** up. Now it is sound so I have to reboot my damn mythtv box about every day.

---

### Post by igorzwx on 2009-07-21
Is this something similar to yours?

   116oss_sblive	pci1102,2	Creative Sound Blaster Live 

   117oss_sblive	pcs1102,8040	Creative Sound Blaster Live 1024/Platinum

   118oss_sblive	pcs1102,8061	Creative Sound Blaster Live 5.1/Platinum IR

   119oss_sblive	pci1102,4	Creative Sound Blaster Audigy/Audigy2

   120oss_sblive	pcs1102,51	Creative Sound Blaster Audigy Platinum

   121oss_sblive	pci1102,8	Creative Sound Blaster Audigy2 Value/Audigy4

   122oss_sblive	pci1102,2001	Creative Sound Blaster Audigy2 ZS PCMCIA

[http://mercurial.opensound.com/?file/6bf18b4a87d6/devlists/Linux](http://mercurial.opensound.com/?file/6bf18b4a87d6/devlists/Linux)
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

---

### Post by mikey_likesit on 2009-07-21
a quick look at the man page for alsactl suggests you might want to try something like

alsactl -F restore
or
alsactl init

but then, I'm only just starting to learn about this so I may be totally off course here

---

### Post by sebovespa on 2009-07-21
as my opinion sir, i dont get your problem.

try this anyhow,

sudo killall pulseaudio
sudo alsa force-reload

---

### Post by Volt9000 on 2009-07-26
Ah finally some activity here!

> **igorzwx said:**
> Is this something similar to yours?

   116oss_sblive	pci1102,2	Creative Sound Blaster Live 

   117oss_sblive	pcs1102,8040	Creative Sound Blaster Live 1024/Platinum

   118oss_sblive	pcs1102,8061	Creative Sound Blaster Live 5.1/Platinum IR

   119oss_sblive	pci1102,4	Creative Sound Blaster Audigy/Audigy2

   120oss_sblive	pcs1102,51	Creative Sound Blaster Audigy Platinum

   121oss_sblive	pci1102,8	Creative Sound Blaster Audigy2 Value/Audigy4

   122oss_sblive	pci1102,2001	Creative Sound Blaster Audigy2 ZS PCMCIA

[http://mercurial.opensound.com/?file/6bf18b4a87d6/devlists/Linux](http://mercurial.opensound.com/?file/6bf18b4a87d6/devlists/Linux)
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

Yes I have a Sound Blaster Audigy 2 as I stated in my original post, but I'm using ALSA, not OSS.


> **mikey_likesit said:**
> a quick look at the man page for alsactl suggests you might want to try something like

alsactl -F restore
or
alsactl init

but then, I'm only just starting to learn about this so I may be totally off course here
Thanks for the suggestions, but the first command gave me:

```

alsactl: set_control:1407: Cannot write control '3:0:0:EMU10K1 PCM Send Routing:0' : Operation not permitted
alsactl: set_control:1407: Cannot write control '3:0:0:EMU10K1 PCM Send Volume:0' : Operation not permitted

```

and the second gave me

```

alsactl: Unknown command 'init'...

```

> **sebovespa said:**
> as my opinion sir, i dont get your problem.

try this anyhow,

sudo killall pulseaudio
sudo alsa force-reload

What exactly do you not understand? If you tell me, I can try to clarify.

I tried your commands, and I got a whole bunch of the following warnings:

```

WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/andrew/.gvfs

```

Then this:

```

/sbin/alsa: Warning: Processes using sound devices: 7948(mixer_applet2). 
Unloading ALSA sound driver modules: snd-emu10k1-synth snd-emux-synth snd-seq-virmidi snd-seq-midi-emul snd-emu10k1 snd-ac97-codec snd-usb-audio snd-pcm-oss snd-mixer-oss snd-util-mem snd-pcm snd-page-alloc snd-usb-lib snd-seq-dummy snd-hwdep snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device (failed: modules still loaded: snd-emu10k1 snd-ac97-codec snd-util-mem snd-pcm snd-page-alloc snd-hwdep snd-rawmidi snd-timer snd-seq-device).
Loading ALSA sound driver modules: snd-emu10k1-synth snd-emux-synth snd-seq-virmidi snd-seq-midi-emul snd-emu10k1 snd-ac97-codec snd-usb-audio snd-pcm-oss snd-mixer-oss snd-util-mem snd-pcm snd-page-alloc snd-usb-lib snd-seq-dummy snd-hwdep snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device.

```

So it seemed to do what it was supposed to, but still didn't work.

---

### Post by igorzwx on 2009-07-26
You can be busy with this for months.

It might be better to change to OSS4,
if your hardware is supported by OSS4
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

But this is up to you to decide.

---

### Post by Volt9000 on 2009-09-29
Well I found a slightly better solution.
If I switch to a terminal window (Ctrl+Alt+Fn) and stop then start gdm, that seems to fix the problem.

Now the only challenge is identifying what component in gdm is the culprit, so I only have to restart that one module specifically.

---

