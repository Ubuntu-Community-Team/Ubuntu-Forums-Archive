---
title: "Sun java"
date: 2010-05-27
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by donniezazen on 2010-05-27
I couldn't find sun java in synaptics. Is there any alternative way to install it?

Thanks.

---

### Post by DougieFresh4U on 2010-05-27
Do you have all repo's enabled?
I got it from 'Ubuntu Software Center'

---

### Post by ronacc on 2010-05-27
what repo did you enable to get that , I have all repos enabled and don't see it either .

---

### Post by donniezazen on 2010-05-27
> **DougieFresh4U said:**
> Do you have all repo's enabled?
I got it from 'Ubuntu Software Center'

It's not available in Maverick Repository. I changed it to Lucid and it came up.

Thanks.

---

### Post by donniezazen on 2010-05-27
> **ronacc said:**
> what repo did you enable to get that , I have all repos enabled and don't see it either .

Try this [http://nfolamp.wordpress.com/2010/05/19/howto-install-sun-java-on-ubuntu-10-04-lucid/](http://nfolamp.wordpress.com/2010/05/19/howto-install-sun-java-on-ubuntu-10-04-lucid/)

I just added deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner , installed the Java and removed it.

---

### Post by dagrump on 2010-05-27
It's normally in the partners repository, MM may not have anything in there yet. The repo shows up. Of course I just changed lucid to maverick, so who knows.

---

### Post by ronacc on 2010-05-27
temporarily added the lucid partner repo , installing now . Thought that might be it , this early not everything has caught up .

---

### Post by DougieFresh4U on 2010-05-27
> **ronacc said:**
> what repo did you enable to get that , I have all repos enabled and don't see it either .

> **ronacc said:**
> temporarily added the lucid partner repo , installing now . Thought that might be it , this early not everything has caught up .

Sorry I wasn't more clear in my post but you seem to have it under control :)
Kind of 'forgot' that I started with Lucid and installed Java before I changed sources list. Some thing I have been doing the past few releases as I couldn't get Java one time and I started adding Java and a couple of other things before a source list change on a testing/playing partition.

---

### Post by ktp on 2010-05-27
> **soham_1207 said:**
> It's not available in Maverick Repository. I changed it to Lucid and it came up.

Thanks.

Sun JVM was/is dropped from the Multiverse.

[Sun Java moved to the Partner repository]("https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Sun Java moved to the Partner repository")

---

