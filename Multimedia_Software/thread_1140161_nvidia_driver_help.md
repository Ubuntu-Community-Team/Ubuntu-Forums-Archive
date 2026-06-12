---
title: "nvidia driver help"
date: 2009-04-27
forum: Multimedia Software
---

### Post by 762sks on 2009-04-27
i have install the driver i really like and makes my desktop look real nice. but when i restart or shut down i turn off my effects, install a different driver. restart, then install the driver i like, hope it works. then if it does turn effects back on. 

now when i try to go into the sys/admin/nvidia settings, and try to save the setup to the xorg.conf it wont let me. i actaully went to the folder and i see the file there. but when i right click on it and goto properties then permissions it says that im not the owner. 

so mi guess my question is how do i become the owner to change the permissions on here to save the file i dont have to keep changing this back and forth like i have. 


btw i am running the new jaunty install, plus the update.

---

### Post by hotweiss on 2009-04-27
You just have to sudo it:

> sudo nvidia-settings

---

### Post by Almighty on 2009-04-27
Nevermind, looks like someone beat me to it.

---

### Post by 762sks on 2009-04-27
ty guys

---

### Post by 762sks on 2009-04-27
ok now it looks like when i restarted my system it changed the resolution to 1024x768, which i normally run 1280x1024. i changed it without having to change the drivers this time, but is there something i need to do to get it to stay where i want it?

---

### Post by hotweiss on 2009-04-27
> **762sks said:**
> ok now it looks like when i restarted my system it changed the resolution to 1024x768, which i normally run 1280x1024. i changed it without having to change the drivers this time, but is there something i need to do to get it to stay where i want it?

You shouldn't have to do anything to keep your resolution... So every time you change your resolution it goes back to 1024x768 after a reboot?

---

