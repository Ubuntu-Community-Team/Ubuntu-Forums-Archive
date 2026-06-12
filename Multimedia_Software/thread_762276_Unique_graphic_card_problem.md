---
title: "Unique graphic card problem?"
date: 2008-04-21
forum: Multimedia Software
---

### Post by diplomat.x on 2008-04-21
My setup:
-Core 2 Duo - 2.33GHz
-Asus G33 based board.
-2x1 GB ram 667Mhz ram.
-XFX Nvidia 8600GT 256MB DDR3.

I was dual booting ubuntu gutsy and WinXP.

I was doing normal stuff in ubuntu when it just hanged and the screen went red'ish. I restarted the PC and selected ubuntu from grub, after seeing the ubuntu loading screen everything goes black and there is a cursor flashing on top, nothing happens after it(waited for 10 mins). 
Restarted again and tried booting into WinXP, it hangs too. I can only get XP to work in Safe mode.

I removed my graphic card and booted with the onboard Graphics and ubuntu still hangs at black screen while XP works. 

The ubuntu live cd works with onboard graphics but doesnt with my graphic card. 

Stressed out, i deleted ubuntu partitions from XP computer management.
But i was anyways gonna do that since i am gonna install hardy after 24th. 

But what has happened to my card? It was working awesome since around one year. :confused:

Pic 1 - Red blocks shouldnt be there.
Pic 2 - Green lines unwanted.
Pic 3 - White dots and white lines not usual.
Pic 4 - I will go mad explaining how i feel looking at that.

---

### Post by overdrank on 2008-04-22
> **diplomat.x said:**
> My setup:
-Core 2 Duo - 2.33GHz
-Asus G33 based board.
-2x1 GB ram 667Mhz ram.
-XFX Nvidia 8600GT 256MB DDR3.

I was dual booting ubuntu gutsy and WinXP.

I was doing normal stuff in ubuntu when it just hanged and the screen went red'ish. I restarted the PC and selected ubuntu from grub, after seeing the ubuntu loading screen everything goes black and there is a cursor flashing on top, nothing happens after it(waited for 10 mins). 
Restarted again and tried booting into WinXP, it hangs too. I can only get XP to work in Safe mode.

I removed my graphic card and booted with the onboard Graphics and ubuntu still hangs at black screen while XP works. 

The ubuntu live cd works with onboard graphics but doesnt with my graphic card. 

Stressed out, i deleted ubuntu partitions from XP computer management.
But i was anyways gonna do that since i am gonna install hardy after 24th. 

But what has happened to my card? It was working awesome since around one year. :confused:

Pic 1 - Red blocks shouldnt be there.
Pic 2 - Green lines unwanted.
Pic 3 - White dots and white lines not usual.
Pic 4 - I will go mad explaining how i feel looking at that.

HI and just a thought, could it be a power related issue. I am not familiar with that model but I would assume that has additional power to the card. Maybe change the power cable to it or check the power supply.

---

### Post by diplomat.x on 2008-04-22
Hi overdrank, the card draws all its power from the motherboard. No external power required.

I am quite sure now that there is some serious problem with the graphic card. I may have to take it for repair. Till i do that if anyone has any idea of resetting each and everything in the graphic card(like its bios or memory), please reply. 

Thanks

BTW, will my onboard video i.e intel GMA 3100 be able to work flawlessly with hardy heron? (thats with compiz and effects too)

---

### Post by Fubini on 2008-04-22
I'm not experienced with Linux, but I have seen this problem before on a Windows machine.

What had happened was the video RAM had become corrupted, or something, so that it couldn't pass the memtest equivalent for video cards. Thus, the reason for the strange video anomalies - garbage in means garbage out! We used a built-in Dell diagnostic to figure it out, so I don't know where you could go to find a similar test.

Unfortunately for us the only solution for hardware failure was replace the hardware. Replacing the video card worked for us. I do recall that when I was researching the problem some people suggested that it might be actually a motherboard problem, but we eliminated that suggestion by trying out a friend's video card to determine the problem was the card itself.

Good luck diagnosing it.

---

