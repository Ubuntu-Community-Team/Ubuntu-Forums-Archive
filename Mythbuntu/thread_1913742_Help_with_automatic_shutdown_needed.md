---
title: "Help with automatic shutdown needed"
date: 2012-01-23
forum: Mythbuntu
---

### Post by Errorsmith on 2012-01-23
Hi

I'm running mythbuntu 11.10 as a combined frontend/backend. I configured the machine to autmatically shutdown if it is not needed and wake up when a recording is due. This works like a charm. 
However, I don't want the machine to do any commflag / transcoding jobs at night. Instead I want it to only record at night, but commflag / transcode later. 
I set it up to commflag & transcode from 8 am to 8 pm. This works fine. Unfortunately mythwelcome doesn't shut down the machine, but instead sits there with status "mythtv has pending jobs". I know that, but do not want the machine wait all night, powered on. I want it to wait until next day (after 8:00am) before it does its jobs. 

Is there any way to achieve this? 

with kind regards,
errorsmith

---

### Post by alien878 on 2012-01-26
As far as I know, there is no direct way to do it.

However, you could write a script that replaced the "Pre shutdown check-command" in the backend setup.  This script would call mythshutdown --status, mask out the pending jobs bit and return 1 or 0 as appropriate.

Mythwelcome will probably still indicate there are pending jobs, but the backend should shutdown anyway.

See [http://www.mythtv.org/wiki/Mythwelcome](http://www.mythtv.org/wiki/Mythwelcome) for details on these options.

---

