---
title: "Projector Image Dark and Low Resolution"
date: 2014-06-24
forum: Multimedia Software
---

### Post by hank863 on 2014-06-24
I am running Ubuntu 14.04 on a Lenovo ThinkPad W530 with NVIDIA graphics (nvidia-331 is installed).  I have an external monitor at home that I plug into my VGA port and it works very well.  I am having problems with projectors, though.  When I go to a meeting in a conference room and plug the projector into my VGA port, the projected image is insanely dark.  The only images I can make out are my white mouse on the dark background and the white panel icons on the dark panel.  The projection is also very low resolution and of much worse quality than when other people use the projector.  I have had this problem in three different conference rooms, with different projectors, and I have not seen anyone else have issues using the projectors.  In addition, a colleague of mine uses Ubuntu and has no problems with the projector.  What could I look into to try and resolve this?

Thanks!

---

### Post by tgalati4 on 2014-06-24
Is it possible that because you use an external monitor that the proprietary video driver reserves video RAM for it and when you plug in a projector, you get a low-bit-color and low resolution because you are out of video RAM?

Plug in a projector and look at the log file.  Open a terminal:

```
more /var/log/Xorg.0.log
```

You should get some information about what resolution and color-bit space is selected when the projector is plugged in.

---

### Post by hank863 on 2014-06-24
Thanks for the response!  I'll check tomorrow when I get back to the projectors and post back.

---

### Post by hank863 on 2014-06-25
When I plugged in one of the projectors today, the following was appended to my /var/log/Xorg.0.log file:

