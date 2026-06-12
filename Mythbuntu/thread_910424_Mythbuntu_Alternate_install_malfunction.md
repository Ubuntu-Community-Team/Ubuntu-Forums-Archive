---
title: "Mythbuntu Alternate install malfunction?"
date: 2008-09-04
forum: Mythbuntu
---

### Post by Disparu on 2008-09-04
I used the alternate install CD so I could set up a software raid 1 to install on to.

That part was successful.

After the install... nothing is configured like it is in the mythbuntu desktop install. 

The mythconverg database is not set up. 
When I try to add my user account to the mythtv group by unlocking the control panel users and groups i get an error "could not authenticate"

although I have found solutions to both of these problems I am worried that the mythbuntu alternate CD really jipped me on the things I need and I am worried that if I keep the install I might keep discovering missing or broken features.

Can anyone please advise if there is a problem with the alternate install distribution?

---

### Post by joutsen on 2008-09-05
I can confirm this. Database not setup correctly and cannot unlock users and groups for editing with Mythbuntu Alternate install 8.04.1.

What was your solution to the groups and users problem? Command line?

---

### Post by Disparu on 2008-09-06
this will fix the database problem.

sudo dpkg-reconfigure mythtv-database

this will fix the user account control problem or whatever the linux community calls the equivalent of vista UAC

sudo apt-get install policykit-gnome 

these are from memory and I am not sure if it is correct.

---

### Post by laga on 2008-09-07
Can you please file a bug report at [http://bugs.launchpad.net/mythbuntu](http://bugs.launchpad.net/mythbuntu) so we can get this fixed?

Thanks!

---

### Post by Disparu on 2008-09-07
Bug reported and temporary solution posted.

---

### Post by Disparu on 2008-09-17
i think there may be more issues, can anyone tell me what user groups the "mythtv" user should be apart of. I think the alternate install might have botched that as well since none of my cron jobs assigned to the mythtv user ever run.

---

### Post by anonymousdog on 2008-09-17
$ grep mythtv /etc/group
dialout:x:20:mythtv,ubuntu,<me>
cdrom:x:24:mythtv,ubuntu,<me>
audio:x:29:mythtv,ubuntu,<me>
video:x:44:mythtv,ubuntu,<me>,www-data
mythtv:x:110:ubuntu,<me>

---

### Post by Disparu on 2008-09-17
hmm identical, how can i check the cron.hourly logs?

---

### Post by anonymousdog on 2008-09-17
You'll need redirects in the cron job commands to get log output from cron jobs.

---

### Post by Disparu on 2008-09-18
<--- linux retarded

when i try to run the job manually it prompts me for the mythtv user password since it is set to run as mythtv.

Is the mythtv user suppose to have a password?

su mythtv mythnettv ....

---

