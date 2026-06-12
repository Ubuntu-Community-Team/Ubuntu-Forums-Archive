---
title: "Irxevent only works with &quot;CurrentWindow&quot;"
date: 2016-01-17
forum: Multimedia Software
---

### Post by SagaciousKJB on 2016-01-17
I recently had some trouble setting up irxevent to control Netflix and Amazon Video through the Chrome browser. I had a previously working configuration file, but I found that now when I try to use irxevent it only wants to send signal to "CurrentWindow". If I try the Window name it doesn't work. I tried the Window ID but I don't think I did it right, because the manual says the ID should be a decimal number, whereas xwininfo returns what appears to be a hectic value prefixed with 0x.

I'm using Xubuntu 12.0.4.5 and have whatever most recent version of lirc is in the repositories. Maybe if someone could show me how to properly use the window ID since I can't find an example anywhere. Not sure why it won't recognize the window name, but as it works with CurrentWindow it seems to be a configuration issue.

---

### Post by SagaciousKJB on 2016-01-20
Well I figured out how to do it with the Window ID but that is not much of a solution because it changes from time to time. 

Does nobody have an idea why windowname won't work?

---

