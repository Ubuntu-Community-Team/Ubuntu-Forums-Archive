---
title: "unable to display resolution"
date: 2009-11-13
forum: Multimedia Software
---

### Post by rushinblue on 2009-11-13
I changed my resolution to an unsupported res and after rebooting ubuntu I get a msg that says unable to display resolution. How can I fix this, without reinstalling Ubuntu?

I am using the ATI All-in-Wonder HD Video card

xorg.conf file
```


[COLOR="Blue"]Section "Screen"
     Identifier      "Default Screen"
     Default Depth   24
End Section

Section "Module"
     Load "glx"
End Section

Section "Device"
     Identifier     "Default Device"
     Driver         "fglrx"
End Section
[/COLOR]

```

I ran "sudo dpkg-reconfigure xserver-xorg" from recovery mode and it didn't do anything, not even asked me the first question.

Like this...
```

[COLOR="Red"]user$sudo dpkg-reconfigure xserver-xorg
user$[/COLOR]

```
Thanks

---

