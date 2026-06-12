---
title: "force shutdown of myth front end?"
date: 2008-02-08
forum: Mythbuntu
---

### Post by uncle hammy on 2008-02-08
I have had a couple instances where my video has frozen (not many, but some) and naturally, it occurs when I am in the middle of a scheduled recording on the back end (the box is a back / front end).  When it has happened, the box itself is not locked, only the myth front end.  I am able to use the mouse, get the task bar (which I have set to auto hide), open a terminal session, load other programs, etc.

Is there a command that I can run from a terminal session that will just kill the front end, so I can relaunch without a reboot?

This actually brings up a second question.  This happened to me last night, with 2 programs being recorded on from my HDHomeRun.  I restarted the box, and one of the programs resumed recording when it came back up, and one didn't.  Is this a setting that I can tweak to ensure scheduled recording will resume if power is lost then restored (for instance).

Thanks,
Hammy

---

### Post by newlinux on 2008-02-09
you could try:
```

killall mythfrontend

```

---

### Post by uncle hammy on 2008-02-09
I just get "no process killed"

---

### Post by newlinux on 2008-02-09
You could also find the process ID and kill it directly (find ID using htop or top or pgrep, and kill it with the "kill" command). Or you could run mythfrontend from terminal and when it freezes go back to that terminal and press ctrl-c.

---

### Post by uncle hammy on 2008-02-10
pgrep and kill works, thanks.

---

### Post by uncle hammy on 2008-02-17
I guess now the second part of the question.....

from the actual myth box, I can re-launch mythfrontend by simply opening a terminal window, and enring 'mythfrontend'.  However, I normally don't have a mouse and keyboard attached to the box, and would like to be able to go to my desktop, open a putty session and relaunch the mythfrontend remotely.

If I try it, it doesn't work.  I assume I  need to pass a parameter that indicates the X server to launch in.  Can anyone tell me the correct process to do this?

Thanks

---

### Post by Nikas on 2008-02-17
killall mythfrontend.real does the trick.

---

### Post by uncle hammy on 2008-02-17
I am able to kill the running instance of mythfrontend no problem.  I am now trying to determine how to get in going again remotely, using putty.

---

### Post by jfsylvain on 2008-02-17
> **uncle hammy said:**
> I am able to kill the running instance of mythfrontend no problem.  I am now trying to determine how to get in going again remotely, using putty.

In the putty session enter:
```
DISPLAY=:0 mythfrontend &
```

---

### Post by uncle hammy on 2008-02-17
Cheers, that's the ticket!

---

### Post by indulis on 2010-02-06
Actually with Mythtv 0.22.0+fixes22594-0ubuntu1, mythfrontend does not exit cleanly (at least on Karmic Koala 9.10).  If you try to run something else like xbmc after issuing a "kill" (not even kill -9) then xbmc hangs as soon as it tries to output audio.

Go back into mythfrontend, use menus to exit, and xbmc then runs fine.

---

