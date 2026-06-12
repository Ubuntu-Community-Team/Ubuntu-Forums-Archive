---
title: "Smooth upgrade to 11.04 beta 1"
date: 2011-04-06
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by geovino on 2011-04-06
I recently did an upgrade from 10.10 64bit to 11.04 64bit beta 1. It's the first time an upgrade went smoothly, and to a beta! I've used Ubuntu for five years on and off and in the past upgrades didn't go smoothly and I just backed up files and did clean installs. This one was OK. At first the upgrade didn't show the Unity WM until I installed Nvidia drivers, then after reboot it was there. I have to say that Unity will take getting used to and many will probably want to stay with the Classic WM but the more I use Unity the more I like it. It has some Mac feel and behavior, but that's OK. This will also work well for netbooks as well. :)

One question? If I keep upgrading packages in beta will it eventually upgrade to the final version after April 28? 

Will 
# aptitude safe-upgrade work as it does in Debian?

---

### Post by mörgæs on 2011-04-06
> **geovino said:**
> 
If I keep upgrading packages in beta will it eventually upgrade to the final version after April 28? 


Yes.

---

### Post by geovino on 2011-04-06
> **mörgæs said:**
> Yes.

Thanks. 

Just tried aptitude safe-upgrade... doesn't work, but 

$ sudo apt-get upgrade 

works fine.

---

