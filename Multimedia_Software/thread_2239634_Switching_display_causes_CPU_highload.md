---
title: "Switching display causes CPU highload"
date: 2014-08-14
forum: Multimedia Software
---

### Post by mctiew on 2014-08-14
I am running xubuntu LTS 14.04 with compiz. 

I noticed that I get very high CPU with my notebook with intel graphics when using external monitor connect via VGA port. When I use internal display LCD screen, it CPU usage is very low. 

The high CPU will show up in Xorg, firefox, plugin-container, virtualbox, vmware and so on. Almost all applications need much more CPU if I run it on external monitor. 

Because I switch monitor at work and at home. At home I would use internal display. At work, I will use the bigger LCD display. I don't shutdown the notebook, instead of just close the lid, and put the notebook to sleep.  

But occasionally I don't see high CPU usage even though I use external display. 

So now I suspect it's due to I switch display. I need to do this experiment, ie instead of switch display with Xorg running, I should rather restart xorg whenever I use a different display. That's not ideal, as it will disrupt all application already started in the X environment.

Anyone else has experienced this. By the way, this is not unique to ubuntu. I have the same problem with other distro with the same notebook, and display monitor.

---

