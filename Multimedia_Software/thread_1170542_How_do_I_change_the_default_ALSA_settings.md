---
title: "How do I change the default ALSA settings?"
date: 2009-05-26
forum: Multimedia Software
---

### Post by aysiu on 2009-05-26
So I have an HP Mini 1120nr. It originally came with the Mobile Internet Experience (based on Ubuntu 8.04), but I've found that to be a bit limiting, so I installed vanilla 9.04.

The only issue was sound ([bug #318942](https://bugs.launchpad.net/netbook-remix/+bug/318942)).

So I used a workaround to fix the sound, and that's great. But the settings aren't sticking all the time. So after I did the fix, I had to go into the ALSA settings via the Gnome volume properties and mute the PC Beep and unmute the PC Speaker.

Sometimes, though, it seems to randomly switch back to unmuted PC Beep and muted PC Speaker.

I *chown*ed my entire home directory recursively, so I don't think it's a permission issue. Is there a way to edit the default ALSA mixer settings so if I do get another "reset" it resets back to something I actually want? I tried going into /var/lib/alsa/asound.state, but that config file just confused me.

Thanks in advance for any help.

---

