---
title: "Change Primary Monitor"
date: 2008-11-08
forum: Multimedia Software
---

### Post by ppatalano on 2008-11-08
Can any one help with changing my primary monitor, tried just switching inputs (physically) and it didn't work. Just to be clear when I say primary monitor I mean the one that by default things such as icons appear on.

---

### Post by Mattventura on 2008-11-08
If you manually editied or used a tool to edit your xorg.conf, find your "screen" sections and switch the devices that they use. If that doesn't work, look in the "serverlayout" section. My screens are named "Display 0" and "DIsplay 1", so I would change this:
```

        screen 0 "Display 0" 0 0
        screen 1 "Display 1" leftof "Display 0" 
```
to this:```

        screen 0 "Display 1" 0 0
        screen 1 "Display 0" leftof "Display 1" 
```

If that doesn't work, try using one of the graphical tools to do it.

---

### Post by ppatalano on 2008-11-08
None of this is listed in my xorg.conf file because I am using the restricted ATI driver, but thanks for your help.

---

### Post by kaspar_silas on 2008-11-10
I had exactly the same problem thou using different drivers. I solved my problem by altering my nvidia setting. From the terminal I entered:

nvidia-setting 

which opened a nice simple GUI with a check box to switch the primary monitor. Presumably your restricted drivers have a similar type of option. I hope this is at least some help.

---

### Post by ppatalano on 2008-11-10
I do wish there was a setting like this in the ATI Catalyst Control Center but there is not :(

---

### Post by N00bB00b on 2008-11-14
> **Mattventura said:**
> 
If that doesn't work, try using one of the graphical tools to do it.

So could you be a little more specific?  I just enabled two monitors from the Screen Resolutions control panel (Intrepid).  Now my secondary monitor has been set by Ubuntu to be my primary, which is not what I want, since I'm on a laptop.

---

### Post by Genogp on 2008-11-14
I also have the same problem im using Intel Graphics (GM965/GL960) on my laptop.

any ideas?

---

### Post by Hatch151990 on 2008-12-05
I'm in the exact same boat. I have two screens on an ati card and want to change which on is set as primary but cant find anything

---

