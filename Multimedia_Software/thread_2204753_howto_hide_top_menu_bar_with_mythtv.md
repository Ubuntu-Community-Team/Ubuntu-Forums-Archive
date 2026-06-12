---
title: "howto hide top menu bar with mythtv"
date: 2014-02-10
forum: Multimedia Software
---

### Post by diyhouse on 2014-02-10
I have found many posts giving direction/information on how to change the mode of operation for the top menu bar working like a MAC on the unity display,.. so that menu options are brought within each window app. 

This however does not address my question, which is how to I hide,.. or bring front the mythtv window,.. so that the menu bar is not visible on the myth display,.. 

.....so how can view a full tv page,.. without a ubuntu menu at the top.

Many thanks

---

### Post by diyhouse on 2014-02-24
Sorted,... After some searching and helpful hints I found a solution, as ubuntu is already compiz,. it just needs a little configuration


Full solution is as follows:-


Use compizconfig-settings-manager , sudo apt-get install compizconfig-settings-manager from a terminal (CTRL+ALT+T), then run it from the dash.


Go to Workarounds ( just type "work" in to the filter box ) and check the box for the option Legacy Fullscreen Support. ( 2nd option down on my version,.. 12.04 ).


I saw some other stuff in posting about setting panel opacity to 0 within the unity plugin,.. but in my install with 12.04 this was already set correctly..


I then rebooted,... and started mythtv,... and top menu bar gone... MAGIC!!!

---

