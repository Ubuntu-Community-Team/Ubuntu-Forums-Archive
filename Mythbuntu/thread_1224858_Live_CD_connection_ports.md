---
title: "Live CD connection ports"
date: 2009-07-27
forum: Mythbuntu
---

### Post by turtle02 on 2009-07-27
I was wondering what ports i need to nat through my router to be able to connect to my server from anywhere, thanks

---

### Post by tgm4883 on 2009-07-27
If you are talking about Mythweb, then Port 80

If you are saying you want to have a Frontend and connect it over the Internet to a backend at your house, then your connection isn't fast enough

---

### Post by turtle02 on 2009-07-28
thanks but it isnt actually at my house it is a work we have a ds3 45meg up and down. Do you know the ports?

---

### Post by elgordo123 on 2009-07-28
Good luck with that. I'll be very suprised if it works or if it does, if it is usable.   
You should be able to just forward the mythtv port. I think the default is 3306.   You may have to do some changes to mysql too, but if you have a remote frontend working over lan, it should work from internet, but not sure about that part. 
Please post back and let us know how it goes.   
I actually use a bash script that I use for this. I ssh into my box, run the script, which will then start vlc streaming my videos, recordings, dvd, or live tv.  It allows me set the video size and speed depending on where I am at.

---

### Post by tgm4883 on 2009-07-28
> **turtle02 said:**
> thanks but it isnt actually at my house it is a work we have a ds3 45meg up and down. Do you know the ports?

IF nobody else is using that internet connection at your work AND IF your download connection speed is good enough wherever you are at AND IF you only record Standard Definition AND IF you don't have bottlenecks somewhere between you and your server, it may work.

Not trying to rain on your parade, just trying to give you some of the obstacles.

---

