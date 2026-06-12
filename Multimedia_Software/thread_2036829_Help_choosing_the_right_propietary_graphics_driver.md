---
title: "Help choosing the right propietary graphics driver"
date: 2012-08-03
forum: Multimedia Software
---

### Post by Shadius on 2012-08-03
Hey everybody! :)

I need help choosing the correct graphics drivers. Here's a screenshot of what it says in the *Additional Drivers* window.

---

### Post by 2F4U on 2012-08-03
And what is your graphics card, or did I miss something?

---

### Post by Shadius on 2012-08-03
> **2F4U said:**
> And what is your graphics card, or did I miss something?

Oh, sorry, it's NVIDIA GeForce 6200

---

### Post by MechaMechanism on 2012-08-03
If you don't know what your doing then go with recommended.  But the post-release current version is probably safe.

---

### Post by Shadius on 2012-08-03
Can't say that I know what I'm doing, but I'd like to learn. I'm wondering what these different versions are. Can anyone help me understand?

---

### Post by MechaMechanism on 2012-08-05
> **Shadius said:**
> Can't say that I know what I'm doing, but I'd like to learn. I'm wondering what these different versions are. Can anyone help me understand?
Well the top two are the driver that was available at the time of the development of 12.04.  The two on the bottom are always the current drivers for people who like to live on the edge.  The post release updates are updates to the main drivers.

---

### Post by alan21276 on 2012-08-05
I'm using a very similar card.....NVIDIA GeForce 6150

I find the version current (recommended) works best for me, being the most stable.

Hope this helps

---

### Post by Shadius on 2012-08-05
I've noticed that sometimes the screen would flicker. It *always flickers* when starting up, at the purple screen (don't know the official name) and at the login screen. Sometimes, there would be a black bar across the login screen. I would move the mouse and it would disappear. I thought it might be the graphics drivers? Any ideas/suggestions?

---

### Post by alan21276 on 2012-08-06
> **Shadius said:**
> I've noticed that sometimes the screen would flicker. It *always flickers* when starting up, at the purple screen (don't know the official name) and at the login screen. Sometimes, there would be a black bar across the login screen. I would move the mouse and it would disappear. I thought it might be the graphics drivers? Any ideas/suggestions?

I believe this is to do with the graphics driver being started within the kernel, every fix I've tried seems to be undone after a kernel update.
I believe this will eventually be sorted as I think quite a few people have this problem.

It seems to happen more from a cold boot rather than a restart.

Once fully booted it all seems to work fine, if you have trouble getting that far......try setting nomodeset at boot options, sometimes I need to manually restart lightdm by opening a tty by pressing Ctrl F2 , then log in and use sudo restart lightdm.

---

### Post by wheeze on 2012-08-06
> **Shadius said:**
> Oh, sorry, it's NVIDIA GeForce 6200

I'm using this same graphics card with the nvidia-current-updates driver with no problems in Quantal.

---

