---
title: "Video window sticks to foreground while playing"
date: 2011-06-14
forum: Multimedia Software
---

### Post by misha1983 on 2011-06-14
Whenever I'm playing a video and bring another application to the foreground, the video window appears over the foreground application:

[IMG]http://i.imgur.com/nuaO0.png[/IMG]

I'm running Natty Narwhal 64-bit.  This didn't happen back in Maverick.  The hardware is an Asus K42JR laptop.  If there's any more detailed information that I can provide to help narrow this problem down, please let me know.

I've found a similar issue on the forums, but it seems a bit different.   [This guy]("http://ubuntuforums.org/showthread.php?t=1755902") also has foreground window problems, but in his case they occur with non-video applications and are not consistent (it only happens 10% of the time).

With me, it always occurs with only video playback.  The choice of video application for playback does not appear to matter (I've tried Totem, VLC).  Strangely, the problem doesn't occur when viewing flash videos from within Chrome.

Any ideas?

---

### Post by Zommes on 2011-06-16
Same problem with me. Also consistent.

I must add, that its also with certain games. So I guess we can assume its a graphic-card problem?

TS, what is your graphic card? Mine is an ATI Mobility Radeon HD 4650

---

### Post by misha1983 on 2011-06-16
> **Zommes said:**
> Same problem with me. Also consistent.

I must add, that its also with certain games. So I guess we can assume its a graphic-card problem?

TS, what is your graphic card? Mine is an ATI Mobility Radeon HD 4650

It's probably a *driver* problem, not a *graphics card* problem.  It worked fine with Maverick, so the card itself is probably OK.

My graphics card is:

[PHP]lspci -v | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series] (prog-if 00 [VGA controller])[/PHP]

---

### Post by misha1983 on 2011-06-19
Out of interest, I uninstalled the proprietary driver and the problem went away.

Unfortunately, without the proprietary driver, my laptop quickly overheats (hits 105 degrees Celsius) and shuts down.

I'm going back to Lucid LTS for the time being -- this issue is a bit too annoying for me to live with.

---

### Post by pdkta on 2011-06-19
I have the same card radeon HD 5000 Series. Natty 64bit. with proprietary drivers. No problem here :-)

---

### Post by misha1983 on 2011-06-19
> **pdkta said:**
> I have the same card radeon HD 5000 Series. Natty 64bit. with proprietary drivers. No problem here :-)

Strange.  What else could be the problem?

Could it be some other hardware/driver?  I'm using an Asus K42Jr laptop.

---

