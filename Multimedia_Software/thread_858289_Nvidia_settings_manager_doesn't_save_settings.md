---
title: "Nvidia settings manager doesn't save settings"
date: 2008-07-13
forum: Multimedia Software
---

### Post by Schnare on 2008-07-13
Every time I restart or log out my resolution is reset to 800x600.
I go the the terminal and type 'sudo nvidia-settings' and it opens up the manager, I change the resolution and refresh rate and save to xorg.conf just fine. But it never seems to work past the current session. 

another oddity which I think may be linked to it:
I installed ubuntu studio by updating regular hardy through synaptic.
now in my gurb bootloader it lists 3 versions of ubuntu. two of them are studio and one is regular hardy. The first one loads x but the other two are trying to install the nvidia module and state tha x is not properly configured and then they lock up.

I only installed studio this way because two separate disc images won't start an installation on my computer mo matter what media they are on. 

any help with this would be much appreciated

---

### Post by Fingers &amp; Thumbs on 2008-07-13
Use

```
gksudo nvidia-settings
```

gksudo should be used instead of sudo, when you are launching a GUI application. Something to do with ownership of generated config files apparently.

---

### Post by Schnare on 2008-07-13
it still doesn't work

---

### Post by diffuze on 2008-07-13
I have the same problem but in my case it isn't resolution, it's just the refresh rate. I have to run nvidia-settings to set it to 85 instead of 60 as X always starts up with.

Edit: found the answer in this thread: [http://ubuntuforums.org/showthread.php?t=114240](http://ubuntuforums.org/showthread.php?t=114240)

---

