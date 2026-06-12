---
title: "Cant enable GPU render on Blender with Nvidia GT 710."
date: 2017-02-14
forum: Multimedia Software
---

### Post by Portaro on 2017-02-14
I have a computer with APU quad core AMD 6210 processor that have an R3 radeon graphic card, and recently to use with blender I buy a new GPU to insert on PCIEX slot the new card is an Nvidia GT 710 2GB DDR3.

The problem is with Blender I already try install different version os cuda , reinstall nvidia drivers try use different versions of Blender and I cant make enable teh option of Blender to render cycles with GPU card Nvidia in fact I not see this card in the user preferences & system on Blender and I cant enable this directly on the render menu .

Any option to make this option available in Ubuntu 14.04.5 ?

&#8594;

> joao@A-F-K31DA-K31DAG-K20DA:~$ glxinfo | grep OpenGL
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: Graphics Device/PCIe/SSE2
OpenGL core profile version string: 4.3.0 NVIDIA 340.101
OpenGL core profile shading language version string: 4.30 NVIDIA via Cg compiler
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 4.4.0 NVIDIA 340.101
OpenGL shading language version string: 4.40 NVIDIA via Cg compiler
OpenGL context flags: (none)
OpenGL profile mask: (none)
OpenGL extensions:
joao@A-F-K31DA-K31DAG-K20DA:~$ 



---

### Post by Perfect Storm on 2017-02-15
The configuration of blender is stored either in .config/blender. Try take that directory out of the equation then try again.

---

### Post by Portaro on 2017-02-15
I try your suggestion and others I already try to install differet versions of cuda, different versions of nvidia-drivers and nothing work maybe this only work on windows .

[https://youtu.be/37VdKbHi-5s](https://youtu.be/37VdKbHi-5s)   - here a video as you can see the option that appears is only CPU render option and not GPU

---

### Post by Portaro on 2017-02-16
I think that I solve the problem installing new nvidia driver package - nvidia-346 &#8594;

[IMG]https://framapic.org/aoTs1j1lSdtb/goSKqmYrB77o.png[/IMG]

---

