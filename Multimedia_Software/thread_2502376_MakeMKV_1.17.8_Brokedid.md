---
title: "MakeMKV 1.17.8 Brokedid?"
date: 2024-11-12
forum: Multimedia Software
---

### Post by Shibblet on 2024-11-12
I have been using MakeMKV for the past&#8230; well&#8230; seems like forever. And the most recent update seems to be broken.

I have two problems. First, that each new version of MakeMKV requires a new registration code&#8230; So, once you update your version of MakeMKV you can go to the MakeMKV forum and get the new beta-key.

The second problem, is downgrading. If I install 1.17.8 Flatpak, then downgrade to 1.17.7, it still doesn&#8217;t work.

So, I installed from the tar.gz, version 1.17.7, and it requires a Beta-key that is no longer available.

Am I just stuck with a broken version of this software until the next one comes out? That could be up to 3 months.

I also have looked at the MakeMKV forums&#8230; seems as if this is happening to a lot of people. [https://forum.makemkv.com/forum/viewtopic.php?f=3&t=35703]("https://forum.makemkv.com/forum/viewtopic.php?f=3&t=35703")

So&#8230; does anyone know how to get this working?

---

### Post by 1fallen on 2024-11-12
Mine just works, I can't see enough in your thread to advise anything, what is not working?
```
[FONT=monospace][COLOR=#000000]flatpak run com.makemkv.MakeMKV  [/COLOR]
Failed to create wl_display (No such file or directory) 
qt.qpa.plugin: Could not load the Qt platform plugin "wayland" in "" even though it was found. 
Qt: Session management error: Could not open network socket


[/FONT]
```[FONT=monospace]
Yep I'm on wayland here.
[/FONT]```
[FONT=monospace][COLOR=#000000]flatpak info com.makemkv.MakeMKV [/COLOR]

MakeMKV - DVD and Blu-ray to MKV converter and network streamer 

[COLOR=#000000]**          ID:**[/COLOR][COLOR=#000000] com.makemkv.MakeMKV [/COLOR]
[COLOR=#000000]**         Ref:**[/COLOR][COLOR=#000000] app/com.makemkv.MakeMKV/x86_64/stable [/COLOR]
[COLOR=#000000]**        Arch:**[/COLOR][COLOR=#000000] x86_64 [/COLOR]
[COLOR=#000000]**      Branch:**[/COLOR][COLOR=#000000] stable [/COLOR]
[COLOR=#000000]**     Version:**[/COLOR][COLOR=#000000] 1.17.8 [/COLOR]
[COLOR=#000000]**     License:**[/COLOR][COLOR=#000000] LicenseRef-proprietary AND GPL-2.0 AND LGPL-2.1-only [/COLOR]
[COLOR=#000000]**      Origin:**[/COLOR][COLOR=#000000] flathub [/COLOR]
[COLOR=#000000]**  Collection:**[/COLOR][COLOR=#000000] org.flathub.Stable [/COLOR]
[COLOR=#000000]**Installation:**[/COLOR][COLOR=#000000] system [/COLOR]
[COLOR=#000000]**   Installed:**[/COLOR][COLOR=#000000] 259.2 MB [/COLOR]
[COLOR=#000000]**     Runtime:**[/COLOR][COLOR=#000000] org.kde.Platform/x86_64/5.15-23.08 [/COLOR]
[COLOR=#000000]**         Sdk:**[/COLOR][COLOR=#000000] org.kde.Sdk/x86_64/5.15-23.08 [/COLOR]

[COLOR=#000000]**      Commit:**[/COLOR][COLOR=#000000] b55330a3ec8fe3f67e8c2db2481ee65ad0680e93d754b086d6dc1145733229d5 [/COLOR]
[COLOR=#000000]**      Parent:**[/COLOR][COLOR=#000000] 2963bc2878de531c17d586e0268bfd890fca3e333c9935bd2e49beed03e63370 [/COLOR]
[COLOR=#000000]**     Subject:**[/COLOR][COLOR=#000000] Update ffmpeg to 7.1 (#98) (cc8de39a) [/COLOR]
[COLOR=#000000]**        Date:**[/COLOR][COLOR=#000000] 2024-11-05 21:04:35 +0000[/COLOR]

[/FONT]
```[FONT=monospace]
EDIT2:
[/FONT]```

Drive Information
OS device name: /dev/sr0
Current profile: DVD-ROM
Manufacturer: hp
Product: CDDVDW SN-208FB
Revision: HJ10
Serial number: S11P6YCFC016BE

Disc Information
Label: MATILDA_SPECIAL_EDITION
Timestamp: 2005-04-05 14:29:59
Protection: CSS/CPPM
Data capacity: 7.59 Gb
Disc type: DVD-ROM
Disc size: 120mm
Maximum read rate: 10.08 Mbps [1x]
Number of layers: 2 (PTP)
```
EDIT3:
```
[FONT=monospace][COLOR=#000000]flatpak --columns=name,size list [/COLOR]
[COLOR=#000000]**Name                                               Installed size**[/COLOR][COLOR=#000000] [/COLOR]
MakeMKV                                            259.2 MB 
pwvucontrol                                          4.4 MB 
Mesa                                               512.2 MB 
Mesa (Extra)                                       512.2 MB 
Mesa                                               437.9 MB 
Mesa (Extra)                                       437.9 MB 
nvidia-560-35-03                                     2.1 MB 
openh264                                           790.0 kB 
openh264                                           763.9 kB 
GNOME Application Platform version 46              940.4 MB 
Adwaita theme                                       16.3 MB 
KDE Application Platform                           912.5 MB 
KDE Application Platform                           992.1 MB 
Tor Browser Launcher                                34.9 MB
```
[/FONT]

