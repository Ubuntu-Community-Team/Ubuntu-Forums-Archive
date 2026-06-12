---
title: "Reminder for upcoming program ?"
date: 2009-05-25
forum: Mythbuntu
---

### Post by ianhaycox on 2009-05-25
Is there a MythTV module for notification of an up and coming programme.

For example, Say I want to watch the movie Ronin but it's not listed in the EIT data for the next 7 days, it would be nice to have Myth notify me when it's going to be shown.

I can use the search facility every couple of days, but it's a bit tedious, especially if there's a large list of programmes I want to check for.

I did knock up a simple cron job to run an SQL query every day to check the program table, but it's very very basic. 

Is there anything available ?

Thanks.

---

### Post by ianhaycox on 2009-05-25
Not sure how I missed it before but TVwish, [http://www.templetons.com/brad/myth/tvwish.html](http://www.templetons.com/brad/myth/tvwish.html), works a treat.

---

### Post by jb5 on 2009-06-05
That looks like a neat program, I will give it a whirl. (When I get the chance)!

Additionally you could always go lo-fi and use the search function/s built into mythTV, (search keyword, key-phrase etc. & then select record), it will then wait (indefinitely) for that title to appear.

If you know the exact title this works a treat, it is also possible to cobble together a 'catch all' list of searches.

For instance, in the UK the BBC use subtly differing listing headers for Formula-1 Grand Prix. ->  formula one; formula 1; formula-1; etc... 
So I have several searches set up, which so far have caught all the Grand Prix and a few other formula-1 related programs!

A quick and 'dirty' way to achieve a similar goal, but I will give the program listed above a go. thanks.

---

### Post by ianhaycox on 2009-06-05
Something I find useful in TVWish is the SQL wildcard, %, matching.

For example, I setup

Series: The Wire
Episode: %

to catch all the episodes, so you could try

%formula 1% 

I doubt it would catch stuff on the red button though. You'll just have to scan through STREAM-0 to STREAM-6 for Friday practice and the Classic F1 races.

Occasionally tvwish gets it wrong. For example I set it up as Movie: Spartacus (1960) but it recorded a documentary on Spartacus ! It's not a bit deal as the cron job emails the list of newly scheduled programmes each day.

If there is a good movie on at the cinema that I missed I just add it to my list of tvwish movies then hopefully in a year or two when it's broadcast on TV it gets scheduled!

---

