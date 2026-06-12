---
title: "how to get ndiswrapper to start at boot-up?"
date: 2010-06-06
forum: Networking &amp; Wireless
---

### Post by rcayea on 2010-06-06
I had been having problems with my Asus wireless card connecting to my router. Turns out, using ndiswrapper and the XP driver solved the issue. Based on my title of the thread, the driver worked, I turned off computer at night, next day, I can't seem to start the wireless driver again. How would I go about doing this? I am running Ubuntu 10.04, Asus PCE N13 wireless card. thanks, randy

---

### Post by ajgreeny on 2010-06-06
How did you install the Win XP driver?  I have done the same thing on an old laptop of mine using ndisgtk, and navigating to the winXP driver.INF file which I have in a folder in /home on the laptop.  It works faultlessly, so I wonder if this is how you did it.

---

### Post by rcayea on 2010-06-06
> **ajgreeny said:**
> How did you install the Win XP driver?  I have done the same thing on an old laptop of mine using ndisgtk, and navigating to the winXP driver.INF file which I have in a folder in /home on the laptop.  It works faultlessly, so I wonder if this is how you did it.

Thanks for the response. 

I installed this XP driver from the Asus disc that came with the wireless card. 

I didn't put the driver anywhere on my hard drive, which I am guessing it sounds like I should. Should I take that XP driver and drop it into my home folder?

---

### Post by ajgreeny on 2010-06-07
I am not sure, but it's worth a try.

---

