---
title: "wireless works but i also need ethernet"
date: 2010-09-06
forum: Networking &amp; Wireless
---

### Post by m3t3ors on 2010-09-06
im using ubuntu 10.04 on my dell latitude d520 and have wireless working but i need ethernet for my wireless hifi, (connects to pc via ethernet)
everytime i try to connect via ethernet it says no ethernet device found

how do i enable ethernet?

do i need to disable wireless to enable ethernet?

---

### Post by sgosnell on 2010-09-06
You don't need to disable wireless to enable the ethernet connection.  You do need to enable the ethernet, though.  What to you get from ifconfig?

---

### Post by m3t3ors on 2010-09-06
john@john:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:b9:54:33:92  
          inet6 addr: fe80::219:b9ff:fe54:3392/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:322 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:166746 (166.7 KB)  TX bytes:6374 (6.3 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:19:d2:bc:85:f2  
          inet addr:192.168.0.106  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d2ff:febc:85f2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:297802 errors:0 dropped:0 overruns:0 frame:0
          TX packets:202056 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:300834708 (300.8 MB)  TX bytes:28966875 (28.9 MB)

john@john:~$

---

### Post by sgosnell on 2010-09-06
That says your ethernet (eth0) and wireless (wlan0) are both working.  You might try disabling the wireless to see what you get.

---

### Post by m3t3ors on 2010-09-06
thanks but still says no network adaptor found

john@john:~$ sudo ifconfig up
[sudo] password for john: 
up: error fetching interface information: Device not found
john@john:~$

---

### Post by sgosnell on 2010-09-06
That won't work.  You have to specify a device to enable.  It's already enabled according to ifconfig.  If you use ```
sudo ifconfig eth0 up
``` you should get a null result, meaning you'll get no feedback, it will just happen without any errors.

---

### Post by m3t3ors on 2010-09-06
but when i search for my hifi using the philips install disc through wine it states no network adaptor found

---

### Post by sgosnell on 2010-09-06
Aahhhhh...  wine.  That may not work.  Wine and system hardware have a hard time talking together.  Ifconfig is saying the ethernet connection is working, but getting a Windows CD to find it may be problematic.  I haven't played with wine enough to be able to help you much there.  There are no Linux drivers?  Probably not, but Phillips does have a few Linux drivers available, at least for some devices.

---

### Post by m3t3ors on 2010-09-06
i searched and found out that wachandler works fine under wine and ubuntu but i followed the guide and just get an error on starting wachandler

---

### Post by m3t3ors on 2010-09-06
heres what i get when trying to use wachandler set up according to their website
john@john:~$ sh winetricks
Executing wine /home/john/.winetrickscache/jet40sp8_9xnt.exe
fixme:setupapi:extract_cabinet_file awful hack: extracting cabinet "C:\\users\\john\\Temp\\IXP001.TMP\\Jetsetup.CAB"
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program files\\Common files\\Microsoft shared\\dao\\dao2535.tlb" failed with error 2
Install of jet40 done
winetricks done.
john@john:~$ sh winetricks
Using native,builtin override for following DLLs: odbc32 odbccp32 oledb32
Executing early_wine regedit c:\winetrickstmp\override-dll.reg
REGEDIT4

[HKEY_CURRENT_USER\Software\Wine\DllOverrides]
"*odbc32"="native,builtin"
"*odbccp32"="native,builtin"
"*oledb32"="native,builtin"
Setting Windows version to win98
Executing early_wine regedit c:\winetrickstmp\set-winver.reg
Executing wine /home/john/.winetrickscache/mdac28/mdac_typ.exe
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
fixme:setupapi:SetupAddInstallSectionToDiskSpaceListA Stub
fixme:setupapi:SetupAddInstallSectionToDiskSpaceListA Stub
fixme:setupapi:SetupAddInstallSectionToDiskSpaceListA Stub
fixme:setupapi:SetupAddInstallSectionToDiskSpaceListA Stub
fixme:setupapi:SetupAddInstallSectionToDiskSpaceListA Stub
fixme:setupapi:SetupAddInstallSectionToDiskSpaceListA Stub
fixme:setupapi:SetupAddInstallSectionToDiskSpaceListA Stub
fixme:setupapi:SetupAddInstallSectionToDiskSpaceListA Stub
fixme:setupapi:SetupAddInstallSectionToDiskSpaceListA Stub
fixme:setupapi:SetupAddInstallSectionToDiskSpaceListA Stub
fixme:setupapi:SetupAddInstallSectionToDiskSpaceListA Stub
fixme:setupapi:SetupAddInstallSectionToDiskSpaceListA Stub
fixme:setupapi:SetupAddInstallSectionToDiskSpaceListA Stub
fixme:setupapi:SetupAddInstallSectionToDiskSpaceListA Stub
fixme:setupapi:SetupAddInstallSectionToDiskSpaceListA Stub
fixme:setupapi:SetupAddInstallSectionToDiskSpaceListA Stub
fixme:setupapi:SetupAddInstallSectionToDiskSpaceListA Stub
fixme:setupapi:SetupAddInstallSectionToDiskSpaceListA Stub
fixme:setupapi:SetupAddInstallSectionToDiskSpaceListA Stub
fixme:setupapi:SetupAddInstallSectionToDiskSpaceListA Stub
fixme:setupapi:SetupAddInstallSectionToDiskSpaceListA Stub
fixme:setupapi:SetupAddInstallSectionToDiskSpaceListA Stub
fixme:setupapi:SetupAddInstallSectionToDiskSpaceListA Stub
fixme:setupapi:SetupAddInstallSectionToDiskSpaceListA Stub
fixme:advpack:set_ldids Need to support changing paths - default will be used
fixme:setupapi:extract_cabinet_file awful hack: extracting cabinet "C:\\users\\john\\Temp\\IXP000.TMP\\msvcrt.CAB"
fixme:advpack:set_ldids Need to support changing paths - default will be used
fixme:setupapi:extract_cabinet_file awful hack: extracting cabinet "C:\\users\\john\\Temp\\IXP000.TMP\\mtxfiles.CAB"
fixme:advpack:set_ldids Need to support changing paths - default will be used
fixme:advpack:set_ldids Need to support changing paths - default will be used
fixme:advpack:set_ldids Need to support changing paths - default will be used
fixme:advpack:set_ldids Need to support changing paths - default will be used
fixme:setupapi:extract_cabinet_file awful hack: extracting cabinet "C:\\users\\john\\Temp\\IXP000.TMP\\MDACxpak.CAB"
fixme:advpack:set_ldids Need to support changing paths - default will be used
fixme:setupapi:extract_cabinet_file awful hack: extracting cabinet "C:\\users\\john\\Temp\\IXP000.TMP\\MSXMLX.CAB"
fixme:advpack:set_ldids Need to support changing paths - default will be used
fixme:setupapi:extract_cabinet_file awful hack: extracting cabinet "C:\\users\\john\\Temp\\IXP000.TMP\\SQLXMLXP.CAB"
fixme:advpack:set_ldids Need to support changing paths - default will be used
fixme:setupapi:extract_cabinet_file awful hack: extracting cabinet "C:\\users\\john\\Temp\\IXP000.TMP\\sqlnet.cab"
fixme:advpack:set_ldids Need to support changing paths - default will be used
fixme:setupapi:extract_cabinet_file awful hack: extracting cabinet "C:\\users\\john\\Temp\\IXP000.TMP\\sqlodbc.cab"
fixme:advpack:set_ldids Need to support changing paths - default will be used
fixme:setupapi:extract_cabinet_file awful hack: extracting cabinet "C:\\users\\john\\Temp\\IXP000.TMP\\SQLOLDB.CAB"
fixme:advpack:set_ldids Need to support changing paths - default will be used
fixme:setupapi:extract_cabinet_file awful hack: extracting cabinet "C:\\users\\john\\Temp\\IXP000.TMP\\JETFILES.CAB"
err:setupapi:SetupDefaultQueueCallbackW copy error 32 L"C:\\users\\john\\Temp\\IXP000.TMP\\mswstr10.dll" -> L"C:\\windows\\system32\\mswstr10.dll"
fixme:setupapi:SetupDefaultQueueCallbackW notification 262144 params e42ee0,0
fixme:setupapi:extract_cabinet_file awful hack: extracting cabinet "C:\\users\\john\\Temp\\IXP000.TMP\\JETFILES.CAB"
fixme:setupapi:SetupDefaultQueueCallbackW notification 262144 params e42ee0,0
fixme:setupapi:extract_cabinet_file awful hack: extracting cabinet "C:\\users\\john\\Temp\\IXP000.TMP\\JETFILES.CAB"
fixme:setupapi:SetupDefaultQueueCallbackW notification 262144 params e42ee0,0
fixme:setupapi:extract_cabinet_file awful hack: extracting cabinet "C:\\users\\john\\Temp\\IXP000.TMP\\JETFILES.CAB"
fixme:setupapi:SetupDefaultQueueCallbackW notification 262144 params e42ee0,0
fixme:setupapi:extract_cabinet_file awful hack: extracting cabinet "C:\\users\\john\\Temp\\IXP000.TMP\\JETFILES.CAB"
Clearing Windows version back to default
Executing early_wine regedit c:\winetrickstmp\unset-winver.reg
Install of mdac28 done
winetricks done.

---

### Post by m3t3ors on 2010-09-06
terminal continued
john@john:~$ sh winetricks
Executing /usr/bin/cabextract --directory=/home/john/.wine/dosdevices/c:/winetrickstmp /home/john/.winetrickscache/3725.exe
Extracting cabinet: /home/john/.winetrickscache/3725.exe
  extracting /home/john/.wine/dosdevices/c:/winetrickstmp/3725.inf
  extracting /home/john/.wine/dosdevices/c:/winetrickstmp/prebind.exe
  extracting /home/john/.wine/dosdevices/c:/winetrickstmp/verinst.exe
  extracting /home/john/.wine/dosdevices/c:/winetrickstmp/Wininet.dll
  extracting /home/john/.wine/dosdevices/c:/winetrickstmp/ADVPACK.DLL
  extracting /home/john/.wine/dosdevices/c:/winetrickstmp/W95INF32.DLL
  extracting /home/john/.wine/dosdevices/c:/winetrickstmp/W95INF16.DLL

All done, no errors.
Executing cp -f /home/john/.wine/dosdevices/c:/winetrickstmp/Wininet.dll /home/john/.wine/dosdevices/c:/windows/system32/wininet.dll
Using native,builtin override for following DLLs: wininet
Executing early_wine regedit c:\winetrickstmp\override-dll.reg
REGEDIT4

[HKEY_CURRENT_USER\Software\Wine\DllOverrides]
"*wininet"="native,builtin"
Install of wininet done
winetricks done.
john@john:~$ sh winetricks
prerequisite wsh57 already installed, skipping
Executing wine /home/john/.winetrickscache/MP10Setup.exe
Executing wine /home/john/.winetrickscache/MP10Setup.exe
fixme:advapi:DecryptFileA "C:\\users\\john\\Temp\\IXP000.TMP\\" 00000000
fixme:ras:RasEnumConnectionsA (0x630607a8,0x334ce8,0x6305f610),stub!
fixme:ras:RasEnumConnectionsA RAS support is not implemented! Configure program to use LAN connection/winsock instead!
fixme:service:EnumServicesStatusA 0x1590a0 type=30 state=1 0x334a70 240 0x334cb4 0x334cbc 0x334cb0
fixme:urlmon:SecManagerImpl_ProcessUrlAction Unsupported arguments
fixme:ras:RasEnumEntriesA ((nil),(null),0x5fcc84,0x5fd440,0x5fd43c),stub!
fixme:setupapi:SetupQueryInfOriginalFileInformationW (0x15ac80, 0, (nil), 0x4cace8): semi-stub
fixme:setupapi:SetupPromptReboot 0x1261d0, (nil), 1
fixme:advapi:ParseStringSidToSid String constant not supported: L"DG"
fixme:advapi:ParseStringSidToSid String constant not supported: L"LG"
fixme:advapi:ParseStringSidToSid String constant not supported: L"DG"
fixme:advapi:ParseStringSidToSid String constant not supported: L"LG"
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation (0x00000021,0x12d490,0x00000010,0x33e75c) stub
fixme:ntdll:NtQuerySystemInformation (0x0000002d,0x12d490,0x00000020,0x33e75c) stub
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_INTERRUPT_INFORMATION
fixme:ntdll:NtQuerySystemInformation (0x00000021,0x12d490,0x00000010,0x33e654) stub
fixme:ntdll:NtQuerySystemInformation (0x0000002d,0x12d490,0x00000020,0x33e654) stub
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_INTERRUPT_INFORMATION
fixme:ntdll:NtQuerySystemInformation (0x00000021,0x12d490,0x00000010,0x33e654) stub
fixme:ntdll:NtQuerySystemInformation (0x0000002d,0x12d490,0x00000020,0x33e654) stub
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_INTERRUPT_INFORMATION
fixme:ntdll:NtQuerySystemInformation (0x00000021,0x12d490,0x00000010,0x33e654) stub
fixme:ntdll:NtQuerySystemInformation (0x0000002d,0x12d490,0x00000020,0x33e654) stub
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_INTERRUPT_INFORMATION
fixme:ntdll:NtQuerySystemInformation (0x00000021,0x12d490,0x00000010,0x33e654) stub
fixme:ntdll:NtQuerySystemInformation (0x0000002d,0x12d490,0x00000020,0x33e654) stub
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_INTERRUPT_INFORMATION
fixme:ntdll:NtQuerySystemInformation (0x00000021,0x12d490,0x00000010,0x33e654) stub
fixme:ntdll:NtQuerySystemInformation (0x0000002d,0x12d490,0x00000020,0x33e654) stub
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_INTERRUPT_INFORMATION
fixme:ntdll:NtQuerySystemInformation (0x00000021,0x12d490,0x00000010,0x33e654) stub
fixme:ntdll:NtQuerySystemInformation (0x0000002d,0x12d490,0x00000020,0x33e654) stub

---

### Post by m3t3ors on 2010-09-06
continued
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_INTERRUPT_INFORMATION
fixme:ntdll:NtQuerySystemInformation (0x00000021,0x12d490,0x00000010,0x33e654) stub
fixme:ntdll:NtQuerySystemInformation (0x0000002d,0x12d490,0x00000020,0x33e654) stub
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_INTERRUPT_INFORMATION
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:setupapi:SetupQueryInfOriginalFileInformationW (0x162728, 0, (nil), 0x4cace8): semi-stub

---

### Post by m3t3ors on 2010-09-06
because the terminal code is long is there an easier way for me to post the out come as it keeps telling me theres too many images?

---

### Post by sgosnell on 2010-09-06
Put it between code tags, thus:  'left square bracket', "code", 'right square bracket', 'terminal output', 'left square bracket', "/code", 'right square bracket'.  That will appear as ```
 terminal output 
``` Or you can attach the code as an image.

---

### Post by m3t3ors on 2010-09-06
[http://ubuntuforums.org/newattachment.php?t=1569143&poststarttime=1283803424&posthash=701b07201361ae8913995d3ec88041a5](http://ubuntuforums.org/newattachment.php?t=1569143&poststarttime=1283803424&posthash=701b07201361ae8913995d3ec88041a5)

heres the terminal output
wouldnt let me add it as too many images?

---

### Post by sgosnell on 2010-09-06
I'm far from a wine expert, but I see this repeatedly: ```
wine: Call from 0x7b836852 to unimplemented function ntoskrnl.exe.KeQueryPriorityThread, aborting 
```which makes me think it's not going to work.  However, the end of the output says wininet was installed successfully.  Assuming the installer on the CD still can't find the ethernet connection, I'm afraid I don't have any more ideas right now.  I'm in the middle of other things today, so I don't really have time to use Google to search for a solution.  Maybe you can find something there.

---

### Post by m3t3ors on 2010-09-06
ok thanks for your help, ive searched google and posted on the winehq forum

i really dont want to go back down the windows route, ive stuck with ubuntu this far, but really need this to work
il stick with the problem, theres got to be a way round it
thanks again

---

