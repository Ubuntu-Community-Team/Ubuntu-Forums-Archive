---
title: "geforce8600m GS 512 driver problems"
date: 2009-06-04
forum: Multimedia Software
---

### Post by hammeraxe on 2009-06-04
My Acer laptop has a NVIDIA geforce8600m GS 512 graphics card. I just installed 9.04 on it today and everything works pretty well, except for the video card. When I try going System->Administration->Hardware drivers and choose to activate any of the proprietary NVIDIA drivers it just freezes at 0% and that's it. The only thing I can do is restart the X.
What could be wrong and what can I do to get my video card working?
Thanks

EDIT: After a lot of waiting I get this:
```

Sorry, the Jockey backend crashed. Please file a bug at:

  ubuntu-bug jockey-common

Trying to recover by restarting backend.

```

---

### Post by Arup on 2009-06-04
I get that as well, I ignore it and wait for the router activity to stop, that means driver has been downloaded and then I wait for the hdd light activity to stop. After that I fire Jockey up again and it shows restart needed. Alternatively you can do a sudo apt-get install envy and then do a ctrl+alt+F1, login, do a sudo /etc/init.d/gdm stop and then type sudo envy, you will get a screen asking you what you would like to do, make your selection, reboot and you are ready to go.

---

### Post by hammeraxe on 2009-06-04
ok, I'll try what you suggested and report back.

---

