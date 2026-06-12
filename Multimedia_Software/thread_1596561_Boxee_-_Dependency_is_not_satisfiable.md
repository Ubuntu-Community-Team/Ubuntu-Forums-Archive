---
title: "Boxee - Dependency is not satisfiable"
date: 2010-10-14
forum: Multimedia Software
---

### Post by tsaunders on 2010-10-14
I am trying to install Boxee on 10.10 x64 but I am getting this error and not sure how to correct it.

Dependency is not satisfiable: libdirectfb-1.0-0|libdirectfb-1.2-0

I am running this file:

boxee-0.9.22.13692.x86_64.deb

---

### Post by TBABill on 2010-10-14
Boxee is in the repos. Did you try to install via Synaptic? Looks like the .deb is looking for a dependency you don't have installed (higher version?). I installed via Synaptic and works well.

---

### Post by tsaunders on 2010-10-14
> **TBABill said:**
> Boxee is in the repos. Did you try to install via Synaptic? Looks like the .deb is looking for a dependency you don't have installed (higher version?). I installed via Synaptic and works well.

Do I need to add the repo or is it already in Synaptic?

---

### Post by endotherm on 2010-10-14
so far as i am aware, boxee is 32bit only. I'm seeing some tutorials on getting it to run in a x64 environment, but they all involve using a 32b chroot, which canonical does not recommend at all.

---

### Post by tsaunders on 2010-10-14
They have a 64bit download:  [http://www.boxee.tv/download](http://www.boxee.tv/download)

---

### Post by endotherm on 2010-10-14
Ahh! good on them. I had been waiting a while...

since their version is built for ubuntu, I would ask over at their forums. the installer is for karmic/lucid, but it looks like people are makeing some strides in getting it going in Maverick.
[http://forums.boxee.tv/forumdisplay.php?f=4](http://forums.boxee.tv/forumdisplay.php?f=4)

---

### Post by tsaunders on 2010-10-14
> **endotherm said:**
> Ahh! good on them. I had been waiting a while...

since their version is built for ubuntu, I would ask over at their forums. the installer is for karmic/lucid, but it looks like people are makeing some strides in getting it going in Maverick.
[http://forums.boxee.tv/forumdisplay.php?f=4](http://forums.boxee.tv/forumdisplay.php?f=4)

Thanks!  I hope they get it working.  I really hope they get the Netflix part working or I am going to have to resort to a VM of XP to watch Netflix on my laptop.

---

### Post by endotherm on 2010-10-14
> **tsaunders said:**
> Thanks!  I hope they get it working.  I really hope they get the Netflix part working or I am going to have to resort to a VM of XP to watch Netflix on my laptop.
  unfortunatelyeverything I have heard indicates that Netflix will never end up on linux, until they move away from silverlight. Novell's Moonlight is a port of silverlight, but as I understand it, it is blocked from working with the silverlight DRM.

---

### Post by tsaunders on 2010-10-14
> **endotherm said:**
> unfortunatelyeverything I have heard indicates that Netflix will never end up on linux, until they move away from silverlight. Novell's Moonlight is a port of silverlight, but as I understand it, it is blocked from working with the silverlight DRM.

Looks like the VM route for now.  What I don't understand is that Roku is Linux (correct?) and Netflix works.

---

### Post by tgm4883 on 2010-10-14
> **tsaunders said:**
> Looks like the VM route for now.  What I don't understand is that Roku is Linux (correct?) and Netflix works.

Roku uses a hardware chip to unencrypt the DRM

---

### Post by tsaunders on 2010-10-14
> **tgm4883 said:**
> Roku uses a hardware chip to unencrypt the DRM

Thanks!

---

### Post by Laz23 on 2010-10-16
I had the same issue as the OP, and solved it by downloading libdirectfb [from the Lucid repositories]("http://packages.ubuntu.com/lucid/libdirectfb-1.2-0") (just pick the amd64 link on that page).

---

