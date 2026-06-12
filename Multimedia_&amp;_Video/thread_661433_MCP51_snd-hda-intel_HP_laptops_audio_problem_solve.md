---
title: "MCP51 snd-hda-intel HP laptops audio problem solved"
date: 2008-01-07
forum: Multimedia &amp; Video
---

### Post by mempman on 2008-01-07
I have a HP dv2000 laptop with nVidia sound codec MCP51.  I am running fiesty ubuntu w/  Windows Vista dual boot.  The problem I was having is that occasionally sound would work with Ubuntu and most of the time time it wouldn't work.  

After collecting some observations, I realized that sound would only work in ubuntu if I booted into ubuntu with my Vista partion in HIBERNATE mode.  I.E. if vista was restarted and then ubuntu was selected from grub...my ubuntu sound would NOT work.  To make it absolutely clear, my ubuntu sound only worked when I put my VISTA into hibernate mode, and the selected ubuntu from the grub menu after i powered up.  

Solution: I was able to solve this problem by booting into Vista and removing Conexant audio driver, and instead installing "High Definition Audio Driver" onto my Vista partition.  Now, regardless of how I boot into ubuntu, my sound is fully functional. 

I was really frustrated in trying to figure this one out, as most ubuntu experts (God Bless them) in the forums and IRC don't have dual-boot Vista systems; therefore, it was rather difficult to troubleshoot with them.

If this helps you out, please posts your results.
memp

---

### Post by rnayak on 2008-02-23
Thanks Mempman - 

I have a dv2620us and exactly the same issue - your observation is very accurate.

Can you please explain how to install the "High definition audio driver" in vista.  Appreciate your help.

-Raj

---

### Post by brinkofacomplex on 2008-04-07
I've got the same symptom with XP, but different problem I guess; putting Windows into hibernation doesn't change it for me.

---

### Post by carruthers on 2008-04-10
Could you possibly tell me which high definition audio controller you mean? thx

---

