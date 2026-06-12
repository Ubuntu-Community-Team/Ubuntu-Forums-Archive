---
title: "OpenCL Rendering in Blender 3D"
date: 2016-12-24
forum: Multimedia Software
---

### Post by tommaso-bracigliano on 2016-12-24
Hello to everybody!!!,
I have just made a PC with "AMD Radeon RX 480" Graphic Card and "AMD FX-8370E" Processor.
Operating System is Ubuntu 16.04 and I want to use Open Source drivers.
I know that recently with AMDGPU drivers this is possible.
I want to use Cycles rendering with GPU then with OpenCL in Blender 3D.
I have installed MESA 13 from Padoka repository and LLVM 4.0 + CLang 4.0.

When I execute the command:

```
$ clinfo 
Number of platforms                               1
  Platform Name                                   Clover
  Platform Vendor                                 Mesa
  Platform Version                                OpenCL 1.1 Mesa 13.1.0-devel - padoka PPA
  Platform Profile                                FULL_PROFILE
  Platform Extensions                             cl_khr_icd
  Platform Extensions function suffix             MESA

  Platform Name                                   Clover
Number of devices                                 1
  Device Name                                     AMD POLARIS10 (DRM 3.2.0 / 4.7.0-040700-generic, LLVM 4.0.0)
  Device Vendor                                   AMD
  Device Vendor ID                                0x1002
  Device Version                                  OpenCL 1.1 Mesa 13.1.0-devel - padoka PPA
  Driver Version                                  13.1.0-devel - padoka PPA
  Device OpenCL C Version                         OpenCL C 1.1 
  Device Type                                     GPU
  Device Profile                                  FULL_PROFILE
  Max compute units                               36
  Max clock frequency                             0MHz
  Max work item dimensions                        3
  Max work item sizes                             256x256x256
  Max work group size                             256
incorrect number of operands in llvm.ident metadata
!1 = !{!"clang version 4.0.0-svn289636-0~x~padoka0 (trunk)", !"clang version 4.0.0-svn286863-0~x~padoka0 (trunk)"}
LLVM ERROR: Broken module found, compilation aborted!
```

i have previous results

GPU is seen by Blender 3D, but there is an error result in rendering try.
This is the error:
```

Device init success
Compiling OpenCL program base
OpenCL build failed with error CL_BUILD_PROGRAM_FAILURE, errors in console.
Error: Failed loading render kernel, see console for errors

```

Does Someone know how to resolve this problem?

Thanks!!!

---

