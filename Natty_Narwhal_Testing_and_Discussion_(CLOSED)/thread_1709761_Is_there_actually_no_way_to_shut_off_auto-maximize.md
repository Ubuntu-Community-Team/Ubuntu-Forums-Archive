---
title: "Is there actually no way to shut off auto-maximize?"
date: 2011-03-18
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by outZider on 2011-03-18
I'm trying to search for any keyword I can, but it seems to come down to "If the application wants 75% or more of your display, it will auto maximize".

Is there no way to shut this off in Unity?

---

### Post by jennybrew on 2011-03-18
So are all your applications going full screen ?

---

### Post by cariboo on 2011-03-18
According to this [post]("http://ubuntuforums.org/showpost.php?p=10575025&postcount=12"), you should be able to change the settings using dconf-editor. You need to install dconf-tools in order to use it.

---

### Post by outZider on 2011-03-18
> **jennybrew said:**
> So are all your applications going full screen ?

Not all, but most. I tend to like some windows to be fairly large, but certainly not full screen.

[QUOTE=cariboo907]According to this post, you should be able to change the settings using dconf-editor. You need to install dconf-tools in order to use it.[/QUOTE]

Unfortunately, that's just for the dash. It doesn't do anything for other apps.

---

### Post by mc4man on 2011-03-18
I've no clue what the key home-expanded refers to - atm seems to do nothing if changed 
(maybe it relates to max if..., maybe not.

Anyway the % is defined in the unity source, if you rebuild you can alter.

The reasons behind this are -  to quote
>  Automaximize windows in Unity with some rules like blacklisting some
     applications, initial window size.
     It fixes also some bugs, like maximized window on first map not
     undecorated (LP: #667009, #669716, #693779, #691741)

So there was a reason + it helped w/ some bugs. Whether the bugs still need this help I don't know - one would need to test. The non bug reason is unclear to me.

The initial % was 60%, that seemed much to small so while  I  was using 85% here  I suggested 75% as a likely to be accepted compromise. It's not set in stone and maybe it's needed, maybe not.

If you wish to revisit this as to the current value or even the need here is the bug
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/708809](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/708809)

If you wish to rebuild and adjust it's defined in unity-3.6.6/src/PluginAdapter.cpp, currently line 26
```
PluginAdapter * PluginAdapter::_default = 0;

#define MAXIMIZABLE (CompWindowActionMaximizeHorzMask & CompWindowActionMaximizeVertMask & CompWindowActionResizeMask)
#[COLOR="Blue"]define COVERAGE_AREA_BEFORE_AUTOMAXIMIZE 0.75[/COLOR]

/* static */
```

---

