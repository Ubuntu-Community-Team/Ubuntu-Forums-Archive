---
title: "no sound in wine despite many attempts at fixing this"
date: 2009-05-03
forum: Multimedia Software
---

### Post by momosan on 2009-05-03
Edited to add:  I solved my problem (sort of) by switching from Kubuntu to Ubuntu, but I'd still be curious to know if there's any fix within Kubuntu.

Hi, I joined these forums before but entirely forgot my username.  I've been a linux user for over a decade, and an ubuntu/kubuntu user for nearly half of that.  In the past, I've always been able to find solutions to my problems by searching (more like relentlessly scouring, for hours) this forum or the internet in general.  This time, I've tried everything and still come up with no solution.  (](*,)

The basic problem is this:  When I use wine, I have no sound.  I have tried every sound setting in wine that I can think of.  I have gotten kubuntu to recognize my sound card, which took a lot of fiddling in itself (and downloading stuff that was not in the package repositories).  I have closed all applications that use sound (and just to be doubly sure, since I don't fully understand which programs' sound wine will ignore, I have configured things like the desktop not to use sound either).  

Here's the specific information about my system:

Kubuntu 9.04, Jaunty Jackalope
wine version 1.1.20

```
$ aplay -l     
**** List of PLAYBACK Hardware Devices ****                                 
card 0: Intel [HDA Intel], device 0: ALC662 Analog [ALC662 Analog]          
  Subdevices: 1/1                                                           
  Subdevice #0: subdevice #0                                                
card 0: Intel [HDA Intel], device 1: ALC662 Digital [ALC662 Digital]        
  Subdevices: 1/1                                                           
  Subdevice #0: subdevice #0
``````
$ lspci -v
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
        Subsystem: ASUSTeK Computer Inc. Device 817a                                
        Flags: bus master, fast devsel, latency 0                                   
        Capabilities: <access denied>                                               
        Kernel modules: intel-agp                                                   

00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
        Flags: bus master, fast devsel, latency 0                                  
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0               
        I/O behind bridge: 0000e000-0000efff                                       
        Memory behind bridge: dc000000-dfffffff                                    
        Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff       
        Capabilities: <access denied>                                              
        Kernel driver in use: pcieport-driver                                      
        Kernel modules: shpchp                                                     

[B]00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)                                                                                            
        Subsystem: ASUSTeK Computer Inc. Device 8290                                             
        Flags: bus master, fast devsel, latency 0, IRQ 19                                        
        Memory at dbef8000 (64-bit, non-prefetchable) [size=16K]                                 
        Capabilities: <access denied>                                                            
        Kernel driver in use: HDA Intel                                                          
        Kernel modules: snd-hda-intel[/B]                                                            

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
        Flags: bus master, fast devsel, latency 0                                     
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0                  
        I/O behind bridge: 0000d000-0000dfff                                          
        Capabilities: <access denied>                                                 
        Kernel driver in use: pcieport-driver                                         
        Kernel modules: shpchp                                                        

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
        Flags: bus master, fast devsel, latency 0                                     
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0                  
        I/O behind bridge: 0000c000-0000cfff                                          
        Memory behind bridge: dbf00000-dbffffff                                       
        Capabilities: <access denied>                                                 
        Kernel driver in use: pcieport-driver                                         
        Kernel modules: shpchp                                                        

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
        Subsystem: ASUSTeK Computer Inc. Device 8179                                          
        Flags: bus master, medium devsel, latency 0, IRQ 20                                   
        I/O ports at 6400 [size=32]                                                           
        Kernel driver in use: uhci_hcd                                                        

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
        Subsystem: ASUSTeK Computer Inc. Device 8179                                          
        Flags: bus master, medium devsel, latency 0, IRQ 17                                   
        I/O ports at 6800 [size=32]                                                           
        Kernel driver in use: uhci_hcd                                                        

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
        Subsystem: ASUSTeK Computer Inc. Device 8179                                          
        Flags: bus master, medium devsel, latency 0, IRQ 18                                   
        I/O ports at 7000 [size=32]                                                           
        Kernel driver in use: uhci_hcd                                                        

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
        Subsystem: ASUSTeK Computer Inc. Device 8179                                          
        Flags: bus master, medium devsel, latency 0, IRQ 19                                   
        I/O ports at 7400 [size=32]                                                           
        Kernel driver in use: uhci_hcd                                                        

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20)                                                                                         
        Subsystem: ASUSTeK Computer Inc. Device 8179                                             
        Flags: bus master, medium devsel, latency 0, IRQ 20                                      
        Memory at dbeffc00 (32-bit, non-prefetchable) [size=1K]                                  
        Capabilities: <access denied>                                                            
        Kernel driver in use: ehci_hcd                                                           

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01)
        Flags: bus master, fast devsel, latency 0                           
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32       
        I/O behind bridge: 0000b000-0000bfff                                
        Capabilities: <access denied>                                       

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
        Subsystem: ASUSTeK Computer Inc. Device 8179                                        
        Flags: bus master, medium devsel, latency 0                                         
        Capabilities: <access denied>                                                       
        Kernel modules: iTCO_wdt, intel-rng                                                 

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])                                                                   
        Subsystem: ASUSTeK Computer Inc. Device 8179                                             
        Flags: bus master, medium devsel, latency 0, IRQ 22                                      
        I/O ports at 9000 [size=8]                                                               
        I/O ports at 8800 [size=4]                                                               
        I/O ports at 8400 [size=8]                                                               
        I/O ports at 8000 [size=4]                                                               
        I/O ports at 7800 [size=16]                                                              
        Kernel driver in use: ata_piix                                                           

00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])                                                       
        Subsystem: ASUSTeK Computer Inc. Device 2601                                             
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 23                               
        I/O ports at a800 [size=8]                                                               
        I/O ports at a400 [size=4]                                                               
        I/O ports at a000 [size=8]                                                               
        I/O ports at 9800 [size=4]                                                               
        I/O ports at 9400 [size=16]                                                              
        Capabilities: <access denied>
        Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
        Subsystem: ASUSTeK Computer Inc. Device 8179
        Flags: medium devsel, IRQ 10
        I/O ports at 0400 [size=32]
        Kernel modules: i2c-i801

02:00.0 Ethernet controller: Attansic Technology Corp. L2 100 Mbit Ethernet Adapter (rev a0)
        Subsystem: ASUSTeK Computer Inc. Device 8233
        Flags: bus master, fast devsel, latency 0, IRQ 2300
        Memory at dbfc0000 (64-bit, non-prefetchable) [size=256K]
        Expansion ROM at dbfa0000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: atl2
        Kernel modules: atl2

04:00.0 VGA compatible controller: nVidia Corporation GeForce 9500 GT (rev a1)
        Subsystem: nVidia Corporation Device 0551
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at df000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        Memory at dc000000 (64-bit, non-prefetchable) [size=32M]
        I/O ports at e800 [size=128]
        [virtual] Expansion ROM at def80000 [disabled] [size=512K]
        Capabilities: <access denied>
        Kernel driver in use: nvidia
        Kernel modules: nvidia, nvidiafb
```In winecfg, I have tried ALSA, OSS, JACK, and NAS, as well as with and without driver emulation.  I used to fail the "Test Sound" option, but now I no longer get the fail message.  

