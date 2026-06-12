---
title: "Can't exit frontend mythbuntu 10.10"
date: 2011-03-15
forum: Mythbuntu
---

### Post by kcsrnd on 2011-03-15
I did a fresh install of Mythbuntu 10.10, everything installed fine and it boots up ok.  But i need to exit the frontend to configure my network settings and run updates.  When I go to exit mythbuntu it asks "are you sure?" then locks up.
 
Also, where do you reconfigure the remote control settings?  I enabled remote control during install but the remote does nothing.  But then again, i'm not sure if my card is working properly.  My card is a TBS 6981 PCI-E DVB-S2 Dual Tuner Card.
 
But first and foremost, I need to exit the frontend.  Thanks in advance.

---

### Post by kcsrnd on 2011-03-15
Ok, it was an nvidia driver issue that was causing the frontend to crash. I reinstalled using open source drivers, then could exit set up my wireless, install proprietary drivers.
 

I found the drivers for my card, compiling them now.

---

