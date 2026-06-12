---
title: "wireless problem natty"
date: 2011-06-11
forum: Networking &amp; Wireless
---

### Post by superduperlinuxperson on 2011-06-11
Hi,
 
im using ubuntu 11.04, and i tried to connect my usb wireless adapter, and the instructions said to uncheck enable wireless. i did that, but now i cannot recheck it!! whats going on when i run nm-tool, i get this
 
Status: disconnected
blah blah blah
 
how can i change the disconnected part?
thanks!!

Edit:the way to solve this is to run NetworkManager using sudo from terminal like this:
sudo NetworkManager

it will say it is already running and tell you its pid
sudo kill pid

replace pid with its pid

sudo NetworkManager

thats all!!!!!!!!!

---

