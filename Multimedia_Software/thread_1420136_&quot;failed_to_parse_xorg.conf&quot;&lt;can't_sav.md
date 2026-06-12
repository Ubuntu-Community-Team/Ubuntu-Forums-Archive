---
title: "&quot;failed to parse xorg.conf&quot;&lt;can't save resolution and refresh"
date: 2010-03-02
forum: Multimedia Software
---

### Post by Ben_222 on 2010-03-02
I looked for a solution to this,and found a thread for it ,but I dont know how to do what it says.Here is part of it by the user "cameronol":
             There is a bug in Ubuntu 9.10 Karmic with the default /etc/X11/xorg.conf involving Nvidia..........receive the error"Failed to parse existing X config file '/etc/X11/xorg.conf'.Then he posts:
    
                                                                              My default /etc/X11/xorg.conf looks like this:

    Section "Screen"
    Identifier "Default Screen"
    DefaultDepth 24
    EndSection

    Section "Module"
    Load "glx"
    EndSection

    Section "Device"
    Identifier "Default Device"
    Driver "nvidia"
    Option "NoLogo" "True"
    EndSection    
       Then he says to delete the first section with the default screen,and it will be fixed.But HOW do I look for the /etc/X11/xorg.conf file to edit it,and how do I edit it?I am new to ubuntu,but I have learned to use a terminal(I think)It seems to be just like the "run" box on Windows.I did a search for the file,but came up empty.I want to fix this cause every time I restart,I have a low resolution that is impossible to work in.

---

### Post by wojox on 2010-03-02
Try:

```
sudo nvidia-xconfig
```

Then:

```
gksudo nvidia-settings
```

---

### Post by Ben_222 on 2010-03-02
Thanks,wojox,that worked great! But I had my doubts when I clicked on save configuration" in the XServer,but it worked.

---

