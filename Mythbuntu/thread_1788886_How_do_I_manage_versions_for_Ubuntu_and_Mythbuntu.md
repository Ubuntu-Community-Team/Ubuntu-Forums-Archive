---
title: "How do I manage versions for Ubuntu and Mythbuntu"
date: 2011-06-23
forum: Mythbuntu
---

### Post by Saubazi on 2011-06-23
I am running my media-PC with 10.04 LTS and I would like to jump up to the next LTS - once time is ripe, meanwhile I can see that 0.24 and stuff is also available for that one. At the same time I am running Ubuntu on a laptop and desktop machines. I want to get the latest Ubuntu on them

I had this dilemma in the past with the compability of the myth versions (at that time I was not with mythbuntu). Can I somehow make sure that my laptop and desktop that are now being updated to Ubuntu 11.04 will work with the backend on my mythbuntu 10.04 having same versions of frontends?

I have installed mythbuntu-repos.deb on them, but I do not have the mythbuntu-control-center there so that I can choose the version to follow

What should I do - or am I making a fuss out of nothing?

---

### Post by tgm4883 on 2011-06-23
> **Saubazi said:**
> I am running my media-PC with 10.04 LTS and I would like to jump up to the next LTS - once time is ripe, meanwhile I can see that 0.24 and stuff is also available for that one. At the same time I am running Ubuntu on a laptop and desktop machines. I want to get the latest Ubuntu on them

I had this dilemma in the past with the compability of the myth versions (at that time I was not with mythbuntu). Can I somehow make sure that my laptop and desktop that are now being updated to Ubuntu 11.04 will work with the backend on my mythbuntu 10.04 having same versions of frontends?

I have installed mythbuntu-repos.deb on them, but I do not have the mythbuntu-control-center there so that I can choose the version to follow

What should I do - or am I making a fuss out of nothing?

You can install mythbuntu-control-centre on Ubuntu (from the repositories) or use 'dpkg-reconfigure mythbuntu-repos' to configure mythbuntu-repos.

You will need to be on the same version of each. 10.04 shipped with 0.23, but will have all mythtv releases up until the version that ships with 12.04 (LTS).

---

### Post by Saubazi on 2011-06-24
Thanks that was exactly what I wanted to know...

I jumped yesterday to 0.24 on my LTS and had some grief, but I think I made it now (still holding the breath). I do not know if the machines running Ubuntu desktop run with older version - as if mythbuntu 11.04 comes out with 0.24, whether it or ubuntu would run the older 0.23 anymore - or even have packages for them, so I figured that with LTS as backend I am forced to go for the latest stable (which is a sort of minimum for newer releases). 

Anyway this is what I want - have the latest myth but not need to update OS everytime. So now I can wait for the next LTS.

---

### Post by tgm4883 on 2011-06-24
> **Saubazi said:**
> Thanks that was exactly what I wanted to know...

I jumped yesterday to 0.24 on my LTS and had some grief, but I think I made it now (still holding the breath). I do not know if the machines running Ubuntu desktop run with older version - as if mythbuntu 11.04 comes out with 0.24, whether it or ubuntu would run the older 0.23 anymore - or even have packages for them, so I figured that with LTS as backend I am forced to go for the latest stable (which is a sort of minimum for newer releases). 

**Anyway this is what I want - have the latest myth but not need to update OS everytime. So now I can wait for the next LTS.**

That is what we wanted too :)

---

