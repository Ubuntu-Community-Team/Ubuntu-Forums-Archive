---
title: "New to Mythbuntu problems with &quot;no backend UPnP&quot;"
date: 2008-07-06
forum: Mythbuntu
---

### Post by Peterfc on 2008-07-06
Hi All

I have downloaded mythbuntu and i am trying to get it setup. After selecting English and then going to the next screen i get a message "No UPnp backends found" I have looked in the System under Preferences and also the Administration but found nothing about UPnp. I found nothing under the [www.mythbuntu.org/support](www.mythbuntu.org/support) documentation. Can anybody help.

Thanks for reading this post

---

### Post by Lester_Burnham on 2008-07-06
Did you install the standard backend / Frontend install?
If so, it sounds like the backend isn't running.

sudo /etc/init.d/mythbackend restart

type the above into a terminal and see what it says.

---

### Post by Archmage on 2008-07-07
To make things short: You need to install the backend first and than the frontend.

---

