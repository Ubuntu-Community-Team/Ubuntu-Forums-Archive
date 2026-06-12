---
title: "problem in facebook chat and several other sites.."
date: 2011-06-18
forum: Networking &amp; Wireless
---

### Post by apoorvmunshi on 2011-06-18
i have a dual boot PC with Linux and windows 7. I have observed that facebook chat doesn't work properly when i use linux. and some sites dont open quickly or dont open at all.But there is no such problem in windows. What to do?

---

### Post by nbound on 2011-06-18
Can we have some more specificity in your problem details. And Facebook chat has always worked fine for me.

---

### Post by idoitprone on 2011-06-18
better yet, say your browser and version and the list of sites that does not work properly

---

### Post by apoorvmunshi on 2011-06-19
browser : google chrome 
websites : piratebay - the most imp :P and many others
facebook chat-others  see me online for sometime ,then offline then again online...and so on..
gmail chat doesnt open at all....

---

### Post by apoorvmunshi on 2011-06-19
problem with metacafe and imdb also:(

---

### Post by WorMzy on 2011-06-19
Have you tried creating a new profile?

[http://www.google.com/support/chrome/bin/answer.py?answer=142059](http://www.google.com/support/chrome/bin/answer.py?answer=142059)

---

### Post by apoorvmunshi on 2011-06-20
the command specified is not running..hav a look

---

### Post by nbound on 2011-06-20
> **apoorvmunshi said:**
> the command specified is not running..hav a look

Thats not a command its a directory.

What they want you to do is:
[LIST]
[*]Exit Google Chrome
[*]Goto your home directory.
[*]If you havent enabled viewing hidden folders do that now (in Nautilus preference menu)
[*]Open ".config" directory
[*]Open "google-chrome"
[*]Rename the folder called "Default" to "Backup default"
[*]Open Google Chrome (Note: Your old user profile info is gone), and it will (silently) create a new "Default" folder, to store the info in.
[/LIST]
*Optional:* "Copy bookmarks.bak" from "Backup default" to "Default" to get your old bookmarks back. They do not recommend transferring any of your other user profile info in this way.

---

### Post by apoorvmunshi on 2011-06-23
still the same problem..plz sugggest some other solution

---

### Post by apoorvmunshi on 2011-06-24
the problem still persists even after creating new profile.....please someone help me

---

### Post by nbound on 2011-06-24
Does internet work ok on the ubuntu live cd?

---

