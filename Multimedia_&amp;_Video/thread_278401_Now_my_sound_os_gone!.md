---
title: "Now my sound os gone!"
date: 2006-10-16
forum: Multimedia &amp; Video
---

### Post by pentium on 2006-10-16
This time when I booted this morning I did not have a problem with video thanks to work done there.
However now my sound is dead and clicking the volume control give:
> The volume control did not find any elements and/or devices to control. This means either that you do not have the right GStreamer plugins installed, or that you do not have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

Why is my system constantly dropping dirvers?

---

### Post by Kateikyoushi on 2006-10-16
Did you update your system yesterday ?

To find out what's wrong with your system could you post the output of this command ?

```
aplay -l
```

---

### Post by pentium on 2006-10-16
Nope, I didn't even see any indication that updates were even avalible

as fo that command:

```
ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:544: audio open error: No such device

```

---

### Post by pentium on 2006-10-16
Oh...my...god.
All my admin tools are gone and menu editor says that they are enaled.
Root terminal is also rejecting my password!
Something is *very* wrong with this system!

---

### Post by pentium on 2006-10-17
I still can't get in!
My password has changed and I don't know why.
the closest thing I did was create and later delete a user.

---

### Post by Kateikyoushi on 2006-10-17
Then this turned into a completely different problem.

Select recovery mode from grub and at the prompt type

```
passwd master
```

Or you can add a new user with admin rights.

```
adduser user_name admin
```

---

### Post by pentium on 2006-10-17
what should passwd master do?

---

### Post by Kateikyoushi on 2006-10-17
With root rights it should change your password.

---

### Post by pentium on 2006-10-17
it still won't let me in!

I am also gonna close this thread because it is no longer a sound issue at the moment and start a new thread in a better forum.
It can now be found here:
[http://www.ubuntuforums.org/showthread.php?p=1629687#post1629687]("http://www.ubuntuforums.org/showthread.php?p=1629687#post1629687")

---

