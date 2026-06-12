---
title: "mythfilldatabase Question"
date: 2009-06-16
forum: Mythbuntu
---

### Post by Mattaus on 2009-06-16
What exactly is it? I only ask because I don't like to blindly solve problems - I want to know what is happening behind the scenes for better problem resolution in the future. The wiki seems to only detail its configuration, not what it does exactly.

The reason I ask is because I have just setup MythTV on my Ubuntu machine, and will be using a plugin in XBMC called MythBox as my front end. The problem begins when I did my intial setup. The following guide is what I used to help me set it all up:

[http://parker1.co.uk/mythtv_ubuntu.php]("http://parker1.co.uk/mythtv_ubuntu.php")

However just before it says to test MythTV it makes a deliberate note to not run mythfilldatabase because they are using EIT. Now even though I am not using EIT (I am using shepherd as it was recommended for us Aussie users) I did'nt run it either.

Now MythBox wont run because it needs the database. So my question after all that (!) is will running the database mess anything up? I can't see why it would because from my brief research this morning it seems plenty of people are running mythfilldatabase with shepherd (and having problems but hopefully I wont. If I do I will switch EPG grabber) so I can't see what the harm will be.

This of course all comes back to understanding exactly what it is!

Sorry for rambling but I like to be clear...though I may have messed that up as well ;)

Cheers.

---

### Post by Hobgoblin on 2009-06-16
I may be wrong but I thought mythfilldatabase updated the schedule information from whatever source you have chosen to use.

---

### Post by Mattaus on 2009-06-16
> **Hobgoblin said:**
> I may be wrong but I thought mythfilldatabase updated the schedule information from whatever source you have chosen to use.

I'm the wrong person to ask lol but I'm assuming your asking other people that will (fingers crossed) reply. As far as I can tell you are right and running the mythfilldatabase wont effect jack for me. 

Hopefully.

---

### Post by laffinet on 2009-06-16
I'm by no means an expert on this, but I believe mythfilldatabase does a bit more than just update schedule data. Whenever you rescan channels, edit channels etc. in mythbackend setup you're asked to run mythfilldatabase.

In answer to your concerns about shepherd:
I'm running a "normal" 9.10 install (no XBMC, combined frontend/backend) with shepherd as grabber for schedule data. I do run mythfilldatabase whenever asked to and never had any options. In fact, I think without mythfilldatabase schedule information will not be made available to mythbuntu. Shepherd grabs the schedule information and writes it to a file (some xmltv file somewhere). Mythfilldatabase (or some other process, not sure) grabs the information from there and populates it to mythtv.
In short: I run shepherd and mythfilldatabase and have no problems.

---

### Post by Mattaus on 2009-06-16
Well then it appears that I shall also be running mythfilldatabase. Really odd that the guide I used said not to run it. I wonder if it was more of a "don't bother" than a "this is bad" sort of thing.

One way to find out...

---

### Post by laffinet on 2009-06-16
Good luck. I hope nothing breaks...:D

---

### Post by Mattaus on 2009-06-17
> **laffinet said:**
> Good luck. I hope nothing breaks...:D

If I don't break it doing this, I will when I try one of the other 50 odd things I have set to still do. Such is Linux!

---

