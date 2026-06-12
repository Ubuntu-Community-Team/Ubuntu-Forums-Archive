---
title: "Hard code system output volume value, possible?"
date: 2014-05-06
forum: Multimedia Software
---

### Post by michael151 on 2014-05-06
Hi,

This might be an unusual request, but I'm running Ubuntu 12.04LTS and need a way to hard code the system volume output to a value that never changes, even upon reboot. It's a test machine where we never want the output volume changing.

Is there a way to do this?

Thanks,

Michael

---

### Post by Yellow Pasque on 2014-05-06
You can always use 'amixer' or 'pacmd set-sink-volume' to control volume on startup. Don't ask me which one you should use because I don't run pulseaudio and find the overlapping volume controls between ALSA and pulse confusing...

---

### Post by steeldriver on 2014-05-06
I have used an 'alsactl restore' from within /etc/rc.local to set volume on boot - however I don't know how to lock it down once inside a user-session (possibly there's a polkit setting?)

---

### Post by phedup on 2014-05-06
[COLOR=#DD4814][COLOR=#000000] Dear [michael151]("http://ubuntuforums.org/member.php?u=1922115")[SIZE=4]

[SIZE=2]HA!  Problem NOT solved yet.  The exact thing happens to my sound volume on 13.4.  I don't know whether a CLI command would work.  I read some other posts that this was a common problem. Still waiting for 14.whatever- non-beta, in hopes that this is addressed and fixed.[/SIZE][SIZE=3][/SIZE][/SIZE][/COLOR][/COLOR]

---

### Post by ibjsb4 on 2014-05-06
Is this what your looking for?

[http://ubuntuforums.org/showthread.php?t=2221190&p=13012102&viewfull=1#post13012102](http://ubuntuforums.org/showthread.php?t=2221190&p=13012102&viewfull=1#post13012102)

---

### Post by syntaxerror74 on 2014-05-17
I'd suggest to use **aumix** for that purpose.

You can consider yourself even luckier, since I've just found my old script on a backup flash drive with my sample aumix line:
```
aumix -v95 -w93 -c84 -W95 -m66 -p30 -r70
```

---

