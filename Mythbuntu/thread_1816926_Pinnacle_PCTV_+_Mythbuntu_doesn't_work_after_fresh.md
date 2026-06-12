---
title: "Pinnacle PCTV + Mythbuntu doesn't work after fresh install"
date: 2011-08-02
forum: Mythbuntu
---

### Post by new_tolinux on 2011-08-02
Hi,

I hava a Pinnacle PCTV Rave, which worked on mythbuntu 9.04
But, after a harddrive failure, I'm trying to get it up and running again, only, I absolutely have no clue what I did about 2 years ago...

I tried installing 9.04 (although it's not supported anymore) without luck: mythtv not working
I tried installing 10.04: TVtime and scantv are working, but mythtv isn't
I was on the mythbuntu-chat, where they suggested me upgrading to MythTV 0.24.x, but that also didn't change anything

As far as I know I did set it up correct:
V4L
Pal-BG
europe-west

With MythTV 0.24.x there are channel-locks, but in the end there's a message saying "No channels found" and the screen only displays snow. With 10.04 original (I guess MythTV 0.23) it doesn't find any channels at all.

I also did a lot of modprobing, which in the end didn't really change the results (as in: mythtv still not working).

Any ideas? It should not be that difficult, since I managed to get it working 2 years ago with almost no linux experience.... but I can't manage to get it working again :confused:
I guess the card is installed correct and the cable is working too, since TVtime is working properly and scantv also finds the channels.

---

### Post by new_tolinux on 2011-08-07
*bump*

Edit:
I did more or less fix it for now. In another thread ([**[COLOR=#980101][B][ubuntu]**[/COLOR] Jaunty Repositories: Have you seen me?[/B]]("http://ubuntuforums.org/showthread.php?t=1777488")) I read that it was possible to use the old (obsolete) Jaunty-repositories by editing the sources.list file.
I decided to give it a try, installed Jaunty + updates, and all of a sudden, everything worked out-of-the-box.

Since this did work, I will try to do an update to 10.04.3 (LTS) now, as proposed by the update-manager. Should be finished today, so if it doesn't work, I can always reinstall Jaunty again.
For yet, I won't mark the tread as solved, since Jaunty is obsolete and I know it's preferred to run a supported version, but as soon as I did the upgrade I'll report back here (and mark the thread as solved if it still works).

Edit 2:
Well, that failed almost immediately: "An upgrade from 'jaunty' to 'lucid' is not supported with this tool.", so I guess I'll have to stick with jaunty on this one.

---

