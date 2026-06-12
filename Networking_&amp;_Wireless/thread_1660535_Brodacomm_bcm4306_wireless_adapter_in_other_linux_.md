---
title: "\ Brodacomm bcm4306 wireless adapter in other linux distros?"
date: 2011-01-05
forum: Networking &amp; Wireless
---

### Post by hansolo4949 on 2011-01-05
I was wondering if any of you knew of any linux distro that supported the bcm4306 wireless adapter, or one you could get it working on easily. I have tried Ubuntu, on a 6+year old laptop, which had the afore mentioned wireless adapter, and Ubuntu wouldn't get that miserable piece of hardware to work :D. I don't really care which distro of linux I put on there, as long as I can get the wireless adapter to work, and it isn't a pain to set up and use. I do hope someone knows of a distro that supports it. If you do know a fix for the wireless card in Ubuntu/Xubuntu, please post it on my other thread, which you should find easily in the wireless and networking section.


Thanks!

hansolo4949

   (hoping my broadcomm woes are over)

P.S. I am so sorry about the poor spelling in the title of the thread, I didn't notice the typos until I hit "post"

---

### Post by snowpine on 2011-01-05
Broadcom cards require a "nonfree firmware" and therefore most Linux distros will require a one-time, 5-minute extra step to install this firmware. A temporary wired connection will be helpful. More details here:
[http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by hansolo4949 on 2011-01-05
Thank you for your quick reply, snowpine!

I did know that broadcomm needed a "nonfree" driver, but unfortunately, I have tried to set it up to no avail. Does anyone know how to set up a broadcomm bcm4306 wireless adapter card with ndiswrapper in Xubuntu? or does anyone know any simpler way? I am almost at my wit's end here... I have looked at so many threads here about this problem, but the solutions wouldn't work for me, most of the time because the responses were tailored for that person's specific problem, not mine.

Hoping that someone can help me soon [-o<



Hansolo4949

---

### Post by snowpine on 2011-01-05
Have you tried installing the b43-fwcutter package, while connected via wired ethernet, [as described here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing b43 drivers")?

---

### Post by hansolo4949 on 2011-01-05
ohhhhh yes, I have tried fwcutter every which way. I will try it again though, in high hopes that this time, with this particular method, it will work. 


Hoping to get another response soon,

hansolo4949

---

### Post by hansolo4949 on 2011-01-05
I did as you told me, on a live cd, and the wireless light lit, but network manager doesn't see any connections! I also managed to detirmine that my card is a bcm4306 revision 3 card.

Hope that helps!

hansolo4949

---

### Post by hansolo4949 on 2011-01-05
Update: I just figured out that my card is a bcm4306 revision 3 card

---

### Post by hansolo4949 on 2011-01-05
When I run iwlist, it says that there are no access points. is there something more to this, or am I doing something wrong?
I feel like we are getting close!
hansolo4949

---

### Post by snowpine on 2011-01-05
OK, good, that's Step 1!

Have you tried Step 2 yet?

> Step 2. 
Under the desktop menu System > Administration > Hardware/Additional Drivers, the b43 drivers can be activated for use. 
Note: A computer restart may be required before using the wifi card.

---

### Post by hansolo4949 on 2011-01-05
The saga continues... I was knocking around on that computer, hoping to find a solution, when all of a sudden, it asked me for a password for my wireless network! I will now try it on an installed xubuntu and tell you the results


and yes, I did do step 2, but the livecd way

 yay! we are sooo close, I can almost see it working!

hansolo4949

---

### Post by hansolo4949 on 2011-01-05
Well, I installed Xubuntu, and.....it works!!!!! I have no idea what I had done wrong before, but I installed it, and it works perfectly!! 1,000 thanks, and more! Now, please don't write this thread off quite yet, because I am afraid it will start acting up, but [B][I]_THANK YOU_!!!


[/I][/B]hansolo4949

---

### Post by hansolo4949 on 2011-06-05
Just to clarify, [this]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx") link is what worked for me.

---

