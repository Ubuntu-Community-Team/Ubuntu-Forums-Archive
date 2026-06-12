---
title: "Fglrx black screen issue with Ubuntu 10.10"
date: 2011-04-06
forum: Multimedia Software
---

### Post by bardlehel on 2011-04-06
I upgraded and used the proprietary driver.  Black screen.  Googled for solutions.  Followed some different suggestions.  Things just got worse.  

I was able at one point to go into low-level GUI and remove the 3rd party driver and install synaptic ubuntu package but again, lost all video when x starts.  

I just want to be able to have Ubuntu back on my PC, preferably 10.10 or above, even better if i can run my ATI card on it :P

About to try 11 beta...

Suggestions to clean my system and get everything to work that has been tried and true?

---

### Post by lidex on 2011-04-06
Post these outputs from terminal:
```
sudo lshw -C display
```
```
cat /var/log/Xorg.0.log
```
Use code tags please.

---

