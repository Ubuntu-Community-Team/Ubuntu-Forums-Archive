---
title: "Odd rendering problem with GeForce4 MX"
date: 2008-05-08
forum: Multimedia Software
---

### Post by zvbxrpl on 2008-05-08
I have a Shuttle PC with an onboard nVidia GeForce4 MX AGP graphics card (uses 128MB of system memory).  I'm running a dual screen setup (2 x 1280x1024).  I originally installed Edgy, and although getting the nvidia driver to work took a while, I was able to get both screens working by enabling TwinView, with direct rendering enabled on both (~600 fps).  All my 3D apps worked well.

I did a fresh install of Gutsy back in October, and whilst the restricted drivers manager made installing the nvidia driver rather easier, I encountered a strange problem with direct rendering in some 3D apps.  glxinfo reports that direct rendering is enabled, and compiz works extremely well.  However, some 3D applications don't display properly.  googleearth runs, but the globe is just a black hole with no textures.  planetpenguin-racer starts and the music plays, but I just get a light blue screen with no detail at all.  I upgraded to Hardy, and the problem is still there.

I don't think it's anything to do with the dual screen setup, as I can disable this and I still get the same problem.  I can post my xorg.conf etc if requested, but just wondered if anyone has any general suggestions about what to try.  I don't know if this is an application-specific problem or a problem with the driver.  Does anyone have any ideas?  Many thanks.

---

