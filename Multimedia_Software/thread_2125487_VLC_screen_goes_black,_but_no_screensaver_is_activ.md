---
title: "VLC screen goes black, but no screensaver is active"
date: 2013-03-14
forum: Multimedia Software
---

### Post by dargaud on 2013-03-14
Hello all,
something annoying and contradictory happens on my old laptop (kubuntu). I've disabled all screensaver and screen power options: the laptop/screen never goes to sleep/dark. But when I use VLC to watch a movie, the screen goes black every 10 minutes (moving the mouse wakes it up alright).

I've looked over the options of VLC ten times and don't see anything relating to this minor but annoying issue.
Any idea ?
Thanks.

---

### Post by TiberiusT on 2013-03-14
I had the same problem here on Xubuntu 12.10 x64. I traced it down to DPMS (some kind of TV out power save feature I think....) and following this thread

[http://ubuntuforums.org/showthread.php?t=2059551](http://ubuntuforums.org/showthread.php?t=2059551)

I did this
[HTML]xset s off && xset dpms force on && xset -dpms &&[/HTML]

I then set that line to run on startup and set all and every power off/suspend/screensaver to 2 hrs. That way users can watch a movie. Any other setting and users were in the 10 minute zone - there shud be another way but I couldn't find it.

T

---

### Post by dargaud on 2013-03-17
Nice try but it didn't change anything. The thing is that it used to work as expected (suspend computer after 15 minutes and VLC would keep it from suspending), but at a certain point I started to have those random dark screens in VLC, and at another muddled time the computer started refusing to go in sleep mode by itself, only when the [Sleep] button would be pressed. Any other idea ?

---

### Post by dargaud on 2013-05-24
That laptop died (corrupted BIOS with several other people in the same spot and no solution), so this thread is now off...

---

