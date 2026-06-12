---
title: "Question about GIMP 2.10 snap package and updates"
date: 2019-11-09
forum: Multimedia Software
---

### Post by tomdkat on 2019-11-09
Hi!  I'm running Ubuntu 19.10 and installed GIMP 2.10.12 via the snap package in the Ubuntu Software application.  I see GIMP 2.10.14 is now out.  I haven't installed many snap packages, so I'm not sure how the updates work.  Will GIMP 2.10.12 eventually be upgraded to 2.10.14, via Ubuntu software updates or must I somehow do the upgrade myself, manually?

Thanks in advance!

Peace...

---

### Post by deadflowr on 2019-11-09
snaps auto update without any user interaction required.

To add to that if you want you can manually check and install new updates with
```
snap refresh
```
snap has a bevy of commands, see
```
snap help
```
for a listing of common commands.

---

### Post by tomdkat on 2019-11-09
Great!  Thanks for the information!  It's greatly appreciated!  :)

Peace...

---

### Post by deadflowr on 2019-11-10
ftr here's a current status of the gimp update to 2.10.14:
[https://github.com/snapcrafters/gimp/issues/80]("https://github.com/snapcrafters/gimp/issues/80")
I would expect the initial package to be built for the edge or beta channels before reaching the stable channel.
more on channels here: [https://snapcraft.io/docs/channels]("https://snapcraft.io/docs/channels")

---

### Post by tomdkat on 2019-11-10
> **deadflowr said:**
> ftr here's a current status of the gimp update to 2.10.14:
[https://github.com/snapcrafters/gimp/issues/80]("https://github.com/snapcrafters/gimp/issues/80")
I would expect the initial package to be built for the edge or beta channels before reaching the stable channel.
more on channels here: [https://snapcraft.io/docs/channels]("https://snapcraft.io/docs/channels")

Great!  Thanks for the additional info!  :)

Peace...

---