```
[  3556.097] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[  3556.097] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  3556.097] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[  3556.097] (**) NVIDIA(0):     all display devices.)
[  3556.117] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[  3556.117] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  3556.117] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[  3556.117] (**) NVIDIA(0):     all display devices.)
[  3556.127] (II) modesetting(G0): EDID vendor "LEN", prod id 16562
[  3556.128] (II) modesetting(G0): Printing DDC gathered Modelines:
[  3556.128] (II) modesetting(G0): Modeline "1920x1080"x0.0  139.00  1920 1980 2028 2050  1080 1090 1100 1130 -hsync -vsync (67.8 kHz eP)
[  3556.128] (II) modesetting(G0): Modeline "1920x1080"x0.0  115.83  1920 1980 2028 2050  1080 1090 1100 1130 -hsync -vsync (56.5 kHz e)
[  3556.160] reporting 7 10 50 388
[  3556.362] (II) NVIDIA(0): Setting mode "VGA-0: 1920x1080 @1920x1080 +1920+0 {ViewPortIn=1920x1080, ViewPortOut=1920x1080+0+0}"
[  3556.424] reporting 7 10 50 388
[  3556.428] reporting 7 10 50 388
[  3556.429] reporting 7 10 50 388
[  3556.434] reporting 7 10 50 388
[  3556.435] reporting 7 10 50 388
[  3556.447] reporting 7 10 50 388
[  3556.447] reporting 7 10 50 388
[  3556.447] reporting 7 10 50 388
[  3556.448] reporting 7 10 50 388
[  3556.449] reporting 7 10 50 388
[  3556.449] reporting 7 10 50 388
[  3556.450] reporting 7 10 50 388
[  3556.451] reporting 7 10 50 388
[  3556.451] reporting 7 10 50 388
[  3556.451] reporting 7 10 50 388
[  3556.451] reporting 7 10 50 388
[  3556.452] reporting 7 10 50 388
[  3556.461] reporting 7 10 50 388
[  3556.461] reporting 7 10 50 388
[  3556.461] reporting 7 10 50 388
[  3556.461] reporting 7 10 50 388
[  3556.461] reporting 7 10 50 388
[  3556.461] reporting 7 10 50 388
[  3556.462] reporting 7 10 50 388
[  3556.462] reporting 7 10 50 388
[  3556.470] reporting 7 10 50 388
[  3556.470] reporting 7 10 50 388
[  3556.470] reporting 7 10 50 388
[  3556.470] reporting 7 10 50 388
[  3556.471] reporting 7 10 50 388
[  3556.471] reporting 7 10 50 388
[  3556.471] reporting 7 10 50 388
[  3556.471] reporting 7 10 50 388
[  3556.471] reporting 7 10 50 388
[  3556.471] reporting 7 10 50 388
[  3556.471] reporting 7 10 50 388
[  3556.471] reporting 7 10 50 388
[  3556.471] reporting 7 10 50 388
[  3556.483] reporting 7 10 50 388
[  3556.484] reporting 7 10 50 388
[  3556.484] reporting 7 10 50 388
[  3556.484] reporting 7 10 50 388
[  3556.484] reporting 7 10 50 388
[  3556.484] reporting 7 10 50 388
[  3556.484] reporting 7 10 50 388
[  3556.484] reporting 7 10 50 388
[  3556.484] reporting 7 10 50 388
[  3556.484] reporting 7 10 50 388
[  3556.485] reporting 7 10 50 388
[  3556.485] reporting 7 10 50 388
[  3556.485] reporting 7 10 50 388
[  3556.496] reporting 7 10 50 388
[  3556.497] reporting 7 10 50 388
[  3556.497] reporting 7 10 50 388
[  3556.497] reporting 7 10 50 388
[  3556.497] reporting 7 10 50 388
[  3556.497] reporting 7 10 50 388
[  3556.497] reporting 7 10 50 388
[  3556.497] reporting 7 10 50 388
[  3556.497] reporting 7 10 50 388
[  3556.498] reporting 7 10 50 388
[  3556.498] reporting 7 10 50 388
[  3556.498] reporting 7 10 50 388
[  3556.498] reporting 7 10 50 388
[  3556.531] (II) NVIDIA(0): Setting mode "VGA-0: 1920x1080 @1920x1080 +0+0 {ViewPortIn=1920x1080, ViewPortOut=1920x1080+0+0}"
[  3556.580] reporting 7 10 50 388
[  3556.581] reporting 7 10 50 388
[  3556.581] reporting 7 10 50 388
[  3556.583] reporting 7 10 50 388
[  3556.583] reporting 7 10 50 388
[  3556.583] reporting 7 10 50 388
[  3556.583] reporting 7 10 50 388
[  3556.583] reporting 7 10 50 388
[  3556.588] reporting 7 10 50 388
[  3556.588] reporting 7 10 50 388
[  3556.589] reporting 7 10 50 388
[  3556.589] reporting 7 10 50 388
[  3556.589] reporting 7 10 50 388
[  3556.589] reporting 7 10 50 388
[  3556.589] reporting 7 10 50 388
[  3556.591] reporting 7 10 50 388
[  3556.591] reporting 7 10 50 388
[  3556.609] reporting 7 10 50 388
[  3556.609] reporting 7 10 50 388
[  3556.609] reporting 7 10 50 388
[  3556.609] reporting 7 10 50 388
[  3556.609] reporting 7 10 50 388
[  3556.609] reporting 7 10 50 388
[  3556.610] reporting 7 10 50 388
[  3556.610] reporting 7 10 50 388
[  3556.610] reporting 7 10 50 388
[  3556.610] reporting 7 10 50 388
[  3556.610] reporting 7 10 50 388
[  3556.610] reporting 7 10 50 388
[  3556.610] reporting 7 10 50 388
[  3556.617] reporting 7 10 50 388
[  3556.634] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[  3556.634] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  3556.634] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[  3556.634] (**) NVIDIA(0):     all display devices.)
[  3556.648] reporting 7 10 50 388
[  3556.667] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[  3556.667] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  3556.667] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[  3556.667] (**) NVIDIA(0):     all display devices.)
[  3556.701] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[  3556.701] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  3556.701] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[  3556.701] (**) NVIDIA(0):     all display devices.)
[  3556.714] reporting 7 10 50 388
[  3556.734] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[  3556.734] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  3556.734] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[  3556.734] (**) NVIDIA(0):     all display devices.)
[  3556.750] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[  3556.750] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  3556.750] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[  3556.750] (**) NVIDIA(0):     all display devices.)
[  3556.757] reporting 7 10 50 388
[  3556.784] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[  3556.784] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  3556.784] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[  3556.784] (**) NVIDIA(0):     all display devices.)
[  3556.800] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[  3556.800] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  3556.800] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[  3556.800] (**) NVIDIA(0):     all display devices.)
[  3556.807] reporting 7 10 50 388
[  3556.817] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[  3556.817] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  3556.817] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[  3556.817] (**) NVIDIA(0):     all display devices.)
[  3556.834] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[  3556.834] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  3556.834] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[  3556.834] (**) NVIDIA(0):     all display devices.)
[  3556.841] reporting 7 10 50 388
[  3556.846] reporting 7 10 50 388
[  3556.867] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[  3556.867] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  3556.867] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[  3556.867] (**) NVIDIA(0):     all display devices.)
[  3556.884] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[  3556.884] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  3556.884] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[  3556.884] (**) NVIDIA(0):     all display devices.)
[  3556.891] reporting 7 10 50 388
[  3556.894] reporting 7 10 50 388
[  3556.895] reporting 7 10 50 388
[  3556.900] reporting 7 10 50 388
[  3556.904] reporting 7 10 50 388
[  3556.908] reporting 7 10 50 388
[  3556.937] reporting 7 10 50 388
[  3556.939] reporting 7 10 50 388
[  3556.945] reporting 7 10 50 388
[  3556.954] reporting 7 10 50 388
[  3556.957] reporting 7 10 50 388
[  3556.964] reporting 7 10 50 388
[  3556.967] reporting 7 10 50 388
[  3556.970] reporting 7 10 50 388
[  3556.984] reporting 7 10 50 388
[  3556.989] reporting 7 10 50 388
[  3557.005] reporting 7 10 50 388
[  3557.050] reporting 7 10 50 388
[  3557.125] reporting 7 10 50 388
[  3557.134] reporting 7 10 50 388
[  3557.135] reporting 7 10 50 388
[  3557.136] reporting 7 10 50 388
[  3566.066] reporting 7 10 50 388
```

