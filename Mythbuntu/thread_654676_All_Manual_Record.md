---
title: "All Manual Record"
date: 2007-12-31
forum: Mythbuntu
---

### Post by ljbeng on 2007-12-31
I only have manual recording setup, no tv schedules are used.  I have 8 programs that get recorded weekly.  Today, I noticed that I did not have any new recordings since 12-22-07.  When I went to Upcoming Recording, the unit told me I did not have any programs scheduled to record.  I had to put all 8 programs into my record schedule again.  What happened?

---

### Post by newlinux on 2007-12-31
You could have had some database corruption or tuner problems. Have you looked in your backend logs? Have you changed any configurations? Are all your tuners functioning properly. the more information the better our chances of helping you.

---

### Post by Medieval Cow on 2008-03-25
Hey, just giving this a bump because I'm having the same problem. I can give a bit more detail though, as I've been dealing with this for a bit and trying to fix it or at least nail down what's causing it.

I generally have between 5 and 7 recordings active on a weekly schedule. I set them all up as a manual record because I don't have a Schedules Direct subscription. I have a cable box from my cable company and I get my schedules through there. So my MythTV box is just always on channel 3, taking the input from the cable box. When I want to record something, I set the cable box to turn to that channel at that time, and I then set Mythbuntu to manual record channel 3 at the same time.

Every time I do this on a weekly schedule, whether I do it through MythWeb or the front end interface, it sets up to record for two weeks. After those two weeks, the recording schedule just disappears (though the shows it recorded are still there and are fine). However, if I go in after the first week and sort of poke the schedule by opening it up (again in MythWeb or the front end) and saving it without changing anything, it will populate the recording schedule for one more week. I have to do that for each individual schedule, though. For example, after I look at my recording for Monday, that one will be set up to record for two more weeks, buy my Tuesday one will still only have one more week scheduled.

So essentially, when I set a weekly recording schedule and tell it to record every week at that time, it takes "record at this time every week" as "record at this time for two weeks". I haven't been able to figure out how to fix the problem, but my "poking" solution is at least a decent stop-gap. If I just go in once a week and open and save each recording, they at least don't get deleted and need to be re-entered from scratch every two weeks. If anyone has any ideas about what could be causing that and how to fix it, though, that'd be awesome, because it would definitely be a lot more convenient to not have to check up on those recordings every week to keep them working. Thanks!

---

### Post by Medieval Cow on 2008-04-25
*Bump*

Anyone have any idea on this? I was hoping that upgrading to .21 would fix this, but the same problem is still there.

---

### Post by Medieval Cow on 2008-05-01
Ok, fair enough. New strategy. So the way I'm fixing it now is that once a week I go into MythWeb, open up Recording Schedules, and then click on each recording to open it up, then save it. I don't change anything, but doing that adds one more week of recordings in. (And no, if I do it twice, it does not add another week in. It maxes out at having two weeks of recordings in there.)

So, ok, does anyone know what's being run when I do that? Or how I could find out? Is that triggering an SQL statement that updates the database? I'd assume it is. I'm figuring if I can get to the actual command that's being run, I could set up a script in cron.weekly to run and do the same thing automagically. That would be just as good as fixing the actual problem, really. So, any ideas on that?

---

### Post by Medieval Cow on 2008-06-13
All right, quad posting (!) because I finally managed to put together a workaround for this problem. Just in case anyone else out there happens to be struggling with this. Here's what I did:

I set up a recording far off in the future (December 31st of this year, to be specific). Just a quick little 1 minute, non-repeating recording, so there was something there. Then I set up a cron job to run once a week to restart /etc/init.d/mythtv-backend. For whatever reason, when the backend starts, if there's a recording at least a few weeks out, it will update all of the recordings so that they're scheduled for the next two weeks. 

So for example, it ran this morning on my box. Before it ran, my "Upcoming recordings page" said:

Mon 6/16 Daily Show
Tues 6/17 Daily Show
Wed 6/18 Daily Show
Thu 6/19 Daily Show

After it ran, it said:

Mon 6/16 Daily Show
Tues 6/17 Daily Show
Wed 6/18 Daily Show
Thu 6/19 Daily Show
Mon 6/23 Daily Show
Tues 6/24 Daily Show
Wed 6/25 Daily Show
Thu 6/26 Daily Show

Hurrah! It's kind of a complicated, crazy workaround, but who cares! It works! Now if I could just fix the stupid [Hauppage Remote double press problem]("http://ubuntuforums.org/showthread.php?t=623175") my setup would be perfect.

---

