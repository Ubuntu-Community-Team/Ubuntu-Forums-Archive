---
title: "flash plays no sound, and video cant fullscreen"
date: 2009-07-01
forum: Multimedia Software
---

### Post by Nbasil on 2009-07-01
whenever i use firefox i have no noise, but i do get video still. 

when i opened firefox though the terminal this popped up

LoadPlugin: failed to initialize shared library /usr/lib/flashplugin-installer/libflashplayer.so [/usr/lib/flashplugin-installer/libflashplayer.so: wrong ELF class: ELFCLASS32]
LoadPlugin: failed to initialize shared library /usr/lib/flashplugin-installer/libflashplayer.so [/usr/lib/flashplugin-installer/libflashplayer.so: wrong ELF class: ELFCLASS32]
LoadPlugin: failed to initialize shared library /usr/lib/flashplugin-installer/libflashplayer.so [/usr/lib/flashplugin-installer/libflashplayer.so: wrong ELF class: ELFCLASS32]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libflashplayer.so [/usr/lib/mozilla/plugins/libflashplayer.so: wrong ELF class: ELFCLASS32]
Loading stream: [http://www.fanfiction.net/static/scripts/jstore_1_1_0/jStore.swf](http://www.fanfiction.net/static/scripts/jstore_1_1_0/jStore.swf)
Loading stream: [http://www.fanfiction.net/static/scripts/jstore_1_1_0/jStore.swf](http://www.fanfiction.net/static/scripts/jstore_1_1_0/jStore.swf)
Loading stream: [http://www.fanfiction.net/static/scripts/jstore_1_1_0/jStore.swf](http://www.fanfiction.net/static/scripts/jstore_1_1_0/jStore.swf)
unhandled event 19
unhandled event 19
unhandled event 19

is there any way to fix this? cause i have tried anything and everything to fix this, ive reinstalled flashplugin so many times i cant count.

---

### Post by lovinglinux on 2009-07-01
Never mind. It seems the next post is correct.

---

### Post by kelt65 on 2009-07-01
> **Nbasil said:**
> whenever i use firefox i have no noise, but i do get video still. 

when i opened firefox though the terminal this popped up

LoadPlugin: failed to initialize shared library /usr/lib/flashplugin-installer/libflashplayer.so [/usr/lib/flashplugin-installer/libflashplayer.so: wrong ELF class: ELFCLASS32]
LoadPlugin: failed to initialize shared library /usr/lib/flashplugin-installer/libflashplayer.so [/usr/lib/flashplugin-installer/libflashplayer.so: wrong ELF class: ELFCLASS32]
LoadPlugin: failed to initialize shared library /usr/lib/flashplugin-installer/libflashplayer.so [/usr/lib/flashplugin-installer/libflashplayer.so: wrong ELF class: ELFCLASS32]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libflashplayer.so [/usr/lib/mozilla/plugins/libflashplayer.so: wrong ELF class: ELFCLASS32]
Loading stream: [http://www.fanfiction.net/static/scripts/jstore_1_1_0/jStore.swf](http://www.fanfiction.net/static/scripts/jstore_1_1_0/jStore.swf)
Loading stream: [http://www.fanfiction.net/static/scripts/jstore_1_1_0/jStore.swf](http://www.fanfiction.net/static/scripts/jstore_1_1_0/jStore.swf)
Loading stream: [http://www.fanfiction.net/static/scripts/jstore_1_1_0/jStore.swf](http://www.fanfiction.net/static/scripts/jstore_1_1_0/jStore.swf)
unhandled event 19
unhandled event 19
unhandled event 19

is there any way to fix this? cause i have tried anything and everything to fix this, ive reinstalled flashplugin so many times i cant count.

Obviously you have a 64 bit firefox and a 32 bit plugin? The plugin I installed with Ubuntu is 64 bit - 
```

$ file /usr/lib/mozilla/plugins/libflashplayer.so 
/usr/lib/mozilla/plugins/libflashplayer.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped

```

How'd you get mismatched?

Fullscreen stopped working for me some time after my Jaunty upgrade. I would not be surprised if a firefox update broke it somehow.

---

### Post by Nbasil on 2009-07-02
this seems like it makes the most sense but i thought i was supposed to have a 64-bit type, im running a amd athlon and asus mb.

anyway this code isnt working, terminal keeps giving me

**bash: syntax error near unexpected token `(**'

do you know whats wrong?

ps, thank you this is the most progress ive made so far.

edit: would switching to the 32bit distro fix these issues? because i think i had a 32bit distro at one time and flash worked(not great but worked) and then i rewrote ubuntu 8.10 with latest 9.04 64bit server.

---

