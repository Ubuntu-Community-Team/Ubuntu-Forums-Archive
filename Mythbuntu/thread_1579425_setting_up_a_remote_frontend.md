---
title: "setting up a remote frontend"
date: 2010-09-21
forum: Mythbuntu
---

### Post by benlyboy on 2010-09-21
Hi all hope someone can help.

I'm trying to set up a new front end to work with my existing mythbox front/backend  my existing setup is a mythbuntu 9.10 that was upgraded to 10.1..(I think)

I used the same disk and loaded a frontend only install on the new system then did the updates and upgraded it in the same way as my box had been.

I changed the backend setting on my box. (changing the ip address from 127.0.0.1, to the boxes IP address) was this right?

My main problem is that the new front end seems to want a four digit security code. How ever my back end has a place for a security code but is doesn't seem to be limited to four digits. In any case I entered a 4 digit code in this spot, but when I go back to my front end and try to enter it there. then hit the apply button the mythbuntu control center grays out but then nothing, it never finishes 

If I run the frontend it look as if it almost works the front end comes up for a second then closes.

If I change the backend IP back to the 127.0.0.1, then the new frontend will come up and stay up. a box comes up saying that it can not find the backend and asking if the backend is running or is the ip set wrong.

So does this mean that when it is closing it's because it is connecting to the backend, but that the security is not set up right so it is closing...? 

Any help in setting this up would be great thanks:)

---

### Post by larsolav on 2010-09-21
> **benlyboy said:**
> Hi all hope someone can help.


If I run the frontend it look as if it almost works the front end comes up for a second then closes.


This may be a symptom of the backend and frontend being set to different cities in the time zone setup. From the desktop go to Applications -> System -> Time and Date on both computers and set the time zone to the same city, not just same time zone. I had the exact same problem once and this solution fixed it at least for me.

---

### Post by benlyboy on 2010-09-22
thanks larsolav

That did it...I found that indeed the two boxs has different cities even though they were in the same time zone. I changed one so that they were both the same, and it worked right off. 


Thanks again

---