I have also went through and closed every other program that could possibly be running sound.  I have made sure (with alsamixer) that my sound is not muted, and also made sure that my sound is indeed playing for non-wine apps.

The game I am testing the sound with on wine is World of Warcraft (I've also read through the whole World of Warcraft thread and found nothing I could use).  If relevant, these are the messages I get when I first run the launcher (which does not have sound normally):

```
$ wine Launcher.exe
fixme:shdocvw:PersistStreamInit_Load (0x13ddf0)->(0x32d9a0)                     
fixme:shdocvw:OleControl_FreezeEvents (0x13ddf0)->(1)                           
fixme:shdocvw:OleControl_FreezeEvents (0x13ddf0)->(0)                           
fixme:system:SetProcessDPIAware stub!                                           
fixme:dwmapi:DwmIsCompositionEnabled 0x32c824                                   
0[16ee68]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nspr4.dll") - Symbol NSGetModule not found                                                                         
0[16ee68]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\plc4.dll") - Symbol NSGetModule not found                                                                          
0[16ee68]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nssutil3.dll") - Symbol NSGetModule not found                                                                      
0[16ee68]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\js3250.dll") - Symbol NSGetModule not found                                                                        
0[16ee68]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\xpcom.dll") - Symbol NSGetModule not found                                                                         
0[16ee68]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nss3.dll") - Symbol NSGetModule not found                                                                          
fixme:iphlpapi:NotifyAddrChange (Handle 0x23fe888, overlapped 0x23fe890): stub                   
0[16ee68]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\sqlite3.dll") - Symbol NSGetModule not found                                                                       
0[16ee68]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nssdbm3.dll") - Symbol NSGetModule not found                                                                       
0[16ee68]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\freebl3.dll") - Symbol NSGetModule not found                                                                       
0[16ee68]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nssckbi.dll") - Symbol NSGetModule not found                                                                       
0[16ee68]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\plugins\npnul32.dll") - Symbol NSGetModule not found                                                               
0[16ee68]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\softokn3.dll") - Symbol NSGetModule not found                                                                      
0[16ee68]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\xul.dll") - Symbol NSGetModule not found
0[16ee68]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\ssl3.dll") - Symbol NSGetModule not found
0[16ee68]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\plds4.dll") - Symbol NSGetModule not found
0[16ee68]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\smime3.dll") - Symbol NSGetModule not found
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x13de90)->((null) 1 0x32cdbc (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x13de90)->((null) 25 2 0x32cdd0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x13de90)->((null) 26 2 0x32cdd0 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x13de90)->(0x32ce0c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x13de90)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32cee0 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x1444d8)->(L"" L"" 0 0x32cf18)
fixme:shdocvw:ClOleCommandTarget_Exec (0x13de90)->((null) 29 2 0x32d4bc (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x13de90)
fixme:shdocvw:ClientSite_GetContainer (0x13de90)->(0x32d2fc)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x13de90)->(0xb7ef2051)
fixme:shdocvw:ClOleCommandTarget_Exec (0x13de90)->((null) 25 2 0x32d230 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x13de90)->((null) 26 2 0x32d230 (nil))
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 10000
fixme:shdocvw:ClOleCommandTarget_Exec (0x13de90)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x13de90)->((null) 28 2 0x32df3c (nil))
0[16ee68]: NPN Logging Active!
0[16ee68]: General Plugin Logging Active! (nsPluginHostImpl::ctor)
0[16ee68]: NPP Logging Active!
0[16ee68]: nsPluginHostImpl::ctor
fixme:resource:GetGuiResources (0xffffffff,0): stub
fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented
```And then these are the messages I get after I click on "Play" and load the main World of Warcraft window (which does normally have sound):

```
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x13ddf0)                                      
fixme:mshtml:HlinkTarget_SetBrowseContext (0x1620f0)->((nil))                                    
fixme:shdocvw:OleObject_Close (0x13ddf0)->(1)                                                    
fixme:shell:DllCanUnloadNow stub                                                                 
username@Hostname:~/.wine/drive_c/Program Files/World of Warcraft$ fixme:advapi:SetSecurityInfo stub 
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
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 totalsamplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x3aebd0,0x00000000), stub!
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 totalsamplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x3af0a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af3f0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af588,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af584,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af578,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af140,0x00000000), stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x13c9f0,0x13c8f0): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x3adeec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3adf24,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:reg:GetNativeSystemInfo (0x37404084) using GetSystemInfo()
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
```I doubt that those two sets of messages are useful, but since I can't understand all of them I figured I'd include them in case they *are* more useful than I can see.

Anyway I have always, in the past, been able to resolve these sorts of issues with wine.  Since building the new computer, however, I have found that nothing I do produces sound in wine.  

I would be very grateful for help with this, and I will gladly provide any further information that's necessary.  I keep being sure there's something really obvious that I'm missing, and yet I never seem to find it.

---

