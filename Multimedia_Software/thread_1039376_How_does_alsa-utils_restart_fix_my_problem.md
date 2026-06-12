---
title: "How does alsa-utils restart fix my problem?"
date: 2009-01-14
forum: Multimedia Software
---

### Post by ddixonr on 2009-01-14
I can't run two programs with sound at the same time. If I start a video in VLC, for example, I can't watch youtube videos in Firefox until I run the following command. It is the same for every other combination of programs. Can anyone translate the results of this command and help me finally fix this problem?```
ryan@ryan-laptop:~$ sudo /etc/init.d/alsa-utils restart
 * Shutting down ALSA...                                                         * warning: 'alsactl store' failed with error message 'alsactl: get_control:209: Cannot read control info '2,0,0,Master Playback Volume,0': No such file or directory'...                                                                       amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
                                                                         [fail]
 * Setting up ALSA...                                                            * warning: 'alsactl restore' failed with error message 'alsactl: set_control:981: warning: numid mismatch (11/13) for control #11
alsactl: set_control:983: warning: iface mismatch (2/2) for control #11
alsactl: set_control:985: warning: device mismatch (0/0) for control #11
alsactl: set_control:987: warning: subdevice mismatch (0/0) for control #11
alsactl: set_control:989: warning: name mismatch (Off-hook Switch/Off-hook Switch) for control #11
alsactl: set_control:991: warning: index mismatch (0/0) for control #11
alsactl: set_control:989: warning: name mismatch (Caller ID Switch/Master Playback Switch) for control #12
alsactl: set_control:991: warning: index mismatch (0/0) for control #12
alsactl: set_control:993: failed to obtain info for control #12 (Operation not permitted)'...                                                                   amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
```

---

### Post by markbuntu on 2009-01-14
If you want to use more than one sound app at a time, do this

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

If that does not help, go here

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by ddixonr on 2009-01-14
Thanks. Haven't completed all the steps, but I feel confident one of these options will work.

---

