---
title: "sound card not working"
date: 2008-08-02
forum: Multimedia Software
---

### Post by abredin on 2008-08-02
i just got my video card working on my computer but when i restarted my computer my sound card stop working and before i restarted my sound card was working. I have no clue what i did. Can somebody help.

---

### Post by K2712 on 2008-08-02
Is the Master volume way down or muted in amixer?
 
If not, post the outputs of:

```
asoundconf list
```

```
lshw -C multimedia
```

---

### Post by abredin on 2008-08-02
> **K2712 said:**
> Is the Master volume way down or muted in amixer?
 
If not, post the outputs of:

```
asoundconf list
```

```
lshw -C multimedia
```

*-multimedia UNCLAIMED  
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

---

### Post by K2712 on 2008-08-03
Try:

```
asoundconf set-default-card Intel 
```

---

### Post by Yellow Pasque on 2008-08-03
[http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

---

### Post by abredin on 2008-08-03
the sound card is still not working is there i way i can reformat and just restart my whole computer

---

### Post by abredin on 2008-08-03
never mind i got it working

---

