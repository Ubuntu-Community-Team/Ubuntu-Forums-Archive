---
title: "Playin Prince of Persia with Wine"
date: 2008-09-18
forum: Multimedia Software
---

### Post by sreejithemk on 2008-09-18
I'm using Ubuntu Hardy Heron and I installed Prince of Persia Warrior Within using wine. But when I run the game I get this...

```


sree@BlueGene:~$env WINEPREFIX="/home/sree/.wine" wine "C:\Program Files\Ubisoft\Prince of Persia Warrior Within\PrinceOfPersia.exe"
fixme:dxdiag:DXDiag_AddFileDescContainer (0x136c98,L"ddraw.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x136c98,L"dplayx.dll")
fixme:mixer:ALSA_MixerInit No master control found on USB Device 0x93a:0x2608, disabling mixer
fixme:dxdiag:DXDiag_AddFileDescContainer (0x136c98,L"dpnet.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x136c98,L"dinput.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x136c98,L"dinput8.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x136c98,L"dsound.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x136c98,L"dswave.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x136c98,L"d3d8.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x136c98,L"d3d9.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x136c98,L"dmband.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x136c98,L"dmcompos.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x136c98,L"dmime.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x136c98,L"dmloader.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x136c98,L"dmscript.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x136c98,L"dmstyle.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x136c98,L"dmsynth.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x136c98,L"dmusic.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x136c98,L"devenum.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x136c98,L"quartz.dll")
fixme:win:EnumDisplayDevicesW ((null),0,0x32ed8c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32e82c,0x00000000), stub!
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	ClassEnumerator for clsid({083863f1-70de-11d0-bd40-00a0c911ce86}) pEnum(0x143a38)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x143a38, 1, 0x143a50)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"AVI Splitter"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{1B544C20-FD0B-11CE-8C63-00AA0044B51E}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x143a38, 1, 0x143e50)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"MPEG-I Stream Splitter"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{336475D0-942A-11CE-A870-00AA002FEAB5}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x143a38, 1, 0x1441a0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"ACM Wrapper"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{6A08CF80-0E18-11CF-A24D-0020AFD79767}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x143a38, 1, 0x144908)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"Video Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{6BC1CFFA-8FC1-4261-AC22-CFB4CC38DB50}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x143a38, 1, 0x144ef0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"Video Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{70E102B0-5556-11CE-97C0-00AA0055595A}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x143a38, 1, 0x145318)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"Audio Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{79376820-07D0-11CF-A24D-0020AFD79767}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x143a38, 1, 0x146270)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"Null Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{C1F400A4-3F08-11D3-9F0B-006008039E37}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x143a38, 1, 0x146698)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"AVI Decompressor"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{CF49D4E0-1115-11CE-B03A-0020AF0BA770}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x143a38, 1, 0x146ac0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"Wave Parser"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{D51BD5A1-7548-11CF-A520-0080C77EF58A}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x143a38, 1, 0x146f18)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"File Source (Async.)"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{E436EBB5-524F-11CE-9F53-0020AF0BA770}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	ClassEnumerator for clsid({33d9a760-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x143a10)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	ClassEnumerator for clsid({33d9a761-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x143a10)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	ClassEnumerator for clsid({33d9a762-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x143a18)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x143a18, 1, 0x143a30)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"dsnoop:0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{E30629D2-27E5-11CE-875D-00608CB78066}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	ClassEnumerator for clsid({4efe2452-168a-11d1-bc76-00c04fb9453b}) pEnum(0x1439f0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x1439f0, 1, 0x143a08)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"Midi Through"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{07B65360-C445-11CE-AFDE-00AA006C14F4}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	ClassEnumerator for clsid({860bb310-5d01-11d0-bd3b-00a0c911ce86}) pEnum(0x1472e8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x1472e8, 1, 0x148090)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"Pixart PAC7311"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{1B544C22-FD0B-11CE-8C63-00AA0044B51E}"
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	ClassEnumerator for clsid({cc7bfb41-f175-11d1-a392-00e0291f3959}) pEnum((nil))
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	ClassEnumerator for clsid({cc7bfb46-f175-11d1-a392-00e0291f3959}) pEnum((nil))
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	ClassEnumerator for clsid({e0f158e1-cb04-11d0-bd4e-00a0c911ce86}) pEnum(0x1480a8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x1480a8, 1, 0x1439c0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L""
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L""
sree@BlueGene:~$ 


```

I'm also facing another problem with wine as the keyboard is not functioning well. Only the first keystroke is detected and after that it never works. Please Help me....

Configuration
=============
Graphics : Intel GMA 945
RAM : 1 GB DDR2
Processor : Intel Core 2 Duo E4500
Wine : 1.0.0-1ubuntu4~hardy1

---

