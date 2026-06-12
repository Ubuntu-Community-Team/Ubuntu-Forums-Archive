---
title: "Help with lirc and starting / stopping mythfrontend and steam"
date: 2015-03-15
forum: Mythbuntu
---

### Post by whosmatt on 2015-03-15
Hi all --

I'm experimenting a little, trying to turn my myth box into a Steam box as well. I've installed Steam and checked it out; the streaming function from my Windows gaming PC seems to work as advertised.  I've written two little scripts -- one that kills mythfrontend and then starts Steam (if it's not already running) and one that does the opposite -- it kills Steam and then starts mythfrontend (if it's not already running).  

So now I want to be able to run these scripts from my Streamzap remote.  Here's where I'm running into conflicting info.  I gather that I want to use irexec.  The official docs say I need a config file at ~/.config/lircrc.  I've done this, and started irexec (as my normal user, not root) and tried the scripts, and nothing seems to happen, at least on the frontend.  I did get an error message on my windows box, where I had a MobaXterm shell open, so I'm thinking that one of the button pushes did run the script and it tried to start on my remote machine but failed.

I'm having a hard time finding any directly relevant documentation.  If anyone has experience, I'd appreciate input.

M

---

### Post by whosmatt on 2015-03-16
NM, I'm a dummy.  So, I got it to work one way, meaning that my button press that stops mythfrontend and starts Steam works.  Now I just have to figure out why the opposite isn't working.  Progress.

---

