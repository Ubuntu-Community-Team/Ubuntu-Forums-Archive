---
title: "Totem freezes, sound stops working"
date: 2007-05-17
forum: Multimedia &amp; Video
---

### Post by iml on 2007-05-17
I have a recurring problem that happens just about every day where sound stops working and totem freezes whenever a file is opened. I believe this is connected to flash, as it seems to happen after watching a long Google video. In any case, I can log out and back in and the sound will be restored, even in time for the logout sound. I'm curious to know whether anyone has had this problem, and more importantly how to restore/restart sound without logging out.

---

### Post by leader303 on 2007-11-12
similar problem: when i want to listen to streamed mp3, totem will -almost- freeze (sound stops, visualization goes slide-show like) and needs a forced quit after a random time of running normally. sometimes it's after one, sometimes after 10 minutes. where to troubleshoot? i don't know...
and the crash seems like causing the cpu fan to turn up speed (temperature raise because of extra load? what process do i need to end to calm him down again?)

---

### Post by leader303 on 2007-11-13
edit edit edit
compiled newest alsa driver, same problem as before.
maybe totem just can't handle inconsistent streams?
anyway, here's mtw's howto.
[http://lastkth-en.blogspot.com/2007/11/upgrade-alsa-ubuntu-gutsy-update.html](http://lastkth-en.blogspot.com/2007/11/upgrade-alsa-ubuntu-gutsy-update.html)

---

### Post by leader303 on 2007-11-25
ok, i think i need to bump this.
till recently, totem screwed up now and then, the mighty ctrl+alt+backspace turned my sound back on, and i could refuge to vlc or some other media player (which all did not work with my interface, but some do now. i don't know why they changed their mind). but now logging on again won't bring my sound back, now i just don't hear anything in any player until some system beep and total shutdown totally make my day.:mad:

---

### Post by patryk77 on 2007-11-25
Same thing...

All my media players have no sound after flash uses the sound card in Firefox... Shutting down Firefox fixes it though,, Same thing if I open 2 players at once.

Any way to get the mixer working? I'm using Gutsy with an Intel ICH5 and Gnome.

I also don't know anything about ALSA, and configuring sound though, and didn't find anything legible in the documentation.

---

### Post by leader303 on 2007-12-03
i can't offer a solution, but this might be a general sound problem, because now and then it happens in other programs, too. when closing the concerned app, i still need to kill the process in the system monitor and when i try and start the app again, sound works.

---

