---
title: "Problem with fglrx"
date: 2010-09-25
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by rapiertg on 2010-09-25
As always i have a black screen after installing fglrx, but usually tweaking xorg conf with modes 1280x1024 was enough to make it working again.

This time the driver do not react to changes and makes my monitor out of sync with 1600x1200 over and over. I wondered what happens if i plug my Full Hd wTV with d-sub and change res to my monitors native one in amdcccle.

So clicking apply and ok in amdcccle change the resolution and crashesh the application with error: segmentation fault (core dumped), but after reboot it choose 1600x1200 again.

glxinfo also crashes.

Some ideas whats wrong?

Ubuntu 64 10.10, Sapphire Radeon HD 4650

---

### Post by rapiertg on 2010-09-26
I found a way to change resolution. Since amdcccle crashes when i change it and the resolution changes back to 1600x1200 after reboot i tried to change it with default gnome resolution changer and after login screen in 1600x1200 it changes it to 1280x1024. So i somehow fixed it and am able to use my monitor.

But im not very happy with it and would like to use standard Ati configuration app. Is this a bug it fglrx? Anyone experiencing the same or it it my hardware configuration specific issue? Report it in launchpad?

---

### Post by rapiertg on 2010-09-27
Well, it seems that there was some mistake in last xorg.conf. After:

> sudo aticonfig --resolution=0,1280x1024,1024x768,800x600
Ati CCC seems to work ok. But i have last problem. The 1600x1200 is still the biggest resolution and i cant get rid of it. The login screen makes my monitor out of sync. The startup manager doesn't work. Is there any way to set up smaller res on login screen, or disable too big resolution?
Thanks.

---

### Post by sonicb00m on 2010-09-29
I also have this issue with my lcd tv , as soon as i install and reboot i get nothng but a black screen.

I will try and see if you the suggestion you made will at least give a picture.

---

