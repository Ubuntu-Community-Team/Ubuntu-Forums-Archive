---
title: "mythwelcome: running or pending jobs"
date: 2010-12-30
forum: Mythbuntu
---

### Post by MartinusEx on 2010-12-30
Hi,
i use mythbuntu 8.04 since 2 years
since August 2010 I have set up mythwelcome and all works well.

Recently I started some transcoding jobs.
The next day, starting the pc to programm some stuff mythwelcome came up with:
"running or pending jobs"

I thougt it might have shutdown prematurely the day before,
I can not find any running mythtranscode jobs (ps -A | grep myth)

Still mythwelcome shows "running or pending jobs" but shuts down after a while anyway (didn't measure the time but it might have been the usual 240 sec).

Í found a thread concerning mythshutdown, that it returns exitcode 32 if jobs are running or pending, so it might be mythshutdown. (which i confirmed)

mythshutdown does look into the database mythconverg
so I think pending jobs are listed there.
I assume that with the last jobs at least one was not deleted from the database and I need to delete the job entry manually.

My question:
In which table are the pending jobs listed?


Thanks a lot in advance

---

