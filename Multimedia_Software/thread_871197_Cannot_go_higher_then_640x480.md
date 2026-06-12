---
title: "Cannot go higher then 640x480"
date: 2008-07-26
forum: Multimedia Software
---

### Post by Venality on 2008-07-26
With my 17" Samsung SyncMaster171v
so it should be 1280x1024.. Help please???
I'm new to linux/ubuntu.
I have Nvidia 6800, with out the Nvidia driver installed i can use 800x600, but with i cant go above 640x480

---

### Post by evertmantel on 2008-07-26
Before all: Make sure the driver is installed (but it seems you have done that already)


install  'NVIDIA X Server Settings' with add/remove programs.


play a bit with it. 

If you want to be able to save your settings for the next time:

open the terminal
sudo nvidia-settings    ; this starts the same program with root-rights,so you can change the configuration file

---

### Post by Venality on 2008-07-26
I've done this it also only allows 640x480

---

### Post by xc3RnbFO8P on 2008-07-26
try
atl+f2
> gksudo displayconfig-gtk
Choose Generic
and resolution that your monitor supports

---

### Post by mc4man on 2008-07-26
I would definitely use screens and graphics (displayconfig-gtk ) to get the ball rolling in the right direction. There are several Samsung SyncMaster171's listed but none with a v. I'd ck the samsung site and if you can find a listed  171 model with the same specs as yours (-vsync -hsync are the most important) use that in S&G to set your monitor. Decline any prompt to test.

---

