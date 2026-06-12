---
title: "Kernel update woes"
date: 2009-04-01
forum: Networking &amp; Wireless
---

### Post by FAJALOU on 2009-04-01
Interesting case on my hands:

So I just upgraded my kernel in Hardy (2.6.24-24 generic) and the first thing that happens; no internet...

So okay I try to modprobe ndiswrapper
```
sudo modprobe ndiswrapper
```
and I get ```
FATAL: Module ndiswrapper not found
```

Booting to another kernel I notice that linux-headers-`uname -r` is not installed, nor is linux-ubuntu-restricted-`uname -r`.  So I install both of those, and reboot, and then the VIDEO doesn't work!

So I removed linux-ubuntu-restricted-modules-`uname -r` and restarted and NOW the internet is not working, giving me the same error I started off with!

Oh boy oh boy oh boy!  Fun stuff.  ANY help is definitely helpful thank you in advanced.

---

### Post by FAJALOU on 2009-04-02
AHA I figured out what was wrong; and how to fix it.

So I installed linux-restricted and THEN linux-ubuntu.

What you MUST do is install linux-ubuntu then linux-restricted to get both to work.  If you have installed linux-restricted then linux-ubuntu, simply uninstall both, then reinstall in the order of:
linux-ubuntu-modules-`uname -r`
linux-restricted-modules-`uname -r'

Now restart and wallah!
Hope this helps someone!

:guitar:

---

