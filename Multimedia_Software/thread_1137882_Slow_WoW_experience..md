---
title: "Slow WoW experience."
date: 2009-04-26
forum: Multimedia Software
---

### Post by gecus on 2009-04-26
Distro: Ubuntu 9.04 Jaunty Jackalope
Graphics Card: Nvidia FX 5500
```
john@john-desktop:~$ glxinfo | grep direct
direct rendering: Yes

```

I have the NVIDIA accelerated drivers (version 173) enabled, I still cannot activate desktop effects either but this is not my primary concern. I just finished installing and patching WoW in wine and when I went to play it took me 10 minutes to get to the logon screen it was so bad. I only got to the logon screen 1/4 attempts, the other times the application just suddenly shut down. Here is the contents of my terminal window when running WoW:

```
john@john-desktop:~$ cd ~/.wine/
john@john-desktop:~/.wine$ dir
dosdevices  drive_c  system.reg  userdef.reg  user.reg
john@john-desktop:~/.wine$ cd drive_c
john@john-desktop:~/.wine/drive_c$ cd Program\ Files
john@john-desktop:~/.wine/drive_c/Program Files$ cd World\ of\ Warcraft
john@john-desktop:~/.wine/drive_c/Program Files/World of Warcraft$ wine Launcher.exe
fixme:shdocvw:PersistStreamInit_Load (0x13f7b0)->(0x32d9a0)
fixme:shdocvw:OleControl_FreezeEvents (0x13f7b0)->(1)
fixme:shdocvw:OleControl_FreezeEvents (0x13f7b0)->(0)
fixme:shell:IShellLinkA_fnGetPath (0x13fdb8): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x13fd98): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x13fd98): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x13fd98): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x13fd98): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x13fd98): WIN32_FIND_DATA is not yet filled.
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x32c824
0[16ea00]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\xpcom.dll") - Symbol NSGetModule not found
0[16ea00]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nssutil3.dll") - Symbol NSGetModule not found
0[16ea00]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\softokn3.dll") - Symbol NSGetModule not found
0[16ea00]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nssckbi.dll") - Symbol NSGetModule not found
0[16ea00]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\plugins\npnul32.dll") - Symbol NSGetModule not found
fixme:iphlpapi:NotifyAddrChange (Handle 0x23fe888, overlapped 0x23fe890): stub
0[16ea00]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nspr4.dll") - Symbol NSGetModule not found
0[16ea00]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\smime3.dll") - Symbol NSGetModule not found
0[16ea00]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\sqlite3.dll") - Symbol NSGetModule not found
0[16ea00]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nssdbm3.dll") - Symbol NSGetModule not found
0[16ea00]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\plds4.dll") - Symbol NSGetModule not found
0[16ea00]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\plc4.dll") - Symbol NSGetModule not found
0[16ea00]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\js3250.dll") - Symbol NSGetModule not found
0[16ea00]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\freebl3.dll") - Symbol NSGetModule not found
0[16ea00]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\xul.dll") - Symbol NSGetModule not found
0[16ea00]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\ssl3.dll") - Symbol NSGetModule not found
0[16ea00]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nss3.dll") - Symbol NSGetModule not found
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x13f850)->((null) 1 0x32cdbc (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x13f850)->((null) 25 2 0x32cdd0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x13f850)->((null) 26 2 0x32cdd0 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x13f850)->(0x32ce0c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x13f850)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32cee0 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x145f90)->(L"" L"" 0 0x32cf18)
fixme:shdocvw:ClOleCommandTarget_Exec (0x13f850)->((null) 29 2 0x32d4bc (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x13f850)
fixme:shdocvw:ClientSite_GetContainer (0x13f850)->(0x32d2fc)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x13f850)->(0xb7edb051)
fixme:shdocvw:ClOleCommandTarget_Exec (0x13f850)->((null) 25 2 0x32d230 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x13f850)->((null) 26 2 0x32d230 (nil))
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 10000
fixme:shdocvw:ClOleCommandTarget_Exec (0x13f850)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x13f850)->((null) 28 2 0x32df3c (nil))
0[16ea00]: NPN Logging Active!
0[16ea00]: General Plugin Logging Active! (nsPluginHostImpl::ctor)
0[16ea00]: NPP Logging Active!
0[16ea00]: nsPluginHostImpl::ctor
fixme:resource:GetGuiResources (0xffffffff,0): stub
fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x13f7b0)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x162a00)->((nil))
fixme:shdocvw:OleObject_Close (0x13f7b0)->(1)
fixme:shell:DllCanUnloadNow stub
john@john-desktop:~/.wine/drive_c/Program Files/World of Warcraft$ fixme:advapi:SetSecurityInfo stub
archive Data\enUS\patch-enUS.MPQ opened
archive Data\patch.MPQ opened
archive Data\enUS\patch-enUS-2.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\expansion.MPQ opened
archive Data\lichking.MPQ opened
archive Data\common.MPQ opened
archive Data\common-2.MPQ opened
archive Data\enUS\locale-enUS.MPQ opened
archive Data\enUS\speech-enUS.MPQ opened
archive Data\enUS\expansion-locale-enUS.MPQ opened
archive Data\enUS\lichking-locale-enUS.MPQ opened
archive Data\enUS\expansion-speech-enUS.MPQ opened
archive Data\enUS\lichking-speech-enUS.MPQ opened
fixme:win:EnumDisplayDevicesW ((null),0,0x3aedac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3aebd0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af0a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af2b0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af3f0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af588,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af584,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af5dc,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:win:EnumDisplayDevicesW ((null),0,0x3af008,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af140,0x00000000), stub!
failed to open C:/Program Files/World of Warcraft/Interface/AddOns
fixme:win:EnumDisplayDevicesW ((null),0,0x3adeec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3adf24,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3adee0,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:reg:GetNativeSystemInfo (0x37402bc4) using GetSystemInfo()
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:imm:ImmReleaseContext (0x50066, 0x13c5c0): stub

```

---

### Post by gotos on 2009-04-26
I use the 180.44 Nvidia Drivers and Desktop effects are running, but WoW is running slow for me too.

Are you running WoW in OpenGL mode?
cd /to your Wow Directory
wine Wow.exe -opengl

---

### Post by gecus on 2009-04-26
> **gotos said:**
> I use the 180.44 Nvidia Drivers and Desktop effects are running, but WoW is running slow for me too.

Are you running WoW in OpenGL mode?
cd /to your Wow Directory
wine Wow.exe -opengl

That helps A LOT. Anymore optimization I can do? I lowered all settings and I run at about 9 fps

---

### Post by gotos on 2009-04-27
Try this Troubleshooting guide:
[html]http://www.wowwiki.com/Wine/Troubleshooting[/html]

I have a nvidia 6200 (512Mb) and I have 6-15 FPS in Dala but it is playable. In SW/IF I get 20FPS.

---

