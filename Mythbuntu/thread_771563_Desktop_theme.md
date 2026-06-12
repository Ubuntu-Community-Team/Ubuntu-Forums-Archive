---
title: "Desktop theme?"
date: 2008-04-27
forum: Mythbuntu
---

### Post by bla2000 on 2008-04-27
I installed 8.04 and then added mythbuntu by using the "Add To Ubuntu" link on [http://www.mythbuntu.org]("http://www.mythbuntu.org"). I've created 5 new user accounts and added them to the mythtv users group and when I log in with any of the them I get the mythbuntu xfce desktop and theme.  How do I change the desktop back to the standard 8.04 gnome and theme for those users? 

Thanks.

---

### Post by superm1 on 2008-04-27
> **bla2000 said:**
> I installed 8.04 and then added mythbuntu by using the "Add To Ubuntu" link on [http://www.mythbuntu.org](http://www.mythbuntu.org). I've created 5 new user accounts and added them to the mythtv users group and when I log in with any of the them I get the mythbuntu xfce desktop and theme.  How do I change the desktop back to the standard 8.04 gnome and theme for those users? 

Thanks.
Remove the ~/.dmrc from their directories.

---

### Post by bla2000 on 2008-04-28
It didn't quite work as expected because each time I deleted, it was re-create during the login.  So I modified the parameter for "session" changing it to "default" instead of "mythbuntu".  I'll have to do this for each new user unless you know how to stop the .dmrc from re-creating or can have it re-create with the "session" set to "default".

Thanks.

---

