---
title: "Audigy 2 ZS Platinum Pro sound issue."
date: 2008-08-02
forum: Multimedia Software
---

### Post by Elysian on 2008-08-02
i'm running ubuntu 8.04, on an amd opteron 170 system, 2gb memory, with a dfi lanparty ut ultra-d(nforce 4). i'm having an issue where i'll be using anything that plays sound, be it opera with youtube, or amarok, or vlc media player, where after 5 minutes of sound or so(not an exact time, just an estimate), the sound cuts off and is replaced by a very annoying high pitched beep. once i close the app that is playing the sound, the beep stops, but the computer is absurdly sluggish, to the point where i can't properly shut down or log out, if i try to do either it just locks up, and even going to the terminal and ctrl-alt-del'ing will result in a freeze while trying to shut down. 

i believe it started when i installed kde4 to give it a try(from the latest sources, should be 4.1), i wasn't really impressed by kde4, so i uninstalled it, but the problem remains. i've reinstalled alsa and everything xine related via synaptec, but it did not resolve the issue. the system is perfectly usable for everything else, just not when i want to listen to music...

---

### Post by Elysian on 2008-08-04
update, i reinstalled everything related to pulseaudio and it seems to be working properly now. thanks for all the people who read this thread :lolflag:

---

### Post by Elysian on 2008-08-04
well, i was obviously mistaken. this time though, it took a full 45 minutes for the same problem to happen. anyone have any ideas? pretty please?

---

### Post by Elysian on 2008-08-04
looking in the system log, i find this

Aug  4 00:23:19 adam-desktop kernel: [ 2341.048661] pulseaudio[6446]: segfault at 6879280 rip 7f301d4beac1 rsp 41ea2fc0 error 6

---

### Post by Elysian on 2008-08-05
bueller?

---

### Post by Elysian on 2008-08-16
well, the solution wasn't as simple as i would have liked, but i solved it by installing slackware instead :) oh well. probably could have just reinstalled ubuntu, but i figured i'd install something that i knew a little bit better, as i've been using slack since 7.

---

