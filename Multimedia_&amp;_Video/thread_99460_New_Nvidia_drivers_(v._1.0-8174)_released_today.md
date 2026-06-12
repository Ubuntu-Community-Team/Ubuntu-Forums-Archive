---
title: "New Nvidia drivers (v. 1.0-8174) released today"
date: 2005-12-05
forum: Multimedia &amp; Video
---

### Post by 23meg on 2005-12-05
For anyone who may not have noticed, let me give the heads up that Nvidia released version 1.0-8174 of their Linux x86 and AMD64 drivers today. I'm downloading at the moment, with the hope that the new version will fix [my 2D performance problems]("http://www.ubuntuforums.org/showthread.php?t=94332").

I've not heard from anyone who's installed them, but looking at the changelog I don't see many improvements over the last version (SLI support being the major one), so I'd suggest anyone who's not having any significiant issues with their present driver version to stick to their installed drivers for now. If you do decide to install, read the changelog and the readme file. Nvidia's readme files are very informative and are definitely worth reading.
> **Release Highlights**

    * Fixed GeForce 7800 GTX clocking problem that affected 3D performance.
    * Added support for NVIDIA SLI.  Please see the README for details.
    * Added a new utility 'nvidia-xconfig', which is a commandline tool for updating X configuration files.
    * Added support for new GeForce 6100, GeForce 6150 and GeForce 7800 GTX 512.
    * Added manpages for 'nvidia-xconfig', 'nvidia-settings', and 'nvidia-installer'.
    * Made UseEdidFreqs "on" by default; the NVIDIA X driver will use the valid HorizSync and VertRefresh frequency ranges from the EDID whenever possible.
    * Added support for Stereo Digital Flat Panels such as the SeeReal and Sharp3D DFPs.
    * Added HTML version of the README.
    * Added support for static Rotation; see the "Rotate" X config option in the README.
    * Improved stability on 64-bit Linux 2.6 kernels.
    * Fixed driver installation when SELinux is enabled. 

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

---

### Post by callahan on 2005-12-06
Are these packaged up in backports or the main repositories yet?  I could not use Breezy because it would hard lock my machine within 15 minutes (2nd to last item on the list).  It would be nice if I could install it now.

  Michael

---

### Post by callahan on 2005-12-07
Has anyone gotten this working yet?  I am having problems starting up X11 after I install from the NVidia run package.

  Michael

---

### Post by tseliot on 2005-12-07
[QUOTE=callahan]Has anyone gotten this working yet?  I am having problems starting up X11 after I install from the NVidia run package.

  Michael[/QUOTE]
It works great for me. However I haven't tested it enough.

---

### Post by 23meg on 2005-12-07
[QUOTE=callahan]Has anyone gotten this working yet? [/QUOTE]I'm very disappointed; the new drivers are unusable for me, since they introduce a new bug (confirmed) with my Go6200 chip that doesn't allow the native resolution to be set on my laptop LCD display.

I was expecting better 2D performance with the new drivers and I ended up downgrading to 7667. Having bought a laptop with an Nvidia graphics chip on purpose, for their supposedly better Linux support, my disappointment with Nvidia is growing.

---

