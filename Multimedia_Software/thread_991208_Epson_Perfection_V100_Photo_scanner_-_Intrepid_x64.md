---
title: "Epson Perfection V100 Photo scanner - Intrepid x64?"
date: 2008-11-23
forum: Multimedia Software
---

### Post by niallporter on 2008-11-23
Hello,

I just upgraded to Intrepid x64, was using Hardy x86 previously.  I had my Epson Perfection V100 Photo scanner working using the drivers I found on the Avasys website (via Epson's own site) but there are no x64 drivers provided there.

There are source code archives there but attempting to built them yields this:

```
checking for gtk+-2.0... checking for gtk+... sh: gtk-config: not found
sh: gtk-config: not found
sh: gtk-config: not found
yes
checking GTK_CFLAGS... sh: gtk-config: not found
sh: gtk-config: not found
sh: gtk-config: not found
 
checking GTK_LIBS... sh: gtk-config: not found
sh: gtk-config: not found
sh: gtk-config: not found
 
checking for imlibgdk... Package imlibgdk was not found in the pkg-config search path. Perhaps you should add the directory containing `imlibgdk.pc' to the PKG_CONFIG_PATH environment variable No package 'imlibgdk' found
configure: error: Library requirements (imlibgdk) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
```

Can anyone help with that?  Failing that, does anyone know another way to get these installed?  Alien can't convert the RPM drivers to .deb because there I'm now on x64 architecture...

Any help much appreciated :)

Niall

---

