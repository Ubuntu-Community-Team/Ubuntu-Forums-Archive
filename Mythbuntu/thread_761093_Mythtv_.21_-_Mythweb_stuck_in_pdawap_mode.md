---
title: "Mythtv .21 - Mythweb stuck in pda/wap mode"
date: 2008-04-20
forum: Mythbuntu
---

### Post by agent5150 on 2008-04-20
Everything on mythweb with version .21 was working. Then I browsed the url with my pda... cool. works, I see a smaller version of mythweb pages.

Problem is that now I get that same pda/wap pages on regular PC browsers too !!.  I have restarted the httpd service.. but the problem exists.

With .20.2  i did not have this problem.  pda and pc could browse at the same time with out this problem.

any ideas?

---

### Post by mrand on 2008-04-20
> **agent5150 said:**
> Everything on mythweb with version .21 was working. Then I browsed the url with my pda... cool. works, I see a smaller version of mythweb pages.

Problem is that now I get that same pda/wap pages on regular PC browsers too !!.  I have restarted the httpd service.. but the problem exists.

With .20.2  i did not have this problem.  pda and pc could browse at the same time with out this problem.

any ideas?

Per a thread pointed to by [http://www.gossamer-threads.com/lists/mythtv/users/330637]("http://www.gossamer-threads.com/lists/mythtv/users/330637"),   "Try adding '?RESET_TMPL=true' to the end of a mythweb URL and it
should reset the template."

Have fun,

   Marc

---

### Post by agent5150 on 2008-04-21
Thanks Marc.  I did find another post about using different users for wap and pc.  So Now I have one dedicated for each type.  But its good to know the parameters to force reset the template.  It did work.

---

### Post by Mario_ger on 2009-03-30
Great that you found a good solution. Do you mind sharing it with us?

---

