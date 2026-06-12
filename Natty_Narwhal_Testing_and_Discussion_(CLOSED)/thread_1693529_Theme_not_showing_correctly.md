---
title: "Theme not showing correctly"
date: 2011-02-23
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Jonny87 on 2011-02-23
For some reason the I'm not seeing the theme that I should. almost everything is showing the real basic theme. If I go to appearances and try changing it, it doesn't change, and yet the appearances window is displayed in the correct them. It seems to be the same case in both unit and classic environments and even on the login screen. Any ideas, cause I'm stumped.

I've attached a screen shot to help show what I mean.

---

### Post by SevenMachines on 2011-02-23
I had a similar problem recently, seemingly 2 different themes running at the same type, not being changed when altered in 'appearances'. It turned out to be a bug due tothe speed a new ssd drive was causing the computer to boot. gdm starts gnome-settings-daemon on user login before killing its own. The solution was to kill and restart gnome-settings daemon. I'll dig out the bug and you can see if it looks similar

[EDIT] LP Bug
 [https://bugs.edge.launchpad.net/ubuntu/+source/gdm/+bug/649809](https://bugs.edge.launchpad.net/ubuntu/+source/gdm/+bug/649809)

---

### Post by Jonny87 on 2011-02-23
***UPDATE***
I have solved and fixed this error myself.

I worked out that the problem was with the "gnome-settings-daemon". It must have been from an update.
I had installed;
   **gnome-settings-daemon 2.91.8-1ubuntu2 (natty)**

I forced version down to;
   **gnome-settings-daemon 2.32.1-0ubuntu6 (natty)**

This fixed the problem. Marking this post as solved.

---

### Post by Jonny87 on 2011-02-23
> **SevenMachines said:**
> I had a similar problem recently, seemingly 2 different themes running at the same type, not being changed when altered in 'appearances'. It turned out to be a bug due tothe speed a new ssd drive was causing the computer to boot. gdm starts gnome-settings-daemon on user login before killing its own. The solution was to kill and restart gnome-settings daemon. I'll dig out the bug and you can see if it looks similar

[EDIT] LP Bug
 [https://bugs.edge.launchpad.net/ubuntu/+source/gdm/+bug/649809](https://bugs.edge.launchpad.net/ubuntu/+source/gdm/+bug/649809)

Thanks, I was typing up that second post of mine when you posted this so only just got it. Thanks, I'll check out the bug report anyway for future reference.

---

### Post by Harry33 on 2011-02-23
> **Jonny87 said:**
> ***UPDATE***
I have solved and fixed this error myself.

I worked out that the problem was with the "gnome-settings-daemon". It must have been from an update.
I had installed;
   **gnome-settings-daemon 2.91.8-1ubuntu2 (natty)**

I forced version down to;
   **gnome-settings-daemon 2.32.1-0ubuntu6 (natty)**

This fixed the problem. Marking this post as solved.

This is a good point to know for users that have installed Gnome3 from Gnome3 PPA.
Although Gnome3 beta is now just about to be released (today), there are still issues with theming.
As you can see from the Gnome3 PPA new theme packages have failed to build.

---

