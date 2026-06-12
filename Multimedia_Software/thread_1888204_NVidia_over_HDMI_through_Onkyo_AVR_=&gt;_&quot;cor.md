---
title: "NVidia over HDMI through Onkyo AVR =&gt; &quot;corrupted&quot; video output"
date: 2011-11-28
forum: Multimedia Software
---

### Post by RR123RR on 2011-11-28
Hi,

I'm trying to put the final touch on an HTPC (Ubuntu 11.10) setup by  getting the sound digitally to my AVR (for quality and multi channel  purpuse). 

Sounds seems to work but video is broken. I see either garbage patterns  or a very small version of the desktop, garbled, repeated on the top of  the TV and static noise below... (I do see the BIOS and console!)

The weird part is that if I plug the HTPC to the TV directly, it works,  except of course that it works through the speakers of the TV but video  and sound is perfect.

The setup is as follow:

Zotac Nvidia GTX460 (HTPC) -> Onkyo TX-NR609 (AVR) -> Insignia NSPDP50HD-09 (TV)

I tried with different modes (direct, through), different cables, played with nvidia-settings a little, etc.

Is there anything special to know about outputting to an AVR with the NVidia driver? (280.13)
Anyone has been successful with such a setup or this specific Onkyo serie? (TX-NR?09)

Thanks!

---

### Post by papibe on 2011-11-28
Hi RR123RR.

Could it be that the AVR requires an [HDCP]("http://en.wikipedia.org/wiki/High-bandwidth_Digital_Content_Protection") connection?

Does your card support HDCP output?

Just a thought.
Regards.

---

### Post by RR123RR on 2011-11-28
> **papibe said:**
> Hi RR123RR.

Could it be that the AVR requires an [HDCP]("http://en.wikipedia.org/wiki/High-bandwidth_Digital_Content_Protection") connection?

Does your card support HDCP output?

Just a thought.
Regards.

Hi papibe!