---

### Post by Shibblet on 2024-11-12
> **1fallen said:**
> Mine just works, I can't see enough in your thread to advise anything, what is not working?

Like denoted in the link to the MakeMKV Forum... The app opens up, and then sits there unable to download the SDF (and/or recognize the drive).  I cannot put in the new beta-key, or even my previously purchased key.

---

### Post by 1fallen on 2024-11-12
> **Shibblet said:**
> Like denoted in the link to the MakeMKV Forum...
I read and still nothing solid to act on....
Well there is a little more clairity with your reply, and you stil haven't really given any steps you have taken to resolve this, outside of removals and different versions flatpak tarball.

Sometimes flatpaks can be a bit confusing when we uninstall flatpaks.
```
flatpak uninstall com.makemkv.MakeMKV


        ID                         Branch       Op
 1. [-] com.makemkv.MakeMKV        stable       r

Uninstall complete.

```

```
flatpak uninstall --unused


        ID                                          Branch              Op
 1. [-] org.kde.KStyle.Adwaita                      5.15-23.08          r
 2. [-] org.kde.Platform                            5.15-23.08          r
 3. [-] org.freedesktop.Platform.openh264           2.2.0               r
 4. [-] org.kde.Platform.Locale                     5.15-23.08          r

Uninstall complete.

```
now I'll re-install cleanly
```
flatpak install com.makemkv.MakeMKV
Looking for matches…
Required runtime for com.makemkv.MakeMKV/x86_64/stable (runtime/org.kde.Platform/x86_64/5.15-23.08) found in remote flathub
Do you want to install it? [Y/n]: 

com.makemkv.MakeMKV permissions:
    ipc                   network       x11      devices      file access [1]
    dbus access [2]

    [1] host, xdg-config/kdeglobals:ro
    [2] com.canonical.AppMenu.Registrar, org.kde.KGlobalSettings, org.kde.kconfig.notify


        ID                                      Branch           Op       Remote        Download
 1. [&#10003;] org.freedesktop.Platform.openh264       2.2.0            i        flathub       886.7 kB / 944.3 kB
 2. [&#10003;] org.kde.KStyle.Adwaita                  5.15-23.08       i        flathub         6.6 MB / 6.6 MB
 3. [&#10003;] org.kde.Platform.Locale                 5.15-23.08       i        flathub        18.0 kB / 394.3 MB
 4. [&#10003;] org.kde.Platform                        5.15-23.08       i        flathub       242.0 MB / 340.5 MB
 5. [&#10003;] com.makemkv.MakeMKV                     stable           i        flathub        90.9 MB / 94.0 MB

Installation complete.

```
I have found if snapd is installed then it gets really messy with any or most outside 3rd party apps like>>>flatpak and appimages.
```
apt policy snapd
snapd:
  Installed: (none)
  Candidate: (none)
  Version table:
     2.65.3+24.04 -1
        500 https://mirrors.tuxedocomputers.com/ubuntu/mirror/archive.ubuntu.com/ubuntu noble-updates/main amd64 Packages
     2.63+24.04ubuntu0.1 -1
        500 https://mirrors.tuxedocomputers.com/ubuntu/mirror/security.ubuntu.com/ubuntu noble-security/main amd64 Packages
     2.62+24.04build1 -1
        500 https://mirrors.tuxedocomputers.com/ubuntu/mirror/archive.ubuntu.com/ubuntu noble/main amd64 Packages

```
I do have Enabled Internet, left unchecked.(screenshot) 

I hope this helps.....otherwise just another rabbit hole to go down. ;)

---

### Post by Shibblet on 2024-11-12
[ATTACH=CONFIG]294509[/ATTACH]

---

### Post by 1fallen on 2024-11-13
Better Thanks:
please show this:
```
[FONT=monospace][COLOR=#000000]sudo lshw -C disk|grep -e DVD -e cdrom[/COLOR]

```


[/FONT]

---

### Post by Shibblet on 2024-11-13
I cannot believe I am about to say this... but...

**[SIZE=5]Snap FTW![/SIZE]**

I was able to install the Snap of MakeMKV, which is still at version 1.17.7&#8230; and it had the same issue of not being able to detect the drive.

I did the following, that I found at [https://forum.makemkv.com/forum/viewtopic.php?t=23759]("https://forum.makemkv.com/forum/viewtopic.php?t=23759")

> su root
Enter your Password
echo sg > /etc/modules-load.d/sg.conf
Exit
Reboot

After the reboot, it all started working. So, I keep using this version until 1.17.9 comes out. If that doesn&#8217;t work, then I will restore my system with Timeshift.

Thank you all for the help!

---

### Post by 1fallen on 2024-11-13
Nice! I'll now bet the flatpak works as well.
This is the  key>>> "echo sg > /etc/modules-load.d/sg.conf"

Happy Viewing....:)

---

