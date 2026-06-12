---
title: "Recording takes over Live TV??????"
date: 2008-07-09
forum: Mythbuntu
---

### Post by sardiskan on 2008-07-09
For this problem, let it be known that I have two tuners on this system.

Ok, so I'm watching LiveTV and there is something scheduled to be recorded. Just before it starts, the system prompts me to let me know it wants to record something. I have to select to LET it record and either WATCH that program, or I have to go back to the main menu, hit LiveTV again, and be moved to the second tuner. 

Why does the recording not automatically go to the second tuner when it sees the first tuner is being used. I've got all of my recordings set to auto...which should select an appropriate tuner that is not being used. This function works fine for shows that are being recorded. If something is being recorded on a channel, then another show needs to record from another channel during the other show, it automatically uses the second tuner. Why doesn't it do the same thing when I'm watching LiveTV? I could manually set all programs to record from the second tuner...but then I'll get conflicts if it needs to record two shows at once. This is most frustrating.

---

### Post by tgm4883 on 2008-07-09
Either in mythtv-setup or recording profiles you need to give it the power to move recordings so they don't conflict with live tv

---

### Post by jlagrone on 2008-07-09
If you haven't already looked, there are two settings in Utilities/Setup > Setup > TV Settings > General that may be of interest.


Avoid conflicts between live tv and scheduled shows
Allow live TV to move scheduled shows

The first one should fix your problem and the second will should allow you to continue watching something when all your tuners are set to record and it should reschedule one of those recordings (if it can).  It's been quite a while since I've watched live TV and used these, so they may actually work a little differently.

---

### Post by sardiskan on 2008-07-09
Thanks alot. I'll give these options a try.

---

