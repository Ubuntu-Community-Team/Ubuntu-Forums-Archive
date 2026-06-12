---
title: "HD Homerun question"
date: 2011-01-02
forum: Mythbuntu
---

### Post by 4romany on 2011-01-02
On my HD Homerun box I have both inputs tied to the same OTA antenna via a splitter.  I created two capture cards for each box - two video sources, scan twice, etc.  In earlier versions I would have channels 9.1 and 9_1 - myth would automatically assign them that way (there may have been a drop down choice for that - don't remember).  I pretty much followed the same thing when I rebuilt in the .23 version shipping with mythbuntu now - but I had to go into the channel ediitor and rename all of the channels for one of the inputs from x_y to x.y - keeping the same format that I'm used to.  The problem is:  schedule direct is not updating the channel guide for any of these channels that I have modified.   Any pointers in have to fix this?

---

### Post by newlinux on 2011-01-02
Add the xmltvids to your channels and schedules direct should pick them up then,.

---

### Post by 4romany on 2011-01-02
yep,,,i'm an idiot...that was the problem.   I did not think about that being the issue....

---

### Post by newlinux on 2011-01-02
You're certainly not an idiot for missing that. If you are, a lot of people are :)

---

