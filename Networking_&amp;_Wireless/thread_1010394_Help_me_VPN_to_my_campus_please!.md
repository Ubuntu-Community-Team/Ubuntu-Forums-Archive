---
title: "Help me VPN to my campus please!"
date: 2008-12-13
forum: Networking &amp; Wireless
---

### Post by MaindotC on 2008-12-13
My campus is a Windows shop so when we are off campus we typically use a windows application to install a VPN client.  The file is called MSC_VPN.exe.  I'm like to know which configurations to enter to a linux VPN client to use when I am off campus.  I checked out KVPNC but if you suggest a different client I welcome your suggestions.  Of course my network administrators would not have the time or the desire to help support a *nix client.

I used cabextract to pull out the files from the executable.  I don't know which files will help you help me figure this out but here's what I have from cabextract:  
```

advpack.dll  cmexcept.cat  cnet16.dll   MSC_VPN.cmp  MSC_VPN.inf   w95inf32.dll ccfg95.dll   cmstp.exe     instcm.inf   MSC_VPN.cms  cmbins.exe   cmutoa.dll    msc_vpn.bmp  MSC_VPN.exe  w95inf16.dll

```

I don't know what the forum policy is on uploading files so if anyone can help me figure this out just tell me which file you want to see and I'll post its contents.  For example, the MSC_VPN.inf has some understandable language:
```

===========================================================================

;

; All of the customizable sections of this file are in the [Strings] section

; at the bottom.

;

;===========================================================================

[version]

Signature=$chicago$

AdvancedINF=2.5



[CmDial32.Dll]

Version=458754

Build=248381440



; -------------------------------------------------------------------

; All User Installs

; -------------------------------------------------------------------

[DefaultInstall]

SmartReboot=N

CustomDestination=CustInstDestSectionAllUsers

RunPreSetupCommands=RunPreSetupCommandsSection

CopyFiles=Xnstall.CopyFiles, Xnstall.CopyFiles.ICM

AddReg=Xnstall.RenameReg, Xnstall.AddReg.AllUsers

RegisterOCXs=RegisterOCXSection



; -------------------------------------------------------------------

; Launches the All User postinstall commands

; -------------------------------------------------------------------

[PostInstall]

SmartReboot=N

CustomDestination=CustInstDestSectionAllUsers

RunPostSetupCommands=RunPostSetupCommandsSection



; -------------------------------------------------------------------

; Single User installs cannot handle the RenameReg Section

; -------------------------------------------------------------------

[DefaultInstall_SingleUser]

SmartReboot=N

CustomDestination=CustInstDestSectionSingleUsers

RunPreSetupCommands=RunPreSetupCommandsSection

CopyFiles=Xnstall.CopyFiles.SingleUser, Xnstall.CopyFiles.ICM

AddReg = Xnstall.AddReg.Private

RegisterOCXs=RegisterOCXSection



; -------------------------------------------------------------------

; Launches the Single User postinstall commands

; -------------------------------------------------------------------

[PostInstall_Single]

SmartReboot=N

CustomDestination=CustInstDestSectionSingleUsers

RunPostSetupCommands=RunPostSetupCommandsSection



; -------------------------------------------------------------------

; This file section sets up the desktop icon GUID and is thus

; only needed on legacy systems.

; -------------------------------------------------------------------

[Xnstall_Legacy]

SmartReboot=N

CustomDestination=CustInstDestSectionAllUsers

AddReg=Xnstall.AddReg.DesktopIcon, Xnstall.AddReg.Icon



; These section are kept for legacy compatibility but are no longer used.

[Xnstall_Private]

[Xnstall_AllUser]



; -------------------------------------------------------------------

; Section used to uninstall Private user profiles

; -------------------------------------------------------------------

[Remove_Private]

Cleanup=1

SmartReboot=N

BeginPrompt=RemoveBeginPromptSection

EndPrompt=RemoveEndPromptSection

RunPreSetupCommands=RunPreUnInstCommandsSection

CustomDestination=CustUnInstDestSectionPrivate

DelFiles=Remove.DelFiles, Remove.DelFiles.ICM

DelReg=Remove.DelReg.Private

DelDirs=CleanDir

RunPostSetupCommands=RunPostUnInstCommandsSection



; -------------------------------------------------------------------

; Section used to uninstall All User profiles 

; -------------------------------------------------------------------

[Remove]

Cleanup=1

SmartReboot=N

BeginPrompt=RemoveBeginPromptSection

EndPrompt=RemoveEndPromptSection

RunPreSetupCommands=RunPreUnInstCommandsSection

CustomDestination=CustUninstDestSectionAllUsers

DelFiles=Remove.DelFiles, Remove.DelFiles.ICM

DelReg=Remove.DelReg.AllUser

DelDirs=CleanDir

RunPostSetupCommands=RunPostUnInstCommandsSection



; The following Run(Pre/Post)SetupCommandsSections allow you to run commands before or

; after the profile is installed.

;

; Similarly the following Run(Pre/Post)UnInstCommandsSections will allow you to run

; commands before or after the profile is uninstalled.

;

; An example command line is:

; Myprogram.exe /<switches> <options>



[RunPreSetupCommandsSection]

; Commands Here will be run Before Setup Begins to install



[RunPostSetupCommandsSection]

;Commands here will be run After setup finishes



[RunPreUnInstCommandsSection]

;Commands here will be run before Uninstall Begins



[RunPostUnInstCommandsSection]

;Commands here will be run after Uninstall Finishes



; -------------------------------------------------------------------

; These are the registry entries for installation.

; -------------------------------------------------------------------

[Xnstall.AddReg.DesktopIcon]

"HKCR", "CLSID\%DesktopGUID%",,,"%ServiceName%"

"HKLM", "SOFTWARE\Microsoft\Windows\CurrentVersion\explorer\Desktop\NameSpace\%DesktopGUID%",,,"%ServiceName%"

"HKCR", "CLSID\%DesktopGUID%\ShellFolder","Attributes",1,"00","00","00","00"

; Please make sure the following three commands are alphabetized by the %Open%, %Delete%,

; and %Settings% entries defined in the Strings section

; the Connect Command

"HKCR", "CLSID\%DesktopGUID%\Shell\Open\Command",,,"cmmgr32.exe ""%49000%\%ShortSvcName%.cmp"""

"HKCR", "CLSID\%DesktopGUID%\Shell\Open",,,"%Open%"

; the Delete Command

"HKCR", "CLSID\%DesktopGUID%\Shell\Delete\Command",,,"cmstp.exe /u ""%49000%\%ShortSvcName%\%ShortSvcName%.inf"""

"HKCR", "CLSID\%DesktopGUID%\Shell\Delete",,,"%Delete%"

; the Properties Command

"HKCR", "CLSID\%DesktopGUID%\Shell\Settings...\Command",,,"cmmgr32.exe /settings ""%49000%\%ShortSvcName%.cmp"""

"HKCR", "CLSID\%DesktopGUID%\Shell\Settings...",,,"%Settings%"



[Xnstall.AddReg.AllUsers]

"HKLM", "SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall\%ShortSvcName%", "UninstallDir", "", "%49001%"

"HKLM", "%AppAct%\Mappings","%ServiceName%","","%49001%\%ShortSvcName%.cmp"



[Xnstall.AddReg.Private]

; Single User Mappings is now written in code.

;"HKCU", "%AppAct%\Mappings","%ServiceName%","","%%UserProfile%%\%PathFromProfileDir%\%ShortSvcName%.cmp"



; -------------------------------------------------------------------

; These are the registry settings which

; are deleted during uninstall.

; -------------------------------------------------------------------

[Remove.DelReg.AllUser]

"HKLM", "%AppAct%\%ServiceName%"

"HKLM", "%AppAct%\Mappings","%ServiceName%"

"HKCU", "%AppAct%\UserInfo\%ServiceName%"

"HKCR", "CLSID\%DesktopGUID%"

"HKLM", "SOFTWARE\Microsoft\Windows\CurrentVersion\explorer\Desktop\NameSpace\%DesktopGUID%"

"HKLM", "SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall\%ShortSvcName%"



[Remove.DelReg.Private]

"HKCU", "%AppAct%\%ServiceName%"

"HKCU", "%AppAct%\Mappings","%ServiceName%"

"HKCU", "%AppAct%\SingleUserInfo\%ServiceName%"

"HKCU", "SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall\%ShortSvcName%"



[CleanDir]

%49001%\%ShortSvcName%



; -------------------------------------------------------------------

; These are the directory specifications.

; -------------------------------------------------------------------



[CustInstDestSectionAllUsers]

49000,49001=AllUSer_LDIDSection, 7



[CustInstDestSectionSingleUsers]

49000,49001=SingleUser_LDIDSection, 7



[CustUninstDestSectionAllUsers]

49000,49001=XConnMgrLDIDSectionAllUsers, 5



[CustUnInstDestSectionPrivate]

49000,49001=XConnMgrLDIDSectionPrivate, 5



[SingleUser_LDIDSection]

"HKCU", "%AppAct%", "ProfileInstallPath", "%UnexpectedError%", ""



[AllUSer_LDIDSection]

"HKLM", "SOFTWARE\Microsoft\Windows\CurrentVersion\App Paths\CMMGR32.EXE", "ProfileInstallPath", "%UnexpectedError%", ""



[XConnMgrLDIDSectionAllUsers]

"HKLM", "SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall\%ShortSvcName%", "UninstallDir", "", ""



[XConnMgrLDIDSectionPrivate]

"HKCU", "SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall\%ShortSvcName%", "UninstallDir", "", ""



[DestinationDirs]

Xnstall.CopyFiles=49001, %ShortSvcName%

Xnstall.CopyFiles.SingleUser=49001, %ShortSvcName%

Xnstall.CopyFiles.ICM=49001

Remove.DelFiles=49001, %ShortSvcName%

Remove.DelFiles.ICM=49001



[SourceDisksNames]

55=, , 0



; -------------------------------------------------------------------

; These are the Prompt Sections

; -------------------------------------------------------------------



[RemoveBeginPromptSection]

Prompt=%BeginPrompt%

ButtonType=YESNO

Title=%UninstallAppTitle%



[RemoveEndPromptSection]

Prompt=%EndPrompt%





[Strings]

; -------------------------------------------------------------------

; These are the non localizable strings...

; -------------------------------------------------------------------

KEY_RENAME = "Software\Microsoft\Windows\CurrentVersion\RenameFiles"

AppAct = "SOFTWARE\Microsoft\Connection Manager"



; -------------------------------------------------------------------

; These are the localizable strings...

; -------------------------------------------------------------------

UnexpectedError = "An unexpected error occurred.  Please reboot and try the installation again."



; When you localize these commands (they are the commands for the Desktop Icon on legacy

; platforms) you must make sure to re-alphabetize the Registry add calls above.  Win95

; shows the menus in the order they were added and doesn't alphabetize them for you.

Settings = "P&roperties"

Open = "C&onnect"

Delete = "&Delete"

CmLCID="1033"



; -------------------------------------------------------------------

; The following strings are set by the Connection Manager Administration Kit

; Do not change any of the following strings

; -------------------------------------------------------------------

ServiceName="Morrisville VPN"

ShortSvcName="MSC_VPN"

DesktopGUID="{9E2BF6C6-D2DC-4424-8FD9-08467D8392EF}"

UninstallAppTitle="Morrisville VPN"

DesktopIcon=""

PhonebookPath=""

BeginPrompt="Do you want to remove Morrisville VPN?"

EndPrompt="Successfully removed Morrisville VPN."

DisplayLCID=1033



[CMAK Status]

InfVersion=4

UpdatePhonebook=0

IncludeCMCode=1

LicenseFile=

PhoneName=



[Extra Files]



[Merge Profiles]



[Xnstall.AddReg.Icon]

HKCR,"CLSID\%DesktopGUID%\DefaultIcon",,,"%11%\CMMGR32.EXE,0"



[Xnstall.CopyFiles.SingleUser]

msc_vpn.bmp

MSC_VPN.cms,,,4

MSC_VPN.inf



[Xnstall.CopyFiles]

msc_vpn.bmp

MSC_VPN.cms,,,4

MSC_VPN.inf



[Xnstall.CopyFiles.ICM]

MSC_VPN.cmp



[Remove.DelFiles.ICM]

MSC_VPN.cmp



[SourceDisksFiles]

msc_vpn.bmp= 55

MSC_VPN.inf = 55

MSC_VPN.cmp = 55

MSC_VPN.cms = 55



[Remove.DelFiles]

MSC_VPN.cms

msc_vpn.bmp

```

