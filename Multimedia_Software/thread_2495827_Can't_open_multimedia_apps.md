---
title: "Can't open multimedia apps"
date: 2024-03-03
forum: Multimedia Software
---

### Post by Automat2 on 2024-03-03
Hello,

I have upgraded to Mantic and have noticed that for a while, am unable to open multimedia apps - VLC, videos, rhythmbox, Deepin movie, QM2 play, Audacity... the app doesn't open.

Or, if I try to open the file via Files, and try to select the app to open the audio or video from, I get the same result, the furthest I get is the app opening, but then immediately closing, without playing the file.

I tried removing > ffmepg and > ubuntu-restricted-extras and then reinstalling them both, but I get no joy. I have both now as the most recent version.

Incidentally, I can't open ```
Telegram-desktop
``` either.

I remember having issues with video files in the past, but never with audio files. 

I would certainly post outputs but don't know where to begin with. Any ideas anyone?

---

### Post by Holger_Gehrke on 2024-03-03
First step should be opening the program from the command line. If you do that, the program has a place to send any warnings and errors (the terminal window). If you start programs from some kind of graphical starter these messages either get discarded or end up in a log file (probably ~/.xsession-errors if using X11 or something else for Wayland ...).

Holger

---

### Post by Autodave on 2024-03-03
I assume that you have tried rebooting the machine?  Occasionally, I'll see something on the 'net and afterwards some programs are inop.  Won't happen for weeks or months, but then a couple times in just a few days.  Rebooting makes everything work again.

---

### Post by Automat2 on 2024-03-03
> **Autodave said:**
> Rebooting makes everything work again.

Really? :roll:

---

### Post by Automat2 on 2024-03-03
I think I wanted to switch to flatpack instead of snap for some other app. 
When I tried vlc help  from terminal, I get:

> j-jdesktop:~$ vlc ~/Downloads/IMG_0037.mp4
Command 'vlc' not found, but can be installed with:
sudo snap install vlc      # version 3.0.19, or
sudo apt  install vlc-bin  # version 3.0.18-4
See 'snap info vlc' for additional versions.

And I'm playing an audio podcast at this very moment on VLC. But it still doesn't play videos.

---

### Post by #&amp;thj^% on 2024-03-03
If it is a flatpak, run this then:
```
flatpak run org.videolan.VLC 
```
That might help give us some clues.

---

### Post by Autodave on 2024-03-03
> **Automat2 said:**
> Really? :roll:

Really?  I don't assume that anyone knows anything.  Also, I have been doing this (fixing and building computers) for over 30 years.  You would be surprised at some dumb things that I have "fixed" for others by either having them reboot the machine or remove the laptop battery for a few minutes.  Sorry that my reply seemed stupid to you.

---

### Post by Automat2 on 2024-03-04
I ran the command and got this:
```
flatpak run org.videolan.VLC
=== Begin org.videolan.VLC.Plugin.pause_click Usage Instructions ===
You have installed org.videolan.VLC.Plugin.pause_click.
This plugin must be enabled in order for it to work.

