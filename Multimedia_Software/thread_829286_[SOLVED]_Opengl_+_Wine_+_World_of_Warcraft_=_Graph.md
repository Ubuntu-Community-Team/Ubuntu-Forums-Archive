---
title: "[SOLVED] Opengl + Wine + World of Warcraft = Graphic Problems"
date: 2008-06-14
forum: Multimedia Software
---

### Post by azurepancake on 2008-06-14
I am a big World of Warcraft player and I've actually got it to work quite decently on Ubuntu Hardy with Wine 1.00 RC-4 using a ATI Radeon X1600 with restricted drivers.

When reading guides on setting up WoW with Wine, I was told that running it with the -opengl flag would harbor the best results. Instead it presented me with a graphical mess! 

After this surprise I attempted to load it without the -opengl flag. Believe it or not the game runs pretty well like this. It doesn't match the performance it presented on Windows XP, but it certainly is playable. 

But, if the game would run better with OpenGL, perhaps there is someway to fix this graphical problem.

Here is a link to my personal blog, where I have images comparing WoW with and without OpenGL [http://spiraledoutward.blogspot.com/2008/06/linux-and-wine-incomplete.html](http://spiraledoutward.blogspot.com/2008/06/linux-and-wine-incomplete.html)

If it helps at all, here is the output of running WoW with OpenGL from the terminal.

```

fixme:shdocvw:PersistStreamInit_Load (0x1312d0)->(0x32e328)
fixme:shdocvw:OleControl_FreezeEvents (0x1312d0)->(1)
fixme:shdocvw:OleControl_FreezeEvents (0x1312d0)->(0)
fixme:shell:IShellLinkA_fnGetPath (0x1318f8): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x1318f8): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x1318d8): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x1318d8): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x131c70): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x131c70): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x131c70): WIN32_FIND_DATA is not yet filled.
fixme:midi:OSS_MidiInit Synthesizer supports MIDI in. Not yet supported.
fixme:iphlpapi:NotifyAddrChange (Handle 0x7c95ea08, overlapped 0x7c95e9ec): stub
fixme:system:SetProcessDPIAware stub!
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x12eef34)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x13136c)->((null) 1 0x32bcf4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x13136c)->((null) 25 2 0x32bd08 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x13136c)->((null) 26 2 0x32bd08 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x13136c)->(0x32bd44)
fixme:shdocvw:ClOleCommandTarget_Exec (0x13136c)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32be08 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x1317d8)->(L"" L"" 0 0x32be40)
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:shdocvw:ClOleCommandTarget_Exec (0x13136c)->((null) 29 2 0x32ea0c (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x13136c)
fixme:shdocvw:ClientSite_GetContainer (0x13136c)->(0x32e84c)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x13136c)->(0xb7e906d5)
fixme:shdocvw:ClOleCommandTarget_Exec (0x13136c)->((null) 25 2 0x32e780 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x13136c)->((null) 26 2 0x32e780 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x13136c)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x13136c)->((null) 28 2 0x32e9ac (nil))
fixme:bidi:mirror stub: mirroring of characters not yet implemented
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x1312d0)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x14a618)->((nil))
fixme:shdocvw:OleObject_Close (0x1312d0)->(1)
fixme:shell:DllCanUnloadNow stub
fixme:msimtf:DllCanUnloadNow ()
tristan@panzerkunst:~$ fixme:midi:OSS_MidiInit Synthesizer supports MIDI in. Not yet supported.
fixme:advapi:SetSecurityInfo stub
archive Data\patch.MPQ opened
archive Data\enUS\patch-enUS.MPQ opened
archive Data\enUS\patch-enUS-2.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\expansion.MPQ opened
archive Data\common.MPQ opened
archive Data\enUS\locale-enUS.MPQ opened
archive Data\enUS\speech-enUS.MPQ opened
archive Data\enUS\expansion-locale-enUS.MPQ opened
archive Data\enUS\expansion-speech-enUS.MPQ opened
fixme:powrprof:DllMain (0x7c400000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7c400000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33eda4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33ec94,0x00000000), stub!
fixme:d3d:test_pbo_functionality >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Loading the PBO test texture
 @ directx.c / 3526
fixme:win:EnumDisplayDevicesW ((null),0,0x33f42c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5a0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f57c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f144,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:reg:GetNativeSystemInfo (0x37402bc4) using GetSystemInfo()
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:imm:ImmReleaseContext (0x3004c, 0x12ecd8): stub
fixme:imm:ImmAssociateContextEx (0x3004c, (nil), 16): stub

```

Edit: I just edited the Config.wtf file, adding 'SET M2UseShaders "0"', which is recommended with OpenGL. Same problem.

If anyone has any advice, I will greatly appreciate any input at all. If you need anymore information, just ask!

Thanks

---

### Post by azurepancake on 2008-06-15
Fixed!

Someone added a response to my blog post and recommended me to delete my Config.wtf file and load up WoW. 

Once I did that, the game loaded with a black screen, but everything was where it should be. I then added the following lines to my Config.wtf file..

```

SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"
SET M2UseShaders "0"

```

Also, I had to do a slight registry tweak, that is described here, [http://appdb.winehq.org/objectManager.php?sClass=version&iId=11329](http://appdb.winehq.org/objectManager.php?sClass=version&iId=11329).

I then loaded it back up and it runs perfectly. I'm willing to say equal or even better than it did on Windows XP.

Who ever left that post, thank you so very much!

---

### Post by GreatSunJester on 2008-06-16
I wonder if that is the old ATI vs nVidia thing?  I have a GeForce 8800GTS 512 meg and the only thing I did was add SET gxApi "opengl"
 to the config.wtf file.  I did not touch any of the settings that were copied over from my Vista drive, and the game plays....well.... flawlessly.  Except for the FPS meter showing MORE FPS, I would never know I was running on LINUX.  Well, OK - I would the moment I hit ALT-TAB and selected another application.  If fact, once I am home from work tonight I will probably put a couple hours ingame with Linux, even without my Logitch G5 working correctly (yet!)

---

