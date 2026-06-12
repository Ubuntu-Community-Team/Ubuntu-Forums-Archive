---
title: "Updating OpenGL/installing s3tc"
date: 2007-01-12
forum: Multimedia &amp; Video
---

### Post by kombucha on 2007-01-12
I'm using a Radeon 9000 with the open-source drivers, aiglx and mesa, based on this walkthrough: [https://help.ubuntu.com/community/RadeonDriver#head-363954c23963c39e3a7d633c7ad8667c8e0949c9](https://help.ubuntu.com/community/RadeonDriver#head-363954c23963c39e3a7d633c7ad8667c8e0949c9) and then reinstalling Mesa through Synaptic. Apparently this provided OpenGL 1.3, which is quite old, from what I can tell. In particular, I'm trying to enable 3D in VMWare, which needs OpenGL 1.4 or later (or so I've read).

Actually, if I look closer at my log and at Mesa's site, I notice the log's specific problem:
> Jan 12 14:46:54: mks| GlBackend: Missing requiredextension GL_EXT_texture_compression_s3tc
Jan 12 14:46:54: mks| GlBackend: Missing extension GL_NV_texture_shader 
refers to an extension the Mesa FAQ reports as excluded due to IP issues. I'm not sure about the second... maybe they are related?

So I follow the link about how to implement this extension from the Mesa FAQ ([http://homepage.hispeed.ch/rscheidegger/dri_experimental/s3tc_index.html](http://homepage.hispeed.ch/rscheidegger/dri_experimental/s3tc_index.html)) and that site says "Mesa now supports s3tc". True story? If not, should I download the tar from that page and compile it? Or does that risk screwing up my system?

Thanks for the help, I'm open to any and all suggestions about how to remedy this.

---

### Post by kombucha on 2007-01-13
Also, I fired up Blender for the first time today, and the screen leaks. When I move my mouse around, the window underneath shows through in various sections, and it is generally fairly screwy. Any ideas on how to fix that? That must be another OpenGL issue, since that's how the GUI of Blender is rendered.

---

### Post by kombucha on 2007-01-14
I think perhaps OpenGL overall is running poorly; running PPRacer, things kept flashing through, especially in one place that was like a 1-cm think horizontal line 70% of the way up my screen. Trying to configure Celestia, the rendering bled through the windows and menus. Is there a way I can legitimately test what is going on? If it matters, I've been getting the "3D driver claims to not support visual 0x4b" regularly, but I'm ignoring it...
I'd love some ideas.

---

### Post by kombucha on 2007-01-15
I tried to install Mesa 6.5.2 again, but cannot for the life of me find a binary, and I still can't compile it (I get a crazy amount of errors). Any other means of updating it? The one in the Edgy repositories is outdated... or are there other non-Mesa methods of implementing OpenGL that will use version 1.4 or higher?

---

### Post by mysticmarks on 2007-01-16
nv texture shader is calling out for a nvidia card. try subbing appropriate ati info for that, as to where to find it, can't help with that. Sorry!

---