(Recommended) You can enable it by using the following steps after the VLC launches:
  1. Tick "Pause/Play video on mouse click" checkbox in Tools -> Preferences -> Show settings -> All -> Interface -> Control Interfaces. Screenshot: [https://i.imgur.com/m9yF5Px.png](https://i.imgur.com/m9yF5Px.png)
  2. Tick "Pause/Play video on mouse click" checkbox in Tools -> Preferences -> Show settings -> All -> Video -> Filters. Screenshot: [https://i.imgur.com/OZLqmI6.png](https://i.imgur.com/OZLqmI6.png)
  3. Restart VLC
Note that both checkboxes need to be ticked for the plugin to function!

(Alternative) You can pass:
  --control=pause_click --video-filter=pause_click
arguments when running VLC to enable the plugin.
This method enables the plugin only for this specific VLC run, i.e. it's not persistent.

Plugin settings are available under Tools -> Preferences -> Show settings -> All -> Video -> Filters -> Pause click. Screenshot: [https://i.imgur.com/Kdrekks.png](https://i.imgur.com/Kdrekks.png) . The settings changes apply right away, there is no need to restart VLC.
=== End org.videolan.VLC.Plugin.pause_click Usage Instructions ===
VLC media player 3.0.20 Vetinari (revision 3.0.20-0-g6f0d0ab126b)
[000055ea339c67e0] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Gtk-Message: 18:33:09.558: Failed to load module "canberra-gtk-module"
Gtk-Message: 18:33:09.559: Failed to load module "canberra-gtk-module"
qt.qpa.qgnomeplatform: Could not find color scheme  ""
Qt: Session management error: Could not open network socket
[000055ea33a5a900] main playlist: playlist is empty



```

I installed canberra-gtk via Synaptic (I still had canberra3 installed) and then ran the command to open VLC. I still get the message that canberra has not loaded up.

---

### Post by #&amp;thj^% on 2024-03-04
That message is totally harmless " canberra-gtk".
We are running it through the terminal so "Warnings or Errors" is not uncommon.
Now will you do the same again, but open a Video file or URL and post that back here please.
ie:
```
 flatpak run org.videolan.VLC  
VLC media player 3.0.20 Vetinari (revision 3.0.20-0-g6f0d0ab126b)
[0000599c74957cd0] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Gtk-Message: 12:29:20.185: Failed to load module "canberra-gtk-module"
Qt: Session management error: Could not open network socket
[0000599c74a0c960] main playlist: playlist is empty
libva info: VA-API version 1.19.0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/radeonsi_drv_video.so
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/intel-vaapi-driver/radeonsi_drv_video.so
libva info: Trying to open /usr/lib/x86_64-linux-gnu/GL/lib/dri/radeonsi_drv_video.so
libva info: Found init function __vaDriverInit_1_19
libva info: va_openDriver() returns 0
[00007f8370c21260] avcodec decoder: Using Mesa Gallium driver 24.0.1 for AMD Radeon Graphics (radeonsi, renoir, LLVM 17.0.6, DRM 3.57, 6.8.0-11-generic) for hardware decoding

```

---

### Post by Automat2 on 2024-03-04
```
flatpak run org.videolan.VLC vid\ 5.mp4
=== Begin org.videolan.VLC.Plugin.pause_click Usage Instructions ===
You have installed org.videolan.VLC.Plugin.pause_click.
This plugin must be enabled in order for it to work.

(Recommended) You can enable it by using the following steps after the VLC launches:
  1. Tick "Pause/Play video on mouse click" checkbox in Tools -> Preferences -> Show settings -> All -> Interface -> Control Interfaces. Screenshot: [https://i.imgur.com/m9yF5Px.png](https://i.imgur.com/m9yF5Px.png)
  2. Tick "Pause/Play video on mouse click" checkbox in Tools -> Preferences -> Show settings -> All -> Video -> Filters. Screenshot: [https://i.imgur.com/OZLqmI6.png](https://i.imgur.com/OZLqmI6.png)
  3. Restart VLC
Note that both checkboxes need to be ticked for the plugin to function!

(Alternative) You can pass:
  --control=pause_click --video-filter=pause_click
arguments when running VLC to enable the plugin.
This method enables the plugin only for this specific VLC run, i.e. it's not persistent.

Plugin settings are available under Tools -> Preferences -> Show settings -> All -> Video -> Filters -> Pause click. Screenshot: [https://i.imgur.com/Kdrekks.png](https://i.imgur.com/Kdrekks.png) . The settings changes apply right away, there is no need to restart VLC.
=== End org.videolan.VLC.Plugin.pause_click Usage Instructions ===
VLC media player 3.0.20 Vetinari (revision 3.0.20-0-g6f0d0ab126b)
[000055c9c857b7e0] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Gtk-Message: 20:02:17.166: Failed to load module "canberra-gtk-module"
Gtk-Message: 20:02:17.167: Failed to load module "canberra-gtk-module"
qt.qpa.qgnomeplatform: Could not find color scheme  ""
Qt: Session management error: Could not open network socket
libva info: VA-API version 1.19.0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/r600_drv_video.so
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/intel-vaapi-driver/r600_drv_video.so
libva info: Trying to open /usr/lib/x86_64-linux-gnu/GL/lib/dri/r600_drv_video.so
libva info: Found init function __vaDriverInit_1_19
libva info: va_openDriver() returns 0
[00007f448009bb50] vaapi generic error: vaCreateContext: resolution not supported
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory


```

If I try to open a video file from GUI, I can hear some audio for about 1 sec, and then VLC shuts. But this output is from terminal.

---

### Post by #&amp;thj^% on 2024-03-04
Something is very different with that, anyway will you show me this:
```
flatpak info org.videolan.VLC
```
Are you on a Wayland Session?

---

### Post by Automat2 on 2024-03-04
Yes

---

### Post by #&amp;thj^% on 2024-03-04
I still need to see this:
```
flatpak info org.videolan.VLC
```

---

### Post by Automat2 on 2024-03-04
> **1fallen said:**
> I still need to see this:
```
flatpak info org.videolan.VLC
```
As below:
> flatpak info org.videolan.VLC

VLC - VLC media player, the open-source multimedia player

          ID: org.videolan.VLC
         Ref: app/org.videolan.VLC/x86_64/stable
        Arch: x86_64
      Branch: stable
     Version: 3.0.20
     License: GPL-2.0+
      Origin: flathub
  Collection: org.flathub.Stable
Installation: system
   Installed: 95,7 MB
     Runtime: org.kde.Platform/x86_64/5.15-23.08
         Sdk: org.kde.Sdk/x86_64/5.15-23.08

      Commit: 1bae7b2235134f6f67462b1ca273b536133b60241463f185cc6d31cdb366725d
      Parent: 1c44f0a8769622979606ffdd549a627f35dfe7cef3789d4f0719dbf4d5041e3c
     Subject: Update org.videolan.VLC.appdata.xml (#199) (0092ac1b)
        Date: 2024-01-18 17:09:10 +0000


---

### Post by #&amp;thj^% on 2024-03-04
Thanks, have you tried the same as what we've done here on a X11 session, and is nVidia involved?
```
inxi -Gxxz
```

---

### Post by Automat2 on 2024-03-04
> **1fallen said:**
> Thanks, have you tried the same as what we've done here on a X11 session, and is nVidia involved?

Rebooted and using Xorg
> flatpak info org.videolan.VLC

VLC - VLC media player, the open-source multimedia player

          ID: org.videolan.VLC
         Ref: app/org.videolan.VLC/x86_64/stable
        Arch: x86_64
      Branch: stable
     Version: 3.0.20
     License: GPL-2.0+
      Origin: flathub
  Collection: org.flathub.Stable
Installation: system
   Installed: 95,7 MB
     Runtime: org.kde.Platform/x86_64/5.15-23.08
         Sdk: org.kde.Sdk/x86_64/5.15-23.08

      Commit: 1bae7b2235134f6f67462b1ca273b536133b60241463f185cc6d31cdb366725d
      Parent: 1c44f0a8769622979606ffdd549a627f35dfe7cef3789d4f0719dbf4d5041e3c
     Subject: Update org.videolan.VLC.appdata.xml (#199) (0092ac1b)
        Date: 2024-01-18 17:09:10 +0000


```
inxi -Gxxz
```
Also on Xorg
> Graphics:
  Device-1: AMD Kaveri [Radeon R7 Graphics] vendor: ASRock driver: radeon
    v: kernel arch: GCN-2 ports: active: VGA-1 empty: DVI-D-1,HDMI-A-1
    bus-ID: 00:01.0 chip-ID: 1002:130f
  Device-2: Creative Live! Cam Connect HD VF0750
    driver: snd-usb-audio,uvcvideo type: USB rev: 2.0 speed: 480 Mb/s lanes: 1
    bus-ID: 2-4.4:4 chip-ID: 041e:4093
  Display: x11 server: X.Org v: 1.21.1.7 with: Xwayland v: 23.2.0
    compositor: gnome-shell v: 45.2 driver: X: loaded: radeon
    unloaded: fbdev,modesetting,vesa dri: radeonsi gpu: radeon display-ID: :0
    screens: 1
  Screen-1: 0 s-res: 1680x1050 s-dpi: 96
  Monitor-1: VGA-1 mapped: VGA-0 model: Toshiba Matsushita LCD-MONITOR
    res: 1680x1050 dpi: 99 diag: 510mm (20.1")
  API: OpenGL v: 4.5 Mesa 23.2.1-1ubuntu3.1 renderer: KAVERI ( LLVM 15.0.7
    DRM 2.50 6.5.0-21-generic) direct-render: Yes


No NVidia in this box.

---

### Post by #&amp;thj^% on 2024-03-05
I just am not familiar with your GPU, but you could try this in "/etc/default/grub":
```
amdgpu.dcdebugmask=0x10
```
Update grub and reboot. Any better?

---

### Post by Automat2 on 2024-03-06
> **1fallen said:**
> I just am not familiar with your GPU, but you could try this in "/etc/default/grub":
```
amdgpu.dcdebugmask=0x10
```
Update grub and reboot. Any better?
Yes. Videos play on VLC and QMPlay2 now, but not on Videos or DeepinMovie.
I had downloaded QMPLay2 and Deepin
And audios don't play on Rhythmbox either.
If you can think of something else, good but if not, it's OK. I can live with that.

---

