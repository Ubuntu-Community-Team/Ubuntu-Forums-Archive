---
title: "How can I check if AIGLX is running (gutsy)"
date: 2007-10-20
forum: Multimedia &amp; Video
---

### Post by bootsbradford on 2007-10-20
I am running gutsy with ati radeon x600.

How can I check if AIGLX is working properly at the moment? 
What is the easiest way to enable it if it is not?

---

### Post by BigBob on 2007-10-20
> **bootsbradford said:**
> I am running gutsy with ati radeon x600.

How can I check if AIGLX is working properly at the moment? 
What is the easiest way to enable it if it is not?

Use :

grep -i AIGLX /var/log/Xorg.0.log

You must see something like that :

```
bigbob@bigbob-laptop:~$ grep -i AIGLX /var/log/Xorg.0.log
(**) Option "AIGLX" "true"
(**) AIGLX enabled
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
bigbob@bigbob-laptop:~$ 

```

A++

---

### Post by bootsbradford on 2007-10-20
I get this outcome as well so AIGLX must be running. I'm trying to work out why I can't get desktop effects (compiz-fusion) working on gutsy, when they did this morning. I've had to reconfigure xorg since then...

However, I don't think direct rendering is running. If I run this: 

```
glxinfo | grep direct
```

I get a NO. Does this matter? Does Compiz-Fusion need Direct Rendering? How can I change it?

---

### Post by je1117 on 2007-12-03
I get this with my rv280

(**) Option "AIGLX" "true"
(**) AIGLX enabled
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/r200_dri.so
(II) AIGLX: Suspending AIGLX clients for VT switch
(II) AIGLX: Resuming AIGLX clients after VT switch
(II) AIGLX: Suspending AIGLX clients for VT switch
(II) AIGLX: Resuming AIGLX clients after VT switch
(II) AIGLX: Suspending AIGLX clients for VT switch
(II) AIGLX: Resuming AIGLX clients after VT switch

What is with all the suspending and resuming?

---

### Post by Turin Turambar on 2007-12-03
> **bootsbradford said:**
> I get this outcome as well so AIGLX must be running. I'm trying to work out why I can't get desktop effects (compiz-fusion) working on gutsy, when they did this morning. I've had to reconfigure xorg since then...

However, I don't think direct rendering is running. If I run this: 

```
glxinfo | grep direct
```

I get a NO. Does this matter? Does Compiz-Fusion need Direct Rendering? How can I change it?

It just means that you do not have direct rendering. Does not affect compiz, but 3D.

Try this:
[http://ubuntuforums.org/showthread.php?t=630457](http://ubuntuforums.org/showthread.php?t=630457)

---

