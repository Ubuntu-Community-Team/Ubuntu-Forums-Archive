---
title: "What alternatives ubuntu have to windows DirectX 11?"
date: 2009-06-02
forum: Multimedia Software
---

### Post by KristinaK on 2009-06-02
What alternatives ubuntu have to windows *DirectX 11?*

---

### Post by KristinaK on 2009-06-12
no one knows?  :(

---

### Post by Arup on 2009-06-12
Direct X is windows only implementation, Ubuntu uses Open GL.

---

### Post by Chemical Imbalance on 2009-06-12
Linux doesn't have a huge commercial gaming market yet. DirectX is a Microsoft technology.

OpenGL is the graphics standard on linux, like OP stated.

If you are big into gaming, I'd suggest either keep a windows partition (dual boot) or see if your games work in WINE: [http://appdb.winehq.org/](http://appdb.winehq.org/).

---

### Post by Johan-Steyn on 2009-06-12
Hi KristinaK,

Micro$oft DirectX11 is by no means the begin-all and end-all in future graphics development. There are some interesting developments in the open source arena as well. 

New on the horizon is Nvidia's Cuda and OpenCL (MacOS) which should also be made available in Linux.

Check out these sites: 

[http://www.khronos.org/opencl/](http://www.khronos.org/opencl/)
[http://en.wikipedia.org/wiki/OpenCL](http://en.wikipedia.org/wiki/OpenCL)
[http://www.khronos.org/developers/library/overview/opencl_overview.pdf](http://www.khronos.org/developers/library/overview/opencl_overview.pdf)
[http://www.linuxquestions.org/questions/programming-9/opencl-on-linux-693926/](http://www.linuxquestions.org/questions/programming-9/opencl-on-linux-693926/)

[http://www.nvidia.com/object/cuda_home.html#](http://www.nvidia.com/object/cuda_home.html#) (download available)
[http://en.wikipedia.org/wiki/CUDA](http://en.wikipedia.org/wiki/CUDA)

Regards,

JS

---

### Post by lukeiamyourfather on 2009-06-12
> **Johan-Steyn said:**
> Hi KristinaK,

Micro$oft DirectX11 is by no means the begin-all and end-all in future graphics development. There are some interesting developments in the open source arena as well. 

New on the horizon is Nvidia's Cuda and OpenCL (MacOS) which should also be made available in Linux.

Check out these sites: 

[http://www.khronos.org/opencl/](http://www.khronos.org/opencl/)
[http://en.wikipedia.org/wiki/OpenCL](http://en.wikipedia.org/wiki/OpenCL)
[http://www.khronos.org/developers/library/overview/opencl_overview.pdf](http://www.khronos.org/developers/library/overview/opencl_overview.pdf)
[http://www.linuxquestions.org/questions/programming-9/opencl-on-linux-693926/](http://www.linuxquestions.org/questions/programming-9/opencl-on-linux-693926/)

[http://www.nvidia.com/object/cuda_home.html#](http://www.nvidia.com/object/cuda_home.html#) (download available)
[http://en.wikipedia.org/wiki/CUDA](http://en.wikipedia.org/wiki/CUDA)

Regards,

JS

CUDA and OpenCL are not for rendering realtime graphics. They use the graphics hardware for processing but are not competing with OpenGL. Chances are OpenGL will remain the primary 3D graphics API in Linux for the foreseeable future. Cheers!

---

### Post by Johan-Steyn on 2009-06-12
Hi lukeiamyourfather,

Yes, I would definitely agree that OpenGL is here to stay.

Also cuda is based mainly on Nvidia hardware.

However OpenCL is analogous to OpenGL 

Taken from [http://en.wikipedia.org/wiki/OpenCL](http://en.wikipedia.org/wiki/OpenCL)

> **OpenCL** (**Open** **C**omputing **L**anguage) is a framework for writing programs that execute across [heterogeneous]("http://en.wikipedia.org/wiki/Heterogeneity") platforms consisting of [CPUs]("http://en.wikipedia.org/wiki/Central_processing_unit"), [GPUs]("http://en.wikipedia.org/wiki/Graphics_processing_unit"), and other processors. OpenCL includes a language (based on [C99]("http://en.wikipedia.org/wiki/C99")) for writing *kernels* (functions that execute on OpenCL devices), plus APIs that are used to define and then control the platforms. OpenCL provides [parallel computing]("http://en.wikipedia.org/wiki/Parallel_computing") using task-based and data-based parallelism.
 OpenCL is analogous to the open industry standards [OpenGL]("http://en.wikipedia.org/wiki/OpenGL") and [OpenAL]("http://en.wikipedia.org/wiki/OpenAL"), for 3D graphics and computer audio, respectively. OpenCL extends the power of the GPU beyond graphics ([GPGPU]("http://en.wikipedia.org/wiki/GPGPU")). OpenCL is managed by the [non-profit]("http://en.wikipedia.org/wiki/Non-profit_organization") technology [consortium]("http://en.wikipedia.org/wiki/Consortium") [Khronos Group]("http://en.wikipedia.org/wiki/Khronos_Group").


AMD has decided to support OpenCL (and [DirectX]("http://en.wikipedia.org/wiki/DirectX") 11) instead of the now deprecated [Close to Metal]("http://en.wikipedia.org/wiki/Close_to_Metal") in its [Stream framework]("http://en.wikipedia.org/wiki/AMD_FireStream#Software_Development_Kit").[]("http://en.wikipedia.org/wiki/OpenCL#cite_note-AMDpressrelease-4")[]("http://en.wikipedia.org/wiki/OpenCL#cite_note-eweekAMD-5")_ _[RapidMind]("http://en.wikipedia.org/wiki/RapidMind") announced their adoption of OpenCL underneath their development platform, in order to support GPUs from multiple vendors with one interface.[]("http://en.wikipedia.org/wiki/OpenCL#cite_note-RapidMindHPCWire-6") Nvidia announced its intention to add full support for the OpenCL 1.0 specification to its GPU Computing Toolkit.[]("http://en.wikipedia.org/wiki/OpenCL#cite_note-Nvidia_Press_Release_2008-12-09-7")

Regards,

JS

---

### Post by windows7plusvmware on 2012-04-25
I have used Ubuntu for a few years at Otago Polytechnic here in Dunedin New Zealand.
 
Back when I was at Otago Polytech we used Windows xp as the main operating system with VMWare a Operating system emulation program.
 
This way you get the best of both worlds I think that there is also a version of VMWare for Linux but for windows the latest version is 8.0.
 
Maybe If you get VMWare running on Linux you can Emulate Windows 7 or Windows Vista and maybe get direct x 11 going that way I don't know how good VMWares Drivers will be which is called VMWare tools if I remember correctly.
 
Off Topic.
Who here has seen Windows 8 ive tried it on VMWare think its terrible.

---

