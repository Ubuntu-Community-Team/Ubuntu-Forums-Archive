---
title: "Remote frontend not responding to commands"
date: 2011-12-06
forum: Mythbuntu
---

### Post by alldunn on 2011-12-06
I currently have a backend/frontend machine running Mythbuntu 11.04 in my living room and am in the process of setting up a remote frontend (Mythbuntu 11.10) for my bedroom.  Both are running MythTV 0.24.1 with all the latest fixes.  For some reason when I watch live TV on the remote frontend, no commands work.  The picture is perfect, but I end up having to kill the frontend process and restart it to get anything to function.  This is reproducible every time and unfortunately I can't switch channels or basically do anything once I start watching live TV.  Have any of you guys ran into this issue before?  I have searched around a bit but so far I haven't found any solutions.  I am running both machines on a GigE LAN FWIW.  Thanks for any help.

---

### Post by alldunn on 2011-12-06
OK so it appears that this only happens while the main backend/frontend machine is recording live TV.  Otherwise the remote frontend is responsive as you would expect it to be.  What gives?

---

### Post by nickrout on 2011-12-07
How are you conveying these "commands" to the frontend? keyboard? remote? network socket? carrier pigeon?

---

### Post by alldunn on 2011-12-07
Well for now I am just using a keyboard, but ultimately I will be using lirc for remote control.
Also, during further testing, I noticed that the unresponsiveness is occurring only when both of my tuners are recording on my backend.  If only 1 tuner is recording the remote frontend connects to the other tuner and works just fine.

---

### Post by nickrout on 2011-12-07
Well if both tuners are busy (and don't support multirec) then you can't do live TV on any frontend. However I am unclear whether you are able to watch recordings. You are very vague about the symptoms.

---

### Post by alldunn on 2011-12-07
I am able to watch recorded programs without a problem.  LiveTV that is in the process of being recorded on the backend is what I am having a problem with on the remote frontend.  Basically when I select watch TV on the remote frontend, it starts to play the live video/audio without a problem, but I can't pause or bring up a guide; I basically cannot do anything without forcefully killing the frontend process while the backend is recording on both tuners.  Maybe this is the intended behavior?  But I would expect to be able to at least escape/exit out of the watch TV section on the remote frontend which I cannot do?  I hope this makes thinks a little clearer, but if not let me know.

---

### Post by nickrout on 2011-12-07
> **alldunn said:**
> I am able to watch recorded programs without a problem.  LiveTV that is in the process of being recorded on the backend is what I am having a problem with on the remote frontend.  Basically when I select watch TV on the remote frontend, it starts to play the live video/audio without a problem, but I can't pause or bring up a guide; I basically cannot do anything without forcefully killing the frontend process while the backend is recording on both tuners.  Maybe this is the intended behavior?  But I would expect to be able to at least escape/exit out of the watch TV section on the remote frontend which I cannot do?  I hope this makes thinks a little clearer, but if not let me know.

You don't use "watch TV" in such circumstances, you watch it from "Watch Recorded Programmes"

---

### Post by alldunn on 2011-12-07
OK so if both tuners are in use on the backend, I shouldn't use the watch TV option, I should just watch recorded show?  Otherwise it is safe to use the Watch TV option.  Am I understanding correctly?

---

### Post by nickrout on 2011-12-07
Yes that would be right. I remind you that Watch TV is the poor cousin, it gets less development than recording, as most people don't really use it once they get used to recording what they want to watch.

---

### Post by alldunn on 2011-12-07
Cool thanks for the advice!

---

