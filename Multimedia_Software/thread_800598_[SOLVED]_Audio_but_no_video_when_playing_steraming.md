---
title: "[SOLVED] Audio but no video when playing steraming videos in firefox"
date: 2008-05-20
forum: Multimedia Software
---

### Post by GumbyX on 2008-05-20
Hey all. After fighting with my laptop for the past 3+ hours to get 8.04 up and running on it, I have found myself with one small problem. I cannot watch streaming quicktime or WMV videos through Firefox. I had no problem getting this to work properly on my desktop (running 8.04 AMD64) after I installed the xine and gecko plugins and players for firefox. I have installed these AND the mplayer plugin (not at the same time) and I keep having the same problem. Anyone know what I should do? I am at a loss ATM and tired as hell. If anyone can help me out, I would greatly appreciate it.

---

### Post by GumbyX on 2008-05-20
No one can help me out? Sorry but not sure where else I can ask for help.

---

### Post by guitarman_usa on 2008-05-20
Both WVM and quicktime formats are proprietary, do you have the gstreamer or fluendo plugins installed too?  Can you properly watch WMV's or .mov's with VLC or Totem (is it strictly a firefox issue?).

Can you also provide a link to a web page that's giving you trouble?

---

### Post by Yellow Pasque on 2008-05-20
Also make sure you have the following packages installed:
```
sudo apt-get install ubuntu-restricted-extras libnss-mdsn lib32nss-mdns xine-plugin
```

---

### Post by GumbyX on 2008-05-21
Website in question is : [http://www.gametrailers.com/player/34277.html?type=mov](http://www.gametrailers.com/player/34277.html?type=mov)
If I download the videos it plays fine, so I am completely lost.

Temüjin, I already have ubuntu-restricted-extras installed as well as the xine-plugin. I can't find libnss-msdn or lib32nss-msdn in the repos, so can't install those. It might have been an issue with my repository (for some reason I couldn't download openssh server. I switch from the MIT to the Northeastern repos and it seems to be working now). Going to try and reinstall the restricted-extras and xine-plugin and see if that helps fix anything.

UPDATE: Still have the problem. Seems to be my web browser. :( I have used swiftweasel (my browser of choice) and firefox2 and nothing is working. After a reinstalloing firefox-3.0, I can now watch said video in Firefox-3.0 and Firefox2. The issue with swiftweasel is still there. I am totally lost.

Update Solved: Turns out it has something to do with "Video Output Settings". It wasn't set to anything for some reason. I just set it to "x11" and I now have video. I have no idea why this was such a problem for me on this perticular system, but I am happy its over and done with.

I was uninstalling and reinstalling web browsers for the past 2 hours, so I decided to just write up my experince in gedit and post it all at once, hence the many updates.

---

### Post by Yellow Pasque on 2008-05-21
Good to hear you solved it. For reference, it's lib32nss-mdns (not msdn as you typo'd or mdsn as I typo'd). :P

---

