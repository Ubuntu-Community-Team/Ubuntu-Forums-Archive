---
title: "Network card won't power on after supsended"
date: 2009-06-07
forum: Networking &amp; Wireless
---

### Post by Ceedub2 on 2009-06-07
I have looked many times around this forum without avail. Some posts say its a ongoing problem. 

When I suspend my desktop and wake it again the nic doesn't power back on. I have to reboot to get it working again. 

Is there a setting I can change to prevent the card from powering down when the desktop sleeps? 

The Nic is a integrated Nvidia networking chipset. I have a Amd 64 with 1 gig ram.

Thanks!

---

### Post by gaurang on 2009-06-07
hey , i have the same problem ... bt i use x86 .. with 1 gigs of ram ..

mine wifi too doesn't work untill i reboot ... thing is , i h've been using wifi in hardy with madwifi patched drivers ... and it never problem after wakeup ... but this Junty thing, just can't connect to my router :( ...

is there any solution ?

---

### Post by Ceedub2 on 2009-06-08
Its working right now. I tried several things from the forums. One of them must of took effect after booting. Now when I put Ubuntu asleep the nic stays on. Cool!:D

I changed my Network card to 1492 MTU instead of Automatic. That might of done it.

---

### Post by gaurang on 2009-06-10
and how u did it ? 

i m not good at linux so if you can point it out where to look , i may try .. 

its one of the problem , why i still have to use window$ sometimes :( ...

---

### Post by Ceedub2 on 2009-06-10
Don't know if anything worked. I  changed MTU to 1492.

This morning I had to restart because it did it again. 

I think its a issue with it going in to suspend too fast. Don't know how to change it. When I hit suspend it goes asleep in an instant. 

I learned one thing tho. If you right click on the network icon and uncheck Enable Networking and then suspend Ubuntu. When it comes out of suspension it will Enable Networking again and off ya go.:D 

Not a solution but something that I can live with.

---

### Post by Ceedub2 on 2009-06-21
My network card is still doing this. It just turns off and does not turn back on when resuming. I can leave the pc on all the time but kind of wasting energy that way. 

Any ideas?:confused:

---