---

### Post by tgalati4 on 2014-06-25
Thinkpads have a blue switch sceen function Fn+F7 perhaps and try that a few times to observe the output.  Perhaps you have a bad VGA cable?  The EDID handshake allows the graphics card to switch to the correct video mode based on the native resolution and refresh rate of the display or projection device.  Because this handshake is not working, you get the lowest common denominator.  Check your BIOS settings for any video settings that may have switched EDID detection off.

---

### Post by hank863 on 2014-06-25
When I pressed Fn+F7, nothing was recorded in /var/log/Xorg.0.log and nothing appeared to happen.  I know the VGA cable is not bad because I have tried several that work for other people.  I looked in my BIOS and did not see anything related to EDID detection.  I did decide to switch my graphics to "Discrete" mode (disabling Optimus).  When I booted with this configuration, I still got the EDID errors, but the projector became usable, even though it was not optimal.  I then rebooted, switching the BIOS back to "Optimus," and the projector was just as bad as before.  I should have learned by now to always suspect Optimus.  I find it strange that I have this problem with the projectors, but not my external monitor, though.  I'll report back in a bit on whether I get the EDID errors on my external monitor.

---

### Post by hank863 on 2014-06-25
When I plugged my laptop into my external monitor at home, the following is appended to /var/log/Xorg.0.log:

