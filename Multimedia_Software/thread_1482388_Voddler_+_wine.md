---
title: "Voddler + wine?"
date: 2010-05-13
forum: Multimedia Software
---

### Post by ulriksvensson on 2010-05-13
Hey guys, this is gonna be a long shot. I'm pretty sure this hasn't been solved by anyone and my skills in linux are too poor to tackle this myself. So here's the problem:

I'm trying to run [Voddler]("http://www.voddler.com") with wine. I'm running Ubuntu 10.04 LTS and 

```
ulrik@ulrik-laptop:~$ uname -r
2.6.32-22-generic
```The installation of Voddler seemed to go alright but it doesn't work at all:

```
ulrik@ulrik-laptop:~/.wine/dosdevices/c:/Program Files/Voddler/VoddlerPlayer$ wine VoddlerPlayer.exe 
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
fixme:reg:GetNativeSystemInfo (0xafe530) using GetSystemInfo()
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on VIA 82XX modem, disabling mixer
fixme:lsa:LsaGetLogonSessionData 0x32f184 0x32f178 stub
fixme:reg:GetNativeSystemInfo (0x32ecec) using GetSystemInfo()
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
fixme:win:EnumDisplayDevicesW ((null),0,0x32e858,0x00000000), stub!
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:dwmapi:DwmIsCompositionEnabled 0x32eed0
fixme:d3d:IWineD3DBaseSwapChainImpl_GetRasterStatus iface 0x19f910, raster_status 0x32e89c stub!
```Here it hangs and nothing happens.

Any ideas?

---

### Post by dv3500ea on 2010-05-13
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=17597&iTestingId=48115]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=17597&iTestingId=48115")

It looks like this program can't currently be run with wine :(

---

### Post by syltty on 2010-05-14
somebody managed to get voddler working with ubuntu:

