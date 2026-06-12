---
title: "What now?"
date: 2009-01-28
forum: Networking &amp; Wireless
---

### Post by stopie on 2009-01-28
So after some fun messing around in the terminal, I found that, on my Gateway MX6427, my wireless card isn't even detected by the system...it doesnt exist...

Now what?

---

### Post by Crafty Kisses on 2009-01-28
Well what kind of Wireless card do you have? What are the results of this command?
```
lshw -C network
```

---

### Post by stopie on 2009-01-28
Now it shows up as the BCM4318, so Im following [this]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%201:%20All%20BCM43xx%20-%20Install%20NDISWrapper%20and%20Blacklist%20Native%20Driver") to see if it works...dont know why it wouldnt show up earlier

---

