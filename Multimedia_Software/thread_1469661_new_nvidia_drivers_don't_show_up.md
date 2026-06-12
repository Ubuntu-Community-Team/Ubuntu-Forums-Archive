---
title: "new nvidia drivers don't show up"
date: 2010-05-02
forum: Multimedia Software
---

### Post by moveright on 2010-05-02
I just upgraded to lynx but my nvidia drivers only say "173" and "recommended" as the two options.  no idea which version the "recommended" one is but that's what is enabled.  I did an update but still it does not show the 195 drivers that I thought I read were shipping with lucid.

---

### Post by Linuxforall on 2010-05-02
Usually recommended is the nvidia-current which means latest, in my case it installed 196.36.15 which if not latest is fairly new, quite a refreshing change as usually Ubuntu would install old drivers by default.

---

### Post by moveright on 2010-05-02
> **Linuxforall said:**
> Usually recommended is the nvidia-current which means latest, in my case it installed 196.36.15 which if not latest is fairly new, quite a refreshing change as usually Ubuntu would install old drivers by default.

well, I ended up manually installing the 195 drivers from a tutorial in these forums somewhere.  I thought I read that a lot of times, the recommended drivers were not updated.

oh well, works now.  that was freaky manually installing the drivers though.  I'm pretty comfortable with linux at this point (been a couple months since I replaced windows) but all this "sudo this" and "/etc/that" sort of puts it in the "too much trouble" category.

how do I look and see what driver I am running with my video card?  when I went to admin>hardware drivers it says that no proprietary drivers are running.  is that ok or did I just screw everything up with the manual install?

---

### Post by mc4man on 2010-05-02
> how do I look and see what driver I am running 
If you have nvidia-settings installed then just open it - will be displayed on default screen.
or from cli
```
nvidia-settings -q NvidiaDriverVersion
```

---

