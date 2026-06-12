---
title: "Wireless suddenly not working..."
date: 2011-04-21
forum: Networking &amp; Wireless
---

### Post by theburningor on 2011-04-21
I've been running Ubuntu 10.10 (Maverick) x64 quite happily on my Dell e6500 for the past few months until today when I woke the computer up from sleep mode and could not use the wireless.  The network-manager applet simply has 'Wireless' greyed out.  I tried rebooting, thinking it was an issue with the wireless card not re-powering on properly after sleep, but to no avail.  Any thoughts on how to begin here?

---

### Post by theburningor on 2011-04-22
Well, I feel stupid.  

The wireless switch was turned off.

---

### Post by Mean Mr Mustard on 2011-04-22
Hi theburningor...can you tell me how to switch wireless card on please

---

### Post by ivanovnegro on 2011-04-22
> **Mean Mr Mustard said:**
> Hi theburningor...can you tell me how to switch wireless card on please

If you use a laptop its probable you have a button to switch wireless on/off.

---

### Post by theburningor on 2011-04-22
Yeah that's what it was for me.  I kept poking around all the system internals wondering why in the world it was just transparently ignoring my wireless card: no errors, no noticeable problems, just ignoring. Then I realized I had bumped the stupid switch on the right-hand side of the laptop.

---

### Post by josephmills on 2011-04-22
mean mr mustard: to see if it is being blocked try ```
rfkill list all 
``` this will tell if there is a soft block or a hard block hope that this helps to un block use ```
rfkill unblock all 
``` but this is only works right know it will happen again on reboot

---

