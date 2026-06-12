---
title: "Myth 0.18.1 packages for Feisty?"
date: 2007-04-27
forum: Multimedia &amp; Video
---

### Post by biostatman on 2007-04-27
I am runing dapper on my laptop and run mythfrontend (0.18.1) to connect to a Myth 0.18.1 backend.  I am reluctant to upgrade my mythtv backend since I have everything working.  After trying out the LiveCD for Feisty I am itching to upgrade my laptop, but being able to connect to my Myth backend is a must.  Can anyone point me to myth 0.18.1 packages that will work on Feisty?  Has anyone had any experiences with them?  Thanks!

---

### Post by superm1 on 2007-04-27
Here is the better plan -
0.20 is on the dapper backports server.  Upgrade to the 0.20 on there and you are compatible with feisty directly.

Just make sure you backup your mysql database before the upgrade, and you won't have to worry.  In the event something does go horribly wrong, and you need to go back to the 0.18 dapper packages, just restore those packages and your mysql database.

Also, as a note, after installing the 0.20 dapper packages, you have to remove the libmyth-0.18 libraries.  I don't remember the exact name of them off hand, but you will have to remove them before starting the backend or frontend.

---

### Post by biostatman on 2007-04-27
Thanks, actually I am avoiding upgrading my backend (which actually runs Mandriva) from 0.18.1 if at all possible.  Here is what I have now:

Myth Backend: Mandriva 2006.0 running MythTV 0.18.1 backend
Laptop: Dapper running MythTV 0.18.1 Frontend

Where I want to be is:

Myth Backend: Mandriva 2006.0 running MythTV 0.18.1 backend (no change)
Laptop: Feisty running (backported?) MythTV 0.18.1 Frontend

However, can I infer from your post that I may be able to directly install the dapper 0.18.1 mythtv packages on Feisty, or would I have to recompile from source?

Thanks for any clarification.

---

