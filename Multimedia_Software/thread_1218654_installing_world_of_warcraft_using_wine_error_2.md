---
title: "installing world of warcraft using wine error 2"
date: 2009-07-20
forum: Multimedia Software
---

### Post by Foeburner on 2009-07-20
I've read all the world of warcraft installation posts but none of them get me past this one error while installing world of warcraft. It gets to about half way before i get this message:

 The file "Repack-MPQ\Data#base.MPQ\Data\connection-help.html" in archive "<unknown>" could not be opened, because an error 2 occurred. If this problem persists, please contact Blizzard Technical Support. (MPQFile::OpenFromArchive)

I have copied all the files from all disks to a folder on my desktop and have followed all instructions without skipping a step. I followed this tutorial lastly [http://geeks.pirillo.com/profiles/blogs/how-to-install-world-of]("http://geeks.pirillo.com/profiles/blogs/how-to-install-world-of")

When running wine in the terminal, I get this error before the WoW installer window opens. 

btw is there any extra steps to install wrath of the lich king?

also, i have some experience with ubuntu as I setup a vpn server and a samba server from scratch at my workplace. 

Any help is greatly appreciated.



root@Ubuntu:/home/fuentes/Desktop/wow# wine installer.exe
wine: created the configuration directory '/root/.wine'
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x33cf94
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\gecko\\0.9.1\\wine_gecko\\components\\xpti.dat" 1 536870916 (nil) (nil) 0x33c960 (nil)
fixme:iphlpapi:NotifyAddrChange (Handle 0x2dae888, overlapped 0x2dae890): stub
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\gecko\\0.9.1\\wine_gecko\\components\\compreg.dat" 1 536870916 (nil) (nil) 0x33ca50 (nil)
0[1958b8]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\freebl3.dll") - Symbol NSGetModule not found
0[1958b8]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\xpcom.dll") - Symbol NSGetModule not found
0[1958b8]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\plds4.dll") - Symbol NSGetModule not found
0[1958b8]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\xul.dll") - Symbol NSGetModule not found
0[1958b8]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nssdbm3.dll") - Symbol NSGetModule not found
0[1958b8]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\plugins\npnul32.dll") - Symbol NSGetModule not found
0[1958b8]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\js3250.dll") - Symbol NSGetModule not found
0[1958b8]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\softokn3.dll") - Symbol NSGetModule not found
0[1958b8]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nssutil3.dll") - Symbol NSGetModule not found
0[1958b8]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nss3.dll") - Symbol NSGetModule not found
0[1958b8]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\plc4.dll") - Symbol NSGetModule not found
0[1958b8]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\ssl3.dll") - Symbol NSGetModule not found
0[1958b8]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\sqlite3.dll") - Symbol NSGetModule not found
0[1958b8]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\smime3.dll") - Symbol NSGetModule not found
0[1958b8]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nspr4.dll") - Symbol NSGetModule not found
0[1958b8]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nssckbi.dll") - Symbol NSGetModule not found
fixme:shell:DllCanUnloadNow stub
get fences failed: -1
param: 6, val: 0
wine: configuration in '/root/.wine' has been updated.
root@Ubuntu:/home/fuentes/Desktop/wow# fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:font:CreateScalableFontResourceW (1,L"C:\\windows\\temp\\Blizzard Installer Temp - 00001d62\\FrizQuadrata.fot",L"C:\\windows\\temp\\Blizzard Installer Temp - 00001d62\\FrizQuadrata.ttf",(null)): stub
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:ole:OleCreateStaticFromData (not shown), stub!

---

### Post by Foeburner on 2009-07-21
I just read that an alternative to wine, cedega runs it better but i wasnt able to find if cedega itself is free or if the monthly subscription is needed to run cedega. 

Can anyone elaborate on this?

---

### Post by Blake_K on 2009-11-12
Cedega does have a cost. $25 for 6 months or $45 for 1 year.

---

### Post by Mannatron on 2009-11-14
i installed it on wine 3 moths ago and everything went just fine and dandy until the latest patch came out.  it wouldn't apply(I used every troubleshooting solution on these forums AND blizzard)  so I thought maybe it's be easier to remove it and re install.

I've been working on installing it for the past 2 days with no luck.  when downloading from the blizzard site I get an error message at 87% telling me there is not enough space on my hard drive (I have more than 2x the amount of space needed).

I cleaned up my hard drive with a directory size program to free up space, but every time I downloaded it stopped at the same %

So I tried installing it the old fashioned way (with the cds), and the installer won't run, it gives me the error message

'Sorry, the installer was unable to start up, you may be out of hard drive space'

wow needs 10.1 GB to install, (6.5 after installation) and I have 18.6 GB free..  any ideas what the problem could be?

---

