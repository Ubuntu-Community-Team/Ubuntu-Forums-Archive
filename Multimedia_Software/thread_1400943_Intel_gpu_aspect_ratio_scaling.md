---
title: "Intel gpu aspect ratio scaling?"
date: 2010-02-07
forum: Multimedia Software
---

### Post by epsilon72 on 2010-02-07
I'm working with a laptop that is running 9.10 and has an intel 4500m GPU.  I'm trying to get aspect ratio scaling to work, but I can't figure out what to do.

All of the other widescreen-monitor linux boxes I've worked on up to this point have been nvidia ones, and nvidia-settings makes this really easy.  Since we have no "intel-settings" program, I guess things have to be done with xorg or xrandr, am I right?

I've tried 
```
xrandr --output LVDS1 --set PANEL_FITTING full_aspect
```
but that returns
```
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  11 (RRQueryOutputProperty)
  Serial number of failed request:  33
  Current serial number in output stream:  33
```
Now, I could be totally off base here and trying something that is completely wrong, I don't know.  I saw the "Panel fitting - full aspect" option in a list of what I thought were [_intel gpu xorg variables_](http://ubuntuforums.org/showpost.php?p=7461917&postcount=8).

I know this GPU is capable of scaling because it does it fine in windows.  I just need to know how for linux.  Thankyou to anyone that can help! ;)

---

### Post by epsilon72 on 2010-03-15
This command:
```

xrandr --output LVDS1 --set "scaling mode" "Full aspect"

```
Exits without an error, unlike all the other ones that I've tried.  I got it from an intel man page and it should work, but for whatever reason, X in this ubuntu installation doesn't pay attention to xrandr variables like this.

I've read that this command does work on other distributions, like fedora.

---

### Post by epsilon72 on 2010-03-21
The command I posted above *does* in fact work, but not in Ubuntu 9.10.  It works in Fedora 12 and in Debian Sid, and will probably work in Lucid as well (with version 2.9.1 of the xorg intel driver).

Marking as solved.

---

