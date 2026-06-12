---
title: "DVD ripping problems - bad transcode command line?"
date: 2009-09-25
forum: Mythbuntu
---

### Post by SpareTimeGizmos on 2009-09-25
... trying to rip DVDs in MythBuntu 9.10 (yes, the testing version) the transcode operation is failing. The mtd.log says -

[INDENT]11:49:37: a client socket has been opened
11:49:59: launching job: job dvd 1 1 7 0 -1 /var/lib/mythdvd/162-Rollings
11:49:59: transcode command will be: 'transcode -i /var/lib/mythdvd/temp/162-Rollings/vob/ -g 720x480 -M 2 -1 -j 0,8,0,8 -B 0,2 -y xvid -w 1618 -o /var/lib/mythdvd/162-Rollings.avi --color 0'
11:49:59: job thread beginning to rip dvd title
11:58:36: job thread finished ripping dvd title
11:58:36: Error: Exiting runTranscode(1) transcode exit code: 1
11:58:38: job failed: job dvd 1 1 7 0 -1 /var/lib/mythdvd/162-Rollings
[/INDENT]If I try manually typing (well, with cut and paste!) this transcode command I get -
[INDENT]transcode: unrecognized option '-1'
'transcode -h | more' shows a list of available command line options.
[/INDENT]and if I, just for fun, remove the "-1" option I get
[INDENT]transcode: unrecognized option '--color'
[/INDENT]and if I remove both "-1" and "--color" then the transcode runs succesfully.
 
It's almost as if this is not the right version of transcode, but according to Synaptic it's the latest.
 
BTW, this only happens if you select a "good" or "excellent" DVD copy - if you select "perfect" then it doesn't run transcode and you don't have this problem.
 
I could submit a bug report against 9.10, but I wanted to be sure it's not something stupid that I'm doing before I embarass myself.
 
Thanks,
Bob

---

