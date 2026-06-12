---
title: "Skype 2.0.0.72 and PulseAudio co-existing nicely... :)"
date: 2009-08-12
forum: Multimedia Software
---

### Post by DrWilken on 2009-08-12
I just followed [**[COLOR="Red"]THIS HOWTO[/COLOR]**]("http://worldforum.pardus-linux.nl/index.php?topic=1763.0") to make Skype (only) not use PulseAudio and it works like a charm... 

The only difference is that in the part where You have to comment out **load-module module-hal-detect** You have to do it like this:

Change this:
```
### Automatically load driver modules depending on the hardware available
.ifexists module-hal-detect.so
load-module module-hal-detect tsched=0
.else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
load-module module-detect
.endif
```

to this:

```
### Automatically load driver modules depending on the hardware available
#.ifexists module-hal-detect.so
#load-module module-hal-detect tsched=0
#.else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
#load-module module-detect
#.endif
```

(Comment out the whole section and not just the load-module module-hal-detect part)

Works for me... :)

Remember to select skypein as your input device and skypeout as your ringing and output device in Skype...


Thanks go to Berkus for sending me the link to the above guide... :)

---

### Post by berkus on 2009-08-15
Forum mods: please sticky this!

This guide generally solves multiple co-existence problems between PulseAudio and Skype and some other ALSA applications.

---

### Post by Nyoro on 2009-08-15
<rant>
As usual with any guide to the audio system of Ubuntu, we get a howto that solves the problem on a given subset of systems only. I wish there was some place where you could get a complete overview of the knowledge necessary to setup sound (ie. how does alsa and pulse and modules etc. fit together, which are the relevant daemons and modules and configuration files). Trying to do so atm, is, if you're lucky enough as "easy" as this procedure. 
</rant>

This does not work for me. I have an USB headset. My guess is that I need to change the settings in .asoundrc, but to what? And will this enable me to run skype on my headset while playing music on my speakers?

*edit*
Thanks for the effort OP. My rant is not against you but more the general linux audio experience.

---

### Post by obi1 on 2009-08-16
sory about dum question, bet where can I find .asoundrc?

---

### Post by DrWilken on 2009-08-19
> **obi1 said:**
> sory about dum question, bet where can I find .asoundrc?

Read the first line in the HOWTO ->
**Note: make sure to create the ~/.asoundrc file in home first!**

~/ is the same as Your home directory... :)

(This command will change directory to Your home directory: *cd ~*)

Create a file named **.asoundrc** there...

---

### Post by LostinSpacetime on 2009-08-22
I tried this workaround on two completely different systems with Ubuntu 9.04 and also with alsa 1.0.20, 1.0.19 and 1.0.18 and as well with PulseAudio 0.9.14 and 0.9.15 with the same result:

Everything works perfectly except flash video. Audio is actually working, but the video freezes.

Anyone got it actually working on 9.04?

---

