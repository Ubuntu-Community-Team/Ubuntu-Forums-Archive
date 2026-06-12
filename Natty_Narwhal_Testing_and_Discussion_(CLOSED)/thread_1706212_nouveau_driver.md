---
title: "nouveau driver"
date: 2011-03-13
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by beew on 2011-03-13
I installed the package libgl1-mesa-dri-experimental and tried it out on my laptop (Nvidia card: G105M) I found that while Compiz basically works, the performance was worse than Maverick. For example, rotating the desktop cube shows a lot of rough edges and tearing, desktop animation is a lot smoother in Maverick using Nouveau. It is the same in both Unity and the classic desktop but Unity is a little worse.

I installed Natty in an external hard drive and test it by plugging it in my laptop, I also have a Maverick external install (using just the Nouveau driver and the mesa experimental package) for the same purpose. I am comparing performance of these two installations. Since both are external (and actually on the same external hard drive) this should eliminate differential performance that might have resulted from running the OS from an external drive (I have installed Maverick in this laptop and this internal installation uses the Nvidia driver)

I wonder if anyone else has similar experience.

---

### Post by Quackers on 2011-03-13
Similar here. As you said, beew, the animations work (in my case with cairo-dock) but they are sluggish and sometimes freeze. A marked improvement on the basic driver though.

---

### Post by beew on 2011-03-14
> **Quackers said:**
> Similar here. As you said, beew, the animations work (in my case with cairo-dock) but they are sluggish and sometimes freeze. A marked improvement on the basic driver though.

Yeah, I just installed the Cairo Dock in the classical desktop to test it out. It is kind of sluggish and jerky. This time I just plug my external hdd in a machine with an Intel card so it is not related to nouveau. Probably a Compiz problem.

---

### Post by gnomeuser on 2011-03-14
Same for me, however I believe the change that caused this was required to make nouveau 3D work on more setups. Hopefully the performance and rendering quality will be up to Maverick and early Natty standards again soon.

---

### Post by beew on 2011-04-20
Nouveau performance in Natty apparently still not up to the Maverick standard. Cairo dock (with open GL) animation still sluggish, desktop cube still shows lots of tearings and I just rebooted because the machine has frozen.

However mplayer and googleearth seem to be working a lot smother than in Maverick using nouveau (don't know if that has to do with nouveau)

---

