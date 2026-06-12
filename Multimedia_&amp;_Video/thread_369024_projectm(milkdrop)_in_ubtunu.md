---
title: "projectm(milkdrop) in ubtunu"
date: 2007-02-24
forum: Multimedia &amp; Video
---

### Post by TheDigitalNinja on 2007-02-24
Iv been trying for about an hour to get ProjectM (the milkdrop port to linux) working on my computer. I got the prerequisites installed. but now I'm getting a compiling error.
This is the error Anyone know how to fix this?
```

rperkins@Russell-desktop:~/Download/libprojectM$ make
make  all-recursive
make[1]: Entering directory `/home/rperkins/Download/libprojectM'
Making all in src
make[2]: Entering directory `/home/rperkins/Download/libprojectM/src'
if /bin/bash ../libtool --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I..    -DLINUX -D__CPLUSPLUS -pthread -I/usr/include/FTGL -I/usr/include/freetype2   -g -O2 -MT beat_detect.lo -MD -MP -MF ".deps/beat_detect.Tpo" -c -o beat_detect.lo beat_detect.cc; \
        then mv -f ".deps/beat_detect.Tpo" ".deps/beat_detect.Plo"; else rm -f ".deps/beat_detect.Tpo"; exit 1; fi
 g++ -DHAVE_CONFIG_H -I. -I. -I.. -DLINUX -D__CPLUSPLUS -pthread -I/usr/include/FTGL -I/usr/include/freetype2 -g -O2 -MT beat_detect.lo -MD -MP -MF .deps/beat_detect.Tpo -c beat_detect.cc  -fPIC -DPIC -o .libs/beat_detect.o
In file included from pbuffer.h:42,
                 from projectM.h:54,
                 from beat_detect.cc:31:
/usr/include/GL/glx.h:38:22: error: X11/Xlib.h: No such file or directory
/usr/include/GL/glx.h:39:23: error: X11/Xutil.h: No such file or directory
/usr/include/GL/glx.h:179: error: 'XID' does not name a type
/usr/include/GL/glx.h:180: error: 'XID' does not name a type
/usr/include/GL/glx.h:183: error: 'XID' does not name a type
/usr/include/GL/glx.h:184: error: 'XID' does not name a type
/usr/include/GL/glx.h:185: error: 'XID' does not name a type
/usr/include/GL/glx.h:186: error: 'XID' does not name a type
/usr/include/GL/glx.h:190: error: expected initializer before '*' token
/usr/include/GL/glx.h:193: error: 'Display' was not declared in this scope
/usr/include/GL/glx.h:193: error: 'dpy' was not declared in this scope
/usr/include/GL/glx.h:193: error: 'XVisualInfo' was not declared in this scope
/usr/include/GL/glx.h:193: error: 'vis' was not declared in this scope
/usr/include/GL/glx.h:194: error: expected primary-expression before 'shareList'
/usr/include/GL/glx.h:194: error: 'Bool' was not declared in this scope
/usr/include/GL/glx.h:194: error: initializer expression list treated as compound expression
/usr/include/GL/glx.h:196: error: variable or field 'glXDestroyContext' declared void
/usr/include/GL/glx.h:196: error: 'Display' was not declared in this scope
/usr/include/GL/glx.h:196: error: 'dpy' was not declared in this scope
/usr/include/GL/glx.h:196: error: expected primary-expression before 'ctx'
/usr/include/GL/glx.h:196: error: initializer expression list treated as compound expression
/usr/include/GL/glx.h:198: error: 'Bool' does not name a type
/usr/include/GL/glx.h:201: error: variable or field 'glXCopyContext' declared void
/usr/include/GL/glx.h:201: error: 'Display' was not declared in this scope
/usr/include/GL/glx.h:201: error: 'dpy' was not declared in this scope
/usr/include/GL/glx.h:201: error: expected primary-expression before 'src'
/usr/include/GL/glx.h:201: error: expected primary-expression before 'dst'
/usr/include/GL/glx.h:202: error: expected primary-expression before 'unsigned'
/usr/include/GL/glx.h:202: error: initializer expression list treated as compound expression
/usr/include/GL/glx.h:204: error: variable or field 'glXSwapBuffers' declared void
/usr/include/GL/glx.h:204: error: 'Display' was not declared in this scope
/usr/include/GL/glx.h:204: error: 'dpy' was not declared in this scope
/usr/include/GL/glx.h:204: error: 'GLXDrawable' was not declared in this scope
/usr/include/GL/glx.h:204: error: initializer expression list treated as compound expression
/usr/include/GL/glx.h:206: error: 'GLXPixmap' does not name a type
/usr/include/GL/glx.h:209: error: variable or field 'glXDestroyGLXPixmap' declared void
/usr/include/GL/glx.h:209: error: 'Display' was not declared in this scope
/usr/include/GL/glx.h:209: error: 'dpy' was not declared in this scope
/usr/include/GL/glx.h:209: error: 'GLXPixmap' was not declared in this scope
/usr/include/GL/glx.h:209: error: initializer expression list treated as compound expression
/usr/include/GL/glx.h:211: error: 'Bool' does not name a type
/usr/include/GL/glx.h:213: error: 'Bool' does not name a type
/usr/include/GL/glx.h:215: error: 'Bool' does not name a type
/usr/include/GL/glx.h:217: error: 'Display' was not declared in this scope
/usr/include/GL/glx.h:217: error: 'dpy' was not declared in this scope
/usr/include/GL/glx.h:217: error: 'XVisualInfo' was not declared in this scope
/usr/include/GL/glx.h:217: error: 'visual' was not declared in this scope
/usr/include/GL/glx.h:218: error: expected primary-expression before 'int'
/usr/include/GL/glx.h:218: error: expected primary-expression before 'int'
/usr/include/GL/glx.h:218: error: initializer expression list treated as compound expression
/usr/include/GL/glx.h:222: error: 'GLXDrawable' does not name a type
/usr/include/GL/glx.h:228: error: variable or field 'glXUseXFont' declared void
/usr/include/GL/glx.h:228: error: 'Font' was not declared in this scope
/usr/include/GL/glx.h:228: error: expected primary-expression before 'int'
/usr/include/GL/glx.h:228: error: expected primary-expression before 'int'
/usr/include/GL/glx.h:228: error: expected primary-expression before 'int'
/usr/include/GL/glx.h:228: error: initializer expression list treated as compound expression
/usr/include/GL/glx.h:233: error: 'Display' was not declared in this scope
/usr/include/GL/glx.h:233: error: 'dpy' was not declared in this scope
/usr/include/GL/glx.h:233: error: expected primary-expression before 'int'
/usr/include/GL/glx.h:233: error: initializer expression list treated as compound expression
/usr/include/GL/glx.h:235: error: 'Display' was not declared in this scope
/usr/include/GL/glx.h:235: error: 'dpy' was not declared in this scope
/usr/include/GL/glx.h:235: error: expected primary-expression before 'int'
/usr/include/GL/glx.h:235: error: expected primary-expression before 'int'
/usr/include/GL/glx.h:235: error: initializer expression list treated as compound expression
/usr/include/GL/glx.h:237: error: 'Display' was not declared in this scope
/usr/include/GL/glx.h:237: error: 'dpy' was not declared in this scope
/usr/include/GL/glx.h:237: error: expected primary-expression before 'int'
/usr/include/GL/glx.h:237: error: initializer expression list treated as compound expression
/usr/include/GL/glx.h:241: error: expected initializer before '*' token
/usr/include/GL/glx.h:245: error: 'Display' was not declared in this scope
/usr/include/GL/glx.h:245: error: 'dpy' was not declared in this scope
/usr/include/GL/glx.h:245: error: expected primary-expression before 'int'
/usr/include/GL/glx.h:246: error: expected primary-expression before 'const'
/usr/include/GL/glx.h:246: error: expected primary-expression before 'int'
/usr/include/GL/glx.h:246: error: initializer expression list treated as compound expression
/usr/include/GL/glx.h:248: error: 'Display' was not declared in this scope
/usr/include/GL/glx.h:248: error: 'dpy' was not declared in this scope
/usr/include/GL/glx.h:248: error: expected primary-expression before 'config'
/usr/include/GL/glx.h:249: error: expected primary-expression before 'int'
/usr/include/GL/glx.h:249: error: expected primary-expression before 'int'
/usr/include/GL/glx.h:249: error: initializer expression list treated as compound expression
/usr/include/GL/glx.h:251: error: 'Display' was not declared in this scope
/usr/include/GL/glx.h:251: error: 'dpy' was not declared in this scope
/usr/include/GL/glx.h:251: error: expected primary-expression before 'int'
/usr/include/GL/glx.h:252: error: expected primary-expression before 'int'
/usr/include/GL/glx.h:252: error: initializer expression list treated as compound expression
/usr/include/GL/glx.h:254: error: expected initializer before '*' token
/usr/include/GL/glx.h:257: error: 'GLXWindow' does not name a type
/usr/include/GL/glx.h:260: error: variable or field 'glXDestroyWindow' declared void
/usr/include/GL/glx.h:260: error: 'Display' was not declared in this scope
/usr/include/GL/glx.h:260: error: 'dpy' was not declared in this scope
/usr/include/GL/glx.h:260: error: 'GLXWindow' was not declared in this scope
/usr/include/GL/glx.h:260: error: initializer expression list treated as compound expression
/usr/include/GL/glx.h:262: error: 'GLXPixmap' does not name a type
/usr/include/GL/glx.h:265: error: variable or field 'glXDestroyPixmap' declared void
/usr/include/GL/glx.h:265: error: 'Display' was not declared in this scope
/usr/include/GL/glx.h:265: error: 'dpy' was not declared in this scope
/usr/include/GL/glx.h:265: error: 'GLXPixmap' was not declared in this scope
/usr/include/GL/glx.h:265: error: initializer expression list treated as compound expression
/usr/include/GL/glx.h:267: error: 'GLXPbuffer' does not name a type
/usr/include/GL/glx.h:270: error: variable or field 'glXDestroyPbuffer' declared void
/usr/include/GL/glx.h:270: error: 'Display' was not declared in this scope
/usr/include/GL/glx.h:270: error: 'dpy' was not declared in this scope
/usr/include/GL/glx.h:270: error: 'GLXPbuffer' was not declared in this scope
/usr/include/GL/glx.h:270: error: initializer expression list treated as compound expression
/usr/include/GL/glx.h:272: error: variable or field 'glXQueryDrawable' declared void
/usr/include/GL/glx.h:272: error: 'Display' was not declared in this scope
/usr/include/GL/glx.h:272: error: 'dpy' was not declared in this scope
/usr/include/GL/glx.h:272: error: 'GLXDrawable' was not declared in this scope
/usr/include/GL/glx.h:272: error: expected primary-expression before 'int'
/usr/include/GL/glx.h:273: error: expected primary-expression before 'unsigned'
/usr/include/GL/glx.h:273: error: initializer expression list treated as compound expression
/usr/include/GL/glx.h:275: error: 'Display' was not declared in this scope
/usr/include/GL/glx.h:275: error: 'dpy' was not declared in this scope
/usr/include/GL/glx.h:275: error: expected primary-expression before 'config'
/usr/include/GL/glx.h:276: error: expected primary-expression before 'int'
/usr/include/GL/glx.h:276: error: expected primary-expression before 'shareList'
/usr/include/GL/glx.h:277: error: 'Bool' was not declared in this scope
/usr/include/GL/glx.h:277: error: initializer expression list treated as compound expression
/usr/include/GL/glx.h:279: error: 'Bool' does not name a type
/usr/include/GL/glx.h:282: error: 'GLXDrawable' does not name a type
/usr/include/GL/glx.h:284: error: 'Display' was not declared in this scope
/usr/include/GL/glx.h:284: error: 'dpy' was not declared in this scope
/usr/include/GL/glx.h:284: error: expected primary-expression before 'ctx'
/usr/include/GL/glx.h:284: error: expected primary-expression before 'int'
/usr/include/GL/glx.h:285: error: expected primary-expression before 'int'
/usr/include/GL/glx.h:285: error: initializer expression list treated as compound expression
/usr/include/GL/glx.h:287: error: variable or field 'glXSelectEvent' declared void
/usr/include/GL/glx.h:287: error: 'Display' was not declared in this scope
/usr/include/GL/glx.h:287: error: 'dpy' was not declared in this scope
/usr/include/GL/glx.h:287: error: 'GLXDrawable' was not declared in this scope
/usr/include/GL/glx.h:288: error: expected primary-expression before 'unsigned'
/usr/include/GL/glx.h:288: error: initializer expression list treated as compound expression
/usr/include/GL/glx.h:290: error: variable or field 'glXGetSelectedEvent' declared void
/usr/include/GL/glx.h:290: error: 'Display' was not declared in this scope
/usr/include/GL/glx.h:290: error: 'dpy' was not declared in this scope
/usr/include/GL/glx.h:290: error: 'GLXDrawable' was not declared in this scope
/usr/include/GL/glx.h:291: error: expected primary-expression before 'unsigned'
/usr/include/GL/glx.h:291: error: initializer expression list treated as compound expression
/usr/include/GL/glxext.h:309: error: 'XID' does not name a type
/usr/include/GL/glxext.h:313: error: 'XID' does not name a type
/usr/include/GL/glxext.h:318: error: 'XID' does not name a type
/usr/include/GL/glxext.h:322: error: 'Bool' does not name a type
/usr/include/GL/glxext.h:323: error: expected ';' before '*' token
/usr/include/GL/glxext.h:324: error: 'GLXDrawable' does not name a type
/usr/include/GL/glxext.h:448: error: typedef 'Bool' is initialized (use __typeof__ instead)
/usr/include/GL/glxext.h:448: error: 'PFNGLXMAKECURRENTREADSGIPROC' was not declared in this scope
/usr/include/GL/glxext.h:449: error: typedef 'GLXDrawable' is initialized (use __typeof__ instead)
/usr/include/GL/glxext.h:449: error: 'PFNGLXGETCURRENTREADDRAWABLESGIPROC' was not declared in this scope
/usr/include/GL/glxext.h:477: error: expected initializer before '*' token
/usr/include/GL/glxext.h:478: error: typedef 'PFNGLXQUERYCONTEXTINFOEXTPROC' is initialized (use __typeof__ instead)
/usr/include/GL/glxext.h:478: error: 'Display' was not declared in this scope
/usr/include/GL/glxext.h:478: error: 'dpy' was not declared in this scope
/usr/include/GL/glxext.h:478: error: expected primary-expression before 'context'
/usr/include/GL/glxext.h:478: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:478: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:479: error: typedef 'GLXContextID' is initialized (use __typeof__ instead)
/usr/include/GL/glxext.h:479: error: 'PFNGLXGETCONTEXTIDEXTPROC' was not declared in this scope
/usr/include/GL/glxext.h:480: error: typedef 'PFNGLXIMPORTCONTEXTEXTPROC' is initialized (use __typeof__ instead)
/usr/include/GL/glxext.h:480: error: 'Display' was not declared in this scope
/usr/include/GL/glxext.h:480: error: 'dpy' was not declared in this scope
/usr/include/GL/glxext.h:480: error: 'GLXContextID' was not declared in this scope
/usr/include/GL/glxext.h:481: error: typedef 'PFNGLXFREECONTEXTEXTPROC' is initialized (use __typeof__ instead)
/usr/include/GL/glxext.h:481: error: 'Display' was not declared in this scope
/usr/include/GL/glxext.h:481: error: 'dpy' was not declared in this scope
/usr/include/GL/glxext.h:481: error: expected primary-expression before 'context'
/usr/include/GL/glxext.h:494: error: typedef 'PFNGLXGETFBCONFIGATTRIBSGIXPROC' is initialized (use __typeof__ instead)
/usr/include/GL/glxext.h:494: error: 'Display' was not declared in this scope
/usr/include/GL/glxext.h:494: error: 'dpy' was not declared in this scope
/usr/include/GL/glxext.h:494: error: expected primary-expression before 'config'
/usr/include/GL/glxext.h:494: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:494: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:495: error: typedef 'PFNGLXCHOOSEFBCONFIGSGIXPROC' is initialized (use __typeof__ instead)
/usr/include/GL/glxext.h:495: error: 'Display' was not declared in this scope
/usr/include/GL/glxext.h:495: error: 'dpy' was not declared in this scope
/usr/include/GL/glxext.h:495: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:495: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:495: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:496: error: typedef 'GLXPixmap' is initialized (use __typeof__ instead)
/usr/include/GL/glxext.h:496: error: 'PFNGLXCREATEGLXPIXMAPWITHCONFIGSGIXPROC' was not declared in this scope
/usr/include/GL/glxext.h:497: error: typedef 'PFNGLXCREATECONTEXTWITHCONFIGSGIXPROC' is initialized (use __typeof__ instead)
/usr/include/GL/glxext.h:497: error: 'Display' was not declared in this scope
/usr/include/GL/glxext.h:497: error: 'dpy' was not declared in this scope
/usr/include/GL/glxext.h:497: error: expected primary-expression before 'config'
/usr/include/GL/glxext.h:497: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:497: error: expected primary-expression before 'share_list'
/usr/include/GL/glxext.h:497: error: 'Bool' was not declared in this scope
/usr/include/GL/glxext.h:498: error: expected initializer before '*' token
/usr/include/GL/glxext.h:499: error: typedef 'PFNGLXGETFBCONFIGFROMVISUALSGIXPROC' is initialized (use __typeof__ instead)
/usr/include/GL/glxext.h:499: error: 'Display' was not declared in this scope
/usr/include/GL/glxext.h:499: error: 'dpy' was not declared in this scope
/usr/include/GL/glxext.h:499: error: 'XVisualInfo' was not declared in this scope
/usr/include/GL/glxext.h:499: error: 'vis' was not declared in this scope
/usr/include/GL/glxext.h:511: error: typedef 'GLXPbufferSGIX' is initialized (use __typeof__ instead)
/usr/include/GL/glxext.h:511: error: 'PFNGLXCREATEGLXPBUFFERSGIXPROC' was not declared in this scope
/usr/include/GL/glxext.h:512: error: typedef 'PFNGLXDESTROYGLXPBUFFERSGIXPROC' is initialized (use __typeof__ instead)
/usr/include/GL/glxext.h:512: error: 'Display' was not declared in this scope
/usr/include/GL/glxext.h:512: error: 'dpy' was not declared in this scope
/usr/include/GL/glxext.h:512: error: 'GLXPbufferSGIX' was not declared in this scope
/usr/include/GL/glxext.h:513: error: typedef 'PFNGLXQUERYGLXPBUFFERSGIXPROC' is initialized (use __typeof__ instead)
/usr/include/GL/glxext.h:513: error: 'Display' was not declared in this scope
/usr/include/GL/glxext.h:513: error: 'dpy' was not declared in this scope
/usr/include/GL/glxext.h:513: error: 'GLXPbufferSGIX' was not declared in this scope
/usr/include/GL/glxext.h:513: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:513: error: expected primary-expression before 'unsigned'
/usr/include/GL/glxext.h:514: error: typedef 'PFNGLXSELECTEVENTSGIXPROC' is initialized (use __typeof__ instead)
/usr/include/GL/glxext.h:514: error: 'Display' was not declared in this scope
/usr/include/GL/glxext.h:514: error: 'dpy' was not declared in this scope
/usr/include/GL/glxext.h:514: error: 'GLXDrawable' was not declared in this scope
/usr/include/GL/glxext.h:514: error: expected primary-expression before 'unsigned'
/usr/include/GL/glxext.h:515: error: typedef 'PFNGLXGETSELECTEDEVENTSGIXPROC' is initialized (use __typeof__ instead)
/usr/include/GL/glxext.h:515: error: 'Display' was not declared in this scope
/usr/include/GL/glxext.h:515: error: 'dpy' was not declared in this scope
/usr/include/GL/glxext.h:515: error: 'GLXDrawable' was not declared in this scope
/usr/include/GL/glxext.h:515: error: expected primary-expression before 'unsigned'
/usr/include/GL/glxext.h:523: error: typedef 'PFNGLXCUSHIONSGIPROC' is initialized (use __typeof__ instead)
/usr/include/GL/glxext.h:523: error: 'Display' was not declared in this scope
/usr/include/GL/glxext.h:523: error: 'dpy' was not declared in this scope
/usr/include/GL/glxext.h:523: error: 'Window' was not declared in this scope
/usr/include/GL/glxext.h:523: error: expected primary-expression before 'float'
/usr/include/GL/glxext.h:535: error: typedef 'PFNGLXBINDCHANNELTOWINDOWSGIXPROC' is initialized (use __typeof__ instead)
/usr/include/GL/glxext.h:535: error: 'Display' was not declared in this scope
/usr/include/GL/glxext.h:535: error: 'display' was not declared in this scope
/usr/include/GL/glxext.h:535: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:535: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:535: error: 'Window' was not declared in this scope
/usr/include/GL/glxext.h:536: error: typedef 'PFNGLXCHANNELRECTSGIXPROC' is initialized (use __typeof__ instead)
/usr/include/GL/glxext.h:536: error: 'Display' was not declared in this scope
/usr/include/GL/glxext.h:536: error: 'display' was not declared in this scope
/usr/include/GL/glxext.h:536: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:536: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:536: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:536: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:536: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:536: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:537: error: typedef 'PFNGLXQUERYCHANNELRECTSGIXPROC' is initialized (use __typeof__ instead)
/usr/include/GL/glxext.h:537: error: 'Display' was not declared in this scope
/usr/include/GL/glxext.h:537: error: 'display' was not declared in this scope
/usr/include/GL/glxext.h:537: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:537: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:537: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:537: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:537: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:537: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:538: error: typedef 'PFNGLXQUERYCHANNELDELTASSGIXPROC' is initialized (use __typeof__ instead)
/usr/include/GL/glxext.h:538: error: 'Display' was not declared in this scope
/usr/include/GL/glxext.h:538: error: 'display' was not declared in this scope
/usr/include/GL/glxext.h:538: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:538: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:538: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:538: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:538: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:538: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:539: error: typedef 'PFNGLXCHANNELRECTSYNCSGIXPROC' is initialized (use __typeof__ instead)
/usr/include/GL/glxext.h:539: error: 'Display' was not declared in this scope
/usr/include/GL/glxext.h:539: error: 'display' was not declared in this scope
/usr/include/GL/glxext.h:539: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:539: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:539: error: expected primary-expression before 'synctype'
/usr/include/GL/glxext.h:557: error: typedef 'PFNGLXJOINSWAPGROUPSGIXPROC' is initialized (use __typeof__ instead)
/usr/include/GL/glxext.h:557: error: 'Display' was not declared in this scope
/usr/include/GL/glxext.h:557: error: 'dpy' was not declared in this scope
/usr/include/GL/glxext.h:557: error: 'GLXDrawable' was not declared in this scope
/usr/include/GL/glxext.h:557: error: 'GLXDrawable' was not declared in this scope
/usr/include/GL/glxext.h:566: error: typedef 'PFNGLXBINDSWAPBARRIERSGIXPROC' is initialized (use __typeof__ instead)
/usr/include/GL/glxext.h:566: error: 'Display' was not declared in this scope
/usr/include/GL/glxext.h:566: error: 'dpy' was not declared in this scope
/usr/include/GL/glxext.h:566: error: 'GLXDrawable' was not declared in this scope
/usr/include/GL/glxext.h:566: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:567: error: typedef 'Bool' is initialized (use __typeof__ instead)
/usr/include/GL/glxext.h:567: error: 'PFNGLXQUERYMAXSWAPBARRIERSSGIXPROC' was not declared in this scope
/usr/include/GL/glxext.h:575: error: typedef 'Status' is initialized (use __typeof__ instead)
/usr/include/GL/glxext.h:575: error: 'PFNGLXGETTRANSPARENTINDEXSUNPROC' was not declared in this scope
/usr/include/GL/glxext.h:583: error: typedef 'PFNGLXCOPYSUBBUFFERMESAPROC' is initialized (use __typeof__ instead)
/usr/include/GL/glxext.h:583: error: 'Display' was not declared in this scope
/usr/include/GL/glxext.h:583: error: 'dpy' was not declared in this scope
/usr/include/GL/glxext.h:583: error: 'GLXDrawable' was not declared in this scope
/usr/include/GL/glxext.h:583: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:583: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:583: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:583: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:591: error: typedef 'GLXPixmap' is initialized (use __typeof__ instead)
/usr/include/GL/glxext.h:591: error: 'PFNGLXCREATEGLXPIXMAPMESAPROC' was not declared in this scope
/usr/include/GL/glxext.h:599: error: typedef 'Bool' is initialized (use __typeof__ instead)
/usr/include/GL/glxext.h:599: error: 'PFNGLXRELEASEBUFFERSMESAPROC' was not declared in this scope
/usr/include/GL/glxext.h:607: error: typedef 'Bool' is initialized (use __typeof__ instead)
/usr/include/GL/glxext.h:607: error: 'PFNGLXSET3DFXMODEMESAPROC' was not declared in this scope
/usr/include/GL/glxext.h:627: error: typedef 'Bool' is initialized (use __typeof__ instead)
/usr/include/GL/glxext.h:627: error: 'PFNGLXGETSYNCVALUESOMLPROC' was not declared in this scope
/usr/include/GL/glxext.h:628: error: typedef 'Bool' is initialized (use __typeof__ instead)
/usr/include/GL/glxext.h:628: error: 'PFNGLXGETMSCRATEOMLPROC' was not declared in this scope
/usr/include/GL/glxext.h:629: error: typedef 'PFNGLXSWAPBUFFERSMSCOMLPROC' is initialized (use __typeof__ instead)
/usr/include/GL/glxext.h:629: error: 'Display' was not declared in this scope
/usr/include/GL/glxext.h:629: error: 'dpy' was not declared in this scope
/usr/include/GL/glxext.h:629: error: 'GLXDrawable' was not declared in this scope
/usr/include/GL/glxext.h:629: error: expected primary-expression before 'target_msc'
/usr/include/GL/glxext.h:629: error: expected primary-expression before 'divisor'
/usr/include/GL/glxext.h:629: error: expected primary-expression before 'remainder'
/usr/include/GL/glxext.h:630: error: typedef 'Bool' is initialized (use __typeof__ instead)
/usr/include/GL/glxext.h:630: error: 'PFNGLXWAITFORMSCOMLPROC' was not declared in this scope
/usr/include/GL/glxext.h:631: error: typedef 'Bool' is initialized (use __typeof__ instead)
/usr/include/GL/glxext.h:631: error: 'PFNGLXWAITFORSBCOMLPROC' was not declared in this scope
/usr/include/GL/glxext.h:671: error: typedef 'PFNGLXQUERYHYPERPIPENETWORKSGIXPROC' is initialized (use __typeof__ instead)
/usr/include/GL/glxext.h:671: error: 'Display' was not declared in this scope
/usr/include/GL/glxext.h:671: error: 'dpy' was not declared in this scope
/usr/include/GL/glxext.h:671: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:672: error: typedef 'PFNGLXHYPERPIPECONFIGSGIXPROC' is initialized (use __typeof__ instead)
/usr/include/GL/glxext.h:672: error: 'Display' was not declared in this scope
/usr/include/GL/glxext.h:672: error: 'dpy' was not declared in this scope
/usr/include/GL/glxext.h:672: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:672: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:672: error: expected primary-expression before '*' token
/usr/include/GL/glxext.h:672: error: 'cfg' was not declared in this scope
/usr/include/GL/glxext.h:672: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:673: error: typedef 'PFNGLXQUERYHYPERPIPECONFIGSGIXPROC' is initialized (use __typeof__ instead)
/usr/include/GL/glxext.h:673: error: 'Display' was not declared in this scope
/usr/include/GL/glxext.h:673: error: 'dpy' was not declared in this scope
/usr/include/GL/glxext.h:673: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:673: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:674: error: typedef 'PFNGLXDESTROYHYPERPIPECONFIGSGIXPROC' is initialized (use __typeof__ instead)
/usr/include/GL/glxext.h:674: error: 'Display' was not declared in this scope
/usr/include/GL/glxext.h:674: error: 'dpy' was not declared in this scope
/usr/include/GL/glxext.h:674: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:675: error: typedef 'PFNGLXBINDHYPERPIPESGIXPROC' is initialized (use __typeof__ instead)
/usr/include/GL/glxext.h:675: error: 'Display' was not declared in this scope
/usr/include/GL/glxext.h:675: error: 'dpy' was not declared in this scope
/usr/include/GL/glxext.h:675: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:676: error: typedef 'PFNGLXQUERYHYPERPIPEBESTATTRIBSGIXPROC' is initialized (use __typeof__ instead)
/usr/include/GL/glxext.h:676: error: 'Display' was not declared in this scope
/usr/include/GL/glxext.h:676: error: 'dpy' was not declared in this scope
/usr/include/GL/glxext.h:676: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:676: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:676: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:676: error: expected primary-expression before 'void'
/usr/include/GL/glxext.h:676: error: expected primary-expression before 'void'
/usr/include/GL/glxext.h:677: error: typedef 'PFNGLXHYPERPIPEATTRIBSGIXPROC' is initialized (use __typeof__ instead)
/usr/include/GL/glxext.h:677: error: 'Display' was not declared in this scope
/usr/include/GL/glxext.h:677: error: 'dpy' was not declared in this scope
/usr/include/GL/glxext.h:677: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:677: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:677: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:677: error: expected primary-expression before 'void'
/usr/include/GL/glxext.h:678: error: typedef 'PFNGLXQUERYHYPERPIPEATTRIBSGIXPROC' is initialized (use __typeof__ instead)
/usr/include/GL/glxext.h:678: error: 'Display' was not declared in this scope
/usr/include/GL/glxext.h:678: error: 'dpy' was not declared in this scope
/usr/include/GL/glxext.h:678: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:678: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:678: error: expected primary-expression before 'int'
/usr/include/GL/glxext.h:678: error: expected primary-expression before 'void'
/usr/include/GL/glx.h:347: error: 'Display' was not declared in this scope
/usr/include/GL/glx.h:347: error: 'dpy' was not declared in this scope
/usr/include/GL/glx.h:347: error: expected primary-expression before 'int'
/usr/include/GL/glx.h:347: error: expected primary-expression before 'size'
/usr/include/GL/glx.h:347: error: expected primary-expression before 'float'
/usr/include/GL/glx.h:347: error: expected primary-expression before 'float'
/usr/include/GL/glx.h:347: error: expected primary-expression before 'float'
/usr/include/GL/glx.h:347: error: initializer expression list treated as compound expression
/usr/include/GL/glx.h:348: error: variable or field 'glXFreeMemoryMESA' declared void
/usr/include/GL/glx.h:348: error: 'Display' was not declared in this scope
/usr/include/GL/glx.h:348: error: 'dpy' was not declared in this scope
/usr/include/GL/glx.h:348: error: expected primary-expression before 'int'
/usr/include/GL/glx.h:348: error: expected primary-expression before 'void'
/usr/include/GL/glx.h:348: error: initializer expression list treated as compound expression
/usr/include/GL/glx.h:349: error: 'Display' was not declared in this scope
/usr/include/GL/glx.h:349: error: 'dpy' was not declared in this scope
/usr/include/GL/glx.h:349: error: expected primary-expression before 'int'
/usr/include/GL/glx.h:349: error: expected primary-expression before 'const'
/usr/include/GL/glx.h:349: error: initializer expression list treated as compound expression
/usr/include/GL/glx.h:350: error: typedef 'PFNGLXALLOCATEMEMORYMESAPROC' is initialized (use __typeof__ instead)
/usr/include/GL/glx.h:350: error: 'Display' was not declared in this scope
/usr/include/GL/glx.h:350: error: 'dpy' was not declared in this scope
/usr/include/GL/glx.h:350: error: expected primary-expression before 'int'
/usr/include/GL/glx.h:350: error: expected primary-expression before 'size'
/usr/include/GL/glx.h:350: error: expected primary-expression before 'float'
/usr/include/GL/glx.h:350: error: expected primary-expression before 'float'
/usr/include/GL/glx.h:350: error: expected primary-expression before 'float'
/usr/include/GL/glx.h:351: error: typedef 'PFNGLXFREEMEMORYMESAPROC' is initialized (use __typeof__ instead)
/usr/include/GL/glx.h:351: error: 'Display' was not declared in this scope
/usr/include/GL/glx.h:351: error: 'dpy' was not declared in this scope
/usr/include/GL/glx.h:351: error: expected primary-expression before 'int'
/usr/include/GL/glx.h:351: error: expected primary-expression before 'void'
/usr/include/GL/glx.h:352: error: typedef 'PFNGLXGETMEMORYOFFSETMESAPROC' is initialized (use __typeof__ instead)
/usr/include/GL/glx.h:352: error: 'Display' was not declared in this scope
/usr/include/GL/glx.h:352: error: 'dpy' was not declared in this scope
/usr/include/GL/glx.h:352: error: expected primary-expression before 'int'
/usr/include/GL/glx.h:352: error: expected primary-expression before 'const'
/usr/include/GL/glx.h:364: error: 'Bool' does not name a type
/usr/include/GL/glx.h:365: error: 'Bool' does not name a type
/usr/include/GL/glx.h:366: error: 'Bool' does not name a type
/usr/include/GL/glx.h:389: error: 'Display' was not declared in this scope
/usr/include/GL/glx.h:389: error: 'dpy' was not declared in this scope
/usr/include/GL/glx.h:389: error: 'GLXDrawable' was not declared in this scope
/usr/include/GL/glx.h:389: error: expected primary-expression before 'float'
/usr/include/GL/glx.h:389: error: initializer expression list treated as compound expression
/usr/include/GL/glx.h:390: error: 'Display' was not declared in this scope
/usr/include/GL/glx.h:390: error: 'dpy' was not declared in this scope
/usr/include/GL/glx.h:390: error: 'GLXDrawable' was not declared in this scope
/usr/include/GL/glx.h:390: error: initializer expression list treated as compound expression
/usr/include/GL/glx.h:391: error: 'Display' was not declared in this scope
/usr/include/GL/glx.h:391: error: 'dpy' was not declared in this scope
/usr/include/GL/glx.h:391: error: 'GLXDrawable' was not declared in this scope
/usr/include/GL/glx.h:391: error: initializer expression list treated as compound expression
/usr/include/GL/glx.h:392: error: 'Display' was not declared in this scope
/usr/include/GL/glx.h:392: error: 'dpy' was not declared in this scope
/usr/include/GL/glx.h:392: error: 'GLXDrawable' was not declared in this scope
/usr/include/GL/glx.h:392: error: expected primary-expression before '*' token
/usr/include/GL/glx.h:392: error: 'swapCount' was not declared in this scope
/usr/include/GL/glx.h:392: error: expected primary-expression before '*' token
/usr/include/GL/glx.h:392: error: 'missedFrames' was not declared in this scope
/usr/include/GL/glx.h:392: error: expected primary-expression before 'float'
/usr/include/GL/glx.h:392: error: initializer expression list treated as compound expression
/usr/include/GL/glx.h:394: error: typedef 'PFNGLXGETFRAMEUSAGEMESAPROC' is initialized (use __typeof__ instead)
/usr/include/GL/glx.h:394: error: 'Display' was not declared in this scope
/usr/include/GL/glx.h:394: error: 'dpy' was not declared in this scope
/usr/include/GL/glx.h:394: error: 'GLXDrawable' was not declared in this scope
/usr/include/GL/glx.h:394: error: expected primary-expression before 'float'
/usr/include/GL/glx.h:395: error: typedef 'PFNGLXBEGINFRAMETRACKINGMESAPROC' is initialized (use __typeof__ instead)
/usr/include/GL/glx.h:395: error: 'Display' was not declared in this scope
/usr/include/GL/glx.h:395: error: 'dpy' was not declared in this scope
/usr/include/GL/glx.h:395: error: 'GLXDrawable' was not declared in this scope
/usr/include/GL/glx.h:396: error: typedef 'PFNGLXENDFRAMETRACKINGMESAPROC' is initialized (use __typeof__ instead)
/usr/include/GL/glx.h:396: error: 'Display' was not declared in this scope
/usr/include/GL/glx.h:396: error: 'dpy' was not declared in this scope
/usr/include/GL/glx.h:396: error: 'GLXDrawable' was not declared in this scope
/usr/include/GL/glx.h:397: error: typedef 'PFNGLXQUERYFRAMETRACKINGMESAPROC' is initialized (use __typeof__ instead)
/usr/include/GL/glx.h:397: error: 'Display' was not declared in this scope
/usr/include/GL/glx.h:397: error: 'dpy' was not declared in this scope
/usr/include/GL/glx.h:397: error: 'GLXDrawable' was not declared in this scope
/usr/include/GL/glx.h:397: error: expected primary-expression before '*' token
/usr/include/GL/glx.h:397: error: 'swapCount' was not declared in this scope
/usr/include/GL/glx.h:397: error: expected primary-expression before '*' token
/usr/include/GL/glx.h:397: error: 'missedFrames' was not declared in this scope
/usr/include/GL/glx.h:397: error: expected primary-expression before 'float'
/usr/include/GL/glx.h:465: error: variable or field 'glXBindTexImageEXT' declared void
/usr/include/GL/glx.h:465: error: 'Display' was not declared in this scope
/usr/include/GL/glx.h:465: error: 'dpy' was not declared in this scope
/usr/include/GL/glx.h:465: error: 'GLXDrawable' was not declared in this scope
/usr/include/GL/glx.h:465: error: expected primary-expression before 'int'
/usr/include/GL/glx.h:465: error: expected primary-expression before 'const'
/usr/include/GL/glx.h:465: error: initializer expression list treated as compound expression
/usr/include/GL/glx.h:466: error: variable or field 'glXReleaseTexImageEXT' declared void
/usr/include/GL/glx.h:466: error: 'Display' was not declared in this scope
/usr/include/GL/glx.h:466: error: 'dpy' was not declared in this scope
/usr/include/GL/glx.h:466: error: 'GLXDrawable' was not declared in this scope
/usr/include/GL/glx.h:466: error: expected primary-expression before 'int'
/usr/include/GL/glx.h:466: error: initializer expression list treated as compound expression
/usr/include/GL/glx.h:481: error: 'Bool' does not name a type
/usr/include/GL/glx.h:482: error: expected ';' before '*' token
/usr/include/GL/glx.h:483: error: 'GLXDrawable' does not name a type
make[2]: *** [beat_detect.lo] Error 1
make[2]: Leaving directory `/home/rperkins/Download/libprojectM/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/rperkins/Download/libprojectM'
make: *** [all] Error 2

