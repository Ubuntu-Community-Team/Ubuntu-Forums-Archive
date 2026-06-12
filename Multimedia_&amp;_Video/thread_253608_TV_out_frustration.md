---
title: "TV out frustration"
date: 2006-09-08
forum: Multimedia &amp; Video
---

### Post by moofdaddy on 2006-09-08
I've been setting up my ubuntu box for the last couple of days.  Today I got around to hooking up the TV Out portion of my video card.  Before hand I installed or at least I think I installed the Nvida drivers.  I had to manually go in and change nv to nvidia in one of the config files because it was giving me an error.

Anyway, my TV is still looking at me all blue and happy with no signal.  The frusterating part of all this is that it worked for a very brief span of time.  Whenever I restart, while the bios and the core are loading the tv mirrors the display of my monitor.  As soon as Ubuntu loads it kicks it back off.  

Any ideas what my problem might be?

---

### Post by daller on 2006-09-08
Try this guide:

[https://help.ubuntu.com/community/NvidiaTVOutNewbieEdition](https://help.ubuntu.com/community/NvidiaTVOutNewbieEdition)

---

### Post by moofdaddy on 2006-09-08
> **daller said:**
> Try this guide:

[https://help.ubuntu.com/community/NvidiaTVOutNewbieEdition](https://help.ubuntu.com/community/NvidiaTVOutNewbieEdition)

Excellent.  I'll read through there.  Quick question though, is there a command to check what version of video drivers are installed?  I think I got the nvidia drivers installed correctly, but I would like to be sure before I spend time trying to get this working only to find out I had it wrong from the beginning.

---

### Post by daller on 2006-09-08
Just run this command:

```

sudo apt-get install nvidia-glx

```

That will install the present repo-version, which the guide is based on!

If it doesn't install anything, then it means that you have the right version! (If you haven't messed up your sources.list)

Enjoy!

---

### Post by moofdaddy on 2006-09-08
sigh.  well I ran through the guide and now x server won't boot.  I knew I should have created a backup copy of the config file.

---

### Post by daller on 2006-09-08
run this command:

```

sudo dpkg-reconfigure xserver-xorg

```

...and basically just press enter through all the questions... 

(though you should be careful - something may be system-specific...)

---

