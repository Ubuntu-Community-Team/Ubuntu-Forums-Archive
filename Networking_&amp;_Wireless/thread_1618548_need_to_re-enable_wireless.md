---
title: "need to re-enable wireless"
date: 2010-11-10
forum: Networking &amp; Wireless
---

### Post by drrfrost on 2010-11-10
When the wireless icon disappeared in ubuntu, I created another ubuntu partition so I could keep doing necessary work while I worked to solve the original problem,

The new partition works fine though it is small. 

How do I get the icon back to my primary ubuntu partition and or how can I replace the existing ubuntu os with the same os.

---

### Post by cipherboy_loc on 2010-11-10
What is the output of:
```
ps aux | grep -i '[n]m-applet'
```


If the output is nothing, try running (from a terminal):
```
nm-applet &
```

If that fixes your issue, then add that to the start up, and mark the thread as solved. Else, post back here.

---

