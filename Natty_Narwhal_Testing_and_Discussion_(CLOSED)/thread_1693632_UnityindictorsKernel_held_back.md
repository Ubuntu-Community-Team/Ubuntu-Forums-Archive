---
title: "Unity/indictors/Kernel held back"
date: 2011-02-23
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ELD on 2011-02-23
Okay so those packages have been held back for a couple days now, anyone know why/when they will be available to update?

---

### Post by arpanaut on 2011-02-23
I don't want to steer you wrong here, but if you are using "aptitude safe-upgrade" I don't think it will work because Unity depends on the indicator packages, which want to remove the old and replace with the new.

Try Synaptic and pay attention to what is removed and added, you should see three packages to remove but are replaced by packages of the same name. Not sure about the kernel thet came through no-problem for me.

I had these others hanging for a while too until I upgraded all that would go then dealt with the others with Synaptic. Not seeing any problems as yet... Proceed with caution.

---

### Post by MadCow108 on 2011-02-23
install them manually with apt-get install and review what changes before executing.

indicator will remove libindicator2 and replace it with libindicator3 this is what probably also holds back your unity upgrade
unity-2d is currently broken by this update, if you need it better wait until bug 722298 is fixed

the kernel update is probably also save in respect to the packages, it is probably held back because it wants to install new headers

---

### Post by ELD on 2011-02-23
Yeah synaptic got it, forgot you can check what it's doing there.

It was the notify issue wanting to go from 2 to 3 :)

---

