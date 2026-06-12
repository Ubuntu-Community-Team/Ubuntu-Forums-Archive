---
title: "Starting Darkice at boot"
date: 2010-12-10
forum: Multimedia Software
---

### Post by londondeveloper on 2010-12-10
I have written a init.d script based on the skeleton in the /etc/init.d directory of Ubuntu 10.10 and start, stop, status and restart all work with Darkice no problem.

I have run ```
update-rc.d darkice defaults 99
``` to add symbolic links to  the start up directories.

It won't start up on restart. I can see nothing in the logs.

Ezra had the same problem 2 years ago [here]("http://ubuntuforums.org/showthread.php?t=331277&highlight=darkice+startup").

I have now written 3 different init files just in case but actually none of them work.

Any ideas?

---

### Post by produnis on 2011-01-10
same problem here, running lucid...

---

### Post by configt on 2011-03-16
Same problem here.  I have tried numerous variations of an init script, that all work from the command line, but refuse to run on bootup.

---

### Post by keyboarderror on 2011-03-20
The best answer I've seen so far in 10.04 is a cron job every minute executing:  /usr/bin/darkice -v 10 -c /etc/darkice.cfg  (adjust paths for your configuration if needed)  It runs with user permissions, not sudo. It autostarts, and will re-start quickly if needed.

---

### Post by itismike on 2011-05-09
Also using darkice and found it to not behave as expected from a standard install. I'm not eager to set a one-minute cronjob though. I'll take a look at this later but it seems like we're missing something...

---

### Post by q.dinar on 2011-12-05
i have set auto login, and darkice in startup applications
```
sh -c "sleep 70 && darkice"
```
and also locking screen:
```
sh -c "sleep 10 && gnome-screensaver-command --lock"
```


but i would run darkice with its own user, without launching dasktop for it, if i knew how. but today i have seen that it looks like possible with "screen" command.
see [http://wiki.radioreference.com/index.php/Live_Audio/Ubuntu_Darkice](http://wiki.radioreference.com/index.php/Live_Audio/Ubuntu_Darkice)
they say in ubuntu 10.04 there are problems. i am running 9.10 now. but they say that oss do not work in 10.04 but i think i do not use oss but pulseaudio.

i use 2 sound cards, 1 for general desktop use ie with microphone, sound recording, skype and 2nd for line-in for darkice, because my 1st soundcard does not support line-in and microphone working separately together.

now i am going to install debian 6.0.3 or ubuntu 10.04.3.

---