Please let me know of any info I can post to help resolve this.  Thanks!

---

### Post by MrVincent on 2008-12-13
There is vpnc which usually does a good job. sudo apt-get vpnc...
Now you'll probably need to convert your VPN profile into a valid vpnc profile, so you might want to look at the Windows config files your University supplies...

I don't think you have the connection info in that file you showed us...

---

### Post by MaindotC on 2008-12-13
I don't know what the forum's policies are on hosting files so I'll just upload these.  Feel free to examine them and please tell me how you garner information from them.  Sorry didn't know how to .gz only .tar.

---

### Post by MaindotC on 2008-12-13
It looks like the MSC_VPN.inf file is some sort of script to handling installation and where to place files and so forth.

After looking at the MSC_VPN.cms file it seems it contains information relative to what server to connect to and the configuration.  CHeck it out:
```

[Profile Format]

Version=4



[ISP]

PBFile=

RegionFile=

PBURL=

Mask&SignOn=0x0001

Match&SignOn=0x0000

Mask&SignUp=0x0002

Match&SignUp=0x0002

Mask&Modem=0x0004

Match&Modem=0x0000

Mask&ISDN=0x0008

Match&ISDN=0x0000

Mask&Custom1=0x0010

Match&Custom1=0x0010

Mask&Custom2=0x0080

Match&Custom2=0x0080

Mask&MultiCast=0x0020

Match&MultiCast=0x0000

Mask&Surcharge=0x0040

Match&Surcharge=0x0040

Mask&MultiCastModem=0x0024

Match&MultiCastModem=0x0000

Mask&MultiCastISDN=0x0028

Match&MultiCastISDN=0x0000

Mask&NosurchargeSignon=0x0041

Match&NosurchargeSignon=0x0000

Mask&SurchargeSignon=0x0041

Match&SurchargeSignon=0x0040

FilterA&=NosurchargeSignon

FilterB&=SurchargeSignon



[Service Types]

Modem=Modem

ISDN=ISDN

Modem MultiCast=MultiCastModem

ISDN MultiCast=MultiCastISDN



[Connection Manager]

RedialCount=3

RedialDelay=5

Version=0

DownloadDelay=15

ServiceName=Morrisville VPN

ServiceMessage=Please Call the HelpDesk for Assistance

PBMessage=

DUN=Morrisville VPN

UserNamePrefix=

UserNameSuffix=

PasswordHandling=0

Logo=MSC_VPN\msc_vpn.bmp

Icon=

SmallIcon=

TrayIcon=

PBLogo=

Dialup=0

Direct=1

ConnectionType=0

Tunnel=1

TunnelReferences=0

TunnelAddress=vpn.morrisville.edu

TunnelFile=

TunnelDUN=Morrisville VPN Tunnel

UseSameUserName=0

HelpFile=

HideDomain=1

DisableICS=1

HideAdvancedTab=1

HideRememberPassword=1



[Animated Logo]



[Animation Actions]



[Pre-Init Actions]



[Pre-Connect Actions]



[Pre-Dial Actions]



[Pre-Tunnel Actions]



[Connect Actions]



[Auto Applications]



[Disconnect Actions]



[On-Cancel Actions]



[On-Error Actions]



[Menu Options]



[Server&Morrisville VPN Tunnel]

NetworkLogon=1

SW_Compress=1

Disable_LCP=0

Negotiate_TCP/IP=1

SecureLocalFiles=0

EnforceCustomSecurity=1

Custom_Security=1

Require_PAP=0

Require_SPAP=0

Require_CHAP=0

Require_MSCHAP=1

Require_MSCHAP2=1

Require_W95MSCHAP=0

EncryptionType=1

[TCP/IP&Morrisville VPN Tunnel]

IP_Header_Compress=1

Gateway_On_Remote=0

Specify_Server_Address=0

[Networking&Morrisville VPN Tunnel]

VpnStrategy=2

VpnEntry=1

[Server&Morrisville VPN]

NetworkLogon=1

SW_Compress=1

Disable_LCP=0

Negotiate_TCP/IP=1

SecureLocalFiles=0

EnforceCustomSecurity=0

Custom_Security=1

Require_PAP=0

Require_SPAP=0

Require_CHAP=1

Require_MSCHAP=1

Require_MSCHAP2=1

Require_W95MSCHAP=0

EncryptionType=3

PW_Encrypt=1

PW_EncryptMS=0

DataEncrypt=0

[TCP/IP&Morrisville VPN]

IP_Header_Compress=1

Gateway_On_Remote=0

Specify_Server_Address=0


```

