---
title: "having projector running kills touchpad"
date: 2008-12-05
forum: Multimedia Software
---

### Post by chiefofthejojos on 2008-12-05
I have a very strange problem that I think maybe should be posted on some electricians forum instead, but I'm hoping someone here has some ideas.

Laptop: HP Pavilion dv2000z, Nvidia GForce Go 6150, latest nvidia drivers provided by restricted drivers manager (I think 177)
Projector: Lumenlab Evo 1.2
They are plugged into the same outlet in the wall (only outlet with a ground in my room)

My laptop runs happily until I start up the projector, but when the projector is running the mouse cursor control get really glitchy.  The cursor starts jumping across the screen and clicking randomly.  Here's the strange part: the projector is not even connected to the computer at this point.  I have found that if I unplug the power adapter from the laptop it works fine.  However, if I then proceed to connect the laptop (via External VGA port) to the projector, the mouse cursor stops moving altogether (although random clicks still happen, even touchpad clicks).  My IR remote stops working as well at this point.

I have searched high and low for a solution to this and have found nothing, not even evidence that anyone else is having this problem.

Please, if you have any ideas pleas suggest them.  I will try an external mouse, but I'm actually more concerned about the remotee working because I wanted to try MythBuntu on this laptop.

Thanks,
Brad

---

### Post by girishsasikumar on 2008-12-05
looks like u have a Ground Interference problem. I suggest you try checking the earthing connection of the Projector and whether earthing of you wall socket is proper. See whether there is a voltage between wall socket ground and wall socket neutral with and without the projector connected. I believe u will get a voltage when projector is connected.

---

### Post by chiefofthejojos on 2008-12-05
I would like to say that I will check those thing when I get home today but I didn't understand a lot of what you said.  What is the earthing of the projector/socket?  Also, I don't have a voltmeter to test those voltages with.  Would replacing the socket hardware fix a ground interference problem or am I over simplifying?  Thanks so much for the response.

---

### Post by girishsasikumar on 2008-12-05
Well I would say since it involves the main AC power supply system of your house and some costly electronic equipment better get a qualified electrical technician to fix it up. Tell him to check for earthing problem in your home electrical system especially at the wall socket to which you connect your projector, maybe you should give your projector a check up too.
      A suggestion I would like to give is to try using the projector in another apartment, maybe your friends apartment and see whether you laptop still gets problem.
      And about you not understanding what I wrote last time, most people don't ......... check up with me if you still have problem after doing what i suggested, and u still have some doubt

---

### Post by chiefofthejojos on 2008-12-07
Well I did a little more troubleshooting.  I tested a socket in the living room and had the same problem on multiple laptops(both Ubuntu 8.10).  So, it seems that it may be a whole house issue like you suggested.  An external mouse works, which is great, and the remote works fine under Mythbuntu.  Actually, I am completely satisfied with the way things are(or satisfied enoughh to not pay an electrician to fix it) but the big question I have now is: can it cause any harm to my laptop and/or projector to keep using my electrical system as is?
Thanks so much for all the help.

---

### Post by girishsasikumar on 2008-12-07
Yes you have a problem that needs to be fixed and it could be dangerous if you don't do that.
1. Suppose that your house does not have a proper grounding as is evident from a similar thing happening all over your house, your electrical system could harm you a lot. The earthing system of your house is designed to ensure that in case of a fault such as some short circuit, or somebody getting a shock the electrical system, the excess current is supposed to get connected to earth and get 'drained'. So you see there is a problem on that count.
2. Well you can classify and say that there are basically two types of electrical systems in your house, 
a) large power devices like aircons, refrigerator, kitchen appliances, water heater which use a lot of current. with these devices there will be  a leakage current almost always and in some cases significantly high which normally flows down the earth terminal of your wall socket and gets drained off.
b) electronic devices which use very less power compared to those in (a) like your computer, laptops, music systems, television etc whose earth also gets connected to the wall socket earth.
         What happens is that if there is no proper grounding/earthing the leakage current of power devices or faulty devices keep flowing to the low power electronic devices and they start behaving strange like you had. In computers they generally tend to harm the RAM first (my experiences in some cases like this) and you get errors in some RAM addresses.
         So as you can see this can lead to unnecessary repair costs for quiet sensitive and costly equipment, one which you can easily avoid by getting it fixed by somebody qualified to do that.
         Secondly you are putting yourself in way of body harm in case of electrical faults in your house.

         The concrete solution of this problem lies what is the construction of your home. If you live in an apartment or flats with many other families this could be a common problem because you all most probably will be sharing a common earthing.
         If however you live in separate house, what i mean is something live individual houses  with their own earthing you have no choice but to get it fixed yourself.

---

