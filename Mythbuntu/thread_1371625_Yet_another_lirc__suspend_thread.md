---
title: "Yet another lirc / suspend thread"
date: 2010-01-03
forum: Mythbuntu
---

### Post by bcgrown on 2010-01-03
I've tried the suggestions in every other thread and none of them made any difference.

I use mythwelcome to put the PC in suspend using "sudo pm-suspend"

When the PC resumes from suspend, a script in /etc/pm/sleep.d runs mythshutdown --startup,  and starts the frontend if a manual start is detected.

If I just type in "sudo pm-suspend" on a terminal, everything works fine.

If I let MythWelcome do the suspending,  then MythFrontend doesn't respond to my remote after resuming (keyboard control works).  Running "sudo service lirc restart" has no effect.

The events are detected by irw, and if I restart mythfrontend, it works again but obviously that's not a good solution.

---

### Post by SiHa on 2010-01-04
I've found that if LIRC is restarted whilst the frontend is running, then the frontend stops responding. So maybe the script in etc/pm/sleep.d is running before lirc is being restarted?

Maybe you need to renumber the script, I too have a special script in etc/pm/sleep.d, I called it **00mythresume** so it will be the first to run on suspend and last on resume.

Failing that, maybe you could either put a ```
sleep 5
```...in the script to delay it a while.

---

### Post by bcgrown on 2010-01-04
I had the script name starting with "20_". Renamed it to 00_ and no change.

I previously tried the "sleep" trick, and even with a 30 second sleep it didn't make any difference.

If I add "service lirc stop" on suspend with a "service lirc start" on resume,  the PC never goes to sleep at all.

Edit: Also tried "modunload lirc_mceusb2 lirc_dev" on suspend with a corresponding "modreload lirc_mceusb2 lirc_dev" line on resume and still not fixed.

---

