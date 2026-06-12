---
title: "kde sc 4.5.2"
date: 2010-10-05
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by oobuntoo on 2010-10-05
With Maverick Meerkat final just five days away, will kde 4.5.2 (released today) make it into the official repo? Anybody knows? I've been in a constant testing mode this whole year and itching for this.

---

### Post by danbuter on 2010-10-05
It's not likely.

---

### Post by 67GTA on 2010-10-05
No. You can get 4.5.2, as well as any other updates to the KDE platform by adding the Kubuntu PPA. Instructions here: [http://www.kubuntu.org/news/kde-sc-4.5.2](http://www.kubuntu.org/news/kde-sc-4.5.2)

---

### Post by xebian on 2010-10-05
Interesting call to not upgrade 10.04 LTS since it already has 4.5.1.  Why force users to 10.10 in order to get 4.5.2?:confused:

---

### Post by Temar09 on 2010-10-07
> **xebian said:**
> Interesting call to not upgrade 10.04 LTS since it already has 4.5.1.  Why force users to 10.10 in order to get 4.5.2?:confused:

I agree, forcing the users to immediately upgrade to the latest distribution is a bad descision.

I finally got a stable Lucid installation with everything working as expected and now I have to upgrade again. As Maverick is brand new, I bet that all the problems start all over again.

---

### Post by 67GTA on 2010-10-07
You are not being forced to upgrade to Maverick. The Kubuntu PPA repo is not just for Maverick, you can just update Lucid to 4.5.2 if you wanted.

---

### Post by Quadchris on 2010-10-07
Directly from Kubuntu web page :

"There are no packages planned for Kubuntu 10.04 LTS, we recommend updating to 10.10 if you want to try the newest software, either upgrade to the release candidate or wait for the final release on Sunday.

Thanks to Jonathan and Rohan for helping to package this release."

It seems the upgrade will be forced !

---

### Post by buzzmandt on 2010-10-07
it's not forced, go to kde and build it. or don't update, 4.5.1 is really good. I'll be using it on my main for a while at least.

---

### Post by Quadchris on 2010-10-07
Me too ... but it seems that there are some people who want to be on the edge with KDE but on a lucid version ... which actually not possible by the ordinary way.

Compiling package is not natural for end-users :)

---

### Post by Temar09 on 2010-10-07
> **buzzmandt said:**
> it's not forced, go to kde and build it. or don't update, 4.5.1 is really good. I'll be using it on my main for a while at least.

4.5.1 is not good at all. There are at least two very annoying bugs:

1) Pixmap-Cache Problem when using Nvidia ([https://bugs.kde.org/show_bug.cgi?id=234463](https://bugs.kde.org/show_bug.cgi?id=234463)).

2) Dolphin hangs all the time

At least the first bug seems to be fixed/improved in 4.5.2. It was also the reason why I updated to KDE 4.5. I don't mind working with 4.4 but I want a usable configuration. Neither the default KDE shipped with Lucid nor the 4.5.1 update is usable if you are affected by this bug. So now I have to update to Maverick and have to deal with even more bugs.

Forcing the users to update to a brand new release is a bad descision! Is it really that hard to build 4.5.2 packages if you already have a working build environment for 4.5.1? I thought launchpad would do that automatically.

---

### Post by 67GTA on 2010-10-07
> **Quadchris said:**
> Directly from Kubuntu web page :

"There are no packages planned for Kubuntu 10.04 LTS, we recommend updating to 10.10 if you want to try the newest software, either upgrade to the release candidate or wait for the final release on Sunday.

Thanks to Jonathan and Rohan for helping to package this release."

It seems the upgrade will be forced !

That just sucks. I didn't read that far down. Normally the newest KDE is supported on all the releases using the Kubuntu PPA. I wonder sometimes why they even bother with Kubuntu anymore. I don't install it anymore. I install Ubuntu, and then install kde-full.

---

### Post by xebian on 2010-10-07
> **67GTA said:**
> You are not being forced to upgrade to Maverick. The Kubuntu PPA repo is not just for Maverick, you can just update Lucid to 4.5.2 if you wanted.

The kubuntu-ppa/ppa 4.5.2 packages are just for maverick only.  Tried getting it to Lucid but not workable atm without heavy lifting.

---

