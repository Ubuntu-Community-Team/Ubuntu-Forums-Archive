---
title: "run as mythtv user?"
date: 2008-06-15
forum: Mythbuntu
---

### Post by IndieRockSteve on 2008-06-15
what does mythbuntu use the mythtv user for? I'd like to be able to run mythfrontend as the mythtv user so i can have a dedicated login for mythtv to run sans xfce for a dedicated frontend system. I notice theres already a mythtv user but the regular gui user editor won't let me access this user nor will the autologin gui preference setup. i was going to delete the user and add it anew as a "normal" user I just want to make sure its not being used for anything important?

thanks!

---

### Post by tgm4883 on 2008-06-15
Use MCC and setup your box to autologin for your normal user.  You can do what you want from MCC

---

### Post by superm1 on 2008-06-15
> **IndieRockSteve said:**
> what does mythbuntu use the mythtv user for? I'd like to be able to run mythfrontend as the mythtv user so i can have a dedicated login for mythtv to run sans xfce for a dedicated frontend system. I notice theres already a mythtv user but the regular gui user editor won't let me access this user nor will the autologin gui preference setup. i was going to delete the user and add it anew as a "normal" user I just want to make sure its not being used for anything important?

thanks!
It is used for backend daemon type processes and group management so that if you make a multiuser system, they all can belong to the "mythtv" group and have access to myth stuff.

If you want an auto login without xfce, you can do it as your normal user too.  I'd avoid doing it as the "mythtv" user.

---

### Post by IndieRockSteve on 2008-06-17
> **superm1 said:**
> It is used for backend daemon type processes and group management so that if you make a multiuser system, they all can belong to the "mythtv" group and have access to myth stuff.

If you want an auto login without xfce, you can do it as your normal user too.  I'd avoid doing it as the "mythtv" user.

ok, I just have it setup to run mythfrontend as the mythtv user on my other non-mythbuntu frontends so I figured I'd see if there was a reason not to on mythbuntu.

thanks!

---

