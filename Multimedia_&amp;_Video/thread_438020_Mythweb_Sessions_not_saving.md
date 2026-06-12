---
title: "Mythweb Sessions not saving"
date: 2007-05-09
forum: Multimedia &amp; Video
---

### Post by SyvanX on 2007-05-09
I upgraded my MythTV box to Feisty, and I everything is working fine, except for mythweb.  

The mythweb sessions are not saving, and there is no data being entered into the mysql table mythweb-sessions.  I can't get mythweb to remember my sorting and filtering options.  Mythweb is distributing a cookie with a user-id, but that's not being used.

Is anyone else having this problem?

---

### Post by teet on 2007-05-10
mythweb + feisty works fine here.

I can't remember doing anything special to get it to work... just a 'sudo apt-get install mythweb' and I was up and running.

-teet

---

### Post by SyvanX on 2007-05-10
Mine is displaying everything it needs to, it just used to save my sorting options in recordings and filtering options in upcoming recordings.  

Does it save your sorting preference if you navigate to another page, and then come back?  I just want to know if I screwed something up in the fresh install of feisty.

---

### Post by teet on 2007-05-10
I'm not sure if I understand exactly.

If I click on "Upcoming Recordings" I see  4 checkboxes (scheduled, duplicates, deactivated, conflicts) towards the top of the screen so I can choose what I want to be displayed on the "upcoming recordings" page.  If I deselect some of them and then navigate away form that page and then back to it, they're all selected again.  I assume this is what you're talking about.  In which case, I can confirm your "problem".

-teet

---

### Post by deoncarr on 2007-07-31
I have the same problem with feisty and not saving mythweb session info. 

The bug is mentioned here [URL="https://bugs.launchpad.net/ubuntu/+source/mythplugins/+bug/97599"]https://bugs.launchpad.net/ubuntu/+source/mythplugins/+bug/97599
[/URL]

Went into the database with myphpadmin and couldnt view the mythweb session  table either. 

Have you found any more info?

---

### Post by SyvanX on 2007-07-31
I have not tried to look into this much more.  While I had it, I didn't realize it was saving sessions, but when it was gone, I couldn't live without it.

If you plan on troubleshooting yourself, here are the steps I took:
[LIST]
[*]I checked to make sure the mysql sessions table had the correct permissions
[*]I checked the mythweb location to make sure it had the correct permissions
[*]I switched between digest and basic authentication
[*]I set the authentication domain to MythWeb and MythTV
[/LIST]

I looked briefly at the php code in the mythweb directory, but I don't know much about php.  I'm guessing the problem lies there, I've tried just about everything else I could think of.  

If you solve the problem, please post it here.

---

### Post by Scorpuk on 2007-08-01
Not sure if this is any help, but it is related to the session.php file and I just checked and I can uncheck / check options and my selection is remembered the next time.


[http://ubuntuforums.org/showthread.php?t=474638]("http://ubuntuforums.org/showthread.php?t=474638")

---

### Post by deoncarr on 2007-08-03
Thanks Scorpuk. 

Exactly what I needed. mythweb sessions is saving now.

---

