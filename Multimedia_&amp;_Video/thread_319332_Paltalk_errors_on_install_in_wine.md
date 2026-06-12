---
title: "Paltalk errors on install in wine"
date: 2006-12-15
forum: Multimedia &amp; Video
---

### Post by pneaveill on 2006-12-15
Not sure where exactly to post this, so if it needs to be moved, that is fine. The problem that I am having (as many others are also) is trying to get paltalk to work under wine. All I need is the voice on it, don't care about video (at least yet). Here is what I did someone somewhere suggested I go to [http://www.frankscorner.org/index.php?p=paltalk5](http://www.frankscorner.org/index.php?p=paltalk5) and followed these directions:

> 
[FONT=verdana][SIZE=2] Type **wine pal_install.exe** to install Paltalk.
Make sure you have the following dlls in the Wine system directory:
commctrl,
comctl32,
riched20,
riched32.

[/SIZE][/FONT]
and this is what it gave me:

```

root@paul:/home/paul#  wine pal_install_r17707.exe
fixme:midi:OSS_MidiInit Synthesizer supports MIDI in. Not yet supported.
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
/usr/bin/wineshelllink: line 220: /root/Desktop/Upgrade Paltalk.desktop: No such file or directory
fixme:midi:OSS_MidiInit Synthesizer supports MIDI in. Not yet supported.
err:statusbar:StatusWindowProc unknown msg 2210 wp=e8010001 lp=0007011a
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files\\Paltalk Messenger\\paltalk.exe" failed with error 1813
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files\\Paltalk Messenger\\paltalk.exe" failed with error 1813
fixme:shdocvw:PersistStreamInit_InitNew (0x1ef668)
fixme:shdocvw:WebBrowser_QueryInterface (0x1ef668)->({3af24292-0c96-11ce-a0cf-00aa00600ab8} 0x10708e0) interface not supported
fixme:shdocvw:OleObject_Advise (0x1ef668)->(0x10708b4, 0x107090c)
fixme:shdocvw:ViewObject_SetAdvise (0x1ef668)->(1 00000000 0x10708b4)
fixme:shdocvw:OleObject_SetHostNames (0x1ef668)->(L"AXWIN", (null))
fixme:shdocvw:ViewObject_Draw (0x1ef668)->(1 -1 (nil) (nil) (nil) 0x2a40 0x1070924 0x1070924 (nil) 00000000)
fixme:shdocvw:WebBrowser_QueryInterface (0x1ef668)->({fc4801a3-2ba9-11cf-a229-00aa003d7352} 0x34d450) interface not supported
root@paul-desktop:/home/paul# err:ole:CoGetClassObject apartment not initialised
err:cabinet:FDICopy FDIIsCabinet failed.
err:mshtml:InstallCallback_OnStopBinding Could not extract package: 80004005
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
Could not load Mozilla. HTML rendering will be disabled.
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x1ef704)->((null) 1 0x34d24c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1ef704)->((null) 25 2 0x34d260 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1ef704)->((null) 26 2 0x34d260 (nil))
fixme:shdocvw:ClDispatch_Invoke (0x1ef704)->(-709 {00000000-0000-0000-0000-000000000000} 2048 0002 0x34d1a4 0x34d1f0 (nil) 0x34d1b4)
fixme:shdocvw:ClDispatch_Invoke (0x1ef704)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x34d164 0x34d1b0 (nil) 0x34d174)
fixme:shdocvw:ClDispatch_Invoke (0x1ef704)->(-5501 {00000000-0000-0000-0000-000000000000} 2048 0002 0x34d1a4 0x34d1f0 (nil) 0x34d1b4)
fixme:shdocvw:ClDispatch_Invoke (0x1ef704)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x34d164 0x34d1b0 (nil) 0x34d174)
fixme:shdocvw:ClDispatch_Invoke (0x1ef704)->(-5502 {00000000-0000-0000-0000-000000000000} 2048 0002 0x34d1a4 0x34d1f0 (nil) 0x34d1b4)
fixme:shdocvw:ClDispatch_Invoke (0x1ef704)->(-5513 {00000000-0000-0000-0000-000000000000} 2048 0002 0x34d1a4 0x34d1f0 (nil) 0x34d1b4)
fixme:shdocvw:ClDispatch_Invoke (0x1ef704)->(-726 {00000000-0000-0000-0000-000000000000} 2048 0002 0x34d1a4 0x34d1f0 (nil) 0x34d1b4)
fixme:shdocvw:ClientSite_GetContainer (0x1ef704)->(0x34d28c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1ef704)->({000214d1-0000-0000-c000-000000000046} 37 0 0x34d3b0 (nil))
fixme:shdocvw:ClDispatch_Invoke (0x1ef704)->(-5502 {00000000-0000-0000-0000-000000000000} 2048 0002 0x34d274 0x34d3a0 (nil) 0x34d284)
fixme:shdocvw:ClDispatch_Invoke (0x1ef704)->(-5501 {00000000-0000-0000-0000-000000000000} 2048 0002 0x34d274 0x34d390 (nil) 0x34d284)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:mshtml:BSCServiceProvider_QueryService (0x1f1130)->({79eac9e4-baf9-11ce-8c82-00aa004ba90b} {79eac9e4-baf9-11ce-8c82-00aa004ba90b} 0x1f1938)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1ef704)->((null) 29 2 0x34d9cc (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x1ef704)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1ef704)->((null) 26 2 0x34d9ac (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1ef704)->((null) 29 2 0x34d9bc (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1ef704)->({de4ba900-59ca-11cf-9592-444553540000} 2315 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1ef704)->((null) 35 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1ef704)->((null) 28 2 0x34d99c (nil))
fixme:shdocvw:ClientSite_GetContainer (0x1ef704)->(0x34d8b8)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x1ef704)->(0xb7ee84f7)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1ef704)->((null) 25 2 0x34d7f4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1ef704)->((null) 26 2 0x34d7f4 (nil))
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:midi:OSS_MidiInit Synthesizer supports MIDI in. Not yet supported.
fixme:advapi:CheckTokenMembership ((nil) 0x1f0c88 0x34c8c0) stub!
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files\\Paltalk Messenger\\paltalk.exe" failed with error 1813
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files\\Paltalk Messenger\\paltalk.exe" failed with error 1813
fixme:shdocvw:PersistStreamInit_Load (0x1f45b20)->(0x1f33e28)
fixme:shdocvw:WebBrowser_QueryInterface (0x1f45b20)->({3af24292-0c96-11ce-a0cf-00aa00600ab8} 0x1056e80) interface not supported
fixme:shdocvw:OleObject_Advise (0x1f45b20)->(0x1056e54, 0x1056eac)
fixme:shdocvw:ViewObject_SetAdvise (0x1f45b20)->(1 00000000 0x1056e54)
fixme:shdocvw:OleObject_SetHostNames (0x1f45b20)->(L"AXWIN", (null))
fixme:shdocvw:ViewObject_Draw (0x1f45b20)->(1 -1 (nil) (nil) (nil) 0x3840 0x1056ec4 0x1056ec4 (nil) 00000000)
fixme:shdocvw:WebBrowser_QueryInterface (0x1f45b20)->({fc4801a3-2ba9-11cf-a229-00aa003d7352} 0x34bc50) interface not supported
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x1f45bbc)->((null) 1 0x34b9b8 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1f45bbc)->((null) 25 2 0x34b9cc (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1f45bbc)->((null) 26 2 0x34b9cc (nil))
fixme:shdocvw:ClDispatch_Invoke (0x1f45bbc)->(-709 {00000000-0000-0000-0000-000000000000} 2048 0002 0x34b910 0x34b95c (nil) 0x34b920)
fixme:shdocvw:ClDispatch_Invoke (0x1f45bbc)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x34b8d0 0x34b91c (nil) 0x34b8e0)
fixme:shdocvw:ClDispatch_Invoke (0x1f45bbc)->(-5501 {00000000-0000-0000-0000-000000000000} 2048 0002 0x34b910 0x34b95c (nil) 0x34b920)
fixme:shdocvw:ClDispatch_Invoke (0x1f45bbc)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x34b8d0 0x34b91c (nil) 0x34b8e0)
fixme:shdocvw:ClDispatch_Invoke (0x1f45bbc)->(-5502 {00000000-0000-0000-0000-000000000000} 2048 0002 0x34b910 0x34b95c (nil) 0x34b920)
fixme:shdocvw:ClDispatch_Invoke (0x1f45bbc)->(-5513 {00000000-0000-0000-0000-000000000000} 2048 0002 0x34b910 0x34b95c (nil) 0x34b920)
fixme:shdocvw:ClDispatch_Invoke (0x1f45bbc)->(-726 {00000000-0000-0000-0000-000000000000} 2048 0002 0x34b910 0x34b95c (nil) 0x34b920)
fixme:shdocvw:ClientSite_GetContainer (0x1f45bbc)->(0x34b9f8)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1f45bbc)->({000214d1-0000-0000-c000-000000000046} 37 0 0x34bb1c (nil))
fixme:shdocvw:ClDispatch_Invoke (0x1f45bbc)->(-5502 {00000000-0000-0000-0000-000000000000} 2048 0002 0x34b9e0 0x34bb0c (nil) 0x34b9f0)
fixme:shdocvw:ClDispatch_Invoke (0x1f45bbc)->(-5501 {00000000-0000-0000-0000-000000000000} 2048 0002 0x34b9e0 0x34bafc (nil) 0x34b9f0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1f45bbc)->((null) 29 2 0x34c6d4 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x1f45bbc)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1f45bbc)->((null) 26 2 0x34c6b4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1f45bbc)->((null) 29 2 0x34c6c4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1f45bbc)->({de4ba900-59ca-11cf-9592-444553540000} 2315 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1f45bbc)->((null) 35 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1f45bbc)->((null) 28 2 0x34c6a4 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x1f45bbc)->(0x34c450)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x1f45bbc)->(0xb7ee84f7)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1f45bbc)->((null) 25 2 0x34c38c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1f45bbc)->((null) 26 2 0x34c38c (nil))
fixme:shdocvw:ViewObject_SetAdvise (0x1f45b20)->(1 00000000 (nil))
fixme:shdocvw:OleObject_Unadvise (0x1f45b20)->(1650610020)
fixme:shdocvw:OleObject_Close (0x1f45b20)->(1)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x1f47ba0)->((nil))
fixme:shdocvw:WebBrowser_QueryInterface (0x1f45b20)->({fc4801a3-2ba9-11cf-a229-00aa003d7352} 0x34be00) interface not supported
fixme:wavemap:wodWrite Not all src buffer has been written, expect bogus sound
fixme:setupapi:SetupDiGetClassDevsW : returning empty list
fixme:setupapi:SetupDiEnumDeviceInterfaces 0x209c078, (nil), {a7c7a5b1-5af3-11d1-9ced-00a024bf0407}, 0x00000000, 0x34d52c
fixme:setupapi:SetupDiGetClassDevsW : returning empty list
fixme:setupapi:SetupDiEnumDeviceInterfaces 0x209c078, (nil), {a7c7a5b1-5af3-11d1-9ced-00a024bf0407}, 0x00000000, 0x34d52c
fixme:setupapi:SetupDiGetClassDevsW : returning empty list
fixme:setupapi:SetupDiEnumDeviceInterfaces 0x209c078, (nil), {a7c7a5b1-5af3-11d1-9ced-00a024bf0407}, 0x00000000, 0x34d52c
fixme:setupapi:SetupDiGetClassDevsW : returning empty list
fixme:setupapi:SetupDiEnumDeviceInterfaces 0x209c078, (nil), {a7c7a5b1-5af3-11d1-9ced-00a024bf0407}, 0x00000000, 0x34d52c
fixme:setupapi:SetupDiGetClassDevsW : returning empty list
fixme:setupapi:SetupDiEnumDeviceInterfaces 0x209c078, (nil), {a7c7a5b1-5af3-11d1-9ced-00a024bf0407}, 0x00000000, 0x34d508
fixme:setupapi:SetupDiGetClassDevsW : returning empty list
fixme:setupapi:SetupDiEnumDeviceInterfaces 0x209c078, (nil), {a7c7a5b1-5af3-11d1-9ced-00a024bf0407}, 0x00000000, 0x34d508
fixme:setupapi:SetupDiGetClassDevsW : returning empty list
fixme:setupapi:SetupDiEnumDeviceInterfaces 0x209c078, (nil), {a7c7a5b1-5af3-11d1-9ced-00a024bf0407}, 0x00000000, 0x34d508
fixme:setupapi:SetupDiGetClassDevsW : returning empty list
fixme:setupapi:SetupDiEnumDeviceInterfaces 0x209c078, (nil), {a7c7a5b1-5af3-11d1-9ced-00a024bf0407}, 0x00000000, 0x34d508
fixme:ras:RasEnumConnectionsA (0x349750,0x34962c,0x349624),stub!
fixme:ras:RasEnumConnectionsA RAS support is not implemented! Configure program to use LAN connection/winsock instead!
fixme:mshtml:HlinkTarget_SetBrowseContext (0x1f0ca0)->((nil))
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x1ef704)->((null) 1 0x34d994 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1ef704)->((null) 25 2 0x34d9a8 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1ef704)->((null) 26 2 0x34d9a8 (nil))
fixme:shdocvw:ClDispatch_Invoke (0x1ef704)->(-709 {00000000-0000-0000-0000-000000000000} 2048 0002 0x34d8ec 0x34d938 (nil) 0x34d8fc)
fixme:shdocvw:ClDispatch_Invoke (0x1ef704)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x34d8ac 0x34d8f8 (nil) 0x34d8bc)
fixme:shdocvw:ClDispatch_Invoke (0x1ef704)->(-5501 {00000000-0000-0000-0000-000000000000} 2048 0002 0x34d8ec 0x34d938 (nil) 0x34d8fc)
fixme:shdocvw:ClDispatch_Invoke (0x1ef704)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x34d8ac 0x34d8f8 (nil) 0x34d8bc)
fixme:shdocvw:ClDispatch_Invoke (0x1ef704)->(-5502 {00000000-0000-0000-0000-000000000000} 2048 0002 0x34d8ec 0x34d938 (nil) 0x34d8fc)
fixme:shdocvw:ClDispatch_Invoke (0x1ef704)->(-5513 {00000000-0000-0000-0000-000000000000} 2048 0002 0x34d8ec 0x34d938 (nil) 0x34d8fc)
fixme:shdocvw:ClDispatch_Invoke (0x1ef704)->(-726 {00000000-0000-0000-0000-000000000000} 2048 0002 0x34d8ec 0x34d938 (nil) 0x34d8fc)
fixme:shdocvw:ClientSite_GetContainer (0x1ef704)->(0x34d9d4)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1ef704)->({000214d1-0000-0000-c000-000000000046} 37 0 0x34daf8 (nil))
fixme:shdocvw:ClDispatch_Invoke (0x1ef704)->(-5502 {00000000-0000-0000-0000-000000000000} 2048 0002 0x34d9bc 0x34dae8 (nil) 0x34d9cc)
fixme:shdocvw:ClDispatch_Invoke (0x1ef704)->(-5501 {00000000-0000-0000-0000-000000000000} 2048 0002 0x34d9bc 0x34dad8 (nil) 0x34d9cc)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1ef704)->((null) 29 2 0x34d9cc (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x1ef704)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1ef704)->((null) 26 2 0x34d9ac (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1ef704)->((null) 29 2 0x34d9bc (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1ef704)->({de4ba900-59ca-11cf-9592-444553540000} 2315 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1ef704)->((null) 35 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1ef704)->((null) 28 2 0x34d99c (nil))
fixme:shdocvw:ClientSite_GetContainer (0x1ef704)->(0x34d8b8)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x1ef704)->(0xb7ee84f7)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1ef704)->((null) 25 2 0x34d7f4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1ef704)->((null) 26 2 0x34d7f4 (nil))
fixme:wavemap:wodWrite Not all src buffer has been written, expect bogus sound
err:tooltips:TOOLTIPS_WindowProc unknown msg 204e wp=00040116 lp=0034d934
err:tooltips:TOOLTIPS_WindowProc unknown msg 204e wp=00040116 lp=0034d93c
fixme:shdocvw:ViewObject_SetAdvise (0x1ef668)->(1 00000000 (nil))
fixme:shdocvw:OleObject_Unadvise (0x1ef668)->(-1691558509)
fixme:shdocvw:OleObject_Close (0x1ef668)->(1)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x2023f8)->((nil))
fixme:shdocvw:WebBrowser_QueryInterface (0x1ef668)->({fc4801a3-2ba9-11cf-a229-00aa003d7352} 0x34bf80) interface not supported

```What did I do wrong and how do I fix it please?

Thanks in advance

---

### Post by meng on 2006-12-15
A search of the forums suggests that recent versions of paltalk don't work under wine. Remember wine is not a perfect implementation of Windows compatibility.

---

### Post by pneaveill on 2006-12-15
Had seen that too, but was hoping someone else had done it since then or had found a workaround or someone affiliated with paltalk or similar might be working on a workaround.

Thanks for the reply.

---

### Post by [Alsharifi] on 2007-09-18
i have windows vista and ubuntu on my laptop , whenever i miss the things which work with microsoft only i login to my vista and whenever i like to spin the cube i come back to ubuntu . after all ubuntu is not perfect , so you gatta have both ,and ya i know what you mean , i use the chat which depends on activex , and activex is not supported with ubuntu . and i like paltalk and that's not working here . so ya you got things working here and things working there. have fun install vista or xp or wateva you like so you can use paltalk .

---

### Post by Sweet Spot on 2007-10-09
From what I've heard, Paltalk engineers are working on a version for Mac. Would this mean a version that didn't use Active X controls ?

---

