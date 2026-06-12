---
title: "Is there a way to tell what each frontend is watching?"
date: 2009-05-19
forum: Mythbuntu
---

### Post by Antharian on 2009-05-19
Title says it all.

What tables do I need to join in the query to find out which frontend is watching TV and what the show is.

I would like to write a sort of "Parental" plugin to monitor and even change the channels on frontends from another room.

Thanks,

-A

---

### Post by ian dobson on 2009-05-19
Hi,

Have a look at the inuseprograms table, that'll give you a list of what is using what resources. To find out the name of the program actually being viewed you'll have to join the inuseprograms table fields chanid & starttime with the program table.

This is only a view function, you cannot force the frontend to use a different channel by writing to the db. 

Maybe you could use the telnet interface on port 6546? to remotely control the frontend.

Regards
Ian Dobson

---

### Post by Antharian on 2009-05-19
> **ian dobson said:**
> 

Maybe you could use the telnet interface on port 6546? to remotely control the frontend.


The Telnet interface was exactly the plan.  Thanks for the table information ...  Once I can tell what systems are active I can find their recordings.

Regards,

-A

---

### Post by ian dobson on 2009-05-19
Hi,

It's quite simple to see whats active. You have the hostname and status (recusage) fields that give you all the info you need.

Note: The recusage field can contain values for recording, playback, transcode, commflagging etc, you'll have to play about abit yourself to work out what value what means.

Regards
Ian Dobson

---

