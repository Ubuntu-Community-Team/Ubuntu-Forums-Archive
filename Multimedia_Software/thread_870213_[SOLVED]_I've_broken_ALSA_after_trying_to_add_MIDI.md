---
title: "[SOLVED] I've broken ALSA after trying to add MIDI support"
date: 2008-07-25
forum: Multimedia Software
---

### Post by gmjs on 2008-07-25
Hello,

After trying to enable MIDI support, I've managed to break all sound output on my linux box.

In an attempt to restore it, I've downloaded the latest versions of gstreamer and plugins, and alsa drivers, libs and utils and installed them.  I'm still without sound :(

Then I removed them and reinstalled them using the Synaptic Package Manager.  No change.

aplay states that it is playing the sound when I test a WAVE file using it, but there is not sound.

In alsamixer, none of the channels are muted.  I'm really stuck!

Does anyone know of anything I can try before I give in an reinstall?

Many thanks,

Graham

---

### Post by mocha on 2008-07-25
That seems a little strange.  Did you follow the ubuntu wiki page on Timidity?  As far as I recall that involves loading some modules in /etc/modules  Maybe you made a typo somewhere that is screwing your system?  Double check all the text files that you modified.

---

### Post by gmjs on 2008-07-25
Thanks for the reply.

I didn't modify any text files (not directly anyway :)).

I'm going to have to reinstall I think (I really hate having to do that!).

I've attached my bash history if it's any help.  As you can see, I type first and think afterwards!

Many thanks,

Graham

---

### Post by markbuntu on 2008-07-25
Check if you have an instance or 3 of jack running. Nothing will screw up your sound better than jack running wild. I found that jack would often not close like it is suppoed to when the app I was using it with closed. So, I always had to kill jack manually to get my sound back for everything else.

I ususally do it from the system monitor. I have an aversion to terminals. It is a long story that involves assembly language programming on actual terminals connected to mainframes.

---

### Post by gmjs on 2008-07-26
Thanks for the reply.

I haven't installed JACK and it is not running.

I think PulseAudio might be causing the problem, but when I try to remove it I'm told that it is part of the ubuntu-desktop package, along with many others.  So I'd need to reinstall those afterwards.  I might as well reinstall!  Serves me right for not being content with the sound half-working!

Thanks,

Graham

---

### Post by gmjs on 2008-07-26
I've given up.  I'll reinstall Ubuntu when I've got nothing better to do.  It's times like this when I remember why I would never leave Windows for Linux.

---

### Post by gmjs on 2008-07-27
I thought I'd try and put off a reinstall one last time.  Now, I've lost sound completely (muted and alsamixer won't start with error function snd_ctl_open not found) and my PS/2 mouse has stopped working (not keyboard, just mouse).

I give up.

---

### Post by aimpau on 2008-07-27
I think it's no longer about the OS. It's now concerning your BIOS Setup.

---

### Post by gmjs on 2008-07-27
I've reinstalled now.  All working fine.  Many thanks for the help though.

---

