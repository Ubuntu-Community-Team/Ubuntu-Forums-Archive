---
title: "screen resolution reverts automatically to the wrong setting"
date: 2012-06-14
forum: Multimedia Software
---

### Post by noob5000 on 2012-06-14
my screen is capable of displaying 1920 x 1080, but the x-server resets back to 1280 x 800 every time i boot or log out & in.

the "save x to configutration file" in the nvidia x server settings window seems not to work.

is there anything i can do to make the screen resolution a permanent  setting, rather than having to adjust it every time i start my pc? :confused:

---

### Post by wojox on 2012-06-14
Run it as root and reboot:
```
gksudo nvidia-xconfig
```

---

### Post by noob5000 on 2012-06-14
> **wojox said:**
> Run it as root and reboot:
```
gksudo nvidia-xconfig
```
thanks, but didn't work - after reboot or logout it's still back to 1280x800 :(

at the login/splash screen the automatic resolution is different, much bigger (as always). as soon as i log in it goes back to 1280x800.

so the 1280x800 setting must be determined by some line in some configuration textfile associated with the user/session settings... but where?

---

### Post by noob5000 on 2012-06-18
?

---

### Post by kelvin spratt on 2012-06-18
its gksudo  nvidia-settings you need 
don't forget to save the settings

---

### Post by Baldrick_NZ on 2012-06-18
depending on what you use your PC for, it might be better to remove the nvidia drivers altogether and use the default noveaux ones.

---

