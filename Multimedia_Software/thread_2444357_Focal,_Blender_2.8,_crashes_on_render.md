---
title: "Focal, Blender 2.8, crashes on render"
date: 2020-05-29
forum: Multimedia Software
---

### Post by lazyteddy on 2020-05-29
Hi,

I wanted to take a new look at blender, which I had been dabbling in a long time ago (about ten years or so.) Trying to make myself familiar with the interface again, so tried to render the default scene. Crashes every time. Here's the output when started from the command line:
```
Read prefs: /home/tanja/.config/blender/2.82/config/userpref.blend
Warning: property 'release_confirm' not found in keymap item 'OperatorProperties'
blender(BLI_system_backtrace+0x37) [0x555eda4ca897]
blender(GPU_framebuffer_recursive_downsample+0x337) [0x555eda3cb567]
blender(EEVEE_downsample_cube_buffer+0x54) [0x555ed811af54]
blender(EEVEE_lightbake_filter_glossy+0x13c) [0x555ed80cac8c]
blender(EEVEE_lightbake_update_world_quick+0x102) [0x555ed80c8202]
blender(EEVEE_render_draw+0x214) [0x555ed80d2dc4]
blender(+0x16daaaf) [0x555ed80c4aaf]
blender(DRW_render_to_image+0x216) [0x555ed80b9646]
blender(RE_engine_render+0x36c) [0x555ed9edd90c]
blender(+0x34fd881) [0x555ed9ee7881]
blender(+0x3500bf8) [0x555ed9eeabf8]
blender(RE_RenderFrame+0xf2) [0x555ed9eeb482]
blender(+0x238e824) [0x555ed8d78824]
blender(+0x15e1746) [0x555ed7fcb746]
/lib/x86_64-linux-gnu/libpthread.so.0(+0x9609) [0x7f42bb4f5609]
/lib/x86_64-linux-gnu/libc.so.6(clone+0x43) [0x7f42b6b6b103]
BLI_assert failed: /build/blender-RL3axj/blender-2.82.a+dfsg/source/blender/gpu/intern/gpu_framebuffer.c:780, GPU_framebuffer_recursive_downsample(), at '0x8CD5 == __glewCheckFramebufferStatus(0x8D40)'
Aborted
```

Graphics card: GeForce GTS 250

[IMG]https://hub.lazyteddy.eu/photo/f8d3d07a-d5d0-4827-9986-c7e5b10772a9-0.png[/IMG]

Any help would be much appreciated.

---

### Post by monkeybrain20122 on 2020-05-29
How did you install blender?

---

### Post by lazyteddy on 2020-05-30
> **monkeybrain20122 said:**
> How did you install blender?

From the repositories. I have two versions of Ubuntu installed on separate partitions - Ubuntu Studio for anything art related and a regular Xubuntu desktop for everything else. I first came across this on Ubuntu Studio, where it was pre-installed, of course. Then I installed it on my regular desktop, also from the repositories, got the same result.

Thanks for responding.

---

### Post by monkeybrain20122 on 2020-05-30
> **lazyteddy said:**
> From the repositories. I have two versions of Ubuntu installed on separate partitions - Ubuntu Studio for anything art related and a regular Xubuntu desktop for everything else. I first came across this on Ubuntu Studio, where it was pre-installed, of course. Then I installed it on my regular desktop, also from the repositories, got the same result.

Thanks for responding.

Blender doesn't need installation. You can just download from its [website]("https://www.blender.org/download/Blender2.82/blender-2.82a-linux64.tar.xz/"). It is already compiled. Open the folder and click the blender binary, that's it. It also provides a desktop launcher if you want (need editing to get the correct path)

---

### Post by lazyteddy on 2020-05-30
> **monkeybrain20122 said:**
> Blender doesn't need installation. You can just download from its [website]("https://www.blender.org/download/Blender2.82/blender-2.82a-linux64.tar.xz/"). It is already compiled. Open the folder and click the blender binary, that's it. It also provides a desktop launcher if you want (need editing to get the correct path)
Interesting. Running this binary, it *does* work. So it must be something related to the Ubuntu packages.

I'll just use that for now, and try and find a place to report a bug.

Thanks!

---

