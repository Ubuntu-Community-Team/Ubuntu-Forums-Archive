---
title: "webcam works with Cheese but not with Skype"
date: 2011-08-30
forum: Multimedia Software
---

### Post by wandersw on 2011-08-30
Why a webcam would work with Cheese 2.32.0 with no issues and not with Skype 2.2.0.35? Both softwares are configured to access the camera at /dev/video0. Am I missing something here or was just "lucky" enough to get a buggy version of Skype?

---

### Post by no2498 on 2011-08-31
see if this helps
open a terminal type / copy paste

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

---

### Post by norman2050 on 2011-08-31
It works. But is there anything to do to make this without terminal?

---

### Post by no2498 on 2011-09-01
if you can make it a bin/bash file

#!/bin/bash
          LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so
          /usr/bin/skype

---

### Post by AgentWD-40 on 2011-09-02
I have the same problem here. My Logitech webcam will work just great with Cheese, but not under Skype. I'm also on 11.04 and I tried the fix mentioned above, but I get this error:

ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

Anybody have an idea of what's going on here?

Thank you!

---

### Post by AgentWD-40 on 2011-09-02
Never mind. I got it working. I'm running 64-bit so the command has to be altered slightly. Try this:

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

---

### Post by erudite on 2011-09-08
norman2050 the best bet is to go System > Preferences > Main Menu

Then find skype and edit the command from skype to ```
bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'
```

---

### Post by Fizz.LeChat on 2012-02-12
Tried several ways but I can't get it to work... 

If I open terminal and type this: 
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

Skype opens and the cam works fine however it stays on all the time, not just when I make a call.

I tried following the instructions various instructions to make a bin/bash file but that just locked everything up... Or nothing happened...
Maybe I'm just doing it wrong? 

I went to the "skype" file in usr/local/bin and edited it with this text:

#!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so 
skype 

Then when I open skype the webcam is in the options but when I test it there is nothing, it doesn't turn on... If I go to the terminal and enter the command:

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

A second skype opens but says there is another one, and neither one works so I close them both and then reenter the command from terminal and it works when I test the webcam.

Soooo, the only way I can start skype is by the terminal with preload... I would like to know how to automate the process? Or at least if I can modify the launcher so that when I click the icon it works...

Since my skype comes on automatically at boot, is there a way to edit the startup of skype at boot?

I think it would really be helpful if an explicit instruction was added to the skype trouble shooting page here: 

[https://help.ubuntu.com/community/SkypeTroubleshooting](https://help.ubuntu.com/community/SkypeTroubleshooting)


> **no2498 said:**
> if you can make it a bin/bash file

#!/bin/bash
          LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so
          /usr/bin/skype

Thanks for any help... I've usually found all the info I need in these forums, usually because someone else asked first, but not this time...

BTW, I'm running Lucid on 3 of my machines. The other 2 are running Natty with Gnome. And I hate Unity!!! It just doesn't do what I want!

---

### Post by salsahil87 on 2013-05-01
[QUOTE=no2498;11206001]see if this helps
open a terminal type / copy paste

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.



now what?

---