So far I identify the server address as "TunnelAddress".  Some of the protocols like CHAP and PAP are set with a "1" so I'm assuming that means they are enabled.  I'll examine this some more.

---

### Post by MaindotC on 2008-12-22
Bump - now I'm officially living off campus so I need this VPN client working. Help me!

---

### Post by alemic48 on 2008-12-24
> **strAlan said:**
> Bump - now I'm officially living off campus so I need this VPN client working. Help me!

In Windows, this would be a three click solution.

I actually need this as well, so can we post what you have already tried and we'll go from there.

:guitar::popcorn:

---

### Post by MaindotC on 2008-12-24
In Windows, it's a three-click solution made up of a series of commands and directives that I have shown in the above files.  All this is a matter of translating them into whatever settings the linux client needs.  Don't diss the U.

---

### Post by ieee488 on 2008-12-24
You are not understanding.

Post **what you have done in Linux** to try to get it to work. If you haven't done anything, say so. People are more willing to help people who try to help themselves.

---

### Post by mpokrywka on 2008-12-27
Try connecting with Network Manager - create pptp vpn connection.
Use "vpn.morrisville.edu" as vpn server and use MSCHAPv2.
Also select "debug" checkbox in case there are any problems with connection.
You will find connection debug in /var/log/messages

---

