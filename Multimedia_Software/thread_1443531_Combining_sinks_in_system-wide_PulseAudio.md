---
title: "Combining sinks in system-wide PulseAudio"
date: 2010-03-31
forum: Multimedia Software
---

### Post by unimatrix on 2010-03-31
I'm trying to combine 3 sinks in PulseAudio that is running in system-wide (daemon) mode. This is particularly problematic, because I cannot run *pacmd*. It complains that: "No PulseAudio daemon running, or not running as session daemon."

I can however run *pactl*.

To list all sink names, run:
> pactl list | grep -A2 "Sink #"
Sink names will be specified under "Name:", obviously.

Now to combine the sinks, run:
> pactl load-module module-combine module-name="All" slaves="sinkname1,sinkname2,sinkname3,..."
Where *sinknameX* should be replaced by sink names returned by the previous command.

This works. All well and great. But the problem is that I do not want to do this manually every time I log in. Now since pulse is running in system-wide mode, I should simply put the module-combine line in /etc/pulse/system.pa right? Well, I've tried that but it fails.

Any ideas how to combine them automatically?

---

