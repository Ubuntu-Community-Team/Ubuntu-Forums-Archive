---
title: "Ubuntu software center problem"
date: 2012-01-23
forum: Networking &amp; Wireless
---

### Post by Arahgon1048 on 2012-01-23
Ok I installed ubuntu 11.10 on my toshiba satellite A205-S508 everything went smooth I can get online and everything but when I try to install something from the Ubuntu software center it tell's me I'm not online when in fact I am connected to the net and switching to my browser proves this any ideas?

---

### Post by bluexrider on 2012-01-23
Open a terminal using "Alt+F2" and type this or copy and paste:

```
sudo apt-get update && sudo apt-get upgrade 
```

Then retry. 

If you get an error code then paste it back here so we can look at it.

---

### Post by Arahgon1048 on 2012-01-23
ran that update all went well tried to get openTTD from Ubuntu software center and again it told me I wasn't connected to the internet

---

### Post by bluexrider on 2012-01-23
It may be the 'server' issue then. Try this:

To switch your server, open 'Software Sources' and click on the drop down  list for 'Download from:'. You can then choose 'Main server' or better yet choose 'other' then 'best server' click and wait the servers to appear. It should choose the fastest then choose that one.

[IMG]http://i.stack.imgur.com/Y4RgC.png[/IMG]

After switching your server, you can now proceed to download software  from the software-center or upgrade software using the update-manager.

---

### Post by Arahgon on 2012-01-23
?

---

### Post by Arahgon1048 on 2012-01-23
Thanks for the help that did the trick.

---

### Post by bluexrider on 2012-01-23
Glad to get you going. Please mark this 
(SOLVED)

---

