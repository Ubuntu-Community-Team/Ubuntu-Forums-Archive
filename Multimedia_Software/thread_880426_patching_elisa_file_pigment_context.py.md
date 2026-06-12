---
title: "patching elisa file pigment_context.py"
date: 2008-08-05
forum: Multimedia Software
---

### Post by meg23 on 2008-08-05
I am trying to patch an elisa configuration file to try and fix some fullscreen issues with the xinerama. After using the patch terminal program, this is the output I get:

> sudo patch  /usr/lib/python2.5/site-packages/elisa/plugins/pigment/pigment_context.py /tmp/resize.patch

patching file /usr/lib/python2.5/site-packages/elisa/plugins/pigment/pigment_context.py
Hunk #1 FAILED at 261.
1 out of 1 hunk FAILED -- saving rejects to file /usr/lib/python2.5/site-packages/elisa/plugins/pigment/pigment_context.py.rej

here is a link to the patch:

[https://code.fluendo.com/elisa/trac/attachment/ticket/555/resize.patch](https://code.fluendo.com/elisa/trac/attachment/ticket/555/resize.patch)

Anyone familiar with this problem?

---

### Post by loell on 2008-08-05
you should have passed a --dry-run first before patching ;)

---

### Post by meg23 on 2008-08-05
This script results in the same output.
 
sudo patch --dry-run /usr/lib/python2.5/site-packages/elisa/plugins/pigment/pigment_context.py /tmp/resize.patch

---

### Post by loell on 2008-08-05
try 

```
sudo patch **-p1** /usr/lib/python2.5/site-packages/elisa/plugins/pigment/pigment_context.py /tmp/resize.patch
```

---

### Post by meg23 on 2008-08-05
same output. I just need this file patched in what ever way is possible. Any other ways of patching it?

---

### Post by meg23 on 2008-08-05
Here is the patch file:

Index: pigment_context.py
===================================================================
--- pigment_context.py	(revision 4725)
+++ pigment_context.py	(working copy)
@@ -261,27 +261,24 @@
                                                      self._resize_canvas)
 
     def _resize_canvas(self):
-        # only reacts if the size of the viewport changed
-        if self.viewport_size != self.viewport_handle.size:
-            self.debug("regeneration of the drawables")
-            self.viewport_size = self.viewport_handle.size
-            self.canvas_resized.emit(self.canvas.size)
+        viewport_ratio = float(self.viewport_handle.width) / \
+                         float(self.viewport_handle.height)
 
-        """
-        # resize the canvas to follow the aspect ratio of the viewport
-        viewport_ratio = float(self.viewport_handle.width)/float(self.viewport_handle.height)
         canvas_ratio = float(self.canvas.width)/float(self.canvas.height)
 
         # only resize the canvas if the aspect ratio of the viewport has changed
         if viewport_ratio != canvas_ratio:
-            # FIXME: only one of width/height needs to change (multiplied by
-            # viewport_ratio)
-            self.canvas.size = (self.viewport_handle.width/100.0,
-                                self.viewport_handle.height/100.0)
+            self.canvas.size = (self.canvas.size[0],
+                                self.canvas.size[0] / viewport_ratio)
             self.debug("The canvas is getting resized. New size = (%s, %s)" % \
                         (self.canvas.size[0], self.canvas.size[1]))
-        """
 
+        # only reacts if the size of the viewport changed
+        if self.viewport_size != self.viewport_handle.size:
+            self.debug("regeneration of the drawables")
+            self.viewport_size = self.viewport_handle.size
+            self.canvas_resized.emit(self.canvas.size)
+
     def _motion_notify_callback(self, viewport, event):
         # show the cursor
         viewport.cursor = pgm.VIEWPORT_INHERIT

---

### Post by loell on 2008-08-05
did you install elisa from  ubuntu repo or was it from another source?

---

### Post by meg23 on 2008-08-05
I installed it from the repo. Is it possible that patch might be old and incompatible with the current piment_context.py file?

---

