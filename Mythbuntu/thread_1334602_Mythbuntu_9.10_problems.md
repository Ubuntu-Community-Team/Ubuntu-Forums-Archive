---
title: "Mythbuntu 9.10 problems"
date: 2009-11-22
forum: Mythbuntu
---

### Post by codymyth on 2009-11-22
I recently wanted to use mythtv-frontend on another computer and it said my database was out of date. I upgraded my mythbuntu from 8.10 to 9.04 and my backend would no longer open up, so i decided to upgrade to 9.10. my backend loads up now and i can see everything from mythweb, but when i try to open the frontend from my computer with the master backend or from my other computer the frontend just flashes open and closes. Also the programs I schedule for recording from mythweb record, but it does not initiate my channel change script so it records on the wrong channel.

My question is, is there a way i can fix this or do I need a fresh install? if fresh install is what's need, how do I go about that without losing all my recorded shows.

Thanks.

---

### Post by ianhaycox on 2009-11-23
Try running mythfrontend from a terminal and see what errors it logs

---

### Post by codymyth on 2009-11-23
I actually fixed it on the computer with the master backend by using the older nvidia graphics driver (like 175 or something). it seems that the newest nvidia driver for 9.10 doesn't like mythfrontend, it has no problems with the backend though.

---

