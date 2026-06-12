---
title: "Many problems .. maybe un-fixable? What do I need to back up and how?"
date: 2008-05-26
forum: Mythbuntu
---

### Post by Daminator on 2008-05-26
Hello all,

The 'upgrade' to 8.10 completely destroyed my graphics card set up and somewhere in the fruitless journey to try to fix that my beautifully working MythTV system is now completely broken.

I'll skip the graphics card bit ..

The first Myth problem I noticed was that none of the frontends could connect to the backend. If I run mythbackend from a terminal, I get:
damian@MythBox:~$ mythbackend
NVIDIA OpenGL Driver requires CPUs with SSE to run.

The current CPU does not support SSE.
damian@MythBox:

Why the backend is interested in my graphics card drivers I have no idea!
At one point, it was telling me that mythebackend wasn't installed, but installing it again didn't really fix things.

An update just tried to updave mythbackend, but returned this:
E: mythtv-backend: subprocess post-installation script returned error exit status 255

My nvidia graphics card problems are still unresolved, so I may bo looking at a hardware upgrade before starting again from scratch. If I could get the backend running ok for the other frontends in the mean time, that would be great.

So, I guess this post is really 2 questions:
1) Can anyone help me to get the backend working? (It's a backend/fontend machine, but the frontend isn't very useful at the moment as I can't get graphics talking to my projector very nicely)

2) What do I need to back up and how before scrapping and starting again?
(My recordings were always on a different drive. I need to know how to back up my database, lirc settings, and anything else that comes to mind and how to restore them.)

Looking forward to any help I can get!
Damian

---

### Post by laga on 2008-05-26
I believe that downgrading to an older nvidia driver might fix the problem. If you have "nvidia-glx-new", try "nvidia-glx". If you have "nvidia-glx", try "nvidia-glx-legacy" (assuming that your hardware is supported by these drivers).

The SSE problem has happened to people before, so maybe the forums search or google can turn up some better solutions.

---

### Post by Daminator on 2008-05-26
Any ideas how I can uninstall the 173 driver i installed. That might help things along.

Damian

---

### Post by Daminator on 2008-05-28
I got 173.08 uninstalled (but using a --uninstall option) and now, like magic, my myth backend is working again and all the frontends are connecting fine.

Now I just have to try to get the nvidia drivers to give me the resolution I want.

Damian

---

