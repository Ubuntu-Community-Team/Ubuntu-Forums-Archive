---
title: "Upcoming recordings missing"
date: 2008-04-02
forum: Mythbuntu
---

### Post by se99paj on 2008-04-02
I restarted my mythbuntu box last night, no particular reason why as I didn't install anything new or make any changes.

But now I cannot find anything in my upcoming recordings page, there are programmes schedule to be watched and one of them is this evening, but there is nothing in the upcoming recordings page. I also cannot add anything new either.

I have found a few similar problems but they haven't resolved the problem. Does anyone have any ideas?

Thanks for your help.

---

### Post by foxbuntu on 2008-04-02
> **se99paj said:**
> I restarted my mythbuntu box last night, no particular reason why as I didn't install anything new or make any changes.

But now I cannot find anything in my upcoming recordings page, there are programmes schedule to be watched and one of them is this evening, but there is nothing in the upcoming recordings page. I also cannot add anything new either.

I have found a few similar problems but they haven't resolved the problem. Does anyone have any ideas?

Thanks for your help.
Which version of MythTV are you using? When you rebooted did you hard reset (i.e was the machine hung up and you powered it off and back on, not a normal reboot)?

---

### Post by volkswagner on 2008-04-02
You may have corrupt mysql database.  You can check and fix errors by 

```
mysqlcheck --auto-repair -A -u mythtv -pmysqlpass
```

edit the above by inserting you password, in place of "mysqlpass".  You will need to retain the "p" in front with no spaces.  Note if any errors were found.

As foxbuntu has hinted, corruption can occur if you were not shutdown properly.

---

### Post by billy_big_time on 2008-04-03
I had a similar thing occur last night (all upcoming recordings dissappeared, can't add new ones).  Not sure if it's the same problem as yours but I traced mine back to mythbackend deleting all the capture cards from the database, so although the programme searches were matched to the schedule there were no tuners to record on.
I don't know for sure but I think this was caused by trying to connect a 0.21 frontend to the 0.20.2 backend - I have absolutely no idea why this would delete my capture cards.

I've tried repairing the database and adding the capture cards again with no luck, so I'm just going to take this opportunity to try out the mythbuntu 8.04 beta.

---

### Post by billy_big_time on 2008-04-03
Replying to my own post.  My database problem was caused by me stupidly hitting 'upgrade' when the 0.21 frontend asked to upgrade the database schema.

(apologies for the thread hijack)

---

### Post by se99paj on 2008-04-03
I'll check the version when I get home, I have recently upgraded.

I did look at the mythbackend and it did have a problem initiating the capture card, unfortunately the capture card is temperamental with MythTV, I'll try and reinstall the card tonight. As it sounds like if the card isn't working then it can cause the problems that I'm having.

---

