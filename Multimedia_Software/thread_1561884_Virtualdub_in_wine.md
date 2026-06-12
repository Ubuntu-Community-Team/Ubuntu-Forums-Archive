---
title: "Virtualdub in wine"
date: 2010-08-26
forum: Multimedia Software
---

### Post by someitalian123 on 2010-08-26
I'm getting this problem when I try to open a video file.

An out-of-bounds memory access (access violation) occurred in module 'wined3d'......reading address 00000030.

Is their anything that can be done?

---

### Post by someitalian123 on 2010-09-07
Heres a little more information 


wine: cannot find L"C:\\windows\\system32\\gearsec.exe" 
fixme:volume:GetVolumePathNameW (L"Z:\\home\\linux\\Desktop\\VirtualDub-1.9.10\\VirtualDub.jobs", 0x7bfe50, 260), stub! 
fixme:volume:GetVolumePathNameW (L"Z:\\home\\linux\\Desktop\\XM.avi", 0x7d1508, 260), stub! 
fixme:volume:GetVolumePathNameW (L"Z:\\home\\linux\\Desktop\\XM.avi", 0x7d1680, 260), stub! 
fixme:volume:GetVolumePathNameW (L"Z:\\home\\linux\\Desktop\\XM.avi", 0x7d1698, 260), stub! 
err:bitmap:DIB_GetBitmapInfo (0): unknown/wrong size for header 
err:bitmap:GetDIBits Invalid bitmap format 
err:bitmap:DIB_GetBitmapInfo (0): unknown/wrong size for header 
err:bitmap:GetDIBits Invalid bitmap format 
err:bitmap:DIB_GetBitmapInfo (0): unknown/wrong size for header 
err:bitmap:GetDIBits Invalid bitmap format 
err:bitmap:DIB_GetBitmapInfo (0): unknown/wrong size for header 
err:bitmap:GetDIBits Invalid bitmap format 
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems 
err:d3d_caps:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat.                        
err:d3d:InitAdapters Failed to get a gl context for default adapter                                 
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x5dd42460                   
wine client error:9: write: Bad file descriptor

Edit
NVM, problem solved by updating my video driver

---

