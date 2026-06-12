---
title: "WINE d3d problem"
date: 2008-10-02
forum: Multimedia Software
---

### Post by Nyquist562 on 2008-10-02
When running WINE for a video game, I am seeing the following output (in the console):


fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d_shader:shader_glsl_load_constantsF >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB() @ glsl_shader.c / 265
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 445
fixme:d3d_surface:fb_copy_to_texture_direct Doing a pixel by pixel copy from the framebuffer to a texture, expect major performance issues



The noticeable slow down comes precisely when the 3D rendering starts.

I have the Nvidia Drivers installed fine, 3D hardware accelleration is enabled, and the  game 'runs' but as the output says, I have MAJOR performance issues (about 1 frame every 5-10 seconds, which is 100% unbearable).
I am trying to get Everquest II to run using Ubuntu Hardy 8.04, Wine 1.1.5, and an Nvidia GeForce 8600GTS.

And my hardware is not the problem, it runs many other even more gfx intensive programs just fine.

Much Thanks!

---