### Post by MaindotC on 2008-12-29
$(*&!$#@ Vpn server doesn't seem to be responding...

---

### Post by MaindotC on 2008-12-29
Ok it's up!  Of course it didn't work.  Here's debug:
```

Dec 29 22:25:15 a34lkj2348dsf311-desktop pppd[22830]: Plugin nm-pppd-plugin.so loaded.
Dec 29 22:25:15 a34lkj2348dsf311-desktop pppd[22830]: nm-pppd-plugin: plugin initialized.
Dec 29 22:25:15 a34lkj2348dsf311-desktop pppd[22832]: pppd 2.4.4 started by root, uid 0
Dec 29 22:25:15 a34lkj2348dsf311-desktop pppd[22832]: Using interface ppp0
Dec 29 22:25:15 a34lkj2348dsf311-desktop pppd[22832]: Connect: ppp0 <--> /dev/pts/2
Dec 29 22:25:16 a34lkj2348dsf311-desktop pppd[22832]: Warning - secret file /etc/ppp/pap-secrets has world and/or group access
Dec 29 22:25:16 a34lkj2348dsf311-desktop pppd[22832]: nm-pppd-plugin: CHAP check hook.
Dec 29 22:25:26 a34lkj2348dsf311-desktop pppd[22832]: Terminating on signal 15
Dec 29 22:25:26 a34lkj2348dsf311-desktop pppd[22832]: Child process /usr/sbin/pptp 136.204.12.11 --nolaunchpppd (pid 22833) terminated with signal 15
Dec 29 22:25:26 a34lkj2348dsf311-desktop pppd[22832]: Modem hangup
Dec 29 22:25:26 a34lkj2348dsf311-desktop pppd[22832]: Connection terminated.
Dec 29 22:25:26 a34lkj2348dsf311-desktop pppd[22832]: Exit.

```

---

### Post by mpokrywka on 2008-12-30
Sorry, I mixed up log name, show us contents of **/var/log/daemon.log**
There should be more debug info (I hope you checked "debug" checkbox in connection settings, on third tab I think)

---

### Post by MaindotC on 2009-01-22
Sorry I didn't reply to this sooner.  About a week ago our network administrator sent out an email stating the VPN server would be down for maintenance to resolve some of the issues people have been having.  Tonight I decided "what the hell" and tried the VPN connection in nm-applet.  On the screen that prompts you to refuse protocols, I selected them all (Refuse EAP, CHAP, etc) and it worked!  I was prompted for my username and password and I logged into the network and was able to access my campus network shares and other services.

Unfortunately, it seemed to interfere with general internet connectivity as I lost contact to instant message servers and when I requested a webpage the FF status bar would say "Connecting to <website_name>" but it never actually connected.  I'll experiment with it more but for my purposes this thread is solved.  No thanks to any of you.

---

