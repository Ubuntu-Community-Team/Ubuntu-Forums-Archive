---
title: "Using VLC"
date: 2009-01-06
forum: Mythbuntu
---

### Post by dsbw on 2009-01-06
Weirdly (or so it seems to me), the mythtv internal player doesn't work on all my ISOs. Outside of MythTV, if I open up my (say) "Duckman" ISO in VLC, it works.

Per the wiki, I've used the following special command for "Duckman":

vlc file://%s vlc://quit

But when the window comes up (I haven't done the full-screen/remote/etc stuff), I get a scrambled image and messed up sound. 

Any thoughts on what might be different between running inside of MythTV or out?

---

### Post by joho500 on 2009-01-07
Did you open the file with the same command on the commandline or did you open it in the interface of VLC? I can't check at this moment but I dont think I used the file:// option.
Probably the iso contains a DVD and in that case I use the command ```
vlc dvd://%s vlc://quit
``` in MythTV.

Cheers,
Joost

---

### Post by dsbw on 2009-01-14
> **joho500 said:**
> Did you open the file with the same command on the commandline or did you open it in the interface of VLC? I can't check at this moment but I dont think I used the file:// option.
Probably the iso contains a DVD and in that case I use the command ```
vlc dvd://%s vlc://quit
``` in MythTV.

Cheers,
Joost

Yes, thank you! That did the trick!

Now to get all the other bits working (full-screen, remote control, etc).

---

