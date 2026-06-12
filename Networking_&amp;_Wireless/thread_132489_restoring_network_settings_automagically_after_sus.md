---
title: "restoring network settings automagically after suspend"
date: 2006-02-18
forum: Networking &amp; Wireless
---

### Post by upthepunx on 2006-02-18
Hello there. I'm running kubuntu 5.10 on a Thinkpad X40, and it works smashingly. But, for some fine-tuning, I'd like to set this thing up so that it resumes (after a suspend to RAM) with whatever network settings were in effect when it suspended. In other words, if it was connected via ethernet, be connected by ethernet on resume; if via wireless, reconnect to the wireless network. 

Currently on resume, it looks for a wired ethernet connection (eth0), which works fine when I am connected to that, but I have to manually reassociate if I want to use wireless with ifup eth1. 

As a potential side-issue, any ideas as to why, after a resume, it takes a while for the shell to run this command (sudo ifup eth1)? It pauses for a good 30-45 seconds after promting for my password. 

Thanks!

---

