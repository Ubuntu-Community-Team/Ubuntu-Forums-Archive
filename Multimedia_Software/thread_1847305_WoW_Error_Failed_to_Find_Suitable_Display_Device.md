---
title: "WoW Error Failed to Find Suitable Display Device"
date: 2011-09-20
forum: Multimedia Software
---

### Post by EmyrB on 2011-09-20
Hi All

I'm running 64 bit Oneiric and up until Sunday WoW was fine. Now when I try to launch WoW I get the above error.

In WoW config.wtf I've added

SET gxAPI "OpenGL"

glxinfo | grep rendering
direct rendering: Yes

wine --version
wine-1.2.3

I get the following when I run through Terminal

> 
wine: cannot find L"C:\\windows\\system32\\plugplay.exe"
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 3000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 3000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 3000
archive Data/Cache/SoundCache-1.MPQ opened
archive Data/Cache/SoundCache-2.MPQ opened
archive Data/Cache/SoundCache-3.MPQ opened
archive Data/Cache/SoundCache-0.MPQ opened
archive Data/Cache/enGB/SoundCache-enGB.MPQ opened
archive Data/wow-update-13164.MPQ opened
archive Data/Cache/patch-base-13164.MPQ opened
archive Data/Cache/enGB/patch-enGB-13164.MPQ opened
archive Data/Cache/SoundCache-patch-13164.MPQ opened
archive Data/Cache/enGB/SoundCache-patch-enGB-13164.MPQ opened
archive Data/wow-update-13205.MPQ opened
archive Data/Cache/patch-base-13205.MPQ opened
archive Data/Cache/enGB/patch-enGB-13205.MPQ opened
archive Data/Cache/SoundCache-patch-13205.MPQ opened
archive Data/Cache/enGB/SoundCache-patch-enGB-13205.MPQ opened
archive Data/wow-update-13287.MPQ opened
archive Data/Cache/patch-base-13287.MPQ opened
archive Data/Cache/enGB/patch-enGB-13287.MPQ opened
archive Data/Cache/SoundCache-patch-13287.MPQ opened
archive Data/Cache/enGB/SoundCache-patch-enGB-13287.MPQ opened
archive Data/wow-update-13329.MPQ opened
archive Data/Cache/patch-base-13329.MPQ opened
archive Data/Cache/enGB/patch-enGB-13329.MPQ opened
archive Data/Cache/SoundCache-patch-13329.MPQ opened
archive Data/Cache/enGB/SoundCache-patch-enGB-13329.MPQ opened
archive Data/wow-update-13596.MPQ opened
archive Data/Cache/patch-base-13596.MPQ opened
archive Data/Cache/enGB/patch-enGB-13596.MPQ opened
archive Data/Cache/SoundCache-patch-13596.MPQ opened
archive Data/Cache/enGB/SoundCache-patch-enGB-13596.MPQ opened
archive Data/wow-update-13623.MPQ opened
archive Data/Cache/patch-base-13623.MPQ opened
archive Data/Cache/enGB/patch-enGB-13623.MPQ opened
archive Data/Cache/SoundCache-patch-13623.MPQ opened
archive Data/Cache/enGB/SoundCache-patch-enGB-13623.MPQ opened
archive Data/wow-update-base-13914.MPQ opened
archive Data/enGB/wow-update-enGB-13914.MPQ opened
archive Data/Cache/patch-base-13914.MPQ opened
archive Data/Cache/enGB/patch-enGB-13914.MPQ opened
archive Data/Cache/SoundCache-patch-13914.MPQ opened
archive Data/Cache/enGB/SoundCache-patch-enGB-13914.MPQ opened
archive Data/wow-update-base-14007.MPQ opened
archive Data/enGB/wow-update-enGB-14007.MPQ opened
archive Data/Cache/patch-base-14007.MPQ opened
archive Data/Cache/enGB/patch-enGB-14007.MPQ opened
archive Data/Cache/SoundCache-patch-14007.MPQ opened
archive Data/Cache/enGB/SoundCache-patch-enGB-14007.MPQ opened
archive Data/wow-update-base-14333.MPQ opened
archive Data/enGB/wow-update-enGB-14333.MPQ opened
archive Data/Cache/patch-base-14333.MPQ opened
archive Data/Cache/enGB/patch-enGB-14333.MPQ opened
archive Data/Cache/SoundCache-patch-14333.MPQ opened
archive Data/Cache/enGB/SoundCache-patch-enGB-14333.MPQ opened
archive Data/wow-update-base-14480.MPQ opened
archive Data/enGB/wow-update-enGB-14480.MPQ opened
archive Data/Cache/patch-base-14480.MPQ opened
archive Data/Cache/enGB/patch-enGB-14480.MPQ opened
archive Data/Cache/SoundCache-patch-14480.MPQ opened
archive Data/Cache/enGB/SoundCache-patch-enGB-14480.MPQ opened
archive Data/wow-update-base-14545.MPQ opened
archive Data/enGB/wow-update-enGB-14545.MPQ opened
archive Data/Cache/patch-base-14545.MPQ opened
archive Data/Cache/enGB/patch-enGB-14545.MPQ opened
archive Data/Cache/SoundCache-patch-14545.MPQ opened
archive Data/Cache/enGB/SoundCache-patch-enGB-14545.MPQ opened
archive Data\enGB\speech-enGB.MPQ opened
archive Data\enGB\locale-enGB.MPQ opened
archive Data\sound.MPQ opened
archive Data\world.MPQ opened
archive Data\art.MPQ opened
fixme:win:EnumDisplayDevicesW ((null),0,0x32ecdc,0x00000000), stub!
err:d3d_caps:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat.
err:d3d:InitAdapters Failed to get a gl context for default adapter
Direct3D9 is not available without OpenGL.
err:d3d_caps:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat.
err:d3d:InitAdapters Failed to get a gl context for default adapter
Direct3D9 is not available without OpenGL.


