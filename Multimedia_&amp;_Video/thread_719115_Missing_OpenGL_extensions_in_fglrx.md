---
title: "Missing OpenGL extensions in fglrx?"
date: 2008-03-08
forum: Multimedia &amp; Video
---

### Post by alexforcefive on 2008-03-08
Hi guys, forgive me if I get this wrong, it's not my area of expertise :)

Basically, I'm trying to enable 3d acceleration in vmware player. However, it crashes every time I enable it. The log says:

> Mar 07 21:13:49.391: mks| GLUtil_InstallExtensionLists: Missing extension GL_ARB_imaging
Mar 07 21:13:49.392: mks| GLUtil_InstallExtensionLists: Missing extension GL_NV_texture_shader
Mar 07 21:13:49.392: mks| Using FBO
Mar 07 21:13:50.105: mks| XINFO IO fatal error. Exiting ... 

So my question is, can I enable these extensions? My graphics card is an agp ATI x1950 using the latest proprietary drivers. I have direct rendering working

I would appreciate any help you can give! 

-alex

---

### Post by Tarmael on 2008-03-08
isn't direct rendering in a virtual machine still in Beta?

I hear VMWare has it, but I would like to see the bug list...

The GL_NV_texture_shader sounds like an nVidia thing (Correct me if I'm wrong. Which is probably the case).

Where did this error come up?

And does any other direct rendering work?

---

### Post by alexforcefive on 2008-03-08
Yeah, I think it's still a very experimental subject. Seems like in my case it's not working for a specific reason though. When I run vmware with direct rendering enabled, it crashes my x server. The log gives me the information I posted above.

Direct rendering works in general, apart from in vmware. You could be right about that extension being an nvidia thing though! 

Is there any way to add opengl extensions? As in, are they like plugins? Or do you just have to accept what the driver offers you?

---

### Post by Tarmael on 2008-03-08
Well, I would assume you would be able to get those extensions if you googled them correctly.

Mind, you could possibly just ask around for someone who has them and get them to find how to install them and make them usable.

Unless you REALLY need the application you're trying to run in VMWare, I'd probably just leave it alone till more support comes out...

Alternatively, Multi-boot? I know it's a pain, which is another reason why I deleted my M$ partition (One of many reasons).

Eh, good luck,

Bas.

---

