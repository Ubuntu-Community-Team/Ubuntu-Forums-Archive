---
title: "Adjusting the volume range?"
date: 2009-04-02
forum: Multimedia Software
---

### Post by cfogelberg on 2009-04-02
Hi all,

I've recently installed Ubuntu on to my Dell XPS M1330, and one of the challenges has been getting the volume to the same as I get with Vista.

After adding "options snd-hda-intel model=3stack" to /etc/modprobe.d/alsa-base the sound volume on maximum is good.

[This fix is described in more detail here: [http://ubuntuforums.org/showthread.php?t=373287&page=6]](http://ubuntuforums.org/showthread.php?t=373287&page=6])

However, the volume adjustment seems to be badly calibrated. When I adjust the volume to 50% using gnome-volume-control then it's barely a whisper. Any less than 50% and it might as well be on mute. I'm using amarok for playback.

One fact is that whenever I close the main amarok window (but leave it running in the tray, i.e. I don't quit the application) I get a popup:

> KNotify Problem: KNotify

During the previous startup, KNotify crashed while trying to instantiate KNotify. Do you want to try again or disable aRts sound output?

I think this might be unrelated and happens because I'm running a KDE app in Gnome though?

Any help much appreciated!
Christo

---

### Post by connorh123 on 2009-04-02
Type this into terminal
> kmix
If that doesn't work, and you have to install it first, type this
> sudo apt-get install kmix
If THAT doesn't work, go into alsa and make sure every thing's okay there.

---

### Post by cfogelberg on 2009-04-03
> **connorh123 said:**
> Type this into terminal

If that doesn't work, and you have to install it first, type this

If THAT doesn't work, go into alsa and make sure every thing's okay there.

Hi Connor,

OK, I installed kmix it seems functionally equivalent to gnome-volume-control. I don't get the KNotify pop up any more, but that hasn't fixed the problem.

I've had a play with kmix and the volume settings in kmix reflect also what I see in gnome-volume-control. Changing the master channel around in kmix also doesn't resolve the problem.

What do you mean to go into alsa and check if everything is OK there? The volume's are already all maxed out in alsamixer.

Best,
Christo

---