I originally had Wine 1.3.27 installed when the error occurred. I removed this and installed the current stable version of Wine.

I have removed the nvidia propriety driver version 280.13 and reinstalled. I haven't tried version 173 which is available in Jockey. I don't want to do a complete reinstall of WoW but I haven't ruled it out.

Any help will be gratefully received.

Cheers

EmyrB

---

### Post by flintman on 2011-09-22
Same issue here Ill be looking into it tomorrow i need to go to bed

---

### Post by xethm55 on 2011-09-26
As a temporary work around, you can prefix your wine command with the following:
```
LD_PRELOAD=/usr/lib32/nvidia-current/libGL.so
```
If you have an NVidia card, something similar should exist for AMD/ATI cards

---

### Post by Tweak42 on 2011-09-27
> **xethm55 said:**
> As a temporary work around, you can prefix your wine command with the following:
```
LD_PRELOAD=/usr/lib32/nvidia-current/libGL.so
```
If you have an NVidia card, something similar should exist for AMD/ATI cards

Thanks this worked for me.:popcorn:

---

### Post by teh603 on 2011-09-27
Ok, I'm running Kubuntu here so my menu editor probably looks a little different from yours, but I'm having the exact same problem with the Ocelot beta. Can someone give me a slightly more in-depth walkthru on this?

---

### Post by Tweak42 on 2011-09-28
> **teh603 said:**
> Ok, I'm running Kubuntu here so my menu editor probably looks a little different from yours, but I'm having the exact same problem with the Ocelot beta. Can someone give me a slightly more in-depth walkthru on this?

I currently run wow from the command line.  You have to try tacking on the PRELOAD to a launcher script to see it it accepts it.

```
$ LD_PRELOAD=/usr/lib32/nvidia-current/libGL.so wine ~/World\ of\ Warcraft/Wow.exe -opengl
```

---

### Post by EmyrB on 2011-09-30
I solved this. Not sure if this will help anyone else, but basically I was goofing about and installed GnomeShell and then Cairo Dock 2.4.0. I logged into the Cairo Dock session and quite by accident I double-clicked the World of Warcraft icon and it launched correctly. It was like I had just installed the game, I had the Cataclysm intro, had re-enter my username and pick my realm. When I checked it had written a new config.wtf.

