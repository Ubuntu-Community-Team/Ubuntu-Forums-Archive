---
title: "k3b keeps causing a notification for &quot;Extra packages&quot;"
date: 2013-08-04
forum: Multimedia Software
---

### Post by MakOwner on 2013-08-04
I just loaded up Kubuntu from the 12.04 LTS desktop DVD media in order to use k3b for Blu-ray data burns with cdrtools.

k3b keeps causing a notification for "Extra packages"  -- even though the packages in the notificaiton have already been installed.
I burned one disk successfully and k3b can no longer detect media in the burn menu.  
If I use the media info menu item it sees a blank disk just fine.


It would really be great if I could get some of this to work :/

---

### Post by SeijiSensei on 2013-08-05
Install **kubuntu-restricted-extras** and the notifications will disappear.  Note that this package includes some things like add-ons for K3b that are not contained in ubuntu-restricted-extras.

---

### Post by krisbee2000 on 2013-08-19
For me, I installed the extras and I still got hassled, so I just right clicked the notification and told it not to warn me anymore... solved the issue.

---

### Post by MakOwner on 2013-08-19
I installed the extra-restricted packages,  and never had an option to not remind me.  Went back to MATE and am using something else.

---

### Post by Yellow Pasque on 2013-08-19
1. Install libk3b6-extracodecs
2. Enjoy

---

