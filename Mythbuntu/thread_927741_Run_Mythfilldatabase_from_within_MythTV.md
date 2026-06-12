---
title: "Run Mythfilldatabase from within MythTV?"
date: 2008-09-23
forum: Mythbuntu
---

### Post by Caps18 on 2008-09-23
Since my home is without internet for a while, I have to bring the computer into work to download the TV schedule every one to two weeks from Schedules Direct.  

The current way I do it is to exit out of MythTV, open up the backend setup and then exit out of that.  It will ask me if I want to run Mythfilldatabase at that point.  It then downloads all the upcoming days.  

I don't have too much of a problem doing it that way, but I was wondering if there was a way to do this without leaving MythTV?  I currently have it setup to try and do this automatically once a day (and it worked great when I was on-line).

Or is there a way to download the data to a USB drive on a computer without MythTV and then give it to an off-line Mythbuntu box?

Thanks!

---

### Post by klc5555 on 2008-09-23
> **Caps18 said:**
>  but I was wondering if there was a way to do this without leaving MythTV?  I currently have it setup to try and do this automatically once a day (and it worked great when I was on-line).

If by "without leaving Mythtv" you mean without exiting the mythtv frontend, you can do as follows: While still in the Mythtv frontend, go to  Utilities/Setup -- Mythbuntu -- Advanced. There you can open up a terminal window, in which you can run "mythfilldatabase  --refresh-all" from the command prompt. When mythfilldatabase is done, you close the terminal, quit the mythcontrol center and escape back to the usual mythbuntu menus.



> **Caps18 said:**
>  Or is there a way to download the data to a USB drive on a computer without MythTV and then give it to an off-line Mythbuntu box?


No idea on this one. I've never heard of a grabber of this sort having been written for Schedules Direct, though I suppose one could be.

---

### Post by newlinux on 2008-09-23
you can run mythfilldatabase from the commandline without disturbing myth at all (ssh in to the box, or open up a terminal). mythfilldatabase can also read in a file of guide info. What I don't know how to do is download that file from schedules direct. But others on this forum have posted threads about downloading guide information (from free sources) and using those files with mythfilldatabase.
```

mythfilldatabase --help

```
for more info on options

---