I logged out and back into my Unity session and it worked there also. So basically try renaming your config.wtf to something like config.old and then launch the game.

Now the only issue I get is that all sound stops at different points in the game and only comes back if I exit and restart the game. I am pretty sure that this is an issue with Wine 1.2.3

---

### Post by Tweak42 on 2011-09-30
> **EmyrB said:**
> 
Now the only issue I get is that all sound stops at different points in the game and only comes back if I exit and restart the game. I am pretty sure that this is an issue with Wine 1.2.3

Whenever I had the sound die using Wine 1.3, changing a hardware setting in the options->interface->sounds menu fixed it without rebooting.  Not sure if it will do the same in 1.2.

---

### Post by Salachazar on 2012-01-20
Hi All

I'm running 32 bit Ubuntu 11.10, I'm really noob to linux, so pleasy be patient. I downloaded wine, copied wow from win XP. Creater launcher on Desktop...   

env WINEPREFIX="/home/filip/.wine-wow" wine "C:\Program Files\World of Warcraft\Wow.exe" -opengl 

then wrote som stuff do config.wtf, tried to run it with wow-launcher, i googled out that i need to change path to wow.exe, but then...
 
Error Failed to Find Suitable Display Device. Exiting Program

so i googled out

> **xethm55 said:**
> As a temporary work around, you can prefix your wine command with the following:
```
LD_PRELOAD=/usr/lib32/nvidia-current/libGL.so
```If you have an  NVidia card, something similar should exist for AMD/ATI cards

...well yeah, prefix.... what the h***??   i didnt understood because my English & linux & wine skill isnt sufficient... so i saw somewhere that config.wtf rename could help... it didnt... so now i really dont know what to do...  this appears when a type this into terminal: env WINEPREFIX="/home/filip/.wine-wow" wine "C:\Program Files\World of Warcraft\Wow.exe" -opengl 

> Xlib:  extension "GLX" missing on display ":0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
fixme:process:GetLogicalProcessorInformation (0x32f650,0x32fc50): stub
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT/DATA_SEND_TIMEOUT 3000

