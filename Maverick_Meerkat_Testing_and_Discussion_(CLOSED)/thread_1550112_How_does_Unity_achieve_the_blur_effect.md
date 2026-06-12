---
title: "How does Unity achieve the blur effect?"
date: 2010-08-10
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by godhika on 2010-08-10
Not sure where to ask, but I was wondering how does Unity get the blur behind the semitransparent tooltips. I was always under the impression that blur currently works only with Nvida hardware, but I was prooven wrong the first time I tried Unity. Does anyone know about the technical details?

---

### Post by MacUntu on 2010-08-10
From CluTK (/clutk/ctk-effect-blur.c):
```
if (ctk_has_capability (CTK_CAPABILITY_VERTEX_PROGRAM)
    && ctk_has_capability (CTK_CAPABILITY_FRAGMENT_PROGRAM)
    && ctk_asm_shaders_compiled_and_ready ())
  eff_class->paint = ctk_effect_blur_paint;
else
  {
    if (!ctk_has_capability (CTK_CAPABILITY_FBO) || !ctk_has_capability (CTK_CAPABILITY_VERTEX_PROGRAM) || !ctk_has_capability (CTK_CAPABILITY_FRAGMENT_PROGRAM))
      {
        g_message ("WARNING: CtkEffectBlur cannot work without FBO and assembly shader program capabiltities");
      }
    else
      {
        if (!ctk_asm_shaders_compiled_and_ready ())
          g_message ("WARNING: Shaders programs are not ready");
      }
    eff_class->paint = ctk_effect_blur_paint_dummy;
  }
```

So I'd say it's achieved via assembly shader code and framebuffer objects. :p No, seriously... no idea, but it should give you a hint.

---

### Post by jpeddicord on 2010-08-10
> **MacUntu said:**
> So I'd say it's achieved via assembly shader code and framebuffer objects. :p No, seriously... no idea, but it should give you a hint.

That's exactly how. I think it was about a year ago framebuffer objects were implemented on Mesa or the Intel drivers, which enables the blur effect. You can use it in the Blur plugin in Compiz as well.

---

### Post by x-shaney-x on 2010-08-11
I can't speak for ATI but blur also works on Intel cards (more recent ones at least) with both compiz and newer versions of KDE 4/kwin.

---

### Post by godhika on 2010-08-11
Thanks guys, very interesting I didn't know that Clutter is able to do blur effects (especially on my hardware). I am on a ATI card (R600 chipset) and blur is still not working in compiz.

---

