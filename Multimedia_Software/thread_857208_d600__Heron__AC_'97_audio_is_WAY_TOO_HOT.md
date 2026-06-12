---
title: "d600 / Heron / AC '97 audio is WAY TOO HOT"
date: 2008-07-12
forum: Multimedia Software
---

### Post by kr0m3 on 2008-07-12
ok, im stumped.

i have a dell d600 running heron. lspci says this about the soundcard:

```

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)

```

if i turn the master volume up past more than 80% or so, it over-pushes the levels and the sound becomes unbearable.  horribly scratchy, distorted, etc.

since ubuntu, in it's infinite wisdom, has removed alsaconf... and alsamixer doesn't help at all...(just lowers the volume, doesn't fix the issue when i raise it again)

i tried removing alsa so that i could recompile from source...but that wants me to remove ubuntu-desktop.

i have attempted to at least set the specific user to use OSS instead (System > Preferences > Sound > Devices), that didn't have any effect at all...

i even tried a little *chicanery*...

```

sudo update-rc.d -f alsa remove
sudo update-rc.d -f alsa-utils remove

```

but, that didn't address the issue either.  so, at this point I'm opening the floor for suggestions.

thanx in advance...
~k

---

### Post by ajgreeny on 2008-07-12
Try lowering the PCM level in alsamixer or with the gnome volume control.  I have usually found that I need PCM set to about 80% and all the others can then be up to 100% with no problem.  I agree that it appears to mean that I am not getting what would seem to be the full volume use of my system and pseakers, but they are at least as loud as in winXP if not louder and the sound quality is much better than XP.

---

### Post by kr0m3 on 2008-07-12
> **kr0m3 said:**
> ... and alsamixer doesn't help at all...(just lowers the volume, doesn't fix the issue when i raise it again)


i appreciate the post, but im beyond cosmetic fixes at this point.  i need the soundcard to function correctly, as it does in slack, suse etc.

if i could find a way to either completely disable/remove and/or reinstall alsa from source...or revert to oss... or to resolve the driver issues (assumed) so that alsa plays nice with others... then kr0m3 would be a happy boy.

~k

---

