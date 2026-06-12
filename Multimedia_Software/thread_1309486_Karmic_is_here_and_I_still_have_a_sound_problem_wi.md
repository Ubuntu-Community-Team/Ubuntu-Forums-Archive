---
title: "Karmic is here and I still have a sound problem with multiuser and Firefox with Flash"
date: 2009-11-01
forum: Multimedia Software
---

### Post by stelekpl on 2009-11-01
Hi,
So first of all - I've had this problem since I started using Ubuntu. It was always there. In Jaunty I "kind of" solved it by switching Gnome to using Alsa but it never really worked 100%. I have now made a fresh install of Karmic and out-of-the-box the problem is still there. It's so annoying that it still does not work, that I finally would like to ask for some support...

The problem:
I have two accounts on my machine: for me and my wife. Usually both users are logged in and very often both have Firefoxes open. My wife uses the "restore all tabs after crash" feature of Firefox as a way to remember her favorite pages so she always has 2-3 dozens of tabs open, half of them being some flash movies.
The problem starts when my wife is already logged in with Firefox and a flash-based page open. It somehow "locks" the sound. So when I start my own Gnome session and open Firefox and load a page with a flash movie, it usually does not play correctly (pauses every 5 seconds) and crashes Firefox completely when I try to close the corresponding tab.

I'm almost sure that the problem is sound related, since previously I was able to fix it for 99% of cases by switching Gnome from PulseAudio to Alsa. However in Karmic... there seems to be no way of doing it.
The problem is also strictly related to two users being logged in at the same time - in one user session I can open as many flash movies as I want and it always works. But when two users do the same - it causes crashes...

Could anyone give me any advice here? I think I tried to follow every "sound guide" I could find here (I've had the problem for many months now) and it does not really help. Is there anything more I could do to find the root cause of my problem?

---

### Post by Gramler on 2009-11-14
Had something similar... not multi-user & only cropped up in Karmic:

Playing video (incl flash videos) kept stopping if other sound apps where running - ie Could only get sound working from either FF or amaroc. And FF was flaky with Amaroc also running

take a look at this:
[http://www.khattam.info/2009/09/09/solved-sound-problem-in-ubuntu-9-10-karmic-koala-alpha-4-due-to-pulseaudio/](http://www.khattam.info/2009/09/09/solved-sound-problem-in-ubuntu-9-10-karmic-koala-alpha-4-due-to-pulseaudio/)

When I completely removed pulse audio... things went "wobbly".
Lost KDE (Note: I can not say how this behaves with gnome).
Anyway.. I rebooted... and reinstalled KDE (ie the ubuntu desktop - See: [http://ubuntuforums.org/showthread.php?t=207899](http://ubuntuforums.org/showthread.php?t=207899) )

Another reboot and the problem was gone (touch wood)

---

