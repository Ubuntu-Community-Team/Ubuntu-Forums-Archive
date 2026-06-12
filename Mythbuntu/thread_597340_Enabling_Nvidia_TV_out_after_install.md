---
title: "Enabling Nvidia TV out after install"
date: 2007-10-30
forum: Mythbuntu
---

### Post by 7bigjohn on 2007-10-30
Does anyone know how to enable TV out on Mybuntu final.  I saw the option during the install but it's not there any more in the control center.  Thanks

---

### Post by superm1 on 2007-10-30
Open up nvidia-settings from the control centre and do it there.

---

### Post by kyfehr on 2007-10-31
I have another question along this line.

During install it asked me whether my tv-out was composite, svideo, or component. 

I now have a tv that allows svideo, how do I set this as the tv out without reinstalling mythbuntu - have a nvidia graphics on board mobo (in signature) using proprietary drivers.

---

### Post by superm1 on 2007-10-31
> **kyfehr said:**
> I have another question along this line.

During install it asked me whether my tv-out was composite, svideo, or component. 

I now have a tv that allows svideo, how do I set this as the tv out without reinstalling mythbuntu - have a nvidia graphics on board mobo (in signature) using proprietary drivers.
Open up MCC, and choose nvidia configuration utility under proprietary drivers.

---

### Post by kyfehr on 2007-10-31
I have gone in there.. but nowhere does it give me an option to change the tv-out from composite to s-video - the only option it gives me is to disable to tv and enable the monitor and then all the OpenGL info - do I need to manually edit the xorg file?

---

### Post by superm1 on 2007-10-31
> **kyfehr said:**
> I have gone in there.. but nowhere does it give me an option to change the tv-out from composite to s-video - the only option it gives me is to disable to tv and enable the monitor and then all the OpenGL info - do I need to manually edit the xorg file?
If you disable the tv, restart X, and re-enable it - it is supposed to detect the kind of cable its connected with.

Alternatively, you can manually edit the xorg.conf too.

---

### Post by kyfehr on 2007-10-31
yes.. thn superm1 my retardedness i was unpluging from the tv but not the computer.. i am an idiot today.. thank you for your help and patience.

---

