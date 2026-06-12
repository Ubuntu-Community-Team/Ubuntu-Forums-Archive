---
title: "Using Commview for wifi with  Aircrack-ng"
date: 2009-02-05
forum: Networking &amp; Wireless
---

### Post by oddbirdman2009 on 2009-02-05
I have a bachelors in comp sci from before the time of wireless.  

I am in a situation where I am staying in a motel.  I need access to their wifi connection.  I offered them 20 bucks fo acccess.  They aren't sure what the key is for their router.  I was told if I could acquire the key I could have access.

I watched a video on YouTube in which a kid used Commview for WiFi along with the GUI version of Aircrack-ng.  

I am folowing his exact instructions but not getting the same results.  I am monitoring Channel 1, gathering about 850,000 packets, then running aircrack-ng GUI.  I direct Aircrack towards my .cap file then run it.  

It then askes me for the index number of the network.

I enter one of the numbers which indicates there is an IV present.

It runs, says "Failed, next time try 5000 IVs."

it looks like it is only using 1 IV.

I'm lost at this point, can anyone help me out?  I need this conection so I can get back to work and get my but out of a motel and back into a real home....

---

### Post by luig1 on 2009-02-05
Lucky for you I have done this before but I have done this in windows xp. Can you tell me your one(xp,vista,linux)?

---

### Post by oddbirdman2009 on 2009-02-05
I'm using Vista...   I tried this before with the same exact results in XP, however...

---

### Post by luig1 on 2009-02-05
Yes but to get more ivs try using a bssid instead of indexing and aslo use ivstools to filter out all the non ivs. If you need more specifcs just ask.

---

### Post by oddbirdman2009 on 2009-02-05
I need a massive amount of more info...



If I specify the bssid in advanced it reads 10,000 IVs then re-reads them, and then just ends.  nothing happens.

If I specify the Essid from the list it says the target network does not exist.

Please try and detail out what I should be doing....

---

### Post by luig1 on 2009-02-05
Well first of all I need to know what version of aircrack your using. I use aircrack-ng-1.0-rc1-win.

---

### Post by oddbirdman2009 on 2009-02-05
aircrack-ng-1.0-rc2-win   I'm using the GUI also because I have no idea how to use the Cmd mode....  it's been a long long time since I used DOS, maybe when 95 was out? so, I'm kind of lost.

---

### Post by luig1 on 2009-02-05
move all the files as close as the root of the C:\ drive or your local drive. tell me when u move your files. and also do you have a faster way of comunicating like live messenger or something im kinda busy.

---

### Post by oddbirdman2009 on 2009-02-06
you can find me on yahoo messenger:  matthew.mayze   

Obviosly, Idon't have a connection at home.  I am at the library.  It is 12:03pm.  I will stay as long as I can.

please come and find me.

---

### Post by eddiozks on 2012-08-04
Hllo luig1

i want to ask something about those things i have the same problem.

---

### Post by wildmanne39 on 2012-08-05
Hi, this is an old thread so it has been closed and aircrack is not supported on the forums any longer.

You should try the backtrack forum.
Thanks

---