I didn't think about that, thinking it'd be happy with a desktop signal, unencrypted...
Is there a way to enable/disable/make this work? I'll look around in the mean time...
It's strange as it's only a problem in X :-(

EDIT: I seem to get a green screen now. Looking around it looks like it could be a handshake issue. Unplugging the HDMI and pluging it back in makes this turn back to a super low res corrupted fractal of my desktop... argh!

---

### Post by papibe on 2011-11-28
May be the receiver has a feature to enable/disable it.

BTW, the HDCP thing is just an idea, but not necessarily the problem.

Regards.

---

### Post by RR123RR on 2011-11-29
I tried pretty much everything I could understand within 12 hours...

So unless there is a way to force the output to 1080p60 without EDID or anything else, I think I'll have to try something else.

Now, I think I'll try pluging the HDMI to the AVR and a DVI->HDMI cable directly to the TV and see if I can output to both (cloned display?).

---

### Post by RR123RR on 2011-12-05
Well, cloned display kind of worked, I still have to switch the TV input though...

also discussed here:
[http://ubuntuforums.org/showthread.php?p=11500215](http://ubuntuforums.org/showthread.php?p=11500215)

---

### Post by papibe on 2011-12-05
At this point could be a possibility to upgrade your Nvidia driver to the lastest stable from ppa:
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
```
Then recreate your conf file:
```
sudo nvidia-xconfig
```
Then reboot.
After that configure your monitor and TVs using:
```
gksudo nvidia-settings
```
When it is working as you want save the configuration file. Reboot.

Tell us how it goes.

Regards.

---

### Post by BicyclerBoy on 2011-12-05
Your AVR should have EDID/ELD management settings.

The AVR should be able to cache or modify display EDID.
It has to add AVR audio capabilities (ELD).

Note that the display & AVR must be ON before the X server is loaded/started. Caching the display EDID can allow the display to be off.

This EDID issue is a big step back from VGA/DVI EDID interface, it worked with the power off.

If you can get the display resolution correct once you can store the EDID in a file for forced re-use (using nvidia-settings).
You could do this with a direct connection to display BUT this will screw up the audio ELD.

HDCP is negotiated from source not the destination..No linux driver/player is going to ask for HDCP..

With all plugged & powered before X server...
dmesg | HDMI
dmesg | ELD

Should not run nvidia-settings with gksudo..

There has been issues with Onkyo ELD/EDID because they choose to use an odd format (not wrong just different).

---

### Post by RR123RR on 2011-12-05
I already had the latest PPA NVidia while testing...
The TV and AVR are on before for sure (with so many reboots hehe!)

So uhm, not too sure what to try anymore... 
- with UseEDID "False" I get a 640x480 max screen so I can't go higher in nvidia-settings.
- With cloned HDMI to the DVI, I seem to get a 1080i overscanned output to HDMI that looks washed out, when it shows up and not lines or small repeated static copy of the desktop at the top. 

I'm kind of giving up on being able to only use the HDMI without also the DVI for the video to the TV (bypassing the AVR for video, using HDMI for audio)


------------8<------------
... And above all that, I need to also figure out to set the default output over HDMI for audio to 24/192khz. setting S32_LE and 192000 in ~/.pulse/daemon.conf doesn't cut it
Though i can run this just fine and have the AVR say 192khz input:

```
speaker-test -Dhw2,7 -r 192000 -c2 -F S32_LE
```Otherwise it always show up as per the unity sound settings (5.1 44.1khz)

```
#dmesg |grep -i hdmi
[   18.328012] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
[   18.360009] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
[   18.392009] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
[   18.424010] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
[   18.440146] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input4
[   18.440246] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input5
[   18.440317] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input6
[   18.440385] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input7
[   21.342433] HDMI hot plug event: Pin=5 Presence_Detect=1 ELD_Valid=0
[   21.348011] HDMI status: Pin=5 Presence_Detect=1 ELD_Valid=0
[   21.356166] HDMI hot plug event: Pin=5 Presence_Detect=1 ELD_Valid=0
[   21.364004] HDMI status: Pin=5 Presence_Detect=1 ELD_Valid=0
[   21.417577] HDMI hot plug event: Pin=5 Presence_Detect=0 ELD_Valid=1
[   21.424011] HDMI status: Pin=5 Presence_Detect=1 ELD_Valid=1
[   22.196008] HDMI: detected monitor NS-PDP50HD-09 at connection type HDMI
[   22.196011] HDMI: available speakers: FL/FR
[   22.196014] HDMI: supports coding type LPCM: channels = 2, rates = 44100 48000 88200 176400 192000 384000, bits = 16 20
[   22.196017] HDMI: supports coding type AC-3: channels = 2, rates = 44100 48000 88200 176400 192000 384000, max bitrate = 192000
[   22.204014] HDMI hot plug event: Pin=5 Presence_Detect=0 ELD_Valid=1
[   22.212029] HDMI status: Pin=5 Presence_Detect=1 ELD_Valid=1
[   22.980020] HDMI: detected monitor TX-NR609
[   22.980022]      at connection type HDMI
[   22.980025] HDMI: available speakers: FL/FR LFE FC RL/RR RLC/RRC
[   22.980028] HDMI: supports coding type LPCM: channels = 2, rates = 44100 48000 88200 176400 192000 384000, bits = 16 20 24
[   22.980031] HDMI: supports coding type LPCM: channels = 8, rates = 44100 48000 88200 176400 192000 384000, bits = 16 20 24
[   22.980033] HDMI: supports coding type AC-3: channels = 8, rates = 44100 48000 88200, max bitrate = 640000
[   22.980036] HDMI: supports coding type DTS: channels = 8, rates = 48000 88200, max bitrate = 1536000
[   22.980038] HDMI: supports coding type DSD (One Bit Audio): channels = 6, rates = 48000
[   22.980039] HDMI: supports coding type E-AC-3/DD+ (Dolby Digital Plus): channels = 8, rates = 48000 88200
[   22.980042] HDMI: supports coding type DTS-HD: channels = 8, rates = 48000 88200 176400 192000 384000
[   22.980044] HDMI: supports coding type MLP (Dolby TrueHD): channels = 8, rates = 88200 192000

```Fun ahead? ;-)

---

### Post by BicyclerBoy on 2011-12-05
I would not try to force 192/24 except for particular applications..
Doing this will mess up AC3/DTS/DTS-MA/ HDA etc..

If you play a BD disc with MythTV it will output DTS-MA etc.

For audio you could use pulse or alsa re-sampling (very processor intensive).
The **default** pulse resampling is budget at best..

Do you want to re-sample audio ? Most is 44K1Hz/16 bit.

Option "UseEDID"  "false" requires you to have correct monitor section..
There are better sub-options possible.

log file ??
/var/log/Xorg.0.log

I would recommend using separate X screens not twinview..
twinview demands same video mode on both screens, this is bad for video playback.

hw:2,7 should be :
cat /proc/asound/card2/eld#1.0

Notice there is (2) ELD sections in your dmesg output..
Can you search your AVR OSD menus for ELD management options ?

---

### Post by RR123RR on 2011-12-05
[http://forum.xbmc.org/showthread.php?t=59877](http://forum.xbmc.org/showthread.php?t=59877)
Using the guide above but with :
```
resample-method = speex-float-10 
```I get 24bit / 192khz with 20% load on an E8500 and without noticeable issues like some other resample-methods.

I've used some videos with 48khz and I have some audio in 24/96khz (even a 192khz flac file, for testing.)

I'm not hoping to hear anything better at 192khz, I'm just trying to  have a resample-rate hight enough that it works for both 44.1 and 48khz  (and why not 96) without introducing too much noise, taking this into account:
[http://en.wikipedia.org/wiki/Nyquist%E2%80%93Shannon_sampling_theorem](http://en.wikipedia.org/wiki/Nyquist%E2%80%93Shannon_sampling_theorem)

I thought it'd be simpler / more flexible than removing pulseaudio and redoing everything  with alsa? Maybe not... 
I could always try the guide "1" instead of "2"  (above), but I'd loose mixing I guess...

My Xorg.0.log can be seen here: 
[http://ubuntuforums.org/showpost.php?p=11513303&postcount=6](http://ubuntuforums.org/showpost.php?p=11513303&postcount=6)

As for the ELD on the AVR, I don't think I have such an option ... :(

Thanks!

---

### Post by BicyclerBoy on 2011-12-05
Audio is not your problem anyway...

(default-sample-format=s24-32be)
src-sinc-best-quality ?

Have not bothered to try pulse resampling, still don't trust it.
Audio resampling is much more complicated than nyguist theorem.
Intra sample iterpolation etc..

I would point XBMC & MythTV directly at the HDMI audio device so it can bitstream HDA & AC3/DTS & resample other to 192/24.
MythTV does this very well (it also stops pulse server).

Back to video:
log file ??
/var/log/Xorg.0.log

I would recommend using separate X screens not twinview..
twinview demands same video mode on both screens, this is bad for video playback.

---

### Post by RR123RR on 2011-12-05
> **BicyclerBoy said:**
> Audio is not your problem anyway...

(default-sample-format=s24-32be)
src-sinc-best-quality ?

Have not bothered to try pulse resampling, still don't trust it.
Audio resampling is much more complicated than nyguist theorem.
Intra sample iterpolation etc..


Indeed, I'd rather have every ouput seen by the AVR as what it is.
I'd really need a pass-through without losing the ability to have multiple inputs mixed in when necessary. I don't know if that's really possible through pulseaudio?

> **BicyclerBoy said:**
> 
I would point XBMC & MythTV directly at the HDMI audio device so it can bitstream HDA & AC3/DTS & resample other to 192/24.
MythTV does this very well (it also stops pulse server).

I'm really just using normal apps like banshee, rhythmbox, mplayer, vlc, etc. and didn't feel like working on a front end that would add more complexity in the end. 

> **BicyclerBoy said:**
> 
Back to video:
log file ??
/var/log/Xorg.0.log

I would recommend using separate X screens not twinview..
twinview demands same video mode on both screens, this is bad for video playback.

How is it bad for playback? I still get VDPAU right now.
Don't we also lose some acceleration if I have 2 different screens or is this a thing of the past now? 
But it doesn't solve the problem that in the end I'd really just want 1 screen through HDMI without the video through the DVI and that I can't get the HDMI to work, in single screen, through the AVR.

(The Xorg.0.log is the 2nd code block from the link in the last post :-) )

Cheers!

---

### Post by BicyclerBoy on 2011-12-06
Sorry missed that link..

You don't need that EDID stuff, the monitor looks to report EDID okay.
The errors are from your monitor frequencies that do not span the supported video modes.

You seem to have another nvidia config file with twinview order CRT TV stuff in it..
Could be hidden folder in home .session .nvidia-rc etc..
Are you sure your xorg.conf file is exactly
"/etc/X11/xorg.conf"
Your posted file is dated 23rd Nov 2011..

Separate X screens (one X server) never had GLX or VDPAU acceleration problems. It is more flexible with refresh/resolution/colourspace etc..

---

### Post by RR123RR on 2011-12-06
I did a few modification to the file by hand after using the nvidia-settings (which asked me for the root/sudo password to overwrite xorg.conf), removing xorg.conf does go back to the default settings so I'm quite sure it's the one managing everything. :)

Good to know that separate X screens work well but in the end, I really just want one correct output over HDMI... I tried commenting out the line with the horizontal and vertical refresh rate and didn't get any further. 

I'm really confused as to why the HDMI output, _WHEN_ it works, is in 1080i60 (according to the AVR display) and not 1080p60... I'll try and post my non-forced-EDID xorg.conf /Xorg.0.log tomorrow to see if anything obvious shows up with the half-working setup.

thanks! :)

---

### Post by BicyclerBoy on 2011-12-06
That forced EDID file is not helping..except for if the display is turned off when booting PC/X server..
The monitor has internal contradictions in EDID data..

The horizontal freq reported excludes the interlaced video modes. Probably not really a problem. nVidia de-interlacing is better than the TV; especially in feature set C (GT220,240,430,520+D)

Horizontal freq min 1920x1080
24p    26.2KHz
i50    27.4KHz
i60    33.1KHz
50p    55.6KHz
60p (r) 66.6KHz  (reduced cvt)

Your monitor reports range of 31 - 92KHz.

You can use a monitor section with vertical & horizontal frequencies if you use this:
Option "UseEDIDFreqs" "FALSE"
Remove:
Option "UseEDID"  "False"

But maybe your AVR can not handle 1080p, remember it has to provide OSD graphics for setup. 
Do you have some scaler/video processor enabled.
Firmware:
[http://www.intl.onkyo.com/support/firmware/tx-nr609.html](http://www.intl.onkyo.com/support/firmware/tx-nr609.html)

[http://www.avsforum.com/avs-vb/showthread.php?t=1041161&page=3](http://www.avsforum.com/avs-vb/showthread.php?t=1041161&page=3)
post #64 has the EDID dump..

The native preferred modeline matches reduced vert blank timing
cvt -r 1920 1080     (60Hz p only)

---

### Post by RR123RR on 2011-12-07
Here is the xorg.conf:

```
Section "ServerLayout"     Identifier     "Layout0"     Screen      0  "Screen0" 0 0     InputDevice    "Keyboard0" "CoreKeyboard"     InputDevice    "Mouse0" "CorePointer"     Option         "Xinerama" "0" EndSection  Section "Files" EndSection  Section "InputDevice"      # generated from default     Identifier     "Mouse0"     Driver         "mouse"     Option         "Protocol" "auto"     Option         "Device" "/dev/psaux"     Option         "Emulate3Buttons" "no"     Option         "ZAxisMapping" "4 5" EndSection  Section "InputDevice"      # generated from default     Identifier     "Keyboard0"     Driver         "kbd" EndSection  Section "Monitor"     Identifier     "Monitor0"     VendorName     "Unknown"     ModelName      "ProView/EMC/PTS NS-PDP50HD-09"     HorizSync       31.0 - 92.0     VertRefresh     50.0 - 86.0     Option         "DPMS"     Option  "UseEDIDFreqs" "False"     #Option "UseEDIDDpi" "FALSE"     #Option "ModeValidation" "NoEdidModes"     #Option "UseEDID" "False"     #Option "ExactModeTimingsDVI" "True"     # 1920x1080 59.93 Hz (CVT 2.07M9-R) hsync: 66.59 kHz; pclk: 138.50 MHz #    Modeline "1920x1080R"  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync EndSection  Section "Device"     Identifier     "Device0"     Driver         "nvidia"     VendorName     "NVIDIA Corporation"     BoardName      "GeForce GTX 460" EndSection  Section "Screen"     Identifier     "Screen0"     Device         "Device0"     Monitor        "Monitor0"     DefaultDepth    24     Option         "TwinView" "1"     Option         "TwinViewXineramaInfoOrder" "DFP-0"     Option         "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-1: nvidia-auto-select +0+0; DFP-0: 1920x1080 +0+0, DFP-1: NULL; DFP-0: 1920x1080 +0+0, DFP-1: NULL; DFP-0: 640x480 @1920x1080 +0+0, DFP-1: NULL"     SubSection     "Display"         Depth       24     EndSubSection EndSection  
```
and Xorg.0.log:
```
[    19.365]  X.Org X Server 1.10.4 Release Date: 2011-08-19 [    19.365] X Protocol Version 11, Revision 0 [    19.365] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu [    19.365] Current Operating System: Linux HTPC 3.0.0-13-generic-pae #22-Ubuntu SMP Wed Nov 2 15:17:35 UTC 2011 i686 [    19.365] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-13-generic-pae root=UUID=776128ab-f32d-43c6-96c4-2c4e2b8244bc ro quiet splash acpi=off vt.handoff=7 [    19.365] Build Date: 19 October 2011  05:09:41AM [    19.365] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see http://www.ubuntu.com/support)  [    19.365] Current version of pixman: 0.22.2 [    19.365]     Before reporting problems, check http://wiki.x.org     to make sure that you have the latest version. [    19.365] Markers: (--) probed, (**) from config file, (==) default setting,     (++) from command line, (!!) notice, (II) informational,     (WW) warning, (EE) error, (NI) not implemented, (??) unknown. [    19.365] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Dec  7 16:51:40 2011 [    19.365] (==) Using config file: "/etc/X11/xorg.conf" [    19.365] (==) Using system config directory "/usr/share/X11/xorg.conf.d" [    19.365] (==) ServerLayout "Layout0" [    19.365] (**) |-->Screen "Screen0" (0) [    19.365] (**) |   |-->Monitor "Monitor0" [    19.365] (**) |   |-->Device "Device0" [    19.365] (**) |-->Input Device "Keyboard0" [    19.365] (**) |-->Input Device "Mouse0" [    19.365] (**) Option "Xinerama" "0" [    19.365] (==) Automatically adding devices [    19.365] (==) Automatically enabling devices [    19.366] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist. [    19.366]     Entry deleted from font path. [    19.366] (==) FontPath set to:     /usr/share/fonts/X11/misc,     /usr/share/fonts/X11/100dpi/:unscaled,     /usr/share/fonts/X11/75dpi/:unscaled,     /usr/share/fonts/X11/Type1,     /usr/share/fonts/X11/100dpi,     /usr/share/fonts/X11/75dpi,     /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,     built-ins [    19.366] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules" [    19.366] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled. [    19.366] (WW) Disabling Keyboard0 [    19.366] (WW) Disabling Mouse0 [    19.366] (II) Loader magic: 0x823ada0 [    19.366] (II) Module ABI versions: [    19.366]     X.Org ANSI C Emulation: 0.4 [    19.366]     X.Org Video Driver: 10.0 [    19.366]     X.Org XInput driver : 12.3 [    19.366]     X.Org Server Extension : 5.0 [    19.366] (--) PCI:*(0:1:0:0) 10de:0e22:19da:1166 rev 161, Mem @ 0xfc000000/33554432, 0xd8000000/134217728, 0xd4000000/67108864, I/O @ 0x0000bc00/128, BIOS @ 0x????????/524288 [    19.366] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory) [    19.366] (II) LoadModule: "extmod" [    19.383] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so [    19.383] (II) Module extmod: vendor="X.Org Foundation" [    19.383]     compiled for 1.10.4, module version = 1.0.0 [    19.383]     Module class: X.Org Server Extension [    19.383]     ABI class: X.Org Server Extension, version 5.0 [    19.383] (II) Loading extension MIT-SCREEN-SAVER [    19.383] (II) Loading extension XFree86-VidModeExtension [    19.383] (II) Loading extension XFree86-DGA [    19.383] (II) Loading extension DPMS [    19.383] (II) Loading extension XVideo [    19.383] (II) Loading extension XVideo-MotionCompensation [    19.383] (II) Loading extension X-Resource [    19.383] (II) LoadModule: "dbe" [    19.384] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so [    19.384] (II) Module dbe: vendor="X.Org Foundation" [    19.384]     compiled for 1.10.4, module version = 1.0.0 [    19.384]     Module class: X.Org Server Extension [    19.384]     ABI class: X.Org Server Extension, version 5.0 [    19.384] (II) Loading extension DOUBLE-BUFFER [    19.384] (II) LoadModule: "glx" [    19.384] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/libglx.so [    19.414] (II) Module glx: vendor="NVIDIA Corporation" [    19.414]     compiled for 4.0.2, module version = 1.0.0 [    19.414]     Module class: X.Org Server Extension [    19.414] (II) NVIDIA GLX Module  290.10  Wed Nov 16 19:49:02 PST 2011 [    19.414] (II) Loading extension GLX [    19.414] (II) LoadModule: "record" [    19.414] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so [    19.414] (II) Module record: vendor="X.Org Foundation" [    19.414]     compiled for 1.10.4, module version = 1.13.0 [    19.414]     Module class: X.Org Server Extension [    19.414]     ABI class: X.Org Server Extension, version 5.0 [    19.414] (II) Loading extension RECORD [    19.414] (II) LoadModule: "dri" [    19.415] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so [    19.415] (II) Module dri: vendor="X.Org Foundation" [    19.415]     compiled for 1.10.4, module version = 1.0.0 [    19.415]     ABI class: X.Org Server Extension, version 5.0 [    19.415] (II) Loading extension XFree86-DRI [    19.415] (II) LoadModule: "dri2" [    19.415] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so [    19.415] (II) Module dri2: vendor="X.Org Foundation" [    19.415]     compiled for 1.10.4, module version = 1.2.0 [    19.415]     ABI class: X.Org Server Extension, version 5.0 [    19.415] (II) Loading extension DRI2 [    19.415] (II) LoadModule: "nvidia" [    19.415] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so [    19.415] (II) Module nvidia: vendor="NVIDIA Corporation" [    19.415]     compiled for 4.0.2, module version = 1.0.0 [    19.415]     Module class: X.Org Video Driver [    19.415] (II) NVIDIA dlloader X Driver  290.10  Wed Nov 16 19:29:07 PST 2011 [    19.416] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs [    19.416] (++) using VT number 7  [    19.416] (II) Loading sub module "fb" [    19.416] (II) LoadModule: "fb" [    19.416] (II) Loading /usr/lib/xorg/modules/libfb.so [    19.416] (II) Module fb: vendor="X.Org Foundation" [    19.416]     compiled for 1.10.4, module version = 1.0.0 [    19.416]     ABI class: X.Org ANSI C Emulation, version 0.4 [    19.416] (II) Loading sub module "wfb" [    19.416] (II) LoadModule: "wfb" [    19.416] (II) Loading /usr/lib/xorg/modules/libwfb.so [    19.416] (II) Module wfb: vendor="X.Org Foundation" [    19.416]     compiled for 1.10.4, module version = 1.0.0 [    19.416]     ABI class: X.Org ANSI C Emulation, version 0.4 [    19.416] (II) Loading sub module "ramdac" [    19.416] (II) LoadModule: "ramdac" [    19.416] (II) Module "ramdac" already built-in [    19.416] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so [    19.416] (II) Loading /usr/lib/xorg/modules/libwfb.so [    19.416] (II) Loading /usr/lib/xorg/modules/libfb.so [    19.416] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32 [    19.416] (==) NVIDIA(0): RGB weight 888 [    19.416] (==) NVIDIA(0): Default visual is TrueColor [    19.416] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0) [    19.417] (**) NVIDIA(0): Option "UseEdidFreqs" "False" [    19.417] (**) NVIDIA(0): Option "TwinView" "1" [    19.417] (**) NVIDIA(0): Option "MetaModes" "DFP-0: nvidia-auto-select +0+0, DFP-1: nvidia-auto-select +0+0; DFP-0: 1920x1080 +0+0, DFP-1: NULL; DFP-0: 1920x1080 +0+0, DFP-1: NULL; DFP-0: 640x480 @1920x1080 +0+0, DFP-1: NULL" [    19.417] (**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "DFP-0" [    19.417] (**) NVIDIA(0): Enabling 2D acceleration [    20.913] (II) NVIDIA(GPU-0): Display (ONK TX-NR609 (DFP-1)) does not support NVIDIA 3D [    20.913] (II) NVIDIA(GPU-0):     Vision stereo. [    20.914] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 460 (GF104) at PCI:1:0:0 (GPU-0) [    20.914] (--) NVIDIA(0): Memory: 786432 kBytes [    20.914] (--) NVIDIA(0): VideoBIOS: 70.04.2e.00.b1 [    20.914] (II) NVIDIA(0): Detected PCI Express Link width: 16X [    20.914] (--) NVIDIA(0): Interlaced video modes are supported on this GPU [    20.914] (--) NVIDIA(0): Connected display device(s) on GeForce GTX 460 at PCI:1:0:0 [    20.914] (--) NVIDIA(0):     ONK TX-NR609 (DFP-1) [    20.914] (--) NVIDIA(0): ONK TX-NR609 (DFP-1): 165.0 MHz maximum pixel clock [    20.914] (--) NVIDIA(0): ONK TX-NR609 (DFP-1): Internal Single Link TMDS [    20.916] (**) NVIDIA(0): TwinView enabled [    20.916] (II) NVIDIA(0): Display Device found referenced in MetaMode: DFP-1 [    20.916] (WW) NVIDIA(0): TwinView requested, but only 1 display devices found. [    20.916] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been [    20.916] (**) NVIDIA(0):     disabled on all display devices. [    20.958] (II) NVIDIA(0): Assigned Display Device: DFP-1 [    20.958] (WW) NVIDIA(0): Invalid display device in Mode Description [    20.958] (WW) NVIDIA(0):     "DFP-0:nvidia-auto-select+0+0" [    20.958] (WW) NVIDIA(0): Not using mode description "DFP-0:nvidia-auto-select+0+0"; [    20.958] (WW) NVIDIA(0):     unable to map to display device [    20.958] (WW) NVIDIA(0): Invalid display device in Mode Description [    20.958] (WW) NVIDIA(0):     "DFP-0:1920x1080+0+0" [    20.958] (WW) NVIDIA(0): Not using mode description "DFP-0:1920x1080+0+0"; unable to [    20.958] (WW) NVIDIA(0):     map to display device [    20.958] (WW) NVIDIA(0): Invalid display device in Mode Description [    20.958] (WW) NVIDIA(0):     "DFP-0:1920x1080+0+0" [    20.958] (WW) NVIDIA(0): Not using mode description "DFP-0:1920x1080+0+0"; unable to [    20.958] (WW) NVIDIA(0):     map to display device [    20.958] (WW) NVIDIA(0): Invalid display device in Mode Description [    20.958] (WW) NVIDIA(0):     "DFP-0:640x480@1920x1080+0+0" [    20.958] (WW) NVIDIA(0): Not using mode description "DFP-0:640x480@1920x1080+0+0"; [    20.958] (WW) NVIDIA(0):     unable to map to display device [    20.958] (WW) NVIDIA(0): No valid modes for "DFP-0:1920x1080+0+0,DFP-1:NULL"; [    20.958] (WW) NVIDIA(0):     removing. [    20.958] (WW) NVIDIA(0): No valid modes for "DFP-0:1920x1080+0+0,DFP-1:NULL"; [    20.958] (WW) NVIDIA(0):     removing. [    20.958] (WW) NVIDIA(0): No valid modes for "DFP-0:640x480@1920x1080+0+0,DFP-1:NULL"; [    20.958] (WW) NVIDIA(0):     removing. [    20.958] (II) NVIDIA(0): Validated modes: [    20.958] (II) NVIDIA(0):     [    20.958] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select+0+0,DFP-1:nvidia-auto-select+0+0" [    20.958] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080 [    20.996] (--) NVIDIA(0): DPI set to (43, 44); computed from "UseEdidDpi" X config [    20.996] (--) NVIDIA(0):     option [    20.996] (--) Depth 24 pixmap format is 32 bpp [    20.996] (II) NVIDIA: Using 1024.00 MB of virtual memory for indirect memory [    20.996] (II) NVIDIA:     access. [    21.001] (II) NVIDIA(0): Setting mode [    21.001] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select+0+0,DFP-1:nvidia-auto-select+0+0" [    21.056] (II) Loading extension NV-GLX [    21.110] (==) NVIDIA(0): Disabling shared memory pixmaps [    21.110] (==) NVIDIA(0): Backing store disabled [    21.110] (==) NVIDIA(0): Silken mouse enabled [    21.111] (**) NVIDIA(0): DPMS enabled [    21.111] (II) Loading extension NV-CONTROL [    21.111] (WW) NVIDIA(0): Option "TwinViewXineramaInfoOrder" requested "DFP-0", but no [    21.111] (WW) NVIDIA(0):     such display device could be found, or all display devices [    21.111] (WW) NVIDIA(0):     by that name are currently unavailable. [    21.111] (WW) NVIDIA(0): Option "TwinViewXineramaInfoOrder" requested "CRT", but no [    21.111] (WW) NVIDIA(0):     such display device could be found, or all display devices [    21.111] (WW) NVIDIA(0):     by that name are currently unavailable. [    21.111] (WW) NVIDIA(0): Option "TwinViewXineramaInfoOrder" requested "TV", but no such [    21.111] (WW) NVIDIA(0):     display device could be found, or all display devices by [    21.111] (WW) NVIDIA(0):     that name are currently unavailable. [    21.111] (II) Loading extension XINERAMA [    21.111] (II) Loading sub module "dri2" [    21.111] (II) LoadModule: "dri2" [    21.112] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so [    21.112] (II) Module dri2: vendor="X.Org Foundation" [    21.112]     compiled for 1.10.4, module version = 1.2.0 [    21.112]     ABI class: X.Org Server Extension, version 5.0 [    21.112] (II) NVIDIA(0): [DRI2] Setup complete [    21.112] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia [    21.112] (==) RandR enabled [    21.112] (II) Initializing built-in extension Generic Event Extension [    21.112] (II) Initializing built-in extension SHAPE [    21.112] (II) Initializing built-in extension MIT-SHM [    21.112] (II) Initializing built-in extension XInputExtension [    21.112] (II) Initializing built-in extension XTEST [    21.112] (II) Initializing built-in extension BIG-REQUESTS [    21.112] (II) Initializing built-in extension SYNC [    21.112] (II) Initializing built-in extension XKEYBOARD [    21.112] (II) Initializing built-in extension XC-MISC [    21.112] (II) Initializing built-in extension SECURITY [    21.112] (II) Initializing built-in extension XINERAMA [    21.112] (II) Initializing built-in extension XFIXES [    21.112] (II) Initializing built-in extension RENDER [    21.112] (II) Initializing built-in extension RANDR [    21.112] (II) Initializing built-in extension COMPOSITE [    21.112] (II) Initializing built-in extension DAMAGE [    21.112] (II) Initializing built-in extension GESTURE [    21.114] (II) Initializing extension GLX [    21.138] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm [    21.145] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event4) [    21.145] (II) No input driver/identifier specified (ignoring) [    21.145] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event5) [    21.145] (II) No input driver/identifier specified (ignoring) [    21.145] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event6) [    21.145] (II) No input driver/identifier specified (ignoring) [    21.145] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event7) [    21.145] (II) No input driver/identifier specified (ignoring) [    21.147] (II) config/udev: Adding input device HOLTEK Wireless 2.4GHz Trackball Keyboard (/dev/input/event1) [    21.147] (**) HOLTEK Wireless 2.4GHz Trackball Keyboard: Applying InputClass "evdev keyboard catchall" [    21.147] (II) LoadModule: "evdev" [    21.147] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so [    21.147] (II) Module evdev: vendor="X.Org Foundation" [    21.148]     compiled for 1.10.2, module version = 2.6.0 [    21.148]     Module class: X.Org XInput Driver [    21.148]     ABI class: X.Org XInput driver, version 12.3 [    21.148] (II) Using input driver 'evdev' for 'HOLTEK Wireless 2.4GHz Trackball Keyboard' [    21.148] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so [    21.148] (**) HOLTEK Wireless 2.4GHz Trackball Keyboard: always reports core events [    21.148] (**) HOLTEK Wireless 2.4GHz Trackball Keyboard: Device: "/dev/input/event1" [    21.148] (--) HOLTEK Wireless 2.4GHz Trackball Keyboard: Found keys [    21.148] (II) HOLTEK Wireless 2.4GHz Trackball Keyboard: Configuring as keyboard [    21.148] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/input/input1/event1" [    21.148] (II) XINPUT: Adding extended input device "HOLTEK Wireless 2.4GHz Trackball Keyboard" (type: KEYBOARD) [    21.148] (**) Option "xkb_rules" "evdev" [    21.148] (**) Option "xkb_model" "pc105" [    21.148] (**) Option "xkb_layout" "ca" [    21.149] (II) XKB: reuse xkmfile /var/lib/xkb/server-3BCFF748FFB6BCDACC88715CBF6A9DF905CD3181.xkm [    21.150] (II) config/udev: Adding input device HOLTEK Wireless 2.4GHz Trackball Keyboard (/dev/input/event2) [    21.150] (**) HOLTEK Wireless 2.4GHz Trackball Keyboard: Applying InputClass "evdev pointer catchall" [    21.150] (**) HOLTEK Wireless 2.4GHz Trackball Keyboard: Applying InputClass "evdev keyboard catchall" [    21.150] (II) Using input driver 'evdev' for 'HOLTEK Wireless 2.4GHz Trackball Keyboard' [    21.150] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so [    21.150] (**) HOLTEK Wireless 2.4GHz Trackball Keyboard: always reports core events [    21.150] (**) HOLTEK Wireless 2.4GHz Trackball Keyboard: Device: "/dev/input/event2" [    21.150] (--) HOLTEK Wireless 2.4GHz Trackball Keyboard: Found 3 mouse buttons [    21.150] (--) HOLTEK Wireless 2.4GHz Trackball Keyboard: Found scroll wheel(s) [    21.150] (--) HOLTEK Wireless 2.4GHz Trackball Keyboard: Found relative axes [    21.150] (--) HOLTEK Wireless 2.4GHz Trackball Keyboard: Found x and y relative axes [    21.150] (--) HOLTEK Wireless 2.4GHz Trackball Keyboard: Found absolute axes [    21.150] (II) evdev-grail: failed to open grail, no gesture support [    21.150] (--) HOLTEK Wireless 2.4GHz Trackball Keyboard: Found keys [    21.150] (II) HOLTEK Wireless 2.4GHz Trackball Keyboard: Configuring as mouse [    21.150] (II) HOLTEK Wireless 2.4GHz Trackball Keyboard: Configuring as keyboard [    21.150] (II) HOLTEK Wireless 2.4GHz Trackball Keyboard: Adding scrollwheel support [    21.150] (**) HOLTEK Wireless 2.4GHz Trackball Keyboard: YAxisMapping: buttons 4 and 5 [    21.150] (**) HOLTEK Wireless 2.4GHz Trackball Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200 [    21.150] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.1/input/input2/event2" [    21.150] (II) XINPUT: Adding extended input device "HOLTEK Wireless 2.4GHz Trackball Keyboard" (type: KEYBOARD) [    21.150] (**) Option "xkb_rules" "evdev" [    21.150] (**) Option "xkb_model" "pc105" [    21.150] (**) Option "xkb_layout" "ca" [    21.150] (II) HOLTEK Wireless 2.4GHz Trackball Keyboard: initialized for relative axes. [    21.150] (WW) HOLTEK Wireless 2.4GHz Trackball Keyboard: ignoring absolute axes. [    21.150] (**) HOLTEK Wireless 2.4GHz Trackball Keyboard: (accel) keeping acceleration scheme 1 [    21.150] (**) HOLTEK Wireless 2.4GHz Trackball Keyboard: (accel) acceleration profile 0 [    21.150] (**) HOLTEK Wireless 2.4GHz Trackball Keyboard: (accel) acceleration factor: 2.000 [    21.150] (**) HOLTEK Wireless 2.4GHz Trackball Keyboard: (accel) acceleration threshold: 4 [    21.151] (II) config/udev: Adding input device HOLTEK Wireless 2.4GHz Trackball Keyboard (/dev/input/mouse0) [    21.151] (II) No input driver/identifier specified (ignoring) [    21.153] (II) config/udev: Adding input device UVC Camera (046d:0821) (/dev/input/event3) [    21.153] (**) UVC Camera (046d:0821): Applying InputClass "evdev keyboard catchall" [    21.153] (II) Using input driver 'evdev' for 'UVC Camera (046d:0821)' [    21.153] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so [    21.153] (**) UVC Camera (046d:0821): always reports core events [    21.153] (**) UVC Camera (046d:0821): Device: "/dev/input/event3" [    21.153] (--) UVC Camera (046d:0821): Found keys [    21.153] (II) UVC Camera (046d:0821): Configuring as keyboard [    21.153] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4:1.2/input/input3/event3" [    21.153] (II) XINPUT: Adding extended input device "UVC Camera (046d:0821)" (type: KEYBOARD) [    21.153] (**) Option "xkb_rules" "evdev" [    21.153] (**) Option "xkb_model" "pc105" [    21.153] (**) Option "xkb_layout" "ca" [    21.158] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event0) [    21.158] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall" [    21.158] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard' [    21.158] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so [    21.159] (**) AT Translated Set 2 keyboard: always reports core events [    21.159] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event0" [    21.159] (--) AT Translated Set 2 keyboard: Found keys [    21.159] (II) AT Translated Set 2 keyboard: Configuring as keyboard [    21.159] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input0/event0" [    21.159] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD) [    21.159] (**) Option "xkb_rules" "evdev" [    21.159] (**) Option "xkb_model" "pc105" [    21.159] (**) Option "xkb_layout" "ca" [    25.719] (II) XKB: reuse xkmfile /var/lib/xkb/server-81EC4871279DB1D73113D19E789F270C19322F52.xkm 
```]I tried the useEDIDFreqs False with/without the cvt modeline... 
I'm pretty sure the AVR does support 1080p, it even upscales to a lesser 4k mode and supports 3D etc. It works with the X-Box (only other device here that has 1080p output).
So, uhm, I'm pretty confused... :-)

Cheers!

EDIT: Why can't I get a proper CODE quote...!

---

### Post by BicyclerBoy on 2011-12-08
There is stuff in your xorg.conf referring to DFP-0 & twinview metamodes.

I still think there is another config file interfering.

I would backup/delete your xorg.conf. Then run
sudo nvidia-xconfig

Then reboot run:
nvidia-settings

see how it works..
(nvidia-settings has it own config file)

---

