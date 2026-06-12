---
title: "EPG description info is wrong"
date: 2010-11-15
forum: Mythbuntu
---

### Post by mnclayshooter on 2010-11-15
Hi,
 
I've been using 10.04 with myth and I've been having a great time using it for recordings etc.  One issue I haven't been able to solve is that my EPG data seems to be wrong for some shows.  The show titles are correct, but the descriptions are wrong.  Almost like they're for shows which aired a few hours earlier.  Its not consistent though, otherwise I'd assume it was an issue of time zones or daylight savings etc.  Any thoughts? Anyone else see this happen?  Its not only annoying, it causes my duplicate checking to not work correctly.  
 
I have a Hauppage 2250 card if that makes any difference.

---

### Post by nickrout on 2010-11-15
What is the source of your epg listings?

---

### Post by Senkoboy on 2010-11-15
I have had the same problems with OTA information.  Sometimes it will be right for a couple of days on a weekly show, then before it records the description will change.

---

### Post by LowSky on 2010-11-15
> **mnclayshooter said:**
> Hi,
 
I've been using 10.04 with myth and I've been having a great time using it for recordings etc.  One issue I haven't been able to solve is that my EPG data seems to be wrong for some shows.  The show titles are correct, but the descriptions are wrong.  Almost like they're for shows which aired a few hours earlier.  Its not consistent though, otherwise I'd assume it was an issue of time zones or daylight savings etc.  Any thoughts? Anyone else see this happen?  Its not only annoying, it causes my duplicate checking to not work correctly.  
 
I have a Hauppage 2250 card if that makes any difference.

Change your recording to only record new listings, or only use the title and not the description.

Be careful though some shows might not list the name or if its a new episode. Some channels are very bad at it.

---

### Post by mnclayshooter on 2010-11-15
I'm getting all of my EPG data from OTA EIT source.  I've read so many responses on other sites and here blah blah blah OTA sucks yadda yadda yadda.. but when it first pulls the EIT data, its correct, somehow it gets corrupted over time as other poster had mentioned. My set-top box has no issues with the very same channels/times.  There's something about how Myth chews on this info that gets the show descriptions all jumbled up.   The titles all remain correct.  
 
I'd have no problem getting a subscription for listings, however my myth box is not on a full-time internet connection, so it would always have to be manual.  I'd ideally like to sort out the EIT/OTA method.

---

