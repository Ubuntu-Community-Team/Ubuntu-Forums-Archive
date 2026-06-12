---
title: "&quot;no soundcards detected&quot; and policykit"
date: 2009-07-18
forum: Multimedia Software
---

### Post by wizard10000 on 2009-07-18
After fighting with two clean installs and two different sound cards on the same machine I found the problem was with policykit.

Backstory:  Two clean installs of 64-bit jaunty, two different sound cards work.  Run recommended upgrades from upgrade manager killed both the sound card and my TV tuner card.  Also, I could no longer suspend, hibernate or shut down the system.

After fighting with this for almost a week I learned I no longer had permission to access the sound card or the TV tuner card.  If you look in System --> Administration --> Authorizations you'll see that the active console has rights to both, but in my case neither device worked.  When I set "console" to yes as well, both devices started working.

Grrr.

Oh, well.  At least it's fixed  :)

edit:  I don't know how to mark a thread solved, but it's solved.  Thanks -

---

