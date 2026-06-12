---
title: "Does my computer even have wifi?"
date: 2012-10-21
forum: Networking &amp; Wireless
---

### Post by Jgumm on 2012-10-21
I received an old eMac with Ubuntu installed on it. I have been attempting to connect it to my wireless connection and am having a hard time. 

When I open the network connections and follow instructions I found through a tutorial on YouTube, I am still unable to connect. There is a grayed out wireless signal with a red exclamation point through it on my top bar. In network connections it has all the options for wireless connections but now I am starting to wonder if it is even capable of connecting wirelessly without an adapter. 

I am new to Ubuntu and eMac's so, I am not too sure of what I am doing. Any help would be much appreciated.

---

### Post by chili555 on 2012-10-21
Perhaps there is a wireless device but no driver. Let's find out. Please open a terminal and run and post:```
lspci -nn | grep 0280
sudo lshw -C network
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

