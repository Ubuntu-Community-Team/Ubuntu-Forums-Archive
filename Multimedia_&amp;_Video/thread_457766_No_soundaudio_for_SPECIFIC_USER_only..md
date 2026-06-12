---
title: "No sound/audio for SPECIFIC USER only."
date: 2007-05-29
forum: Multimedia &amp; Video
---

### Post by kizale on 2007-05-29
Hi, I've spent the last couple days trying to find somebody else who already had and solved this problem, but I've lost patience, so here it is:

I installed Feisty and found that the sound was not working when I logged in as the default user (user1).  It recognizes the sound card and alsamixer also acts as if everything is fine.  It simply wasn't coming out the speakers.

I then created a second account (user2) and I logged in as that user.  The sound worked just fine and I was listening to my old Backstreet Boys mp3s without any problems.

Any ideas why user1 can't hear sound and user2 can?

Thanks in advance!

---

### Post by mbradlcu on 2007-05-29
make sure the new user is part of the "audio" group. You can use the gui user and groups or the following:
```
sudo that_new_user audio
```

---

### Post by kizale on 2007-05-29
Thanks for the reply.  Both user1 and user2 are already members of the group audio.

---

### Post by kizale on 2007-06-09
SOLUTION: I gave up and reinstalled Kubuntu all over again.  Problem solved.

---

