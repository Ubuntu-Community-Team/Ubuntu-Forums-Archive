---
title: "Bad video...bad"
date: 2008-01-28
forum: Mythbuntu
---

### Post by RFinn on 2008-01-28
I've been trying to get the video out working on my Radeon 9600 Pro card (so far it works, but it's garbled), and I accidentally clicked on the wrong setting in the unspoorted devices porion of the Mythbuntu config screen and now neither my TV nor my monitor will display in a form that I can see well enough to change anything. Please tell me there is an easy way to reset my original video settings and that I don't have to start from scratch. I can boot into recovery ok, but I'm unsure of what commands to use.

---

### Post by stdPikachu on 2008-01-29
Can you post the output of the /etc/X11/xorg.conf file on the afflicted box? Chances are that editing a couple of lines in that will get the problem fixed.

In case you were wondering, `cat /etc/X11/xorg.conf`. If you have SSH enabled (/etc/init.d/ssh start) you'll be able to log into it from another box, which should make copying and pasting easier.

---

### Post by RFinn on 2008-01-31
Should have posted earlier on this one, but it's resolved. I got impatient and just reinstalled.

---