fixme:process:GetLogicalProcessorInformation (0x15fbf6c,0x15fc56c): stub
fixme:process:GetLogicalProcessorInformation (0x15fbf6c,0x15fc56c): stub
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:process:GetLogicalProcessorInformation (0x16fe2f0,0x16fe8f0): stub
fixme:process:GetLogicalProcessorInformation (0x16fe2f0,0x16fe8f0): stub
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT/DATA_SEND_TIMEOUT 3000
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:(fu... smiles) process:GetLogicalProcessorInformation (0x16fe2f0,0x16fe8f0): stub
fixmerocess:GetLogicalProcessorInformation (0x16fe2f0,0x16fe8f0): stub
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT/DATA_SEND_TIMEOUT 3000
fixmerocess:GetLogicalProcessorInformation (0x16fe2f0,0x16fe8f0): stub
fixmerocess:GetLogicalProcessorInformation (0x16fe2f0,0x16fe8f0): stub
fixmerocess:GetLogicalProcessorInformation (0x32f584,0x32fb84): stub
fixme:process:GetLogicalProcessorInformation (0x32f584,0x32fb84): stub
archive Data/Cache/SoundCache-1.MPQ opened
archive Data/Cache/SoundCache-2.MPQ opened
archive Data/Cache/SoundCache-3.MPQ opened
archive Data/Cache/SoundCache-0.MPQ opened
archive Data/Cache/enGB/SoundCache-enGB.MPQ opened
archive Data/wow-update-13164.MPQ opened
archive Data/Cache/patch-base-13164.MPQ opened
archive Data/Cache/enGB/patch-enGB-13164.MPQ opened
archive Data/Cache/SoundCache-patch-13164.MPQ opened
archive Data/Cache/enGB/SoundCache-patch-enGB-13164.MPQ opened
archive Data/wow-update-13205.MPQ opened
archive Data/Cache/patch-base-13205.MPQ opened
archive Data/Cache/enGB/patch-enGB-13205.MPQ opened
archive Data/Cache/SoundCache-patch-13205.MPQ opened
archive Data/Cache/enGB/SoundCache-patch-enGB-13205.MPQ opened
archive Data/wow-update-13287.MPQ opened
archive Data/Cache/patch-base-13287.MPQ opened
archive Data/Cache/enGB/patch-enGB-13287.MPQ opened
archive Data/Cache/SoundCache-patch-13287.MPQ opened
archive Data/Cache/enGB/SoundCache-patch-enGB-13287.MPQ opened
archive Data/wow-update-13329.MPQ opened
archive Data/Cache/patch-base-13329.MPQ opened
archive Data/Cache/enGB/patch-enGB-13329.MPQ opened
archive Data/Cache/SoundCache-patch-13329.MPQ opened
archive Data/Cache/enGB/SoundCache-patch-enGB-13329.MPQ opened
archive Data/wow-update-13596.MPQ opened
archive Data/Cache/patch-base-13596.MPQ opened
archive Data/Cache/enGB/patch-enGB-13596.MPQ opened
archive Data/Cache/SoundCache-patch-13596.MPQ opened
archive Data/Cache/enGB/SoundCache-patch-enGB-13596.MPQ opened
archive Data/wow-update-13623.MPQ opened
archive Data/Cache/patch-base-13623.MPQ opened
archive Data/Cache/enGB/patch-enGB-13623.MPQ opened
archive Data/Cache/SoundCache-patch-13623.MPQ opened
archive Data/Cache/enGB/SoundCache-patch-enGB-13623.MPQ opened
archive Data/wow-update-base-13914.MPQ opened
archive Data/enGB/wow-update-enGB-13914.MPQ opened
archive Data/Cache/patch-base-13914.MPQ opened
archive Data/Cache/enGB/patch-enGB-13914.MPQ opened
archive Data/Cache/SoundCache-patch-13914.MPQ opened
archive Data/Cache/enGB/SoundCache-patch-enGB-13914.MPQ opened
archive Data/wow-update-base-14007.MPQ opened
archive Data/enGB/wow-update-enGB-14007.MPQ opened
archive Data/Cache/patch-base-14007.MPQ opened
archive Data/Cache/enGB/patch-enGB-14007.MPQ opened
archive Data/Cache/SoundCache-patch-14007.MPQ opened
archive Data/Cache/enGB/SoundCache-patch-enGB-14007.MPQ opened
archive Data/wow-update-base-14333.MPQ opened
archive Data/enGB/wow-update-enGB-14333.MPQ opened
archive Data/Cache/patch-base-14333.MPQ opened
archive Data/Cache/enGB/patch-enGB-14333.MPQ opened
archive Data/Cache/SoundCache-patch-14333.MPQ opened
archive Data/Cache/enGB/SoundCache-patch-enGB-14333.MPQ opened
archive Data/wow-update-base-14480.MPQ opened
archive Data/enGB/wow-update-enGB-14480.MPQ opened
archive Data/Cache/patch-base-14480.MPQ opened
archive Data/Cache/enGB/patch-enGB-14480.MPQ opened
archive Data/Cache/SoundCache-patch-14480.MPQ opened
archive Data/Cache/enGB/SoundCache-patch-enGB-14480.MPQ opened
archive Data/wow-update-base-14545.MPQ opened
archive Data/enGB/wow-update-enGB-14545.MPQ opened
archive Data/Cache/patch-base-14545.MPQ opened
archive Data/Cache/enGB/patch-enGB-14545.MPQ opened
archive Data/Cache/SoundCache-patch-14545.MPQ opened
archive Data/Cache/enGB/SoundCache-patch-enGB-14545.MPQ opened
archive Data/wow-update-base-14946.MPQ opened
archive Data/enGB/wow-update-enGB-14946.MPQ opened
archive Data/Cache/patch-base-14946.MPQ opened
archive Data/Cache/enGB/patch-enGB-14946.MPQ opened
archive Data/Cache/SoundCache-patch-14946.MPQ opened
archive Data/Cache/enGB/SoundCache-patch-enGB-14946.MPQ opened
archive Data/wow-update-base-15005.MPQ opened
archive Data/enGB/wow-update-enGB-15005.MPQ opened
archive Data/Cache/patch-base-15005.MPQ opened
archive Data/Cache/enGB/patch-enGB-15005.MPQ opened
archive Data/Cache/SoundCache-patch-15005.MPQ opened
archive Data/Cache/enGB/SoundCache-patch-enGB-15005.MPQ opened
archive Data/wow-update-base-15050.MPQ opened
archive Data/enGB/wow-update-enGB-15050.MPQ opened
archive Data/Cache/patch-base-15050.MPQ opened
archive Data/Cache/enGB/patch-enGB-15050.MPQ opened
archive Data/Cache/SoundCache-patch-15050.MPQ opened
archive Data/Cache/enGB/SoundCache-patch-enGB-15050.MPQ opened
archive Data\enGB\expansion3-speech-enGB.MPQ opened
archive Data\enGB\expansion3-locale-enGB.MPQ opened
archive Data\expansion3.MPQ opened
archive Data\enGB\expansion2-speech-enGB.MPQ opened
archive Data\enGB\expansion2-locale-enGB.MPQ opened
archive Data\expansion2.MPQ opened
archive Data\enGB\expansion1-speech-enGB.MPQ opened
archive Data\enGB\expansion1-locale-enGB.MPQ opened
archive Data\expansion1.MPQ opened
archive Data\enGB\speech-enGB.MPQ opened
archive Data\enGB\locale-enGB.MPQ opened
archive Data\sound.MPQ opened
archive Data\world.MPQ opened
archive Data\art.MPQ opened
fixme:win:EnumDisplayDevicesW ((null),0,0x32ed50,0x00000000), stub!
err:d3d_caps:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat.
err:d3d:InitAdapters Failed to get a gl context for default adapter
Direct3D9 is not available without OpenGL.
err:d3d_caps:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat.
err:d3d:InitAdapters Failed to get a gl context for default adapter
Direct3D9 is not available without OpenGL.
filip@filip-Ideapad-Z570:~$
then it throw another error window failed to find suitable display device...

