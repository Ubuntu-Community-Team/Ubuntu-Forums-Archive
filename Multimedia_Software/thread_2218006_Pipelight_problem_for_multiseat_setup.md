---
title: "Pipelight problem for multiseat setup"
date: 2014-04-19
forum: Multimedia Software
---

### Post by malaTG on 2014-04-19
Hi everyone, 

I am running a multiseat setup that works perfect(more or less...:-))

Anyway I am running XBMC on one of my seats(Living room) and it works really well(Video and audio etc.)

However now I installed pipelight and it gets some kind of issue with my graphic card. It works on my other seat but for the living room setup it gogets really choppy and in the terminal I get the following log. 

```
NVIDIA: could not open the device file /dev/nvidia1 (Operationen inte tillåten). 
NVIDIA: could not open the device file /dev/nvidia1 (Operationen inte tillåten). 
[PIPELIGHT:LIN:unknown] attached to process. 
[PIPELIGHT:LIN:unknown] checking environment variable PIPELIGHT_WIDEVINE_CONFIG. 
[PIPELIGHT:LIN:unknown] searching for config file pipelight-widevine. 
[PIPELIGHT:LIN:unknown] trying to load config file from '/home/xbmc/.config/pipelight-widevine'. 
[PIPELIGHT:LIN:unknown] trying to load config file from '/etc/pipelight-widevine'. 
[PIPELIGHT:LIN:unknown] trying to load config file from '/usr/share/pipelight/configs/pipelight-widevine'. 
[PIPELIGHT:LIN:unknown] sandbox not found or not installed! 
[PIPELIGHT:LIN:widevine] using wine prefix directory /home/xbmc/.wine-pipelight. 
[PIPELIGHT:LIN:widevine] checking plugin installation - this might take some time. 
[install-dependency] wine-widevine-installer is already installed in '/home/xbmc/.wine-pipelight'. 
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe" 
err:wineboot:ProcessRunKeys Error running cmd L"C:\\windows\\system32\\winemenubuilder.exe -a -r" (2) 
[PIPELIGHT:WIN:widevine] embedded mode         is on. 
[PIPELIGHT:WIN:widevine] windowless mode       is off. 
[PIPELIGHT:WIN:widevine] linux windowless mode is off. 
[PIPELIGHT:WIN:widevine] force SetWindow       is on. 
[PIPELIGHT:WIN:widevine] unity hacks           is off. 
[PIPELIGHT:WIN:widevine] window class hook     is off. 
[PIPELIGHT:WIN:widevine] replaced API function TrackPopupMenuEx. 
[PIPELIGHT:WIN:widevine] replaced API function TrackPopupMenu. 
WVMK NP_Initialize 
[PIPELIGHT:WIN:widevine] init successful! 
[PIPELIGHT:LIN:unknown] attached to process. 
[PIPELIGHT:LIN:unknown] checking environment variable PIPELIGHT_SILVERLIGHT5_1_CONFIG. 
[PIPELIGHT:LIN:unknown] searching for config file pipelight-silverlight5.1. 
[PIPELIGHT:LIN:unknown] trying to load config file from '/home/xbmc/.config/pipelight-silverlight5.1'. 
[PIPELIGHT:LIN:unknown] sandbox not found or not installed! 
[PIPELIGHT:LIN:silverlight5.1] enableGPUAcceleration set manually - skipping compatibility check. 
[PIPELIGHT:LIN:silverlight5.1] using wine prefix directory /home/xbmc/.wine-pipelight. 
[PIPELIGHT:LIN:silverlight5.1] checking plugin installation - this might take some time. 
[install-dependency] wine-silverlight5.1-installer is already installed in '/home/xbmc/.wine-pipelight'. 
[install-dependency] wine-mpg2splt-installer is already installed in '/home/xbmc/.wine-pipelight'. 
[PIPELIGHT:WIN:silverlight5.1] embedded mode         is on. 
[PIPELIGHT:WIN:silverlight5.1] windowless mode       is on. 
[PIPELIGHT:WIN:silverlight5.1] linux windowless mode is off. 
[PIPELIGHT:WIN:silverlight5.1] force SetWindow       is off. 
[PIPELIGHT:WIN:silverlight5.1] unity hacks           is off. 
[PIPELIGHT:WIN:silverlight5.1] window class hook     is on. 
[PIPELIGHT:WIN:silverlight5.1] replaced API function CreateWindowExA. 
[PIPELIGHT:WIN:silverlight5.1] replaced API function CreateWindowExW. 
[PIPELIGHT:WIN:silverlight5.1] replaced API function TrackPopupMenuEx. 
[PIPELIGHT:WIN:silverlight5.1] replaced API function TrackPopupMenu. 
fixme:advapi:RegisterTraceGuidsW (0x2b22a7, 0x350120, {aa087e0e-0b35-4e28-8f3a-440c3f51eef1}, 1, 0x72f688, (null), (null), 0x350120): stub 
[PIPELIGHT:WIN:silverlight5.1] init successful! 
fixme:advapi:UnregisterTraceGuids 0: stub 
NVIDIA: could not open the device file /dev/nvidia1 (Operationen inte tillåten). 
NVIDIA: could not open the device file /dev/nvidia1 (Operationen inte tillåten). 
[PIPELIGHT:LIN:unknown] attached to process. 
[PIPELIGHT:LIN:unknown] checking environment variable PIPELIGHT_WIDEVINE_CONFIG. 
[PIPELIGHT:LIN:unknown] searching for config file pipelight-widevine. 
[PIPELIGHT:LIN:unknown] trying to load config file from '/home/xbmc/.config/pipelight-widevine'. 
[PIPELIGHT:LIN:unknown] trying to load config file from '/etc/pipelight-widevine'. 
[PIPELIGHT:LIN:unknown] trying to load config file from '/usr/share/pipelight/configs/pipelight-widevine'. 
[PIPELIGHT:LIN:unknown] sandbox not found or not installed! 
[PIPELIGHT:LIN:widevine] using wine prefix directory /home/xbmc/.wine-pipelight. 
[PIPELIGHT:LIN:widevine] checking plugin installation - this might take some time. 
[install-dependency] wine-widevine-installer is already installed in '/home/xbmc/.wine-pipelight'. 
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe" 
err:wineboot:ProcessRunKeys Error running cmd L"C:\\windows\\system32\\winemenubuilder.exe -a -r" (2) 
[PIPELIGHT:WIN:widevine] embedded mode         is on. 
[PIPELIGHT:WIN:widevine] windowless mode       is off. 
[PIPELIGHT:WIN:widevine] linux windowless mode is off. 
[PIPELIGHT:WIN:widevine] force SetWindow       is on. 
[PIPELIGHT:WIN:widevine] unity hacks           is off. 
[PIPELIGHT:WIN:widevine] window class hook     is off. 
[PIPELIGHT:WIN:widevine] replaced API function TrackPopupMenuEx. 
[PIPELIGHT:WIN:widevine] replaced API function TrackPopupMenu. 
WVMK NP_Initialize 
[PIPELIGHT:WIN:widevine] init successful! 
[PIPELIGHT:LIN:widevine] using timer based event handling. 

(exe:32429): Gdk-WARNING **: XID collision, trouble ahead 
fixme:winhttp:WinHttpDetectAutoProxyConfigUrl discovery via DHCP not supported 
SessionSetupCompleted 
http://localhost:10000/cgi-bin/ 
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot 
fixme:toolhelp:Heap32ListFirst : stub 
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot 
fixme:toolhelp:Heap32ListFirst : stub 
fixme:resource:GetGuiResources (0x1ac,0): stub 
[PIPELIGHT:LIN:widevine] unscheduled event timer. 
```

Any ideas on what to do next?

/Mala

---

