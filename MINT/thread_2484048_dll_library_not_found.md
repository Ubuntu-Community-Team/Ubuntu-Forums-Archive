---
title: "dll library not found"
date: 2023-02-16
forum: MINT
---

### Post by ardv2 on 2023-02-16
i'm trying to lanch this program:[https://dev.shamela.ws/downloads/windows/shamela_empty1443.605.zip](https://dev.shamela.ws/downloads/windows/shamela_empty1443.605.zip) -https://shamela.ws/page/download- which is a library for ebooks that use elastic search
in Linux Mint 21.1 Cinnamon - i posted here because it is derived from ubuntu

this is the code error that i get:
01a4:err:module:import_dll Library Qt5Pdf.dll (which is needed by L"Z:\\media\\pc\\01D93B76FB51C4C0\\shamela_4\\1443.608\\lib\\PySide2\\plugins\\imageformats\\qpdf.dll") not found
01a4:err:module:import_dll Library Qt5Svg.dll (which is needed by L"Z:\\media\\pc\\01D93B76FB51C4C0\\shamela_4\\1443.608\\lib\\PySide2\\plugins\\imageformats\\qsvg.dll") not found

i saerched for these files: Qt5Pdf.dll Qt5Svg.dll  and put theme in the directory of the program
this is the code error that i get:
0154:err:winediag:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path. Usually, you can find it in the winbind package of your distribution.
0154:err:module:import_dll Library Qt5Pdf.dll (which is needed by L"Z:\\media\\pc\\01D93B76FB51C4C0\\shamela_4\\1443.608\\lib\\PySide2\\plugins\\imageformats\\qpdf.dll") not found
0154:err:module:import_dll Loading library Qt5Svg.dll (which is needed by L"Z:\\media\\pc\\01D93B76FB51C4C0\\shamela_4\\1443.608\\lib\\PySide2\\plugins\\imageformats\\qsvg.dll") failed (error c000035a).

wine version: 6.0.3~repack-1
i'm also using winetricks

i hope that you can help

---

### Post by jeremy31 on 2023-02-16
Moved to Mint

---

### Post by ardv2 on 2023-02-16
now i'm getting a dialog box that says in arabic that the search engine cannot be started
and this error in terminal

0168:err:module:import_dll Loading library Qt5Pdf.dll (which is needed by L"Z:\\media\\pc\\01D93B76FB51C4C0\\shamela_4\\1443.608\\lib\\PySide2\\plugins\\imageformats\\qpdf.dll") failed (error c000007b).
0168:err:module:import_dll Loading library Qt5Svg.dll (which is needed by L"Z:\\media\\pc\\01D93B76FB51C4C0\\shamela_4\\1443.608\\lib\\PySide2\\plugins\\imageformats\\qsvg.dll") failed (error c000007b).
^[[B^[[B^[[B^[[Bwine: Unhandled page fault on write access to 00000045 at address 7BC282A6 (thread 017c), starting debugger...
0188:err:ntdll:RtlpWaitForCriticalSection section 00580094 "dlls/ntdll/heap.c: main process heap section" wait timed out in thread 0188, blocked by 017c, retrying (60 sec)

edit: the problem was that that dlls was for x64
i managed to find one of them in x32 and now i need this one: qt5pdf.dll

edit2:
i found qt5dll in [https://www.aladdin-rd.ru/support/downloads/jc-webclient/f200fad1-bb2d-4d30-89c6-6c38648ba4ea/](https://www.aladdin-rd.ru/support/downloads/jc-webclient/f200fad1-bb2d-4d30-89c6-6c38648ba4ea/)

now this is the error code:
wine: Unhandled page fault on write access to 00000045 at address 7BC282A6 (thread 0260), starting debugger...
026c:err:ntdll:RtlpWaitForCriticalSection section 00580094 "dlls/ntdll/heap.c: main process heap section" wait timed out in thread 026c, blocked by 0260, retrying (60 sec)

---

