---
title: "mythtv-status segfaults with no apparent reason"
date: 2008-09-09
forum: Mythbuntu
---

### Post by Verzweifler on 2008-09-09
Out of nowhere (as usual), there arose another issue for which I do not have any explanation: On my MBE I periodically run a script that uses the output of mythtv-status as input to determine whether there are no encoders still watching LiveTV or recording so the MBE can safely restart itself. (Do not ask for details yet, since this will go off-topic)

For no apparent reason, mythtv-status does not work any longer. If called, it just sits there for some seconds and returns a "Segmentation Fault". 

I do not recall any major changes on the system or weird situations apart from the following:
[LIST]
[*]There was a power outage some days ago during my BackEnd's uptime
[*]I moved the files of a storage group from one disk to another disk
[/LIST]
No apt-get upgrades /dist-upgrades or the like, no strange package installations, no weird mythtv behaviour... Just business as usual. 

However, I already tried an "apt-get purge mythtv-status" followed by a reinstall, I installed version 0.9.0 (by hand) instead of 0.7.3 available as .deb also crapping on me, I did a filesystemcheck on all my drives with no error returned... and now I have no idea where to continue searching.

Google pointed me to a discussion with laga earlier this year, so I tried debugging the script using perl -d , but that is not my favorite field of engangement, since I do not know what to do. I determined that the script dies at line 510 with an "unable to parse XML" or something error refering to an empty string in line 507, but I still have no clue what this means.

So, please, HELP...

---

### Post by ian dobson on 2008-09-09
Hi,

I think there is a memory leak in the http status page in MythTV backend.

I'm also running a script to monitor my Backend but I use a SQL query on he inuseprograms table and since then I've not had any more problems.

Regards
Ian Dobson

---

### Post by Verzweifler on 2008-09-09
Hi Ian,

that sounds really interesting, but I wonder why it worked like a charme before... 

I also thought about running an SQL-query but I found another way instead: I am now monitoring traffic on my interfaces and changes in disk consumption to identify "LiveTV/watching a recording" and "recording" taking place, respectively. A quite rough approach but it works for me. 

However, I am still curious what caused mythtv-status to die...

---

### Post by Verzweifler on 2008-09-29
*bump*

it is still segfaulting... and I still have no clue why.

---

