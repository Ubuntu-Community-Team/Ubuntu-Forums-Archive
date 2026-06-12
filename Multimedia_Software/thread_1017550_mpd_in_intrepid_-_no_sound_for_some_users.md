---
title: "mpd in intrepid - no sound for some users"
date: 2008-12-21
forum: Multimedia Software
---

### Post by DMcA on 2008-12-21
I've just installed intrepid and I'm really struggling to get mpd (music player daemon) running as I had it with gutsy. 

Basically if I run mpd as root or as the user, it works fine. If I run it as mpd it will start but will not play anything. This to me sounds like a permissions problem. However, I've tried

```
sudo usermod -a -G pulse-access mpd
sudo usermod -a -G pulse mpd
sudo usermod -a -G pulse-rt mpd
```

and in fact I've added mpd to all the same lines in /etc/group as the user is.

I have also changed PULSEAUDIO_SYSTEM_STAR and DISALLOW_MODULE_LOADING to 1 in /etc/default/pulseaudio as per [http://ubuntuforums.org/showthread.php?t=1009674&highlight=mpd](http://ubuntuforums.org/showthread.php?t=1009674&highlight=mpd)

And I have put "load-module module-native-protocol-tcp auth-anonymous=1" into /etc/pulse/default.pa

None of these have done any good. I suspect the problem very similar to [https://bugs.launchpad.net/ubuntu/+source/mpd/+bug/192735](https://bugs.launchpad.net/ubuntu/+source/mpd/+bug/192735) and indeed I did see a "E: client-conf-x11.c: XOpenDisplay() failedbut" type message initially but that seems to have gone away during my attempt. 

(By the way I do have 

```
audio_output {
	type    "pulse"
	name    "My MPD PulseAudio Output"
}
```

in my mpd.conf file)

I still can't get sound with with "mpd" as the user though. I want  mpd to run at startup and not have to log in to X to get music which is why this is a problem. If it makes a difference all the mpd configuration is after a fresh install of intrepid but with the same home folder that I was using in gutsy.

---

### Post by DMcA on 2008-12-22
if anyone's interested, adding "pulseaudio --system" to rc.local should make what I was trying to do possible. I don't think it's the ideal solution however

EDIT: scrap that, it stopped working again after I copied over my old home folder. I really don't understand this, the combination of mpd and pulseaudio seems to be incredibly temperamental. Any help would be appreciated

---

### Post by qball on 2008-12-24
The main problem with mpd and pulseaudio is that mpd is a system service. (in the ubuntu installation) and pulse runs per user-session.

So for mpd to be able to play there must be a pulsedeamon running and have permission to it.

---

### Post by DMcA on 2008-12-26
thanks for the reply. Yes I've realised this, and I've been trying to get pulseaudio to run as a system service but with not particularly successful results (probably because I don't really know the proper way of doing this). 

The alternative solution, which is what I'm currently doing, is of course to run mpd as a user-session. Aside from defeating one of the main points of using mpd, this also seems to be a bit buggy. I can't get my statefile to be used correctly, for example.

---

### Post by Nepherte on 2008-12-26
Does the "alternate solution" from the pulseaudio site work for you? [http://mpd.wikia.com/wiki/PulseAudio#An_alternate_solution_for_fixing_access_rights](http://mpd.wikia.com/wiki/PulseAudio#An_alternate_solution_for_fixing_access_rights)

---

### Post by DMcA on 2008-12-26
> **Nepherte said:**
> Does the "alternate solution" from the pulseaudio site work for you? [http://mpd.wikia.com/wiki/PulseAudio#An_alternate_solution_for_fixing_access_rights](http://mpd.wikia.com/wiki/PulseAudio#An_alternate_solution_for_fixing_access_rights)

Nope

---

### Post by alan.briolat on 2009-03-27
I don't know if you've had any luck with this (since your last reply was 3 months ago), but I was having the same problem and figured out a way to fix it.  You were halfway there, but the root of the problem is that per-user instances of PulseAudio start even when you've got a system-wide instance running.

You can find my method at: [http://www.alanbriolat.co.uk/2009/03/mpd-pulseaudio-ubuntu-intrepid-810/](http://www.alanbriolat.co.uk/2009/03/mpd-pulseaudio-ubuntu-intrepid-810/)

---

### Post by DMcA on 2009-03-27
> **alan.briolat said:**
> I don't know if you've had any luck with this (since your last reply was 3 months ago), but I was having the same problem and figured out a way to fix it.  You were halfway there, but the root of the problem is that per-user instances of PulseAudio start even when you've got a system-wide instance running.

You can find my method at: [http://www.alanbriolat.co.uk/2009/03/mpd-pulseaudio-ubuntu-intrepid-810/](http://www.alanbriolat.co.uk/2009/03/mpd-pulseaudio-ubuntu-intrepid-810/)

Cheers for that. I hadn't really got much further - I'd resorted to running mpd as root, which still didn't work properly. And I'd have never been able to figure out what was going on on my own, the ubuntu implementation of pulse really is bizarre. Anyway, all good now, thanks again.

---

### Post by DMcA on 2009-03-29
Actually no, this doesn't fully work. It fails when attempting to suspend or resume from suspend. 

On going into suspend, sound jitters, but the process continues normally as far as I can tell. on resume there's no sound at all and pulse needs to be restarted. mpd also needs to be restarted (although having tested this a few times in one instance mpd continued running normally, no idea why it fails most of the time). Obviously this this is far from ideal. 

I'm going to try and figure out what's going on (some permissions issue maybe, although that wouldn't explain the jittering) but if you have any idea please do let me know.

Edit:

A workaround is to explicitly stop and then start the daemons manually. this can be automated by putting a script in /etc/pm/sleep.d

for example:

```

#!/bin/bash
case $1 in
    hibernate)
	/etc/init.d/mpd stop
	/etc/init.d/pulseaudio stop
        ;;
    suspend)
	/etc/init.d/mpd stop
	/etc/init.d/pulseaudio stop
        ;;
    thaw)
	/etc/init.d/pulseaudio start
	/etc/init.d/mpd start
        ;;
    resume)
	/etc/init.d/pulseaudio start
	/etc/init.d/mpd start
        ;;
esac

```

---

### Post by alan.briolat on 2009-04-01
Glad I could be of some assistance!

For me, suspending when playing any sound at all shows that behaviour (although I've only tested this going through pulseaudio, not bare ALSA).  Have you had it behave differently when running a per-user session before?  Generally speaking, I don't suspend when playing sound, so it's a non-issue for me, but I'd be interested to hear if you manage to find out why it happens.

BTW, nice workaround with the sleep script!

---

### Post by markbuntu on 2009-04-02
To run pulse as a system daemon you can edit the /etc/pulse/daemon.conf file. There is a line

;system-instance = no

uncomment it and change it to yes and pulse will run as a system deamon. This is not reccomended by the pulse devs.

You can also set

autospawn = yes

and pulse will restart itself

---

### Post by DMcA on 2009-04-05
> **alan.briolat said:**
> Glad I could be of some assistance!

For me, suspending when playing any sound at all shows that behaviour (although I've only tested this going through pulseaudio, not bare ALSA).  Have you had it behave differently when running a per-user session before?  Generally speaking, I don't suspend when playing sound, so it's a non-issue for me, but I'd be interested to hear if you manage to find out why it happens.

BTW, nice workaround with the sleep script!

Sound continues nicely for me during and resuming from suspend so long as the 70pulseaudio file is in /etc/X11/Xsession.d/ (or if the sleep script is present). I'm afraid I don't really have time to investigate the Xsession script at the moment though (and I guess it won't help much anyway if I haven't got an x-session running).

---