```
[   693.379] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[   693.379] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   693.379] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[   693.379] (**) NVIDIA(0):     all display devices.)
[   693.392] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[   693.392] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   693.392] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[   693.392] (**) NVIDIA(0):     all display devices.)
[   693.398] (II) modesetting(G0): EDID vendor "LEN", prod id 16562
[   693.398] (II) modesetting(G0): Printing DDC gathered Modelines:
[   693.398] (II) modesetting(G0): Modeline "1920x1080"x0.0  139.00  1920 1980 2028 2050  1080 1090 1100 1130 -hsync -vsync (67.8 kHz eP)
[   693.398] (II) modesetting(G0): Modeline "1920x1080"x0.0  115.83  1920 1980 2028 2050  1080 1090 1100 1130 -hsync -vsync (56.5 kHz e)
[   693.428] reporting 7 10 50 388
[   693.497] (II) NVIDIA(0): Setting mode "VGA-0: 1920x1080 @1920x1080 +0+0 {ViewPortIn=1920x1080, ViewPortOut=1920x1080+0+0}"
[   693.551] reporting 7 10 50 388
[   693.551] reporting 7 10 50 388
[   693.551] reporting 7 10 50 388
[   693.551] reporting 7 10 50 388
[   693.553] reporting 7 10 50 388
[   693.554] reporting 7 10 50 388
[   693.556] reporting 7 10 50 388
[   693.560] reporting 7 10 50 388
[   693.560] reporting 7 10 50 388
[   693.560] reporting 7 10 50 388
[   693.560] reporting 7 10 50 388
[   693.561] reporting 7 10 50 388
[   693.562] reporting 7 10 50 388
[   693.562] reporting 7 10 50 388
[   693.562] reporting 7 10 50 388
[   693.562] reporting 7 10 50 388
[   693.562] reporting 7 10 50 388
[   693.562] reporting 7 10 50 388
[   693.562] reporting 7 10 50 388
[   693.562] reporting 7 10 50 388
[   693.578] reporting 7 10 50 388
[   693.578] reporting 7 10 50 388
[   693.578] reporting 7 10 50 388
[   693.578] reporting 7 10 50 388
[   693.578] reporting 7 10 50 388
[   693.579] reporting 7 10 50 388
[   693.579] reporting 7 10 50 388
[   693.579] reporting 7 10 50 388
[   693.579] reporting 7 10 50 388
[   693.579] reporting 7 10 50 388
[   693.579] reporting 7 10 50 388
[   693.579] reporting 7 10 50 388
[   693.579] reporting 7 10 50 388
[   693.579] reporting 7 10 50 388
[   693.589] reporting 7 10 50 388
[   693.589] reporting 7 10 50 388
[   693.589] reporting 7 10 50 388
[   693.590] reporting 7 10 50 388
[   693.590] reporting 7 10 50 388
[   693.590] reporting 7 10 50 388
[   693.590] reporting 7 10 50 388
[   693.590] reporting 7 10 50 388
[   693.590] reporting 7 10 50 388
[   693.590] reporting 7 10 50 388
[   693.590] reporting 7 10 50 388
[   693.590] reporting 7 10 50 388
[   693.590] reporting 7 10 50 388
[   693.590] reporting 7 10 50 388
[   693.613] reporting 7 10 50 388
[   693.621] reporting 7 10 50 388
[   693.703] (II) NVIDIA(GPU-0): Display (Samsung T22B350 (CRT-0)) does not support NVIDIA 3D
[   693.703] (II) NVIDIA(GPU-0):     Vision stereo.
[   693.703] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   693.703] (**) NVIDIA(0):     device Samsung T22B350 (CRT-0) (Using EDID frequencies has
[   693.703] (**) NVIDIA(0):     been enabled on all display devices.)
[   693.707] reporting 7 10 58 448
[   693.707] reporting 7 10 58 448
[   693.707] reporting 7 10 58 448
[   693.708] reporting 7 10 58 448
[   693.708] reporting 7 10 58 448
[   693.708] reporting 7 10 58 448
[   693.708] reporting 7 10 58 448
[   693.710] reporting 7 10 58 448
[   693.710] reporting 7 10 58 448
[   693.710] reporting 7 10 58 448
[   693.710] reporting 7 10 58 448
[   693.710] reporting 7 10 58 448
[   693.710] reporting 7 10 58 448
[   693.710] reporting 7 10 58 448
[   693.710] reporting 7 10 58 448
[   693.723] reporting 7 10 58 448
[   693.740] (II) NVIDIA(GPU-0): Display (Samsung T22B350 (CRT-0)) does not support NVIDIA 3D
[   693.740] (II) NVIDIA(GPU-0):     Vision stereo.
[   693.740] reporting 7 10 58 448
[   693.755] (II) NVIDIA(GPU-0): Display (Samsung T22B350 (CRT-0)) does not support NVIDIA 3D
[   693.755] (II) NVIDIA(GPU-0):     Vision stereo.
[   693.756] reporting 7 10 58 448
[   693.773] (II) NVIDIA(GPU-0): Display (Samsung T22B350 (CRT-0)) does not support NVIDIA 3D
[   693.773] (II) NVIDIA(GPU-0):     Vision stereo.
[   693.788] (II) NVIDIA(GPU-0): Display (Samsung T22B350 (CRT-0)) does not support NVIDIA 3D
[   693.788] (II) NVIDIA(GPU-0):     Vision stereo.
[   693.790] reporting 7 10 58 448
[   693.809] (II) NVIDIA(GPU-0): Display (Samsung T22B350 (CRT-0)) does not support NVIDIA 3D
[   693.809] (II) NVIDIA(GPU-0):     Vision stereo.
[   693.824] (II) NVIDIA(GPU-0): Display (Samsung T22B350 (CRT-0)) does not support NVIDIA 3D
[   693.824] (II) NVIDIA(GPU-0):     Vision stereo.
[   693.824] reporting 7 10 58 448
[   693.845] (II) NVIDIA(GPU-0): Display (Samsung T22B350 (CRT-0)) does not support NVIDIA 3D
[   693.845] (II) NVIDIA(GPU-0):     Vision stereo.
[   693.861] (II) NVIDIA(GPU-0): Display (Samsung T22B350 (CRT-0)) does not support NVIDIA 3D
[   693.861] (II) NVIDIA(GPU-0):     Vision stereo.
[   693.862] reporting 7 10 58 448
[   693.867] reporting 7 10 58 448
[   693.898] (II) NVIDIA(0): Setting mode "VGA-0: nvidia-auto-select @1920x1080 +0+0 {ViewPortIn=1920x1080, ViewPortOut=1920x1080+0+0}"
[   693.975] reporting 7 10 57 439
[   693.976] reporting 7 10 57 439
[   693.977] reporting 7 10 57 439
[   693.977] reporting 7 10 57 439
[   693.977] reporting 7 10 57 439
[   694.018] reporting 7 10 57 439
[   694.018] reporting 7 10 57 439
[   694.019] reporting 7 10 57 439
[   694.019] reporting 7 10 57 439
[   694.019] reporting 7 10 57 439
[   694.019] reporting 7 10 57 439
[   694.019] reporting 7 10 57 439
[   694.019] reporting 7 10 57 439
[   694.020] reporting 7 10 57 439
[   694.020] reporting 7 10 57 439
[   694.020] reporting 7 10 57 439
[   694.020] reporting 7 10 57 439
[   694.020] reporting 7 10 57 439
[   694.038] reporting 7 10 57 439
[   694.038] reporting 7 10 57 439
[   694.038] reporting 7 10 57 439
[   694.038] reporting 7 10 57 439
[   694.038] reporting 7 10 57 439
[   694.038] reporting 7 10 57 439
[   694.038] reporting 7 10 57 439
[   694.038] reporting 7 10 57 439
[   694.039] reporting 7 10 57 439
[   694.039] reporting 7 10 57 439
[   694.039] reporting 7 10 57 439
[   694.039] reporting 7 10 57 439
[   694.039] reporting 7 10 57 439
[   694.039] reporting 7 10 57 439
[   694.049] reporting 7 10 57 439
[   694.049] reporting 7 10 57 439
[   694.050] reporting 7 10 57 439
[   694.051] reporting 7 10 57 439
[   694.052] reporting 7 10 57 439
[   694.066] (II) NVIDIA(GPU-0): Display (Samsung T22B350 (CRT-0)) does not support NVIDIA 3D
[   694.067] (II) NVIDIA(GPU-0):     Vision stereo.
[   694.082] (II) NVIDIA(GPU-0): Display (Samsung T22B350 (CRT-0)) does not support NVIDIA 3D
[   694.082] (II) NVIDIA(GPU-0):     Vision stereo.
[   694.083] reporting 7 10 57 439
[   694.083] reporting 7 10 57 439
[   694.084] reporting 7 10 57 439
[   694.110] reporting 7 10 57 439
[   694.118] reporting 7 10 57 439
[   694.119] reporting 7 10 57 439
[   694.135] reporting 7 10 57 439
[   694.140] reporting 7 10 57 439
[   694.209] reporting 7 10 57 439
[   694.242] reporting 7 10 57 439
[   694.248] reporting 7 10 57 439
[   694.249] reporting 7 10 57 439
[   694.250] reporting 7 10 57 439
[   694.250] reporting 7 10 57 439
```

