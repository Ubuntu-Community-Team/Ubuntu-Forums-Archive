---
title: "How to FORCE myth to record past the end of show?"
date: 2012-03-14
forum: Mythbuntu
---

### Post by ubnewbie2 on 2012-03-14
I have been using a default setting in the setup to record past the end of the show because our TV channels always overrun the timeslots.  However, this setting isn't always obeyed if the scheduler thinks there isn't enough gap between scheduled shows - and I am sure it gets it wrong often.   

Therefore I want to force it to ALWAYS record past the end of the scheduled time for a show, as per the "End Late" setting you see when you schedule a new show.  The problem is I cannot find a way to set this to default to a predetermined time, it always is zero unless I change it each time.  Is there a way to do this?

---

### Post by nickrout on 2012-03-14
> **ubnewbie2 said:**
> I have been using a default setting in the setup to record past the end of the show because our TV channels always overrun the timeslots.  However, this setting isn't always obeyed if the scheduler thinks there isn't enough gap between scheduled shows - and I am sure it gets it wrong often.   

Therefore I want to force it to ALWAYS record past the end of the scheduled time for a show, as per the "End Late" setting you see when you schedule a new show.  The problem is I cannot find a way to set this to default to a predetermined time, it always is zero unless I change it each time.  Is there a way to do this?

short answer: NO

longer answer - the "default" settings are "soft" and will be ignored if honouring means you have to sacrifice recording the next show.

The per recording rule settings are always honoured, but may result in the next show not being recorded because of the overlap.

Are you using multirec? This can make sure you get both WITH "hard" rules, because one tuner can record many shows.

There was a thread recently on the mailing list which included a script to set hard defaults on every recording. Search and you will find!

---

### Post by ubnewbie2 on 2012-03-14
> **nickrout said:**
> short answer: NO

longer answer - the "default" settings are "soft" and will be ignored if honouring means you have to sacrifice recording the next show.

The per recording rule settings are always honoured, but may result in the next show not being recorded because of the overlap.

Are you using multirec? This can make sure you get both WITH "hard" rules, because one tuner can record many shows.

There was a thread recently on the mailing list which included a script to set hard defaults on every recording. Search and you will find!


Yes I use multirec, but there seems to be bugs in the scheduler that lops off the optional record past end of show even if there is still spare tuner capacity.  Hence I need to force it.

Your suggestion for a search didn't turn up the script, but it found something better.  The setting does indeed exist in Utilities/Setup|Setup|TV Settings|Recording Priorities.   This "DefaultEndOffset" prepopulates the End Late field every time you schedule a show.

---

### Post by RideMan on 2012-03-16
Is the error consistent across channels?

If it is, why not tweak the system clock by a couple of minutes to better match the TV schedule?

Just a thought...

---

### Post by ubnewbie2 on 2012-03-16
> **RideMan said:**
> Is the error consistent across channels?

If it is, why not tweak the system clock by a couple of minutes to better match the TV schedule?

Just a thought...

Then I'd miss the start of the shows that start on time. Actually, occasionally I miss the start because they start the show early- but that's rare and doesn't annoy me nearly as much as missing the ending.   No the only way is to start on time and record about 15 to 30 minutes after the scheduled ending

---

### Post by nickrout on 2012-03-16
15-30 minutes is huge.

Changing the time on the backend is a very silly idea for many reasons, forget that idea.

---

### Post by ubnewbie2 on 2012-03-16
> **nickrout said:**
> 15-30 minutes is huge.




Such is life with our free to air stations.  It is VERY common for shows to start 10 minutes late, and they never seem to attempt to catch up (gotta squeeze in all those sponsers commercials), so 15 minutes is a reasonable minimum to catch the end of 90% of the shows. When they are running reality TV, or talent quest live shows, then 20+ minutes late is not so rare.

---

### Post by RideMan on 2012-03-16
> **nickrout said:**
> 15-30 minutes is huge.

Changing the time on the backend is a very silly idea for many reasons, forget that idea.

I didn't realize we were talking about more than a minute or two.  Normally I would agree that changing the time doesn't make much sense, except that I have noticed that for some unknown reason, my system seems to be running about a minute fast, meaning that recordings are starting and ending early.  I haven't investigated thoroughly to see what is going on...that is, I am using a network time service, but that service disagrees with the WWV time signal that my wristwatch syncs to every night.

Just to point out that I am not entirely crazy.  8-)

---

