---
title: "WoW with Wine/ATI/Beryl"
date: 2007-04-27
forum: Multimedia &amp; Video
---

### Post by thejaymanncan on 2007-04-27
I have a problem getting WoW work with Wine. D3D works, but is the speed of slow. OpenGL however, does not work. The WTF file is configured to use OpenGL, but when I run WoW with Wine, I get this output

```
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
fixme:advapi:SetSecurityInfo stub
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:powrprof:DllMain (0x7e080000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7e080000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33edd4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f33c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5dc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5dc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f544,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f530,0x00000000), stub!

fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:get_fbconfig_from_visualid No fbconfig found for Wine's main visual (0x2c), expect problems!
err:wgl:init_formats Can't get the FBCONFIG_ID for the main visual, expect problems!
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
fixme:win:EnumDisplayDevicesW ((null),0,0x33f544,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f530,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x33f544,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f530,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:get_fbconfig_from_visualid No fbconfig found for Wine's main visual (0x2c), expect problems!
err:wgl:init_formats Can't get the FBCONFIG_ID for the main visual, expect problems!
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 1
err:wgl:X11DRV_ChoosePixelFormat Can't find a matching FBCONFIG_ID for VISUAL_ID 0x2c!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f544,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f530,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:get_fbconfig_from_visualid No fbconfig found for Wine's main visual (0x2c), expect problems!
err:wgl:init_formats Can't get the FBCONFIG_ID for the main visual, expect problems!
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 1
err:wgl:X11DRV_ChoosePixelFormat Can't find a matching FBCONFIG_ID for VISUAL_ID 0x2c!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f544,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f530,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:get_fbconfig_from_visualid No fbconfig found for Wine's main visual (0x2c), expect problems!
err:wgl:init_formats Can't get the FBCONFIG_ID for the main visual, expect problems!
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 1
err:wgl:X11DRV_ChoosePixelFormat Can't find a matching FBCONFIG_ID for VISUAL_ID 0x2c!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f544,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f530,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:get_fbconfig_from_visualid No fbconfig found for Wine's main visual (0x2c), expect problems!
err:wgl:init_formats Can't get the FBCONFIG_ID for the main visual, expect problems!
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 1
err:wgl:X11DRV_ChoosePixelFormat Can't find a matching FBCONFIG_ID for VISUAL_ID 0x2c!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f544,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f530,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:get_fbconfig_from_visualid No fbconfig found for Wine's main visual (0x2c), expect problems!
err:wgl:init_formats Can't get the FBCONFIG_ID for the main visual, expect problems!
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 1
err:wgl:X11DRV_ChoosePixelFormat Can't find a matching FBCONFIG_ID for VISUAL_ID 0x2c!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f544,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f530,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:get_fbconfig_from_visualid No fbconfig found for Wine's main visual (0x2c), expect problems!
err:wgl:init_formats Can't get the FBCONFIG_ID for the main visual, expect problems!
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 1
err:wgl:X11DRV_ChoosePixelFormat Can't find a matching FBCONFIG_ID for VISUAL_ID 0x2c!

```

The screen flickers a few times, and I get the message "could not startup 3d accerleration" or something like that. I don't understand how that is, because I am running Beryl with XGL just fine. Do you guys know whats wrong?

EDIT: Oh yeah, I'm running a X1900GT using fglrx.

---

### Post by LuisGMarine on 2007-04-27
Did you disable beryl before you started to play WoW?  I know that for me ( nvidia 6800 GTX PCI-E ) runing beryl and trying to game is a no go.

---

### Post by thejaymanncan on 2007-04-27
Yup, still doesn't work.

---

### Post by Praill on 2007-05-30
The problem isnt beryl wow or wine, its XGL.
I dont actually know all the technical reasons for why it happens (like it matters) but whatever XGL does to enable composite extensions for running beryl consquently disables opengl functionality as evidenced by this line of your output:
Xlib:  extension "XFree86-DRI" missing on display ":1.0".

This is why I hate XGL and ATI. I want nvidia :(

---

### Post by gummo on 2007-07-04
> **Praill said:**
> 
Xlib:  extension "XFree86-DRI" missing on display ":1.0".


THE line of doom :(

---

