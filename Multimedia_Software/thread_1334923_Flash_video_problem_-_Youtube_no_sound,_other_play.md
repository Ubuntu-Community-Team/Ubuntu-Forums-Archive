---
title: "Flash video problem - Youtube no sound, other players no video"
date: 2009-11-22
forum: Multimedia Software
---

### Post by thedaylights on 2009-11-22
Hello. I recently did a fresh 9.10 install and to get flash working I used Ubuntu Software Centre. The problem is that once I installed Amarok, flash didn't work. I don't know if Amarok caused this or not.

The problem is there is no sound in Youtube. Other flash video players like at cnn.com will play for 2 seconds, then freeze.

I tried installing flash via synaptic instead. When I reinstall, everything works again. But when I reboot (or maybe after reboot + opening Amarok) it stops working.

Any advice please?

---

### Post by thedaylights on 2009-11-28
Update on the situation: if I uninstall flashplugin-nonfree then reinstall it, it fixes the problem for a while. But then it reverts back to it's broken ways.... 

this is what I do:
close firefox

sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree

Then restart firefox. But a message comes up saying it's running somewhere but can't find it. So I kill the process, then load firefox.

Please, anybody have a solution for this? Why doesn't flash just work on Ubuntu??? Or is there not some way to make it work?

---

### Post by zeth01 on 2009-12-03
yup same problems here. worked fine with 32 bit but now im running 9.10 amd64 and it doesnt work for more than a few minutes and i have to refresh the page to get it to work

---