---

### Post by Tweak42 on 2012-01-21
> **Salachazar said:**
> Hi All

I'm running 32 bit Ubuntu 11.10, I'm really noob to linux, so pleasy be patient. I downloaded wine, copied wow from win XP. Creater launcher on Desktop...   

env WINEPREFIX="/home/filip/.wine-wow" wine "C:\Program Files\World of Warcraft\Wow.exe" -opengl 

then wrote som stuff do config.wtf, tried to run it with wow-launcher, i googled out that i need to change path to wow.exe, but then...
 
Error Failed to Find Suitable Display Device. Exiting Program

so i googled out



...well yeah, prefix.... what the h***??   i didnt understood because my English & linux & wine skill isnt sufficient... so i saw somewhere that config.wtf rename could help... it didnt... so now i really dont know what to do...  this appears when a type this into terminal: env WINEPREFIX="/home/filip/.wine-wow" wine "C:\Program Files\World of Warcraft\Wow.exe" -opengl 

then it throw another error window failed to find suitable display device...


What versions of wine and video drivers are you using?

---

### Post by Salachazar on 2012-01-21
hi...
wine1.3   1.3.28-0ubuntu1

video drivers... dunno...  system ->   additional drivers  -> NVIDIA accelerated graphics driver(post release-updates) (version current-updates)
> 
filip@filip-Ideapad-Z570:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation Device 1050 (rev a1)
03:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05) 

---

### Post by Tweak42 on 2012-01-21
> **Salachazar said:**
> hi...
wine1.3   1.3.28-0ubuntu1

video drivers... dunno...  system ->   additional drivers  -> NVIDIA accelerated graphics driver(post release-updates) (version current-updates)

Sounds like you need updated nvidia drivers.  You can check the version by running the nvidia settings GUI tool. Search for adding the ubuntu xupdates ppa to your system so you can update to the latest driver.

---

