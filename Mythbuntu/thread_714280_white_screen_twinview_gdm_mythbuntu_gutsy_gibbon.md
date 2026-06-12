---
title: "white screen twinview gdm mythbuntu gutsy gibbon"
date: 2008-03-03
forum: Mythbuntu
---

### Post by garyt on 2008-03-03
I want to report what appears to be a bug

installing  mythbuntu on gutsy gibbon on an amd64 with twinview and an nvidia 8600 card resulted in a white gdm login screen on one or both monitors (it varied between boots) and a spinning cursor. The user was then unable to login via gdm or kill the x-session

removal of the mythbuntu -gdm-theme package and mythbuntu-desktop package removed the problem...


regards
gary

---

### Post by laga on 2008-03-04
What display manager are you using now? Can you post your gdm config from /etc/gdm/? Make sure there's no confidentation information in here, I'm not sure we save the password there..

---

