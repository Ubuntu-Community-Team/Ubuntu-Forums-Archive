---
title: "avidemux2_cli ( avidemux 2.5.6) crashes in 13.10 x64"
date: 2013-12-15
forum: Multimedia Software
---

### Post by lilrabbit129 on 2013-12-15
Hello,

I'm getting a crash whenever I run avidemux2_cli ( the cli version of avidemux) in Ubuntu 13.10. The QT4 version works fine. Here is the backtrace:

```
[Filters] Registered filter /usr/lib/ADM_plugins/videoFilter//libADM_vf_smartPalShift.so as PAL smart

*********** BACKTRACK **************
/usr/lib/libADM_core.so(ADM_backTrack+0x5c) [0x7fb13a2845dc]:0:<ADM_backTrack>:-2
/lib/x86_64-linux-gnu/libc.so.6(+0x36ff0) [0x7fb138705ff0]:1:<>:-2
/lib/x86_64-linux-gnu/libc.so.6(+0x144bc6) [0x7fb138813bc6]:2:<>:-2
/lib/x86_64-linux-gnu/libglib-2.0.so.0(g_str_equal+0x9) [0x7fb134a519b9]:3:<g_str_equal>:-2
/lib/x86_64-linux-gnu/libglib-2.0.so.0(g_hash_table_lookup+0xb0) [0x7fb134a510e0]:4:<g_hash_table_lookup>:-2
/lib/x86_64-linux-gnu/libglib-2.0.so.0(g_quark_from_static_string+0x30) [0x7fb134a70af0]:5:<g_quark_from_static_string>:-2
/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(+0xb37c) [0x7fb132e4a37c]:6:<>:-2
/lib64/ld-linux-x86-64.so.2(+0xf856) [0x7fb13bdc7856]:7:<>:-2
/lib64/ld-linux-x86-64.so.2(+0xf910) [0x7fb13bdc7910]:8:<>:-2
/lib64/ld-linux-x86-64.so.2(+0x13fdf) [0x7fb13bdcbfdf]:9:<>:-2
/lib64/ld-linux-x86-64.so.2(+0xf6e6) [0x7fb13bdc76e6]:10:<>:-2
/lib64/ld-linux-x86-64.so.2(+0x13809) [0x7fb13bdcb809]:11:<>:-2
/lib/x86_64-linux-gnu/libdl.so.2(+0x1026) [0x7fb1382b3026]:12:<>:-2
/lib64/ld-linux-x86-64.so.2(+0xf6e6) [0x7fb13bdc76e6]:13:<>:-2
/lib/x86_64-linux-gnu/libdl.so.2(+0x163c) [0x7fb1382b363c]:14:<>:-2
/lib/x86_64-linux-gnu/libdl.so.2(dlopen+0x31) [0x7fb1382b30c1]:15:<dlopen>:-2
/usr/lib/libADM_core.so(_ZN14ADM_LibWrapper11loadLibraryEPKc+0x21) [0x7fb13a2844d1]:16:<ADM_LibWrapper::loadLibrary(char const*)>:0
avidemux2_cli(_Z18ADM_vf_loadPluginsPKc+0x115) [0x46d8c5]:17:<ADM_vf_loadPlugins(char const*)>:0
avidemux2_cli(main+0x209) [0x444809]:18:<main>:-2
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xf5) [0x7fb1386f0de5]:19:<__libc_start_main>:-2
*********** BACKTRACK **************
```

Any help would be greatly appreciated!

Thanks!

---