It seems to have the same EDID warning initially, but, unlike with the projector, it doesn't continue reporting EDID errors and the monitor ends up configured properly, with the expected resolution and colors.

---

### Post by tgalati4 on 2014-06-26
Although it is a pain to do, I would switch to the open "nv" video driver and try the projector.  The Optimus graphics has been problematic in linux.  Does this machine dual-boot?  Does the projector work correctly in Windows?

---

### Post by hank863 on 2014-06-26
The projector works on Windows and it works perfectly fine with the nouveau driver.  I guess my problem is related to NVIDIA's driver when I have Optimus enabled and I assume that means I'll just have to wait it out for them to get their act together.  Sadly, I cannot use nouveau because the performance is abysmal.  Among other things, my cursor ghosts on secondary displays and blinks constantly on both my primary and secondary displays.

I really appreciate your help.

---

### Post by hank863 on 2014-06-26
I just figured it out!  If I use the official NVIDIA Settings to configure the resolution of the projector and the Ubuntu Display settings to configure the orientation, I can get the projector to look and function properly.  I had looked through the NVIDIA settings several times, but just noticed there was an option to select the projector in the X Server Display Configuration section.  This may sound really obvious, but I managed to skip over it several times and was originally further confused by the fact my external monitor worked without intervention.

Once again, thank you for your help!

---