### Post by Senkoboy on 2010-11-15
[QUOTE=but when it first pulls the EIT data, its correct, somehow it gets corrupted over time as other poster had mentioned. My set-top box has no issues with the very same channels/times. There's something about how Myth chews on this info that gets the show descriptions all jumbled up. The titles all remain correct. [/QUOTE]

That is the same problem I have.  What is weird is normally ETI data only shows up for 12 hours or so, but sometimes I can get a show description on a weekly recording, correct, several days in advance. Then a few hours before before it records the description will change.  My set top box or other tv will still show the right information.  This is in United States, Oklahoma.

---

### Post by LowSky on 2010-11-15
Schedules direct will give you lisitings for up to 14 days in advance, you can even schedule the hookup as need or run the command yourself when you have a connection.

what I want to know is how did you scan for channels without a lineup? if you never used Schedules direct in the US? Did you label all the channels yourself?
[http://www.mythtv.org/wiki/EIT](http://www.mythtv.org/wiki/EIT)

---

### Post by mnclayshooter on 2010-11-15
> **LowSky said:**
> what I want to know is how did you scan for channels without a lineup? if you never used Schedules direct in the US? Did you label all the channels yourself?
[http://www.mythtv.org/wiki/EIT](http://www.mythtv.org/wiki/EIT)
 
I just ran the normal scan for channels when setting up the tuners and it ran perfectly all on its own by the OTA signals.  All of the channel numbers/names came in correctly for both tuners without any intervention by me other than clicking "next" and "finish" on the setup screens.  Maybe I'm not understanding your question?

---

### Post by mnclayshooter on 2010-11-15
> **Senkoboy said:**
>  Then a few hours before before it records the description will change. My set top box or other tv will still show the right information. 
 
This is exactly what I'm seeing too. Like the data is getting corrupted somehow. I can get data for about 24 hours for most stations in Minneapolis, MN. Some only 12 hours, some out 3+ days. I have EIT scan set to update overnight between 2AM and 11AM (typically I don't have many/any recordings during this window so tuners are available). 
 
I think the only thing I haven't tried is deleting one of the tuners and only using one to see if its an issue of one tuner over-writing the other's EIT data somehow? I can't think of what else would cause this.
 
I'm not sitting at my myth box right now, but as an example from memory - I'll get show description for "Two and a Half Men" when it should be the description for the evening news on the same channel etc.  But then the listing for "How I Met your Mother" will be correct which is right next to "2.5 men".  Its not consistently shifting the descriptions on this channel... more like its jumbling them up.  When I use phpmyadmin and take a look at the mythdatabase, its all screwed up in there too (which I had no real reason to assume it wouldn't be).

---

### Post by winewood on 2010-11-15
If you plan on using your Mythbox for any serious TV watching /scheduling, the EIT off air scans will not be sufficient. I tried using them for a week or two for testing, but schedules direct is too cheap, accurate, and well incorporated into myth not to use.
They offer a 7 day trial version. I would seriously recommend trying it. You will see the value quickly.  AND this will fix your EPG problem :)
 
[http://www.schedulesdirect.org/](http://www.schedulesdirect.org/)
 
It will take you 30 minutes tops to get this working.

---

### Post by Senkoboy on 2010-11-15
Its not the price of schedules direct that's the problem.  I need to buy a router and run a cable into the garage to hook the computer to the internet.

---

### Post by mnclayshooter on 2010-11-16
senkoboy - I hear ya... that's essentially my situation. I use cell provider for internet service (mobile) and don't have a convenient way to share the connection to the myth box in a dedicated way. 
 
I know all about schedules direct and how it works. I agree, its pretty sweet, but, OTA EIT *should* work, and its free. I just wish I knew more about linux so I could figure it out! That's really why this post exists... 
 
Thanks for the help everyone... I'm interested in suggestions that don't have anything to do with trying to get schedules direct. :)
 
LowSky - huge thanks to you!!! I've used many of your other posts to help get my setup working.  We have several ubuntu boxes running here and most have variations on the install for testing purposes.  Your tips/write-ups have been invaulable at testing things.  Thank you!

---

### Post by LowSky on 2010-11-16
> **Senkoboy said:**
> Its not the price of schedules direct that's the problem.  I need to buy a router and run a cable into the garage to hook the computer to the internet.

Run cable? Why not go WIFI, less mess and they do make USB models.


> **mnclayshooter said:**
> senkoboy - I hear ya... that's essentially my situation. I use cell provider for internet service (mobile) and don't have a convenient way to share the connection to the myth box in a dedicated way. 
 
I know all about schedules direct and how it works. I agree, its pretty sweet, but, OTA EIT *should* work, and its free. I just wish I knew more about linux so I could figure it out! That's really why this post exists... 
 
Thanks for the help everyone... I'm interested in suggestions that don't have anything to do with trying to get schedules direct. :)
 
LowSky - huge thanks to you!!! I've used many of your other posts to help get my setup working.  We have several ubuntu boxes running here and most have variations on the install for testing purposes.  Your tips/write-ups have been invaulable at testing things.  Thank you!

Wow, you're welcome for whatever I have done to get your setups working.

I'm sorry we really don't have a better answer than to use Schedules Direct. In the US we have no real choice in the matter. Congrats that you have a channel line up and EPG working even if just sort of.

My best advice is to just record first showings or set them to only record at a given time. Remember that the 2250 can record 2+ shows at a time as long as the channels are sharing the same digital frequency. So if your worried about not recording a few things you might have to open live TV and PIP using the same tuner and see if what you can watch at the same time.

---

