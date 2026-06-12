---
title: "help with ATI Catalyst control center"
date: 2011-07-23
forum: Multimedia Software
---

### Post by BudBear on 2011-07-23
for a long time i have had the proprietary driver installed and catalyst control center was working correctly. but after a recent kernel update, i had a very difficult time getting the driver installed, and now it seems installed but the ATI Catalyst Control Center won't run.  the driver appears to be installed because fglrxinfo gives:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4800 Series        
OpenGL version string: 3.3.10362 Compatibility Profile Context

and fgl_glxgears runs fine.  but if i try to run amdcccle, nothing happens.
 if i run it as root thru nautilus the following error appears:

/usr/lib/fglrx/bin/amdcccle: error while loading shared libraries: /usr/share/ati/lib64/libQtGui.so.4: file too short

i'd like to have the control center working so any suggestions or help is much appreciated.
thanks
Joe

---

