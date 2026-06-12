---
title: "internect connection stopped working"
date: 2011-06-27
forum: Networking &amp; Wireless
---

### Post by highrik on 2011-06-27
My friends computer has been running ubuntu for a couple of years.  Suddenly about a week ago she could no longer get an internet connection.

Firefox goes into 'work off line' mode on boot and when this is unticked the message is 'could not find server'.  

I know the hardware all works because a live CD gains internet access.  Any advice to solve this problem would be much appriecated.

cheers
Rick

---

### Post by highrik on 2011-06-27
Actually I think it's xubuntu not ubuntu.

---

### Post by Iowan on 2011-06-27
Depending on version - there are probably some GUI equivalents, but...
What are the results of **ifconfig -a ** (from a terminal - Applications>Accessories>Terminal)?
If no IP address is shown, **sudo lshw -C network** should provide more details about the hardware.

(It would be helpful if you could post the results)

---

### Post by highrik on 2011-06-28
thanks for advice.. I'll pop round today and let you know how I get on.

---

### Post by highrik on 2011-06-29
Hi Iowan, my friends internet connection is back up and running.  I think it must have been a modem problem as I rebooted both the modem and PC and then the internet worked. Having said that I'm sure I did that the first time I popped round to look at it but it didn't solve the problem.  

Hopefully thats an end to it though.. but thankyou so much for your advice :-) 

Rick.

---

