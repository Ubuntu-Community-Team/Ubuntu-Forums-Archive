---
title: "FX5500 and Userful dual station software"
date: 2006-01-23
forum: Multimedia &amp; Video
---

### Post by mealz on 2006-01-23
I am trying to setup dual station linux with the software from [http://www.userful.com/products/free-2-user](http://www.userful.com/products/free-2-user) . 
So far I get the X server locking up or something when it try's to initialize the 2 screens. I see independent pictures on the screens for about 1 second, then they both go blank and the num lock key flashes. The system is still up however because I can still connect through ssh.


I have installed a fresh ubuntu system, installed nvidia-glx, nvidia-settings and restricted-modules.
A reboot of X came up with the nvidia logo so i believe that is working properly.
Then installed userful's product, rebooted and their configuration screen came up and performed as above.

Where should I start?

note: i just found in one of the userful's logs:

(EE) failed to load glx

---

