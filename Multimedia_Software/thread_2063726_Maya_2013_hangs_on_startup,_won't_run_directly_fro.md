---
title: "Maya 2013 hangs on startup, won't run directly from the binary file"
date: 2012-09-27
forum: Multimedia Software
---

### Post by odinist7 on 2012-09-27
Hey, so I was trying to get Maya 2013 installed on my Ubuntu 12.04.1 LTS x64 machine and found a useful script [here]("https://gist.github.com/3772559") to automate it. The installation went just fine as far as I could tell, but now when I try to run Maya via the maya shell script, the program just hangs forever, no splash screen, no errors to stdout, it doesn't even look like it's doing much when I run htop.

When I try to run the maya.bin file directly, something happens at least:
[IMG]http://i.imgur.com/t3VGX.png[/IMG]
But it's not particularly helpful since I know that the serial key is installed via ```
/usr/autodesk/maya2013-x64/bin/adlmreg -i S 657E1 657E1 2013.0.0.F <sn> /var/opt/Autodesk/Adlm/Maya2013/MayaConfig.pit
``` saying so.

Anyone else have this problem?

---

### Post by kewlt on 2012-10-25
This looks like an old post but its the only one i found on this issue. This worked for me so am posting this solution here.
I tried running the program from root (sudo -i) and it worked.

---

### Post by scarletshark on 2012-11-17
Thanks, this fix worked for me!  But only for registering my serial number.  Now when I run $ maya from the command line, I get ONLY the Maya Command window.  The following is in the command window:

```
// Error: file: /usr/autodesk/maya/scripts/startup/HotboxMenus.mel line 157:  // 

// mental ray for Maya 2013 

// Mental ray for Maya: using startup file /usr/autodesk/maya/mentalray//maya.rayrc.

// mental ray for Maya: setup

// mental ray for Maya: initialize

// mental ray for Maya: register extensions

// mental ray Node Factory: loaded

// mental ray for Maya: successfully registered

// mental ray for Maya: loading startup file: /usr/autodesk/maya/mentalray//maya.rayrc

// parsing /usr/autodesk/maya/mentalray/shaders/include/AdskShaderSDKWrappers.mi

// generating Maya nodes...

// parsing /usr/autodesk/maya/mentalray/shaders/include/abcimport.mi

// loading /usr/autodesk/maya/mentalray/shaders/abcimport.so

// generating Maya nodes...

// parsing /usr/autodesk/maya/mentalray/shaders/include/architectural.mi

// loading /usr/autodesk/maya/mentalray/shaders/architectural.so

// generating Maya nodes...

// parsing /usr/autodesk/maya/mentalray/shaders/include/base.mi

// loading /usr/autodesk/maya/mentalray/shaders/base.so

// generating Maya nodes...

// parsing /usr/autodesk/maya/mentalray/shaders/include/builtin_bsdf.mi

// generating Maya nodes...

// parsing /usr/autodesk/maya/mentalray/shaders/include/contour.mi

// loading /usr/autodesk/maya/mentalray/shaders/contour.so

// generating Maya nodes...

// parsing /usr/autodesk/maya/mentalray/shaders/include/paint.mi

// loading /usr/autodesk/maya/mentalray/shaders/paint.so

// generating Maya nodes...

// parsing /usr/autodesk/maya/mentalray/shaders/include/physics.mi

// loading /usr/autodesk/maya/mentalray/shaders/physics.so

// generating Maya nodes...

// parsing /usr/autodesk/maya/mentalray/shaders/include/production.mi

// loading /usr/autodesk/maya/mentalray/shaders/production.so

// generating Maya nodes...

// parsing /usr/autodesk/maya/mentalray/shaders/include/ptex.mi

// loading /usr/autodesk/maya/mentalray/shaders/ptex.so

// generating Maya nodes...

// parsing /usr/autodesk/maya/mentalray/shaders/include/subsurface.mi

// loading /usr/autodesk/maya/mentalray/shaders/subsurface.so

// generating Maya nodes...

// parsing /usr/autodesk/maya/mentalray/shaders/include/surfaceSampler.mi

// loading /usr/autodesk/maya/mentalray/shaders/surfaceSampler.so

// generating Maya nodes...

// parsing /usr/autodesk/maya/mentalray/shaders/include/userdata.mi

// loading /usr/autodesk/maya/mentalray/shaders/userdata.so

// generating Maya nodes...

// parsing /usr/autodesk/maya/mentalray/shaders/include/useribl.mi

// loading /usr/autodesk/maya/mentalray/shaders/useribl.so

// generating Maya nodes...

// AbcExport v1.0 using Alembic 1.0.4 (built Jan 16 2012 13:07:28)

// AbcImport v1.0 using Alembic 1.0.4 (built Jan 16 2012 13:07:28)

updateRendererUI;

// Error: file: /usr/autodesk/maya/mentalray/scripts/mentalrayUI.mel line 1607: menu: Object 'mainRenderMenu' not found. // 
```

So I tried the following, and got the resulting output:

```
$ sudo -i maya


maya encountered a fatal error

Signal: 11 (Unknown Signal)
Fatal Error. Attempting to save in /usr/tmp/root.20121117.1555.ma
Segmentation fault (core dumped)
```

Thoughts?

---

