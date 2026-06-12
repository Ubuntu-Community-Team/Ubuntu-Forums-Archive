---
title: "mythshutdown while frontend still running"
date: 2011-07-28
forum: Mythbuntu
---

### Post by daveshep on 2011-07-28
Gday, I'm hoping someone can help me here - I've got an annoying problem I just can't fix... 

I've been having some phone line/adsl issues lately which have required switching off/restarting the modem/router. The issue is that about a minute later my myth machine shuts down - no matter what i'm doing (watching tv, video, listening to music etc). i've noticed in the logs that the frontend loses its connection to the backend, and the backend starts up and reports it "appears to have been woken by a USER", but then says it's idle and will shut down in 60 seconds and so on, it does the "mythshutdown --check" which reports back "OK", even though the frontend is still running (and i'm watching cadel win the tdf)! and then writes the wakeup time for the next recording (I use mythwelcome etc) and down it goes. 

So it appears to not like the network going down, but the bit that is puzzling me about that is it's a combined frontend/backend (ie master server ip address 127.0.0.1), so i didn't think it mattered what was going on with the network... 

any ideas?

shep

---

### Post by BigPacks on 2011-07-29
I thought you were a Myth guru Dr?

---

### Post by daveshep on 2011-07-29
how did you find me here? 

since you did, can you check your backend log and see if you got any

New DB connection, total: 3

or

Empty LocalHostName.
Using localhost value of shep-htpc 

?

just wondering if these are a clue to whats going on. i've found that that unplugging the ethernet cable OR plugging it IN if i booted the machine with no cable plugged in, causes it to shutdown. 

what i don't get is this

Seem to be woken up by USER
I'm idle now... shutdown will occur in 60 seconds.

if it's woken by USER then it should start the frontend and therefore NOT shutdown. but maybe the issue is cause the frontend is already running? don't know... whatever, this happens

CheckShutdownServer returned - OK to shutdown
Running the command to set the next scheduled wakeup time :-
						mythshutdown --setwakeup 2011-07-29T18:39:00
Running the command to shutdown this computer :-
						mythshutdown --shutdown

really annoying...

---

