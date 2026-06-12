---
title: "recording two episodes every day"
date: 2009-05-12
forum: Mythbuntu
---

### Post by reformy on 2009-05-12
Hi
There is a show with two episodes back to back every day at 20:00, then the same two again at 23:00. I want to record it.
I used "record in this timeslot every day" on both episodes at 20:00. It works fine, but if I want to record something else at the same time, it doesn't use the 23:00 shows instead.
If I use "record one episode of this showing every day", it records only one episode from the four episodes every day.

what can I do to record the two episodes every day and make the mythtv to use the re occurrences if needed?

Thanks,
Yair

---

### Post by klc5555 on 2009-05-12
> **reformy said:**
> Hi
There is a show with two episodes back to back every day at 20:00, then the same two again at 23:00. I want to record it.
I used "record in this timeslot every day" on both episodes at 20:00. It works fine, but if I want to record something else at the same time, it doesn't use the 23:00 shows instead.
If I use "record one episode of this showing every day", it records only one episode from the four episodes every day.

what can I do to record the two episodes every day and make the mythtv to use the re occurrences if needed?

Thanks,
Yair

If you're using ScheduleDirect (or similar) listings, and if the show's upcoming episodes are being properly and completely listed in your database (correct title, subtitle, synopsis) rather than some kind of generic listing, then "Record at any time on this channel" ought to record the first two episodes, but ignore their later repeats unless they failed to record earlier.

Test this by setting it up, then look in Manage Recordings > Upcoming Recordings. If the two earlier daily showings show up highlighted to record, but the two later showings for the day are grayed-out with an "E" (for earlier showing recorded), then you're in business. If a conflict happens later, Myth's scheduler should adjust automatically.

---

### Post by reformy on 2009-05-12
Thanks for your answer.
That didn't work. It marked all the episodes (4 of them) for recording.
I'm sure that the title and the subtitle are correct. The fact that "record at any time" caused mythtv to record all episodes indicates that they are all from the same showing, i guess.
How can I be sure of that? do the "synopsis" needs to be the same too? I think it is.

---

### Post by ReddogOne on 2009-05-12
> **reformy said:**
> That didn't work. It marked all the episodes (4 of them) for recording.

When you say it did not work did it actually record all 4 of are you jumping the gun a little!?!?!?!

Unless you have turned the detect duplicate recording off then it probably highlighted all the showings but will actually only record the 2! 

In the up and coming recordings as you move up and down it should tell you which are recoded earlier, or new episodes. At work at the moment so can't be specific but it should be obvious.

---

### Post by klc5555 on 2009-05-12
> **reformy said:**
> Thanks for your answer.
That didn't work. It marked all the episodes (4 of them) for recording.
I'm sure that the title and the subtitle are correct. The fact that "record at any time" caused mythtv to record all episodes indicates that they are all from the same showing, i guess.
How can I be sure of that? do the "synopsis" needs to be the same too? I think it is.

Sorry. Looks like the guide information you're getting for this particular program is not sufficient for myth to recognize and differentiate the individual episodes. News programs, for example, and various local shows tend to suffer from this a lot. 

Since you need 2 episodes per day, and not one, and since time-scheduling or "daily" scheduling are not possible, I don't see any solution simpler than setting up to record all four per day and deleting what you don't use. If this is a show with a short shelf-life (like a news show) you could also go into "Storage Options" and set some episode retention limit (say, 20) to keep just a week's worth of episodes and automatically dump the oldest ones.

---

### Post by reformy on 2009-05-12
> **ReddogOne said:**
> When you say it did not work did it actually record all 4 of are you jumping the gun a little!?!?!?!

Unless you have turned the detect duplicate recording off then it probably highlighted all the showings but will actually only record the 2! 

In the up and coming recordings as you move up and down it should tell you which are recoded earlier, or new episodes. At work at the moment so can't be specific but it should be obvious.

I know the "upcoming recordings" screen, and the "later/earlier recording" option. It works in other shows.
Using "record at any time on this channel" marked all, no E or L.

---

### Post by reformy on 2009-05-12
> **klc5555 said:**
> Sorry. Looks like the guide information you're getting for this particular program is not sufficient for myth to recognize and differentiate the individual episodes. News programs, for example, and various local shows tend to suffer from this a lot. 


BTW, The show in hand is "backer"...
I've just checked that TV XML for these shows. I don't want to post it here since it is in Hebrew, but:
The title and sub-title are the same, but the synopsis is slightly different: the second show has an addition saying "second time" in Hebrew. Could that be the problem? How can I fix this? Manually or automatically removing this addition after getting the XML?

---

### Post by ReddogOne on 2009-05-12
> **reformy said:**
> I know the "upcoming recordings" screen, and the "later/earlier recording" option. It works in other shows.
Using "record at any time on this channel" marked all, no E or L.

Then I'm afraid its what klc5555 said. 

Working on PVR software a while back lots of people would say to me "Sky+ missed this or record all of that" but when it comes down to it if the broadcaster is lazy then the STB (or MythTV in this case) hasn't a chance :(

EDIT: With respect to your previous post... that'll confuse it. Once again... pain the bottom broadcasters!

---

### Post by tgm4883 on 2009-05-12
I'm not at home right now, but can't you set the duplicate detection to look at the title (sub-title) only and skip the synopsis?

---

### Post by Boppy3125 on 2009-05-12
You might be able to handle the two at a time by telling it to record 30 minutes after.  But you still have the problem of when to record the first set versus that second.

---

### Post by reformy on 2009-05-12
> **tgm4883 said:**
> I'm not at home right now, but can't you set the duplicate detection to look at the title (sub-title) only and skip the synopsis?

I'm not aware of such configuration. If you can check later I'll appreciate it.

---

### Post by Chuckels550 on 2009-05-13
Way back I had the same issue.  I record 5 min before and 5 min after episodes to deal with drift on my end and the station's.  My fix was to add another TV tuner.

---

### Post by tgm4883 on 2009-05-13
Totally spaced looking at it last night.  I just sent myself an email to remind me when I get home tonight.  Sorry for the inconvenience.

---

### Post by newlinux on 2009-05-13
> **reformy said:**
> I'm not aware of such configuration. If you can check later I'll appreciate it.

I'm not at home either, but via mythweb it is an option when setting up/modifying a recordings, so I would guess it's in the recording schedule in mythfrontend.

It is duplicate check method. You can choose:
Subtitle and Description
None
Subtitle
Description
Subtitle then description.

---

### Post by tgm4883 on 2009-05-13
> **newlinux said:**
> I'm not at home either, but via mythweb it is an option when setting up/modifying a recordings, so I would guess it's in the recording schedule in mythfrontend.

It is duplicate check method. You can choose:
Subtitle and Description
None
Subtitle
Description
Subtitle then description.

Yep, I remember seeing that in mythweb.  That is what I would do to set it up.

Alternatively, you might be able to setup an advanced rule for it, but I think the dupe check method above (just check subtitle) would work for it.  It's a per recording schedule setting, so it won't affect your other recording schedules.

---

### Post by reformy on 2009-05-14
> **newlinux said:**
> I'm not at home either, but via mythweb it is an option when setting up/modifying a recordings, so I would guess it's in the recording schedule in mythfrontend.

It is duplicate check method. You can choose:
Subtitle and Description
None
Subtitle
Description
Subtitle then description.

Thanks!! That did the trick.
Thanks to tgm4883 too.

---

