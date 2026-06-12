---
title: "Sims 3 Graphical Errors"
date: 2010-04-22
forum: Multimedia Software
---

### Post by X-Malleus on 2010-04-22
Hey guys,

I'm on Jaunty, with an Intel GM965 graphics chip, using the intel (mesa) graphics driver, and I set up my graphics using the Optimal instructions in the Intel Jaunty Performance guide that's stickied in this forum.  I got some things, such as World of Warcraft, to work just fine, but I get these graphical errors when I try to play The Sims 3.  When the game starts, I can hear all of the sounds/music and see the game's cursor, but the rest of the screen is black.  Here's what I get in the terminal:

fixme:xinput:XInputGetState (1 0x32fc58)
fixme:imm:ImmGetOpenStatus (0x15c1f0): semi-stub
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT (0x8cd6)
fixme:d3d:context_check_fbo_status     Color attachment 0: (0x18a2c0) WINED3DFMT_B8G8R8A8_UNORM 1024x768
fixme:d3d:context_check_fbo_status     Depth attachment: (0x18a430) WINED3DFMT_D24_UNORM_S8_UINT 1024x768
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 4562
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 4562
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 4562
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 756
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION (0x506) from glDrawElements @ drawprim.c / 47
fixme:d3d:context_apply_state Activating for CTXUSAGE_BLIT for an offscreen target with ORM_FBO. This should be avoided.
fixme:d3d:context_bind_fbo >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindFramebuffer() @ context.c / 83
fixme:d3d:context_set_draw_buffer >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer() @ context.c / 2130

It seems like that is probably how it looks from beginning to end, but it's impossible to tell for sure, because this just repeats over and over, as long as the game is open.  Any idea at all what's going on here?

---

