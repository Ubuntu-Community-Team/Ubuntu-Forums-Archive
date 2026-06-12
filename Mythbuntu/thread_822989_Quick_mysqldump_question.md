---
title: "Quick mysqldump question"
date: 2008-06-08
forum: Mythbuntu
---

### Post by Kawayanan on 2008-06-08
I've run into a problem trying to make a backup of my mythtv database.  I am trying to follow the [description on the mythtv wiki]("http://mythtv.org/wiki/index.php/User_Manual:Periodic_Maintenance").  I just get a error.  "Access denied for user: 'mythtv@localhost'"  Ive tried it with sudo, no better.  I've also tried using  -password='password', but that doesn't seem to help either.  I found [this page]("https://help.ubuntu.com/community/MythTV/Install/Troubleshooting"), but it didn't help either.  I am a member of the mythtv group.  I can run mythfilldatabase without a problem, so I seem to have access to the database at some level.  Am I missing something simple?

Thanks

---

### Post by danbodoh on 2008-06-08
mysqldump -u mythtv -p mythconverg

With just '-p', mysqldump will prompt for a password.  You could also put the password on the command line with -pPASSWORD (no space or quotes, just substitute your password for PASSWROD).

Note that the mysql maintains its own concept of users.  The 'mythtv' mysql user doesn't have the same password as the mythtv linux user.

You can see your mythtv mysql password in the mythfrontend setup screens (General).

Dan Bodoh

---

