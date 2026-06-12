---
title: "xserver/compiz(?) crashes"
date: 2011-04-07
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ace214 on 2011-04-07
My desktop is crashing almost every boot (after about 20 minutes of use) of Natty. I can't identify a single, common event, but it goes to a scrambled screen randomly. When I switch to the virtual terminal (Ctrl-Alt-F1) and switch back (Ctrl-Alt-F7) the screen returns to normal, but I'm not able to click on anything.

Any ideas? Is there a command to reset X from the virtual terminal?
This makes Natty very unstable for me. I'm on Intel graphics.

---

### Post by cariboo on 2011-04-07
You can setup Ctrl-Alt-backspace to restart X in compizconfig-settings-manager. Did you do an upgrade, or is this a fresh install?

---

### Post by ace214 on 2011-04-07
> **cariboo907 said:**
> You can setup Ctrl-Alt-backspace to restart X in compizconfig-settings-manager. Did you do an upgrade, or is this a fresh install?
Is that separate from the keyboard layout setting? What is it under in CCSM?

I upgraded from Maverick.

ADD: I set that key combo in the keyboard layout, but now when I use it the computer does go back to the GDM login (I hear the drum sounds) and I can login with the keyboard, but the screen is black.

---

### Post by ace214 on 2011-04-08
I did grab this from the kernel log. I think this might be the problem. What package should I file this with?
```
Apr  8 09:38:32 jon-laptop kernel: [  638.224076] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
Apr  8 09:38:32 jon-laptop kernel: [  638.225395] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -11 (awaiting 263700 at 263698, next 263701)
Apr  8 09:38:32 jon-laptop kernel: [  638.225551] [drm:i915_reset] *ERROR* Failed to reset chip.
```

Also, sometimes compiz segfaults such as
```
Apr  7 10:47:35 jon-laptop kernel: [ 1998.972172] compiz[31535]: segfault at 0 ip 00ba7ed1 sp bffb4890 error 6 in i915_dri.so[b90000+64000]
```
and
```
Apr  7 10:32:56 jon-laptop kernel: [ 1120.836095] compiz[1319]: segfault at 0 ip 00bf45c6 sp bff5ea78 error 6 in libc-2.13.so[b7f000+15a000]
```
but I think this is probably the result of the earlier error.

---

### Post by PatrickVogeli on 2011-04-09
I also get VERY frequent compiz crashes:

```

compiz[6976]: segfault at 28 ip 00007f7ad086b335 sp 00007fff1d849130 error 4 in libregex.so[7f7ad0866000+8000]


```

```

compiz[7609]: segfault at 30 ip 00007f89be7b267a sp 00007fff5c9a8f70 error 4 in libdecor.so[7f89be79e000+1c000]

```

2 different crashes, one because of libdecor the other because libregex.

---

### Post by badhorse on 2011-04-09
Same problem for me. After 15 o 20 minutes the screen freeze in te same way that ace214 explains. Intel graphics.

---

