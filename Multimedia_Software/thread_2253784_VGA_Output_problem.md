---
title: "VGA Output problem"
date: 2014-11-22
forum: Multimedia Software
---

### Post by sun-love-struck on 2014-11-22
I am having a strange VGA output problem. I recently installed Ubuntu 14.04 (64 bit) on hp elitebook 840 g1. I connected my laptop to an external monitor which has fill HD option.  Everything was working fine. Then suddently the power to my external monitor got disconnected and I switched the display to the laptop. 

After that I have not been able to get the display to the external monitor. In fact when I try to boot my laptop with the external monitor being connected, the external monitor briefly displays the contents. The external monitor shows the display till I login. But once I have logged in, the external monitor goes blank. 

So after logging in, the system is not able to identify the external monitor. In fact, when I click on displays in the system settings, it only shows the "Built-in Display" of the laptop. 

Can someone help me with this strange problem.

Thanks!

---

### Post by sun-love-struck on 2014-11-22
I observed another strange thing about this problem. I do not have this problem when I log onto the guest session. Then the external monitor works fine. But the moment I change and log into the my normal account, it begins to show this problem. 

In fact once I have logged onto the normal account (where the external display does not work), logout  and then go to the guest session, the external monitor continues to be the same way. It does not display any output. So it really seems strange.

Thanks
Xlearner

---

### Post by sun-love-struck on 2014-11-23
I found a temporary fix for this problem. I deleted ~/.config/monitor.xml file and restarted. Everything is properly displayed on the external monitor now.

But this is just a temporary fix. If I switch the display back to the laptop using (Fn + F4) commands, I again have the same problem. The system then stops detecting the external monitor. So I can not again switch to it :-(!

---

