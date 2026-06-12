---
title: "re-recording already recorded shows"
date: 2008-08-14
forum: Mythbuntu
---

### Post by dannyboy79 on 2008-08-14
Hello all,
I am curious how mythtv works when it comes to recordings that I have recorded in the past but deleted. This show is Terminator: The Sara Conner Chronicles. The first series is over but I left the recording schedule the way it was so that when the next series starts I won't miss it. But, apparently some channel is playing re-runs. It states it's a re-run in the listings of mythweb. Well my mythtv 20.02 has been recording them despite I have the setting for not recording duplicates based in description and title. The title and descriptions are all filled out per my schedulesdirect account. So my question is: if I record a show, then delete it, will it record that show again since I deleted it? Seems pointless if this is the case. Let me know if any other users have had this happen to them. Thanks

---

### Post by newlinux on 2008-08-14
Try changing it to recording only new episodes. I do the same thing and that works for me.

---

### Post by mrand on 2008-08-14
I've forgotten 0.20, but on 0.21, I believe there is both <delete> and <delete + allow re-record>.   The implication is that <delete> won't re-record it when it comes back on later.

[INDENT]   Marc[/INDENT]

---

### Post by tgm4883 on 2008-08-14
Tell it to only record new episodes.  The default for MythTV is that if you record something and delete it, it will not re-record it again until it has been 364 days from the last time it was recorded.  They do this to allow for yearly holiday time recordings (ie, christmas programming, etc)

---

### Post by dannyboy79 on 2008-08-15
in mythweb the only place I see anything about recording only new episodes is this "Record new and expire old", is that what everyone is talking about?

---

### Post by newlinux on 2008-08-15
No it should be somewhere in the duplicate settings in .20.2 in mythweb. It should be in a dropdown as "Only New Episodes." In mythfrontend and in mythweb .21 it is more intuitive.

---

### Post by dannyboy79 on 2008-08-15
> **tgm4883 said:**
> Tell it to only record new episodes.  The default for MythTV is that if you record something and delete it, it will not re-record it again until it has been 364 days from the last time it was recorded.  They do this to allow for yearly holiday time recordings (ie, christmas programming, etc)

well then that's obviously not working. I'll try the record new and expire old option within mythweb just to be on the safe side.

---

### Post by newlinux on 2008-08-15
> **dannyboy79 said:**
> well then that's obviously not working. I'll try the record new and expire old option within mythweb just to be on the safe side.

The record new and expire old is for when you reach your recorded episode limit. if this setting isn't set, when it reaches its max episodes recorded it won't record a new episode. If it is set, it will delete an old episode and record the new episode. What you want is confusingly in the check for duplicates in dropdown box (don't remember it exactly in .20.2).

---

### Post by newlinux on 2008-08-15
When you have the duplicate check method set to only new recordings, when a listing has an original air date more than 2 weeks old or it is marked as a repeat it won't record it.

---

### Post by dannyboy79 on 2008-08-15
in the Check for duplicates pull down, there is an option for only new episodes but that doesn't make sense. I would want it to check all my recordings for duplicates not only new episodes or am I misunderstanding what this setting does.

---

### Post by newlinux on 2008-08-15
> **dannyboy79 said:**
> in the Check for duplicates pull down, there is an option for only new episodes but that doesn't make sense. I would want it to check all my recordings for duplicates not only new episodes or am I misunderstanding what this setting does.

That's what I meant by it isn't very intuitive. It does what I wrote in the previous post, it doesn't only check for duplicates in new episodes. In mythweb .21 they separated that out as a filter and made it more intuitive.

---

### Post by kameleon25 on 2008-08-15
I have a similar situation. How would one go about setting it to where it will record all showings unless it has recorded it at some point in the past? Like I take all of my recording and automatically convert them to an avi file. The auto expire option does it's job but I have been getting duplicates in the avi files that are the same exact show but just a different date. I have changed my nuvexportrc file to not put the date on them now so that will help somewhat with duplicate avi files. But to have them not record in the first place would be awesome. Any ideas?

---

### Post by newlinux on 2008-08-15
What recording settings hae you been using? If you have the right settings it could just be bad guide data. You'll want to look in the duplicates section. Are you on .21? It has a few more options. Checking for duplicates in "All Recordings" should do what you want. It won't record things that are currently recorded or have been previously recorded. YOu probably want to check subtitles and descriptions for duplicate matching. this works for me.

---

