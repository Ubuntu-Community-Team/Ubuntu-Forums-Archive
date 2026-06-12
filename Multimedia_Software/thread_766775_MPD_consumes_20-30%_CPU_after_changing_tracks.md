---
title: "MPD consumes 20-30% CPU after changing tracks"
date: 2008-04-25
forum: Multimedia Software
---

### Post by Aikon- on 2008-04-25
Hi everyone,

I've been using MPD under Gutsy for quite some time, with no issues. Having upgraded to Hardy, I'm experiencing a rather strange problem..

If I change tracks, using any client, MPD's CPU usage spikes to 20-30% and stays there "forever". So far, the only ways I have to fix it are to issue a full-stop (mpc stop) and start it using (mpc play), or to kill the mpd process entirely and restart it.

I have issued a bug [on Launchpad](https://bugs.launchpad.net/ubuntu/+source/mpd/+bug/221951).

Aikon-

---

### Post by Hubi17 on 2008-04-27
I have the same problem.
Im thinking of trying and older version of mpd and seeing if the problem persists. Could also be the PulseAudio thats causing this?

---

### Post by Aikon- on 2008-04-27
> **Hubi17 said:**
> I have the same problem.
Im thinking of trying and older version of mpd and seeing if the problem persists. Could also be the PulseAudio thats causing this?

I have high suspicions of it being a PA issue.. unfortunately I have zero experience with it, so I'm kind "high and dry", as it were.


Aikon-

edit: **Hubi17:** Can you take a look at the Launchpad bug and add any version or configuration info that may be different from mine? Will help increase the chance that somebody will look at this and get it fixed =)

Thanks.

---

### Post by Hubi17 on 2008-04-27
Hey,

after some research I found the following post which helped me:

> **Emblem Parade said:**
> I'm running Hardy Heron beta, and this was enough for me:

```
sudo aptitude install paprefs
paprefs
```

In PulseAudio Preferences, make sure these two options are enabled:

* Enable network access to local sound devices
* Don't require authentication

Then, to your /etc/mpd.conf add this:

```
audio_output {
	type    "pulse"
	name    "My MPD PulseAudio Output"
}
```

Don't add any other options to this! Let MPD just use PulseAudio's defaults. Now, restart MPD:

```
sudo /etc/init.d/mpd restart

```

Worked for me! (After hours of fiddling around...)

Found here:
[http://ubuntu-utah.ubuntuforums.org/showthread.php?p=4601963](http://ubuntu-utah.ubuntuforums.org/showthread.php?p=4601963)

Maybe that can help you too!

And I will also look into reporting my "symptoms" on launchpad.
Was rather frustrating setting this up again after Clean Install!

-Hubi

---

### Post by Aikon- on 2008-04-27
Thanks, Hubi! So far this has seemed to work.. I will keep my eye one it =)

-Aikon

---

