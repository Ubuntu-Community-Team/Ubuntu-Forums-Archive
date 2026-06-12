---
title: "strange video problem"
date: 2012-03-19
forum: Multimedia Software
---

### Post by banjobuntu on 2012-03-19
Hi, all.  I'm new here, but a long-time linux user.  I didn't find any discussions that seemed to be about quite what I'm experiencing, so, here we are.

When viewing videos in the totem player, the video freezes, with varying frequency, for perhaps 7 or 8 seconds each time, while the audio continues.

It is fan-freakin-tastically annoying.  I'm sure my neighbors get pissed off, too, at my involuntary exclamations at whatever hour of the night as the movie or tv program I'm in the middle of demonstrates some facet of Murphy's Law by infallibly choking right when something is going on. 

Anyway.  When it happens, if I'm watching it full-screen, the spacebar still acts to pause, but not if it's running windowed, even if the player window has focus.  The volume controls and transport controls north of the keyboard do not function during these events.  Other keyboard input seems to work normally, for example, [ctl][alt][->] will change desktops once normal operation resumes.

I've been keeping a terminal running top and the gnomey sysmonitor thing running on the next desktop over while watching vids.  Switching over there to try to get a peek at what was up during these 'hiccups' shows me (once the video gets moving again) that the CPU is pinned at 100%, and compiz is the culprit, eating up all 100%.

This doesn't seem to happen except with totem.

Anyone got any ideas?

Oh, almost forgot:
HP Pavilion dv9000 laptop
2 gigs of memory

ubuntu 10.04 LTS 
GNOME 2.30.2
totem 2.30.2  using GStreamer 0.10.28

Linux hobbes 2.6.32-39-generic #86-Ubuntu SMP Mon Feb 13 21:50:08 UTC 2012 x86_64 GNU/Linux

not sure what other data I ought to provide.  I tend to just let the system update as it wishes.

Thanks in advance for any ideas, suggestions, etc. :D
[edit - formatting; I wasn't letting the stupid scripts run, and all the newlines went buh-bye]

---

### Post by papibe on 2012-03-20
Hi banjobuntu.

Since your CPU is jumping to 100%, I think you are trying to play an HD video. In order to play a 720p or 1080p video smoothly you need video hardware acceleration.

To accomplish that you need a combination of (1) a relatively modern graphic card, (2) the proper libraries installed, and (3) a player that support the libraries.

It looks like the Pavilion dv9000 may come with an Nvidia card. The following commands will tell us what is your exact graphics. Could you post the results?
```
lspci | grep -i vga

lshw -C display
```
Regards.

---

### Post by banjobuntu on 2012-03-24
Thanks, papiba.  Yeah, I gots me some nvidia up here...
 
Kind of embarassed that I didn't include that info in the first place. I was at the library, and some ... woman ... was a few meters away having a rather loud phone conversation on her cell.  Some people.  Whatever, it was distracting, and that's my excuse.  Yeah, I was distracted, not dumb, yeah, that's the ticket!

lspci says:

00:12.0 VGA compatible controller: nVidia Corporation C67 [GeForce 7150M / nForce 630M] (rev a2)

and lshw, after complaining that i'm not running it as root: 

 *-display               
       description: VGA compatible controller
       product: C67 [GeForce 7150M / nForce 630M]
       vendor: nVidia Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:f5000000-f5ffffff memory:d0000000-dfffffff(prefetchable) memory:f4000000-f4ffffff memory:c0000000-c001ffff(prefetchable)

I think you're right about the HD vid thing... At least, with the worst offenders... Now that I look at it, I see that one of the shows I was watching lately that had some (but not much) of this video hang to it is at 576 x 432, which seems weird to me, but, hey, what do I know?

---