```

---

### Post by kr4z on 2007-03-08
Ah, you're missing some library files. You may have the proper prerequisites in compiled form, but you also need the -dev versions of the packages to get the headers. When I compiled projectm I used these:

libgl1-mesa-dev
libglu1-mesa-dev
libx11-dev
libfreetype6-dev
ftgl-dev
zlib1g-dev

if you install those you should be able to compile.

The other option is to use the projectm .deb files I made for edgy which are located at [http://kr4z.com/debs/]("http://kr4z.com/debs/").

I made these with the intention of uploading them to universe via revu for edgy. Unfortunately, it took several months for somebody to review them. When somebody eventually did look at them they found a few problems, but it had been so long that I had forgotten all the details of how I had set up the package. It was hard to go back to fixing them, and so I lost interest... I think I'm going to go back and try again though, as it's a pretty damn cool visualization. :)

However, there were no big problems with the packages and they install and work fine for me.

---

### Post by Cresho on 2007-05-26
I have been struggling with this for the past few hours.  Some of the files do not include a "make" and cannot finish anything.  I been following some instructions and I just get a dead end.  Your files do not work for amarok since you did not include projectm-libvisual.

---

### Post by Cresho on 2007-05-26
here is the line.  I think its "borked!"

/Desktop/libvisual-projectM$ make
make: *** No targets specified and no makefile found.  Stop.


Ill remind you the bz file structure is unmodified so its useless.

---

