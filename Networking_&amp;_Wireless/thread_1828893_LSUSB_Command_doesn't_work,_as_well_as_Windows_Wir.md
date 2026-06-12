---
title: "LSUSB Command doesn't work, as well as Windows Wireless Drivers."
date: 2011-08-19
forum: Networking &amp; Wireless
---

### Post by MachintoshCJ on 2011-08-19
I can get the command program to work, but not the desktop program to work. Windows Wireless Driver was working, but now every time I try to start it, it won't load, and will just be an empty window. This happened after I tried to installed a driver (which was the wrong one), and I restarted the computer. After this happened, I tried to reinstall the program, but to no avail.

The command program works, but I can't use the command lsusb, because it just pauses and doesn't do anything. Do I have to wait for it to kick in. I'm pretty sure that this is not it, because when I try the lspci, this works fine (but it's not the one I need). Please help, and don't make any stupid replies.

---

### Post by westie457 on 2011-08-19
> **MachintoshCJ said:**
> I can get the command program to work, but not the desktop program to work. Windows Wireless Driver was working, but now every time I try to start it, it won't load, and will just be an empty window. This happened after I tried to installed a driver (which was the wrong one), and I restarted the computer. After this happened, I tried to reinstall the program, but to no avail.

The command program works, but I can't use the command lsusb, because it just pauses and doesn't do anything. Do I have to wait for it to kick in. I'm pretty sure that this is not it, because when I try the lspci, this works fine (but it's not the one I need). Please help, and don't make any stupid replies.

Hi

Open a terminal please and run ```
lspci
```
Then post the output in a new reply between ```
 
``` tags. You get these by clicking the # at the top of the message pane.

---

### Post by MachintoshCJ on 2011-08-19
No offense, but I think this counts as a stupid reply. Because for one thing I don't think you read this all. Plus, I can't find the device there.

---

### Post by westie457 on 2011-08-19
> **MachintoshCJ said:**
> No offense, but I think this counts as a stupid reply. Because for one thing I don't think you read this all. Plus, I can't find the device there.

No offence taken. Was asking for those results to find out if your USB ports are registering with the system.

---

