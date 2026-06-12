---
title: "/dev/dsp in use by another program??"
date: 2005-10-13
forum: Multimedia &amp; Video
---

### Post by gsaathoff on 2005-10-13
Hey All,

Sound works fine for me on system startup, but after listening to music for a bit amarok gives me an error message saying

"/dev/dsp is already in use by another program"

I've disabled system sounds (I don't like them)... I don't know what the problem is.  Any ideas?

Thanks,
Graham Saathoff

---

### Post by mlomker on 2005-10-13
I think it's the default setting, but in Control Center (kcontrol) under Sound & Multimedia, Sound System.  Is the check-box for 'auto-suspend if idle after' box checked?  You could try lowering that number to see if it makes a difference.

---

### Post by shelbydz on 2005-10-14
you can also run
sudo fuser -v /dev/dsp
and that will show you which process ID is using the sound card. then you can KILL it!

---

### Post by CaptainMorgan on 2005-10-21
what's the kill command ? or the proper syntax ? 


thanks

Edit: I only have one PID listed... this is not the primary sound device, is it? I don't want to disable general sound altogether... any suggestions?

Edit: How do I restart the process later?

---

