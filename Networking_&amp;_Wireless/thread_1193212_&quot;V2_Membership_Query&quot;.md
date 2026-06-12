---
title: "&quot;V2 Membership Query&quot;"
date: 2009-06-21
forum: Networking &amp; Wireless
---

### Post by kilgore9 on 2009-06-21
Ok heres my problem.  Since upgrading to 9.04, I have a lag problem playing an online FPS game (open arena).  Ever 2 minutes or so I get a "connection interruption".  I downloaded wireshark to observe my traffic and see what might be causing the problem (for several reasons I was able to rule out the possibility that the game or servers were causing this).  Lo and behold, I found a strange packet being sent back and forth "V2 Membership Query" about every two minutes.  This happens even when no applications are running as long as I am connected. 
 
I suspect that this might be causing the "blip" in my connection.  Anyone know what this is and how I can get rid of it.  If it is something that needs to be happening, I would atleast like to set it to happen ever 30 minutes (for example) instead of every two.  

I will attach a screenshot of wireshark so you can see the packets....

---

