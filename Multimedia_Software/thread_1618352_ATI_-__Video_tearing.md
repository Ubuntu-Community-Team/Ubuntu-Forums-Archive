---
title: "ATI -  Video tearing"
date: 2010-11-10
forum: Multimedia Software
---

### Post by dreKion on 2010-11-10
Hello friends!

Some time ago I have this problem.

I have a notebook with ATI 5850 and a PC with an ATI 3650.

For some time, I had the problem that the videos and moving windows, the image is cut as in the image:

[IMG]http://img573.imageshack.us/img573/1807/probleme.png[/IMG]

I have installed the latest drivers from ATI and not that I can do that if not solved will have to migrate to Windows as this is very annoying to watch movies and work when dragging windows

Any ideas?

I have ubuntu 10.10, I try with 10.04, 9.04, 9.10 8.10 an the same problem...

---

### Post by roguebuck on 2010-11-10
are you using compiz? i fixed this my changing the screen refresh rate in the compiz settings from 50Hz to my monitors native refresh, 60Hz.

you need the compiz settings manager installed;
```
sudo apt-get install compizconfig-settings-manager
```

then
system>preferences>compizconfig settings manager>general>Display Settings>refresh rate (slider)

and/or try checking 'Sync to VBlank' under the same Display Settings tab

Thats what i did!

---

### Post by dreKion on 2010-11-10
> **roguebuck said:**
> are you using compiz? i fixed this my changing the screen refresh rate in the compiz settings from 50Hz to my monitors native refresh, 60Hz.

you need the compiz settings manager installed;
```
sudo apt-get install compizconfig-settings-manager
```

then
system>preferences>compizconfig settings manager>general>Display Settings>refresh rate (slider)

and/or try checking 'Sync to VBlank' under the same Display Settings tab

Thats what i did!

thanks for reply

already had compiz installed and was set to 60Hz (my monitor is 60hz).

I have also tried with 'Sync to VBlank' but does not work

:(

---

