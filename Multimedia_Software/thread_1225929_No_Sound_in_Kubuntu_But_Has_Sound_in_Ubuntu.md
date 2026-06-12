---
title: "No Sound in Kubuntu But Has Sound in Ubuntu"
date: 2009-07-29
forum: Multimedia Software
---

### Post by efrenefren on 2009-07-29
I have the two variants, ubuntu and kubuntu. I installed ubuntu first then kubuntu. When I'm in ubuntu the video and sound plays but when I'm in Kubuntu only the video plays not the sound. What could have gone wrong?

In kubuntu i tried it in konqueror opera and firefox. no sound in all three so it's not a browser issue.

---

### Post by Zorael on 2009-07-29
That's usually Pulseaudio messing up your sound channel volumes. I don't have a similar system so I don't know precisely what to do offhand, though I'd try the following.
```
$ pulseaudio -K
$ alsamixer
```
Raise volumes and unmute channels (sliders should say 00 and not MM, hit M to toggle). My PCM slider sometimes (for some reason) gets zeroed out, which silences my sound output, and Pulse may well simply ignore that sound channel altogether as it seems to create its own, virtual sound device. So with Pulse it's still zeroed out, but ignored, and with Pulse not running it's suddenly a big deal. Anyway, ESC to exit.
```
$ speaker-test -twav -c2
```
Does sound play? If so, ctrl+c to cancel the test, and try it in a normal application.

If not, post the output of the following.
```
$ aplay -L
```
Capital L.

---

### Post by efrenefren on 2009-07-29
e@e:~$ pulseaudio -K                                         
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.                         
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
pulseaudio: invalid option -- 'K'                            
E: main.c: Failed to parse command line.

in also mixer, the only ones that have MM in them are the mic and front mic

e@e:~$ $ speaker-test -twav -c2
bash: $: command not found
e@e:~$ aplay -L
front:CARD=Intel,DEV=0
    HDA Intel, ALC662 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC662 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC662 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC662 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC662 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC662 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
null
    Discard all samples (playback) or generate zero samples (capture)


And my sound works fine in Kubuntu like when I'm playing songs in Kubuntu or with the system sounds. There's only no sound when i'm playing flash.


Although I'm planning on installing kubuntu only in a few minutes but thanks for your reply! :)

---

### Post by efrenefren on 2009-07-29
Oh, it works now. I don't know what happened. Maybe because I rebooted my computer. :)

---

### Post by Zorael on 2009-07-29
Well, as long as it works. ;3 I hate problems that go away by themselves though, then I don't know what to do when they happen again.

FWIW, it's convention to put dollarsigns in front of commands that should be entered in a terminal as your user (Debian convention, % in Fedora I think), and hashmarks in front of commands that should be entered as root.
```
**$** user command           # comment
**#** root command           # also comment
```
But they should be omitted when you're actually invoking them. So it's no wonder it said "command not found" regarding $ speaker-test. ;>
```
e@e:~**$** **[COLOR="Red"]$[/COLOR]** speaker-test -twav -c2
bash: **[COLOR="Red"]$[/COLOR]**: command not found
```
It's one of those things I keep wondering if I should stop using when giving examples, since eventually someone will just copy/paste a line and just get an error message like the above, or no message at all in case it was a root command (as the hashmark # comments out any following text).

As for '**pulseaudio -K**', perhaps it's '**pulseaudio -[COLOR="Lime"]k[/COLOR]**'; my bad.

---

### Post by efrenefren on 2009-07-29
Oh, thanks for letting me know! I'll take note of that next time I copy a command.

Is there any way I can rate you? because i would have given you five stars for the great help :)

---

