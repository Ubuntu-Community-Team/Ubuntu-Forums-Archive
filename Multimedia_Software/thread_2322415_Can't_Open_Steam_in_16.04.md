---
title: "Can't Open Steam in 16.04"
date: 2016-04-27
forum: Multimedia Software
---

### Post by cheese3 on 2016-04-27
Hi All,

I did a fresh install on 16.04.  I ran the "sudo apt-get install steam" command and successfully installed steam.  However, every time I double click the steam icon, the steam icon will show up on the sidebar then promptly close.  I can't get it to run and show the login screen.

I un-installed the files already and purged the file locations then reinstalled, but am still having issues.  Anyone else run into this problem or know how to solve it?

Thanks.

---

### Post by Yellow Pasque on 2016-04-28
Try running it from the terminal to get a more specific error message. Just starting it from the GUI and saying it won't run doesn't give you/us a lot of clues to go on.

---

### Post by El Zoido on 2016-04-28
I take a guess and suppose you have an AMD GPU in your system?

---

### Post by cubenerd on 2016-04-28
Did you try rebooting prior to running the application?
I've encountered this error on 16.04 and sometimes a simple post-install reboot seems to do the trick.

If that doesn't work, check logs/run from terminal to get more robust output :)

---

### Post by El Zoido on 2016-04-28
Just in case you do have an AMD GPU:
It's a known issue with the open-source drivers (which are now used by default since fglrx is not supported in 16.04) and Steam.
Not sure who's to blame here, but there are various solutions to the problem available.

I'm starting Steam on my machine via (either in the console or by creating a custom launcher):
```
LD_PRELOAD='/usr/$LIB/libstdc++.so.6' DISPLAY=:0 steam
```

There might be better solutions, but this at least starts Steam for me.

---

### Post by cheese3 on 2016-04-28
> **El Zoido said:**
> I take a guess and suppose you have an AMD GPU in your system?

I do, yes.

I'm having trouble running certain applications in virtual box too.  Could this be related?

---

### Post by cheese3 on 2016-04-28
> **Temüjin said:**
> Try running it from the terminal to get a more specific error message. Just starting it from the GUI and saying it won't run doesn't give you/us a lot of clues to go on.

Sorry.  Here is what happens when I enter "steam"

~$ steam
Running Steam on ubuntu 16.04 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(0)
libGL error: unable to load driver: radeonsi_dri.so
libGL error: driver pointer missing
libGL error: failed to load driver: radeonsi
libGL error: unable to load driver: swrast_dri.so
libGL error: failed to load driver: swrast

---

### Post by cheese3 on 2016-04-28
> **cubenerd said:**
> Did you try rebooting prior to running the application?
I've encountered this error on 16.04 and sometimes a simple post-install reboot seems to do the trick.

If that doesn't work, check logs/run from terminal to get more robust output :)

I did.  Sorry for lack of details.  I didn't know what to originally enter in my submission.

Here is the output when I enter "steam" in the terminal.

~$ steam
Running Steam on ubuntu 16.04 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(0)
libGL error: unable to load driver: radeonsi_dri.so
libGL error: driver pointer missing
libGL error: failed to load driver: radeonsi
libGL error: unable to load driver: swrast_dri.so
libGL error: failed to load driver: swrast

---

### Post by cheese3 on 2016-04-28
> **El Zoido said:**
> Just in case you do have an AMD GPU:
It's a known issue with the open-source drivers (which are now used by default since fglrx is not supported in 16.04) and Steam.
Not sure who's to blame here, but there are various solutions to the problem available.

I'm starting Steam on my machine via (either in the console or by creating a custom launcher):
```
LD_PRELOAD='/usr/$LIB/libstdc++.so.6' DISPLAY=:0 steam
```

There might be better solutions, but this at least starts Steam for me.

It worked, thanks!  Is there a new AMD driver I need to install for my radeon GPU?

---

### Post by El Zoido on 2016-04-29
> **cheese3 said:**
> It worked, thanks!  Is there a new AMD driver I need to install for my radeon GPU?

No, not really. I think that the problem has to be fixed by Steam, but they probably would say it's Ubuntu's problem.
That's usually how those things go :D

Anyway, I'm not even entirely sure what's causing the problem exactly, I just copied the solution from elsewhere. Apparently some libraries are not fully compatible or not loaded correctly when starting Steam using the open source drivers.

---

### Post by cheese3 on 2016-04-29
> **El Zoido said:**
> No, not really. I think that the problem has to be fixed by Steam, but they probably would say it's Ubuntu's problem.
That's usually how those things go :D

Anyway, I'm not even entirely sure what's causing the problem exactly, I just copied the solution from elsewhere. Apparently some libraries are not fully compatible or not loaded correctly when starting Steam using the open source drivers.

Yup.  Neither probably want to use their resources to fix it.

Random question:  I'm also having problems running some graphic intensive programs in Virtualbox.  Could this be related?

---

### Post by badgeraddiction on 2017-01-15
Thanks, that worked perfect for me.  Wasn't able to get Steam installed properly, but that code did the trick!

---