[http://geexercise.blogspot.com/2010/04/install-newer-voddler.html]("http://geexercise.blogspot.com/2010/04/install-newer-voddler.html")

the script failed to install adobe air deb but I downloaded the package and installed it manually. I still have some problem with video settings, when movie starts all I get is a black screen.

---

### Post by Naguz on 2010-05-15
I have tried follwin the same instructions (adapted a bit to "install" tha Air app manually, since I am running arch linux),but i get "
Oops, something went wrong

You don't seem to have the correct version of Voddler installed"
I first thought this was because the guide uses an outdated Voddler version, and tried doing the same with the updated one. Same result. Then I checked using chromium (not runnin trough wine), and i get the exact same error message. This lead me to believe that the Firefox plugin mentioned in the guide is never really installed by Voddler Setup. It seems strange that I should get the exact same error under chromium in linux. Does it require a specific Firefox version? I just downloaded the latest one for windows from mozilla.com.

Edit: I am trying wit ie7 trough wine now, and it has been testing for ~5 mins. At least it doesn't just error out on me right away, but I doubt it will work after stalling for 5 mins. :(

edit2: The output when launching firefox, if that is any help:
```
[gert@blad opt]$ wine ~/.wine/drive_c/Programfiler/Mozilla\ Firefox/firefox.exe [http://voddler.com/help/test](http://voddler.com/help/test)
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x33fcd4
fixme:iphlpapi:NotifyAddrChange (Handle 0xcfe9a0, overlapped 0xcfe984): stub
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
err:ole:CoGetClassObject class {591209c7-767b-42b2-9fba-44ee4615f2c7} not registered
err:ole:CoGetClassObject class {591209c7-767b-42b2-9fba-44ee4615f2c7} not registered
err:ole:CoGetClassObject no class object {591209c7-767b-42b2-9fba-44ee4615f2c7} could be created for context 0x3
fixme:resource:GetGuiResources (0xffffffff,0): stub
fixme:win:FlashWindowEx 0x33e390
fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented
NPP_New: Got current URL of [http://www.voddler.com/help/test](http://www.voddler.com/help/test)
ScriptableObject::Allocate: Allocated object 03504940
```

---

### Post by a3101 on 2010-06-24
> **Naguz said:**
> I have tried follwin the same instructions (adapted a bit to "install" tha Air app manually, since I am running arch linux),but i get "
Oops, something went wrong

You don't seem to have the correct version of Voddler installed"
I first thought this was because the guide uses an outdated Voddler version, and tried doing the same with the updated one. Same result. Then I checked using chromium (not runnin trough wine), and i get the exact same error message. This lead me to believe that the Firefox plugin mentioned in the guide is never really installed by Voddler Setup. It seems strange that I should get the exact same error under chromium in linux. Does it require a specific Firefox version? I just downloaded the latest one for windows from mozilla.com.

Edit: I am trying wit ie7 trough wine now, and it has been testing for ~5 mins. At least it doesn't just error out on me right away, but I doubt it will work after stalling for 5 mins. :(

edit2: The output when launching firefox, if that is any help:
```
[gert@blad opt]$ wine ~/.wine/drive_c/Programfiler/Mozilla\ Firefox/firefox.exe [http://voddler.com/help/test](http://voddler.com/help/test)
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x33fcd4
fixme:iphlpapi:NotifyAddrChange (Handle 0xcfe9a0, overlapped 0xcfe984): stub
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
err:ole:CoGetClassObject class {591209c7-767b-42b2-9fba-44ee4615f2c7} not registered
err:ole:CoGetClassObject class {591209c7-767b-42b2-9fba-44ee4615f2c7} not registered
err:ole:CoGetClassObject no class object {591209c7-767b-42b2-9fba-44ee4615f2c7} could be created for context 0x3
fixme:resource:GetGuiResources (0xffffffff,0): stub
fixme:win:FlashWindowEx 0x33e390
fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented
NPP_New: Got current URL of [http://www.voddler.com/help/test](http://www.voddler.com/help/test)
ScriptableObject::Allocate: Allocated object 03504940
```

I have the same "something went wrong" prompt, I ran [http://geexercise.blogspot.com/2010/...r-voddler.html]("http://geexercise.blogspot.com/2010/04/install-newer-voddler.html") .sh script. Had to install Air manually. But also if you look at the .sh script, it should create some folders under /opt/, but it doesn't, and it creates the shortcuts to desktop and they lead to non-existing subfolders under /opt. I'm having 10.4 ubuntu.

I really hope some geek can solve this.. ;)

---

### Post by syltty on 2010-08-24
To get VoddlerSetup-2.1.1338.exe to working with wine you have import following to wine registry after running the script from [http://geexercise.blogspot.com](http://geexercise.blogspot.com) site:
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall\VoddlerPlayer.22AA32E1C519F8FB77514A36DC6C2AE2C623240F.1]
"DisplayIcon"="C:\\Program Files\\Voddler\\VoddlerPlayer\\VoddlerPlayer.exe"
"DisplayName"="VoddlerPlayer"
"DisplayVersion"="2.1.1338"
"VersionMajor"="2"
"VersionMinor"="1"
"InstallLocation"="C:\\Program Files\\Voddler\\VoddlerPlayer\\"
"NoModify"=dword:00000001
"NoRepair"=dword:00000001
"Publisher"="Voddler Sweden AB"
"UninstallString"="msiexec /qb /x {E7D6D8D0-B750-0A0E-8FAA-BC0388CBD5F1}"
save above to file and then
export WINEPREFIX=/path/to/wine_voddler_install_dir
regedit
and import the file to registy. After that voddler should work

---

### Post by simosays on 2010-11-27
Wine version 1.3.7 or greater have been recognized to been able to run Voddler (2.2.1521) without any special magic with scripts or registry edit. Only thing to concern is that quite much power needed from your graphics card. 

[http://appdb.winehq.org/objectManager.php?bShowAll=true&bIsQueue=false&bIsRejected=false&sClass=version&sTitle=&sReturnTo=&iId=21956]("http://appdb.winehq.org/objectManager.php?bShowAll=true&bIsQueue=false&bIsRejected=false&sClass=version&sTitle=&sReturnTo=&iId=21956")

---

### Post by RikardSvenningsen on 2011-01-08
> **syltty said:**
> To get VoddlerSetup-2.1.1338.exe to working with wine you have import following to wine registry after running the script from [http://geexercise.blogspot.com](http://geexercise.blogspot.com) site:
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall\VoddlerPlayer.22AA32E1C519F8FB77514A36DC6C2AE2C623240F.1]
"DisplayIcon"="C:\\Program Files\\Voddler\\VoddlerPlayer\\VoddlerPlayer.exe"
"DisplayName"="VoddlerPlayer"
"DisplayVersion"="2.1.1338"
"VersionMajor"="2"
"VersionMinor"="1"
"InstallLocation"="C:\\Program Files\\Voddler\\VoddlerPlayer\\"
"NoModify"=dword:00000001
"NoRepair"=dword:00000001
"Publisher"="Voddler Sweden AB"
"UninstallString"="msiexec /qb /x {E7D6D8D0-B750-0A0E-8FAA-BC0388CBD5F1}"
save above to file and then
export WINEPREFIX=/path/to/wine_voddler_install_dir
regedit
and import the file to registy. After that voddler should work

After running the ubuntu-voddler-installer.sh from this site:
[http://geexercise.blogspot.com/2010/04/ubuddler.html](http://geexercise.blogspot.com/2010/04/ubuddler.html)
And done checking the above Registery settings at this time writing:
"DisplayVersion"="3.1"
"VersionMajor"="3"
"VersionMinor"="1"
then it works on my Ubuntu 10.04 on iMAC (Mac Mini)
You might need to run the installer a few times and watch out, Adobe Air will install and after that VoddlerPlayer will install, but before that the installer script might say it's done, you have to wait a few seconds to bee sure that the player is installed, before you push the done button..
By the way.
After running the installer you need to check the above registry one more time, it seems to loose every time the installer runs.

Running almost as good as in my MAC OS x 10.6
It takes a little more resource, this is done on a screen 1920 x 1080. less resolution gives a smooth movie ...
Thanks for all the effort done...

---

### Post by ksatta on 2011-02-23
> **RikardSvenningsen said:**
> 
And done checking the above Registery settings at this time writing:
"DisplayVersion"="3.1"
"VersionMajor"="3"
"VersionMinor"="1"


Works for me too, just had to run the installer twice. Not sure if it's neccessary because at first I didn't edit the registry. On the first run the installer gave me some errors probably because the backup directories didn't exist (since it was the first install).

On the second run the installer gave me the following errors:
chmod: cannot access `VoddlerPlayer/xml/config.xml': No such file or directory
/usr/bin/gksudo
cp: cannot stat `VoddlerPlayer/xml/config.xml': No such file or directory./ubuntu-voddler-installer.sh: line 58: kdesudo: command not found

These errors might be because I'm running xubuntu, but they don't seem to matter 

The current version of voddler is 3.11, so now you have to put this in the registry:
"DisplayVersion"="3.11"
"VersionMajor"="3"
"VersionMinor"="11"

Also I had to run wine net stop VoddlerNet and then wine net start VoddlerNet.

Great work guys! thanks for the script.

edit: The only (minor?) problem I'm having now is that the vertical sync is not working, so there is tearing in the videos. I started a new thread on the problem: [http://ubuntuforums.org/showthread.php?t=1694446](http://ubuntuforums.org/showthread.php?t=1694446)

---

