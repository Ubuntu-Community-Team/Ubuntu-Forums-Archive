---
title: "kaffeine cannot find demux plugin for MRL"
date: 2010-05-13
forum: Multimedia Software
---

### Post by svaens on 2010-05-13
Hi all, 

Just a quick informational post;

After having installed Kaffeine on Ubuntu to use for watching Terrestrial Digital TV through my tv-tuner, on Lucid, Ubuntu 10.04. 

After installing Kaffeine and the proprietary driver and firmware for the card, starting Kaffeine gave me the following error;

"kaffeine cannot find demux plugin for MRL"

I found this problem difficult to find a solution for; but did eventually find mention of a set of plugins which would provide what Kaffeine needs;

libxine1-all-plugins

This was originally mentioned at old nabble:

[http://old.nabble.com/-Bug-233808--New:-Kaffeine-cannot-find-a-selected-channel-to-allow-it-to-be-watched-td28188685.html]("http://old.nabble.com/-Bug-233808--New:-Kaffeine-cannot-find-a-selected-channel-to-allow-it-to-be-watched-td28188685.html")

I installed this, along with all the Medibuntu plugins (just to make sure) and my Kaffeine then worked without troubles.

Basically, I think if i'd originally installed according to the instructions found at the Kaffeine community website: [https://help.ubuntu.com/community/Kaffeine]("https://help.ubuntu.com/community/Kaffeine") i'd have had no troubles. However, I must say I expected all dependencies to be met simply through the apt-get install process. Not so for the plugins of course, as I should have known.

---

### Post by Dark Linux on 2010-05-15
thanks you saved me dude

---

### Post by PsychoNix on 2010-05-27
Thanks Man i tryed to this and its working like a charm 



sudo apt-get install libxine1-all-plugins

---

### Post by snitchlomy on 2010-06-11
Thanks - much appreciated - works great.

---

### Post by SusieSA on 2010-06-17
Thank you! worked for me too.

---

### Post by fjpos on 2010-06-19
> **svaens said:**
> Hi all, 

Just a quick informational post;

After having installed Kaffeine on Ubuntu to use for watching Terrestrial Digital TV through my tv-tuner, on Lucid, Ubuntu 10.04. 

After installing Kaffeine and the proprietary driver and firmware for the card, starting Kaffeine gave me the following error;

"kaffeine cannot find demux plugin for MRL"

I found this problem difficult to find a solution for; but did eventually find mention of a set of plugins which would provide what Kaffeine needs;

libxine1-all-plugins

This was originally mentioned at old nabble:

[http://old.nabble.com/-Bug-233808--New:-Kaffeine-cannot-find-a-selected-channel-to-allow-it-to-be-watched-td28188685.html]("http://old.nabble.com/-Bug-233808--New:-Kaffeine-cannot-find-a-selected-channel-to-allow-it-to-be-watched-td28188685.html")

I installed this, along with all the Medibuntu plugins (just to make sure) and my Kaffeine then worked without troubles.

Basically, I think if i'd originally installed according to the instructions found at the Kaffeine community website: [https://help.ubuntu.com/community/Kaffeine]("https://help.ubuntu.com/community/Kaffeine") i'd have had no troubles. However, I must say I expected all dependencies to be met simply through the apt-get install process. Not so for the plugins of course, as I should have known.

):P

Thanks that worked  but I did not need to install Medibuntu

---

### Post by captainpotato on 2010-06-20
Thanks also from me - it also got kaffeine working for me too on Lucid.

Now I need to find how to get the driver speed back to stop the picture from stuttering at fullscreen... any ideas?

---

### Post by kristersaurus on 2010-06-29
awesome. huzzah. thank you.

---

### Post by dennis11901 on 2010-07-01
I am new to ubuntu and also to kaffeine after installing kaffeine i got the same error message saying its missing demux plugin for MRL.  I have absolutely no idea how and where from to install these plugins in order to watch a simple dvd. Can please show me one by one how to install these and most importantly where to find the plugins. Thanx in advance

---

### Post by digitaria on 2010-07-11
Another thank you.  This fixed kaffeine for me on Lucid.

---

### Post by JoulSauron on 2010-07-11
I also would like to thank you :)

---

### Post by alchandia on 2010-07-15
thank you very much!

I had the same problem with phonik :)

Al.

---

### Post by Bodsda on 2010-08-19
Excellent, solved my problem with Amarok as well, cheers :)

Bodsda

---

### Post by Pedrinho on 2010-08-26
Brilliant. quick google search and fixed problem in Lucid. Thanks very much.

---

### Post by rafalbertgn on 2010-10-01
OOOOOOOOOhhhhhhhhhhhhhh thanks!!!!!!!!!, i looked everywhere for a way to watch dvd's with my kaffeine and was just missing that library, now it works perfect.
Thank you again.

---

### Post by oregonbob on 2010-11-18
I too must thank Google search and your post for solving this. I had Kaffeine working great on 10.04, but when I upgraded I got the error. Thanks!

Kudos for Kaffeine too! I use it on Gnome to watch over-the-air digital TV on my Hauppage 1600. Nothing works as good as Kaffeine.

---

### Post by leeper69 on 2011-01-08
thanks this works for ubuntu 10.4 and 10.10 for getting free tv.

---

### Post by kduclos on 2011-02-12
Thank you. I was looking all over for this.

---

### Post by ibm450 on 2011-03-06
thanks heaps,

---

### Post by PaulW2U on 2011-03-13
The power of searching!

kaffeine fixed on my test version of Natty!

Thank you!

---

### Post by schum3,1415 on 2011-04-04
Many thanks to svaens and PsychoNix!!

---

### Post by viktoria.s on 2011-04-11
Thank you for this information! You have saved me a lot of time!

---

### Post by reznor on 2011-09-03
Thanks a lot!
Still up to date for 11.04

---

### Post by tlesinsk on 2011-09-29
Thanks ! This solved the same error I got when playing a DVD on 11.10b2.

---

### Post by exsysprog on 2011-10-24
Great!  
Thanks

---

### Post by wonderingwhy on 2012-05-19
Thanks for the suggestion. But for me - after doing this, TV in Kaffeine appears jerky and choppy and no sound whereas before I just had no sound.  And I still have no demux plugin.  

Back to uninstalling all my installs and having to rethink.

---

