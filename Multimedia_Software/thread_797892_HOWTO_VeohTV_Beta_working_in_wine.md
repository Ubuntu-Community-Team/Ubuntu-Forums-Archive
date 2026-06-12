---
title: "HOWTO: VeohTV Beta working in wine"
date: 2008-05-17
forum: Multimedia Software
---

### Post by BwackNinja on 2008-05-17
Okay, this is probably my first worthwhile post here. Anyway...

To get VeohTV Beta working in wine
Prerequisites:
- VeohTV Beta installer ([http://www.veoh.com/veohTV/getStarted.html](http://www.veoh.com/veohTV/getStarted.html))
- wine (of course)
- a working windows partition (more about this later)
- Mozilla Firefox for windows ([http://www.mozilla.com/en-US/firefox/](http://www.mozilla.com/en-US/firefox/))
- winetricks (wget [http://kegel.com/wine/winetricks](http://kegel.com/wine/winetricks))
- a few dlls (urlmon.dll, pdh.dll, wininet.dll, odbcbcp.dll)



1. install VeohTV Beta in Windows and LOGIN (Note: login does not work in wine due to lack of RAS support, but exporting registry keys from an installed copy from windows allows you to be logged in)

2. open regedit and export the key "HKCU/Software/Veoh" as Win9x/NT4 format

3. create a new wineprefix
```
wineprefixcreate --prefix ~/.veohtv
```

4. import the key with wine regedit
```
WINEPREFIX=~/.veohtv wine regedit
```

5. copy C:\Program Files\Veoh Networks\ to ~/.veohtv/drive_c/Veoh Networks/

6. get winetricks if you don't already have it
```
wget [http://kegel.com/wine/winetricks](http://kegel.com/wine/winetricks)
```
and get native gdiplus
```
WINEPREFIX=~/.veohtv sh winetricks gdiplus
```

7. add the other dlls (urlmon.dll, pdh.dll, wininet.dll, odbcbcp.dll) to ~/.veohtv/drive_c/windows/system32/ (overwrite when asked)

8. open winecfg
```
WINEPREFIX=~/.veohtv winecfg
```
and add native dll overrides for urlmon.dll, pdh.dll, wininet.dll, and odbcbcp.dll

9. install windows firefox (make sure it is in this wineprefix) and install flash.

10. run VeohTV Beta
```
WINEPREFIX=~/.veohtv wine "C:\Program Files\Veoh Networks\Veoh\VeohClient.exe"
```
and go into "settings" (right-click the tray icon and click "settings") go to the "Plug-in" tab and install the plugin for firefox
(you can also add this command to your menu)

11. ENJOY!
:popcorn:

tested in wine 0.9.61 on ubuntu hardy

PS: if you have any problems or have anything to add, don't hesitate to post

---

### Post by El Lance-O on 2008-05-17
I don't have a working windows partition. :(

I abandoned that nonsense 2 years ago, and have never had enough interest to go back at all. Virtualbox some day I'm sure though.

Could I message you my account login and could you send me the reg file? I have no access to a windows computer, and I would love to get this working.

Watching movies in 10+ parts in poor quality loses it's interest after awhile.

But thank you for doing this! All the other methods of downloading the .flv file has been patched or just doesn't work. This will definitely be a great improvement since Veoh has no interest in creating a native linux client.

---

### Post by BwackNinja on 2008-05-18
Sure.

As an update to this, some codecs need to be installed for some downloaded files to be able to be played. They work perfectly in native linux media players (but the codecs can be installed in wine too, I'm currently messing around with my setup to get as much as I can to work well. xvid works, and I think I got h.264 or w/e working for a while). This is especially important because veoh had one feature that I never really saw anywhere in linux, a video library. Flash also needs to be installed through firefox for the "interact" tab to display stuff on the side. I'll edit my first post tomorrow...

PS: I also gave up on windows a while ago, and now I only have it in VirtualBox. You'd be surprised about how it comes in handy sometimes. :D

---

### Post by El Lance-O on 2008-05-18
I would love to use VirualBox, but I don't have an XP disk handy. But with a good setup on Compiz I would imagine it to be quit awesome switching to a windows side of the cube.

Quite awesome indeed.

I am going to message you the info now. I noticed a lot of things like you mentioned didn't work when I downloaded the beta installer and just tried it out. Everything installed fine, no errors, no crashes, so I think this method should work no problem.

I'm so excited for Veoh! :popcorn:

---

### Post by koocho on 2008-05-18
thanks for doing the howto! 

but i have the problem that i can't find the key in step 2 :) its not listed in my regedit...?

koocho

---

### Post by BwackNinja on 2008-05-18
did you open veohtv and login with your veoh account first?

edit: oh, HKCU = HKey_Current_User

---

### Post by koocho on 2008-05-18
ah thx^

everything installed fine but when i'm trying to load a video in veoh i got an error and it wants me to install flash player - veoh opens a window with the download site of flash player but when i click on download the window turns white and nothing happens... i followed your guide exactly. any idea whats wrong?

and sry for my bad english ;)

koocho

---

### Post by BwackNinja on 2008-05-18
oops, sorry, I put that in my second post and didn't update the guide, just open firefox and install flash from there.

---

### Post by koocho on 2008-05-19
sry don't want to annoy you but it still won't work. flash was installed on ffox before thats why i wondered that veoh wanted me to install again when i click on "install codecs" ... strange :-D

koocho

---

### Post by BwackNinja on 2008-05-19
did you install it in windows firefox in that wineprefix?

---

### Post by koocho on 2008-05-19
yep... i try it again from the beginning on :?

---

### Post by El Lance-O on 2008-05-19
Yeah I am getting the same problem. I realized I did in fact have the Veoh Networks folder, I just didn't realize the location I was trying to use the wine prefix on was relevant to a Windows partition, not one under WINE.

Confused me a little bit.

I can get VeohTV up and running no problem, but text is impossible to read as it is all blacked out, and every time I try and watch a video, I get a error saying it could not play <video title/> or something like that.

And then it asks me to install flash as well.

Getting close though! :D

---

### Post by BwackNinja on 2008-05-19
if anything is blacked out, that means you don't have native urlmon.dll, download it (just search google) and put it in ~/.veohtv/drive_c/windows/system32/ and put a dll override. and MAKE SURE YOU ARE RUNNING STUFF FROM THAT WINEPREFIX! if you are just doing "wine file" rather than "WINEPREFIX=~/.veoh file" then you are using settings from .wine instead of .veoh, where everything was set. And I'm also talking about installing firefox IN THAT WINEPREFIX, and opening it there, and going to say
[http://www.macromedia.com/software/flash/about/](http://www.macromedia.com/software/flash/about/) in that firefox under wine in that WINEPREFIX
and clicking the little puzzle peice to install missing plugin, flash.

This howto is using wine's slightly lesser known "bottle" functionality, pretty much giving you the equivalent of a new windows drive.

---

### Post by El Lance-O on 2008-05-19
Alright, got some new errors for you. For some reason it doesn't want to acknowledge the .dll overrides, and I get this when starting it.

```
$ WINEPREFIX=~/.veohtv wine "C:\Program Files\Veoh\ Networks\Veoh\VeohClient.exe"
wine: cannot find 'C:\Program Files\Veoh\ Networks\Veoh\VeohClient.exe'
ellanceo@TheThinGreyBox:~$ WINEPREFIX=~/.veohtv wine /home/ellanceo/.wine/drive_c/Program\ Files/Veoh\ Networks/Veoh/VeohClient.exe
err:module:import_dll Library ODBC32.dll (which is needed by L"C:\\windows\\system32\\pdh.dll") not found
err:module:import_dll Library ODBC32.dll (which is needed by L"C:\\windows\\system32\\odbcbcp.dll") not found
err:module:import_dll Library odbcbcp.dll (which is needed by L"C:\\windows\\system32\\pdh.dll") not found
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:EnumDisplayDevicesW ((null),0,0x32e3a4,0x00000000), stub!
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x100aa 0x00000000
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:bitblt:X11DRV_ClientSideDIBCopy potential optimization: pixel format conversion
fixme:bitblt:X11DRV_ClientSideDIBCopy potential optimization: pixel format conversion
fixme:bitblt:X11DRV_ClientSideDIBCopy potential optimization: pixel format conversion
fixme:bitblt:X11DRV_ClientSideDIBCopy potential optimization: pixel format conversion
fixme:bitblt:X11DRV_ClientSideDIBCopy potential optimization: pixel format conversion
fixme:bitblt:X11DRV_ClientSideDIBCopy potential optimization: pixel format conversion
fixme:bitblt:X11DRV_ClientSideDIBCopy potential optimization: pixel format conversion
fixme:bitblt:X11DRV_ClientSideDIBCopy potential optimization: pixel format conversion
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
wine: Call from 0x7b8446d0 to unimplemented function pdh.dll.PdhEnumObjectItemsA, aborting
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set
wine: Unimplemented function pdh.dll.PdhEnumObjectItemsA called at address 0x7b8446d0 (thread 001a), starting debugger...
Unhandled exception: unimplemented function pdh.dll.PdhEnumObjectItemsA called in 32-bit code (0x7b844746).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b844746 ESP:7d9b842c EBP:7d9b8490 EFLAGS:00000212(   - 00      - -IA1)
 EAX:7b82eac9 EBX:7b8b3884 ECX:00000000 EDX:00cca460
 ESI:00cca460 EDI:005f22f0
Stack dump:
0x7d9b842c:  7d9b84b8 00000008 7d9b8454 7bc4257e
0x7d9b843c:  80000100 00000001 00000000 7b8446d0
0x7d9b844c:  00000002 7e4b5020 7e4b51c4 7bc4384e
0x7d9b845c:  00cc0048 00000000 00000000 00000000
0x7d9b846c:  00000000 00000000 00000000 00000000
0x7d9b847c:  00000000 00000000 00000000 00000000
Backtrace:
=>1 0x7b844746 in kernel32 (+0x24746) (0x7d9b8490)
  2 0x7e4b4fb5 in pdh (+0x14fb5) (0x7d9b84c0)
0x7b844746: movl	0xfffffffc(%ebp),%ebx
Modules:
Module	Address			Debug info	Name (124 modules)
PE	  400000-  77c000	Deferred        veohclient
PE	10000000-1001c000	Deferred        bugsplat
PE	39800000-399b2000	Deferred        gdiplus
ELF	7b800000-7b92d000	Export          kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7bc00000-7bca4000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7cf8e000-7cf99000	Deferred        libgcc_s.so.1
ELF	7d0aa000-7d0b0000	Deferred        libnss_dns.so.2
ELF	7d0b0000-7d0b3000	Deferred        libnss_mdns4_minimal.so.2
ELF	7d31c000-7d366000	Deferred        dbghelp<elf>
  \-PE	7d320000-7d366000	\               dbghelp
ELF	7db09000-7db1e000	Deferred        psapi<elf>
  \-PE	7db10000-7db1e000	\               psapi
ELF	7dd4e000-7dd52000	Deferred        libgpg-error.so.0
ELF	7dd52000-7dd9f000	Deferred        libgcrypt.so.11
ELF	7dd9f000-7ddaf000	Deferred        libtasn1.so.3
ELF	7ddaf000-7ddb7000	Deferred        libkrb5support.so.0
ELF	7ddb7000-7dde9000	Deferred        libcrypt.so.1
ELF	7dde9000-7de5e000	Deferred        libgnutls.so.13
ELF	7de5e000-7de81000	Deferred        libk5crypto.so.3
ELF	7de81000-7df0e000	Deferred        libkrb5.so.3
ELF	7df0e000-7df37000	Deferred        libgssapi_krb5.so.2
ELF	7df37000-7df6a000	Deferred        libcups.so.2
ELF	7df6a000-7df7e000	Deferred        wtsapi32<elf>
  \-PE	7df70000-7df7e000	\               wtsapi32
ELF	7dfc7000-7dffa000	Deferred        uxtheme<elf>
  \-PE	7dfd0000-7dffa000	\               uxtheme
ELF	7dffa000-7e020000	Deferred        msacm32<elf>
  \-PE	7e000000-7e020000	\               msacm32
ELF	7e020000-7e037000	Deferred        msacm32<elf>
  \-PE	7e030000-7e037000	\               msacm32
ELF	7e037000-7e0fa000	Deferred        libasound.so.2
ELF	7e0fa000-7e10e000	Deferred        midimap<elf>
  \-PE	7e100000-7e10e000	\               midimap
ELF	7e10e000-7e143000	Deferred        winealsa<elf>
  \-PE	7e120000-7e143000	\               winealsa
ELF	7e143000-7e14c000	Deferred        libxcursor.so.1
ELF	7e14c000-7e151000	Deferred        libxfixes.so.3
ELF	7e151000-7e154000	Deferred        libxcomposite.so.1
ELF	7e154000-7e15a000	Deferred        libxrandr.so.2
ELF	7e15a000-7e162000	Deferred        libxrender.so.1
ELF	7e162000-7e165000	Deferred        libxinerama.so.1
ELF	7e165000-7e185000	Deferred        imm32<elf>
  \-PE	7e170000-7e185000	\               imm32
ELF	7e185000-7e18a000	Deferred        libxdmcp.so.6
ELF	7e18a000-7e1a2000	Deferred        libxcb.so.1
ELF	7e1a2000-7e1a5000	Deferred        libxau.so.6
ELF	7e1a5000-7e28c000	Deferred        libx11.so.6
ELF	7e28c000-7e29a000	Deferred        libxext.so.6
ELF	7e29a000-7e29f000	Deferred        libxxf86vm.so.1
ELF	7e29f000-7e2b7000	Deferred        libice.so.6
ELF	7e2b7000-7e2bf000	Deferred        libsm.so.6
ELF	7e2c1000-7e2c4000	Deferred        libkeyutils.so.1
ELF	7e2ce000-7e2d1000	Deferred        libcom_err.so.2
ELF	7e2d3000-7e369000	Deferred        winex11<elf>
  \-PE	7e2e0000-7e369000	\               winex11
ELF	7e394000-7e3b5000	Deferred        libexpat.so.1
ELF	7e3b5000-7e3df000	Deferred        libfontconfig.so.1
ELF	7e3f3000-7e408000	Deferred        libz.so.1
ELF	7e408000-7e478000	Deferred        libfreetype.so.6
ELF	7e478000-7e47a000	Deferred        libxcb-xlib.so.0
ELF	7e48c000-7e49f000	Deferred        msimg32<elf>
  \-PE	7e490000-7e49f000	\               msimg32
ELF	7e49f000-7e4b9000	Export          pdh<elf>
  \-PE	7e4a0000-7e4b9000	\               pdh
ELF	7e4b9000-7e55b000	Deferred        oleaut32<elf>
  \-PE	7e4d0000-7e55b000	\               oleaut32
ELF	7e55b000-7e591000	Deferred        winspool<elf>
  \-PE	7e560000-7e591000	\               winspool
ELF	7e591000-7e63c000	Deferred        comdlg32<elf>
  \-PE	7e5a0000-7e63c000	\               comdlg32
ELF	7e63c000-7e6a5000	Deferred        msvcrt<elf>
  \-PE	7e650000-7e6a5000	\               msvcrt
ELF	7e6a5000-7e6be000	Deferred        version<elf>
  \-PE	7e6b0000-7e6be000	\               version
ELF	7e6be000-7e6fd000	Deferred        urlmon<elf>
  \-PE	7e6d0000-7e6fd000	\               urlmon
ELF	7e6fd000-7e7bc000	Deferred        comctl32<elf>
  \-PE	7e710000-7e7bc000	\               comctl32
ELF	7e7bc000-7e8cb000	Deferred        shell32<elf>
  \-PE	7e7d0000-7e8cb000	\               shell32
ELF	7e8cb000-7e924000	Deferred        shlwapi<elf>
  \-PE	7e8e0000-7e924000	\               shlwapi
ELF	7e924000-7e945000	Deferred        mpr<elf>
  \-PE	7e930000-7e945000	\               mpr
ELF	7e945000-7e993000	Deferred        wininet<elf>
  \-PE	7e950000-7e993000	\               wininet
ELF	7e993000-7ea37000	Deferred        ole32<elf>
  \-PE	7e9a0000-7ea37000	\               ole32
ELF	7ea37000-7eac9000	Deferred        winmm<elf>
  \-PE	7ea40000-7eac9000	\               winmm
ELF	7eac9000-7eb2a000	Deferred        rpcrt4<elf>
  \-PE	7eae0000-7eb2a000	\               rpcrt4
ELF	7eb2a000-7ebc5000	Deferred        gdi32<elf>
  \-PE	7eb40000-7ebc5000	\               gdi32
ELF	7ebc5000-7ed0c000	Deferred        user32<elf>
  \-PE	7ebe0000-7ed0c000	\               user32
ELF	7ed0c000-7ed74000	Deferred        crypt32<elf>
  \-PE	7ed20000-7ed74000	\               crypt32
ELF	7ed74000-7ed9a000	Deferred        netapi32<elf>
  \-PE	7ed80000-7ed9a000	\               netapi32
ELF	7ed9a000-7edc1000	Deferred        secur32<elf>
  \-PE	7eda0000-7edc1000	\               secur32
ELF	7edc1000-7ee13000	Deferred        advapi32<elf>
  \-PE	7edd0000-7ee13000	\               advapi32
ELF	7ee13000-7ee26000	Deferred        libresolv.so.2
ELF	7ee26000-7ee3a000	Deferred        lz32<elf>
  \-PE	7ee30000-7ee3a000	\               lz32
ELF	7ee3a000-7ee58000	Deferred        iphlpapi<elf>
  \-PE	7ee40000-7ee58000	\               iphlpapi
ELF	7ee58000-7ee84000	Deferred        ws2_32<elf>
  \-PE	7ee60000-7ee84000	\               ws2_32
ELF	7efa4000-7efaf000	Deferred        libnss_files.so.2
ELF	7efaf000-7efc7000	Deferred        libnsl.so.1
ELF	7efc7000-7efec000	Deferred        libm.so.6
ELF	7eff6000-7f000000	Deferred        libnss_nis.so.2
ELF	b7d12000-b7d1b000	Deferred        libnss_compat.so.2
ELF	b7d1c000-b7d20000	Deferred        libdl.so.2
ELF	b7d20000-b7e6f000	Deferred        libc.so.6
ELF	b7e70000-b7e88000	Deferred        libpthread.so.0
ELF	b7e9c000-b7fd2000	Deferred        libwine.so.1
ELF	b7fd4000-b7ff0000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) Z:\home\ellanceo\.wine\drive_c\Program Files\Veoh Networks\Veoh\VeohClient.exe
	0000001e    0
	0000001b    0
	0000001a    0 <==
	00000019    0
	00000009    0
0000000c 
	00000014    0
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000016    0
	00000015    0
	00000011    0
	00000010    0
00000017 
	00000018    0
00000023 
	00000024    0
Backtrace:
=>1 0x7b844746 in kernel32 (+0x24746) (0x7d9b8490)
  2 0x7e4b4fb5 in pdh (+0x14fb5) (0x7d9b84c0)
wine: Call from 0x7b8446d0 to unimplemented function pdh.dll.PdhEnumObjectItemsHA, aborting
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
err:ntdll:RtlpWaitForCriticalSection section 0x720774 "?" wait timed out in thread 001b, blocked by 001a, retrying (60 sec)
```

Everything looks fine when I start it up, kinda. Prompts as I said before are for the most part blacked out. I reinstalled Firefox under that WINEPREFIX, as well as flash, and it is still saying that I don't have it.

:(

---

### Post by RequinB4 on 2008-05-19
Does this HOWTO require Adobe's Flash (flashplugin-nonfree) or is there Gnash support as well?  Most likely this would be in the hands of the VeohTV devs, but...

---

### Post by BwackNinja on 2008-05-20
did you download the dll files and put them in ~/.veohtv/drive_c/windows/system32 ? You need the dlls to do native dll overrides. The native urlmon.dll specifically fixes the blacked out interface. You can download any of these from a quick google search for them.

as for the gnash support, AFAIK, gnash does not work (yet) in windows, and thus wouldn't work in wine. It would be nice though if eventually wine would be able to use linux native libraries instead of windows native ones.

---

### Post by El Lance-O on 2008-05-20
Yeah I did all that, and did the overrides in winecfg under that WINEPREFIX, and set them all as native,builtin, and it still is all blacked out.

odbcbcp doesn't even show up either. :confused:

---

### Post by koocho on 2008-05-21
> **El Lance-O said:**
> odbcbcp doesn't even show up either. :confused:

i have the same problem, too...

---

### Post by Gazelle on 2008-05-24
Hi BwackNinja... I'm really new to all this. I went to Veoh TV and tried to install it. Now it's on my desktop and can be opened with Wine, but after logging in to VeohTV the movie won't play.

So I tried to move the Veoh TV setup into a directory to immediately connect it with Wine, but I don't know where wine is stored. Have flash, haven't got Windows. Can you please tell me what to do?

help very much appreci,,

thanx

---

### Post by BwackNinja on 2008-05-25
If you have any experience with windows, you'd know how the "C:\" drive is setup, and a wineprefix emulates this as well as the windows api, allowing windows programs to function in some non-windows operating systems. The default wineprefix is the folder ".wine" in your home folder. In this howto, I made a new wineprefix to encompass only veohtv so that any dll overrides will not interfere with any other currently working programs in wine that you already have installed.

You say you were able to log into veohtv, how so? Are you talking about logging into the veoh site? I was pretty sure that the login didn't work in wine. Also, the flash that I'm talking about isn't gnash or even flashplugin-nonfree, it is adobe flash player for _windows_ and is necessary for most videos to play in veohtv. This can be done with a "sh winetricks flash" if you have winetricks as I specified in my first post or you can download the installer, which does the same thing, but in firefox, which is also something that must be installed in wine (firefox for _windows_ ) enabling the plugin for flash by going to a site that requires flash and clicking the little puzzle piece to install the plugin allows the "interact" tab of veohtv to display everything.

---

### Post by BwackNinja on 2008-06-16
El Lance-O, if you ever look back here, I think your problem is how you set the whole thing up. Based on your command, you are mixing two WINEPREFIXES, .veohtv and .wine. It looks like you installed veohtv by just double-clicking on the installer, that's why it went to .wine instead of .veohtv, which is why your first command did not work. You also may have used winecfg on the .wine directory rather than the .veohtv directory (aka opening it from the menu probably). Otherwise it would probably have worked.

Maybe I should just tell people to have a clean .wine directory....

---

### Post by rsarda on 2008-08-19
Could you please explain step 9. 

@install windows firefox (make sure it is in this wineprefix) " a bit more please 

Many Thanks

---

### Post by BwackNinja on 2008-08-21
Sorry for the delay, it used to mean something slightly more complicated with a terminal command that could be long, but now its just:

```
WINEPREFIX=~/.veohtv
sh winetricks
```
and then select firefox 3

This howto is getting a bit outdated (the command wineprefixcreate no longer exists) but I can have it all updated tomorrow, seeing that at least one person is interested. I will even add an extra fun part of having it integrate with native firefox rather than having it just connected with a firefox in wine.

As it is now, it may work for you, but stay tuned! I'll even make sure it works on a clean install and may make a script that will do almost all of it for you.

---

### Post by 569874123 on 2009-01-27
bump

---

### Post by BwackNinja on 2009-01-28
This guide is now useless because now VeohTV doesn't work at all, while there is Veoh Web Player that replaces it. If I can find anything interesting related to veoh in linux, I'll post.

---

### Post by NeoZiggy on 2009-02-09
LOL, I suppose it pays to check the end of the posts first. Now to remove all the junk I installed and recover disk space. If anyone knows how to get this thing working easily in hardy, please let me know. Until then I'll just have to use torrents to get the anime I wanted to see.
-sigh-

---

### Post by BwackNinja on 2009-02-09
One word, veohdownloader - [http://code.google.com/p/veohdownloader/](http://code.google.com/p/veohdownloader/)

Happy downloading.

---

### Post by NeoZiggy on 2009-02-10
> **BwackNinja said:**
> One word, veohdownloader - [http://code.google.com/p/veohdownloader/](http://code.google.com/p/veohdownloader/)

Happy downloading.

Ah, yes. Sounds good. Reminds me of another firefox plugin I use called DownloadHelper, which is great for youtube and all those others out there.

Thanks for the tip! :popcorn:

---

### Post by RequinB4 on 2009-02-10
Bwack - you should edit the OP so people don't mess with stuff needlessly.

---

