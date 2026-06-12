---
title: "[SOLVED] Have MythTV enter &amp;quot;watch TV&amp;quot; automatically"
date: 2008-01-14
forum: Mythbuntu
---

### Post by zagor on 2008-01-14
Hi all,

I have my external sky tuner connected to the composite input of my PVR-150.
I can record programs only if when the recording starts I am actually watching TV (regardless of the channel I'm looking at).
Therefore I cannot use any ACPI wakeup or similar, because when Myth frontend starts it stays in the main menu.
I would like it to go to the "watch tv" page automatically.

Any idea on how to do it?
Maybe as a post-startup script in the mythbackend-setup?

Thanks
F.

---

### Post by tgm4883 on 2008-01-19
I'm a little confused by your question.  What it seems that you are saying is that when a scheduled recording is suppose to start, that mythtv will continue to stay in the main menu.  This is by design and should record the show no problem.  Are you saying that the show is failing to record and not showing up in recorded programs?

---

### Post by zagor on 2008-01-21
Exactly.
It fails with a dumb message (found in the Upcoming Recordings page): "Recorder failed".
This does not happen if I am actually watching the liveTV when the scheduled recording is due.
In this case the Mythbox will ask for recording, change the channel accordingly and start recording correctly.
Note that if the program I want to record is from the antenna source, it will be recorded even if the frontend is showing the mainmenu --> so it will behave as you describe.
The problem is only when I try to record from the composite source of my PVR-150.

Thanks for your help

---

### Post by tgm4883 on 2008-01-21
That is very strange.  I have my pvr-150 setup to record from the composite source and it works as designed.  I wonder if there is any additional setup needed if you use > 1 source on a PVR-150?

---

### Post by zagor on 2008-01-22
I have reinstalled the mythbox recently and added only the composite source, so I just have one source and it still behaves as described: no recording if not watching live tv....

Can you post your source config for your composite source?

Thanks for your help!

---

### Post by zagor on 2008-02-12
Thanks to Cal in the mythtv-users mail list I now have the solution to my problem:
> 
Just plug _/bin/true_ into the change channel script field
in mythtv-setup->card setup.

I've added /bin/true in the change channel field and now I can record from the decoder without the need of entering the LiveTV.

Thanks Cal!

---

### Post by mattbatt on 2008-11-11
Thank you I just spent 45 minutes trying to find this answer.  All I kept getting "For my settup I used an IR blaster" on every crappy blog that has YET ANOTHER GUIDE to install mythtv. It was sooo frustrating. 
Keywords for Google
No IR blaster
External Channel change command
Recording Failed
s-video recording failed
mythtv-setup input connections
I hope this bumps up the results.

---

