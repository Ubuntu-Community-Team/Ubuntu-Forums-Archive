---
title: "Problem in the Installation"
date: 2010-09-08
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Maupertus on 2010-09-08
Hey everyone,

I think I found a small, but annoying bug in the Maverick installation process, but I do not know for sure if its a bug, and I haven't been able to replicate it yet.

During install, everyone works out okay, but ubiquity will very often crash. At first, I thought that this was the reason for the installation failing each time, but I now know that this isn't or at least, does not have to be, the case.

When you reach the point in the installation process that you have to fill in your personal information, and you have done this and pressed 'forward' before the installation process states: "Ready when you are" then the installation stalls.

If you wait, fill in the info and press 'forward' when the installation is "Ready" then all works out perfectly. The bug I was able to find was the fact that ubiquity fails to create a user-account.

Can anybody confirm? I didn't do a clean install on my other PC, but a dist-upgrade so I can not confirm myself.

---

### Post by ronparent on 2010-09-08
I guess that I'm to slow filling in the data to have experienced this. It does sound like a bug - the forward button should remain grayed out until the system is ready to receive the data. You are right. It would be best if someone else observed and reported it as a problem, otherwise one bug report on it might not get responded to.

---

