---
title: "nvidia x server config"
date: 2010-02-05
forum: Multimedia Software
---

### Post by SpeedRacer on 2010-02-05
since i reformatted my new hard drive i have been having issues saving my config file when i tried to save to x configuration file it says: Failed to parse existing X config file '/etc/X11/xorg.conf'!

i used to be able to open the file as root and copy over the old x config with the new one but it wont let me even preview the changes until i click save to x configuration file. anyone know how i can fix this error? i tried uninstalling and that didn't help.

---

### Post by TheBig3 on 2010-02-05
I had a similar problem trying to edit my xorg.conf file. 
Here's what worked for me:

At the terminal, type: ```
sudo nvidia-xconfig
```

You should get a response like 
```
Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Undefined Device "(null)" referenced by Screen "Default
                  Screen".

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'
```

After you should be able to run either ```
sudo nvidia-settings
``` or ```
gksu nvidia-settings
```

I hope this helps....

---

### Post by SpeedRacer on 2010-02-05
thanks alot works like a charm!

---

