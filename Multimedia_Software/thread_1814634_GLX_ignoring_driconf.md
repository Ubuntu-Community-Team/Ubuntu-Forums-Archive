---
title: "GLX ignoring driconf?"
date: 2011-07-29
forum: Multimedia Software
---

### Post by keelx on 2011-07-29
I used driconf, to turn off vsync, and it worked at first, but after I restarted my computer, vsync turned back on. I checked the ~/.drirc, and this is it:
[HTML]<driconf>
    <device screen="0" driver="i945">
        <application name="Default">
            <option name="force_s3tc_enable" value="true" />
            <option name="no_rast" value="false" />
            <option name="vblank_mode" value="0" />
            <option name="always_flush_cache" value="false" />
            <option name="stub_occlusion_query" value="false" />
            <option name="always_flush_batch" value="false" />
            <option name="bo_reuse" value="1" />
            <option name="texture_tiling" value="true" />
            <option name="early_z" value="false" />
            <option name="allow_large_textures" value="2" />
            <option name="fragment_shader" value="true" />
        </application>
    </device>
    <device screen="0" driver="i915">
        <application name="Default">
            <option name="force_s3tc_enable" value="true" />
            <option name="no_rast" value="false" />
            <option name="always_flush_cache" value="true" />
            <option name="early_z" value="false" />
            <option name="stub_occlusion_query" value="false" />
            <option name="always_flush_batch" value="false" />
            <option name="bo_reuse" value="1" />
            <option name="texture_tiling" value="true" />
            <option name="vblank_mode" value="0" />
            <option name="allow_large_textures" value="2" />
            <option name="fragment_shader" value="true" />
        </application>
    </device>
</driconf>[/HTML]

As you can see, vsync is turned off. But when I run any application that takes 3d opengl, the framerate is limited to 60, and I get terrible choppiness and inconsistency (This is common when I have vsync on). The only way I can turn vsync off is to place <option name="vblank_mode" value="0" /> at the very top of the file, outside of everything. But this results in a crash when I run driconf, saying: 
```

Configuration file "~/.drirc" contains errors:
option outside an application

```

So my question is, how can i get glx to configure itself based on the contents of .drirc? Without having anything outside of the application?

---

