---
title: "Audacity install problems"
date: 2014-12-19
forum: Multimedia Software
---

### Post by andrew_s4 on 2014-12-19
newbie running Ubuntu 14.04. I installed Audacity from the software center. Everything went fine until I tried to open it up. A pop up jumps up stating: Audacity is already running. The system has detected that another copy of Audacity is already running and opening another...  And that is as far as it goes. It won't open up and this happens every time regardless of clicking on the icon or opening in terminal. I've uninstalled it and reinstalled it and the same thing happens. Any help?

---

### Post by ajgreeny on 2014-12-19
Run **killall audacity** in terminal, then try again.

Perhaps audacity starts at login as you have saved sessions restarting automatically.

---

### Post by andrew_s4 on 2014-12-20
I purged, and killed all and removed and and and. It worked! Thanks

---

