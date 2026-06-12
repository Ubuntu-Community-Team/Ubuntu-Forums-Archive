---
title: "freetuxtv  red code in terminal"
date: 2016-10-27
forum: Multimedia Software
---

### Post by valereguerin on 2016-10-27
14.04.05 fresh install

full update & full upgrade

install Vlc with synaptic + .dev /dbg
freetuxtv

i can watch but :

```
h264 @ 0x7f3b7814ba60] [COLOR=#ff0000]mmco: unref short failure[/COLOR]
[0x7f3b78203f28] packetizer_mpeg4audio packetizer: AAC channels: 2 samplerate: 24000
[COLOR=#ff0000][h264 @ 0x7f3b780f1c20] illegal short term buffer state detected[/COLOR]
[FreetuxTV]    MESSAGE    : Launching channel 'NHK (auto)' at '1:530' -> rtsp://mafreebox.freebox.fr/fbxtv_pub/stream?namespace=1&service=812
[LibVLC-Gtk]   INFO       : Playing rtsp://mafreebox.freebox.fr/fbxtv_pub/stream?namespace=1&service=812
[LibVLC-Gtk]   INFO       : Using vlc options [:deinterlace=0 :access=timeshift :input-timeshift-granularity=50]
[0x7f3b84037258] [COLOR=#ff0000]ts[/COLOR] [COLOR=#ff0000]demux error: MPEG-4 descriptor not found[/COLOR]
Fontconfig warning: FcPattern object size does not accept value "0"
Fontconfig warning: FcPattern object size does not accept value "0"
Fontconfig warning: FcPattern object size does not accept value "0"
Fontconfig warning: FcPattern object size does not accept value "0"
[0x7f3b6c001248] [COLOR=#ff0000]main vout display error: Failed to resize display[/COLOR]
[0x7f3b84019288] packetizer_mpeg4audio packetizer: AAC channels: 1 samplerate: 24000
[FreetuxTV]    MESSAGE    : Launching channel 'CNBC (standard)' at '1:328' -> rtsp://mafreebox.freebox.fr/fbxtv_pub/stream?namespace=1&service=208&flavour=sd
[LibVLC-Gtk]   INFO       : Playing rtsp://mafreebox.freebox.fr/fbxtv_pub/stream?namespace=1&service=208&flavour=sd
[LibVLC-Gtk]   INFO       : Using vlc options [:deinterlace=0 :access=timeshift :input-timeshift-granularity=50]
[0x7f3b9c0110d8] [COLOR=#ff0000]ts[/COLOR] [COLOR=#ff0000]demux error: MPEG-4 descriptor not found[/COLOR]
[0x7f3b9c00d558] packetizer_mpeg4audio packetizer: AAC channels: 2 samplerate: 24000
Fontconfig warning: FcPattern object size does not accept value "0"
Fontconfig warning: FcPattern object size does not accept value "0"
Fontconfig warning: FcPattern object size does not accept value "0"
Fontconfig warning: FcPattern object size does not accept value "0"
[0x7f3b68001248] main vout display error: Failed to resize display
[h264 @ 0x7f3b9c00f720] mmco: unref short failure
[h264 @ 0x7f3b9c00f720][COLOR=#ff0000] illegal short term buffer state detected[/COLOR]
[FreetuxTV]    MESSAGE    : Launching channel 'BFM Business (HD)' at '1:321' -> rtsp://mafreebox.freebox.fr/fbxtv_pub/stream?namespace=1&service=897&flavour=hd
[LibVLC-Gtk]   INFO       : Playing rtsp://mafreebox.freebox.fr/fbxtv_pub/stream?namespace=1&service=897&flavour=hd
[LibVLC-Gtk]   INFO       : Using vlc options [:deinterlace=0 :access=timeshift :input-timeshift-granularity=50]
[0x7f3b7c02ddd8] ts demux error: MPEG-4 descriptor not found
Fontconfig warning: FcPattern object size does not accept value "0"
Fontconfig warning: FcPattern object size does not accept value "0"
Fontconfig warning: FcPattern object size does not accept value "0"
Fontconfig warning: FcPattern object size does not accept value "0"
[0x7f3b64011c58] main vout display error: Failed to resize display
[0x7f3b7c02afc8] packetizer_mpeg4audio packetizer: AAC channels: 2 samplerate: 24000
[COLOR=#ff0000][h264 @ 0x7f3b7c026a80] mmco: unref short failure
[h264 @ 0x7f3b7c026a80] illegal short term buffer state detected[/COLOR]
[h264 @ 0x7f3b7c026a80] Reference 3 >= 3
[COLOR=#ff0000][h264 @ 0x7f3b7c026a80] error while decoding MB 17 24, bytestream (7450)
[0x7f3b7c02ddd8] ts demux error: libdvbpsi (PSI decoder): TS discontinuity (received 10, expected 9) for PID 66[/COLOR]
[h264 @ 0x7f3b7c026a80] concealing 3992 DC, 3992 AC, 3992 MV errors
[0x7f3b7c02ddd8] ts demux error: libdvbpsi (PSI decoder): TS discontinuity (received 12, expected 11) for PID 0
[h264 @ 0x7f3b7c02ef80] Reference 2 >= 2
[COLOR=#ff0000][h264 @ 0x7f3b7c02ef80] error while decoding MB 37 32, bytestream (3850)
[h264 @ 0x7f3b7c02ef80] concealing 3252 DC, 3252 AC, 3252 MV errors[/COLOR]
[h264 @ 0x7f3b7c026640] mmco: unref short failure
[h264 @ 0x7f3b7c02f3c0] Reference 7 >= 3
[COLOR=#ff0000][h264 @ 0x7f3b7c02f3c0] error while decoding MB 0 56, bytestream (4068)
[h264 @ 0x7f3b7c02f3c0] concealing 1129 DC, 1129 AC, 1129 MV errors[/COLOR]
[FreetuxTV]    INFO       : Writing config file /home/freeman/.config/FreetuxTV/config.ini
[GMMKeys]      INFO       : Deactivating media player keys
freeman@freeman-SatelliteTosh:~$ 

```

and song cut not fluid

ubuntu-restricted-extra + addon installed  Universe repository.....an idea ?

I try with software center (no video no....nothing just the window freetux...."remove/ purge" , try with apt on videolan web site and now with synaptic with .dev & dbg ; always the same error....but now i can watch it.not very stable.....on my NEW LTS....

```
freeman@freeman-SatelliteTosh:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation HM55 Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV710/M92 [Mobility Radeon HD 4530/4570/545v]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] RV710/730 HDMI Audio [Radeon HD 4000 series]
07:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)
0c:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller (rev 02)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation 1st Generation Core i3/5/7 Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation 1st Generation Core i3/5/7 Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation 1st Generation Core i3/5/7 Processor Reserved (rev 02)
freeman@freeman-SatelliteTosh:~$ 

```

Vlc alone on .avi all is very good...

```
freeman@freeman-SatelliteTosh:~$ vlc -vv /path/to/video 2>&1 | tee vlc.log
[0xd48118] main libvlc debug: VLC media player - 2.1.6 Rincewind
[0xd48118] main libvlc debug: Copyright © 1996-2015 the VideoLAN team
[0xd48118] main libvlc debug: revision 2.1.6-0-gea01d28
[0xd48118] main libvlc debug: configured with ./configure  '--includedir=${prefix}/include' '--mandir=${prefix}/share/man' '--infodir=${prefix}/share/info' '--localstatedir=/var' '--libdir=${prefix}/lib/x86_64-linux-gnu' '--libexecdir=${prefix}/lib/x86_64-linux-gnu' '--disable-dependency-tracking' '--build=x86_64-linux-gnu' 'CPPFLAGS=-D_FORTIFY_SOURCE=2' 'LDFLAGS=-Wl,-Bsymbolic-functions -Wl,-z,relro' '--config-cache' '--disable-maintainer-mode' '--disable-silent-rules' '--disable-update-check' '--enable-fast-install' '--prefix=/usr' '--docdir=/usr/share/doc/vlc-nox' '--libdir=/usr/lib' '--sysconfdir=/etc' '--with-binary-version=0ubuntu14.04.2' '--enable-a52' '--enable-aa' '--enable-bluray' '--enable-bonjour' '--enable-caca' '--enable-chromaprint' '--enable-dbus' '--enable-dca' '--enable-dirac' '--enable-directfb' '--enable-dvbpsi' '--enable-dvdnav' '--enable-faad' '--enable-flac' '--enable-fluidsynth' '--enable-freetype' '--enable-fribidi' '--enable-gnutls' '--enable-jack' '--enable-kate' '--enable-libass' '--enable-libfreerdp' '--enable-libmpeg2' '--enable-libxml2' '--enable-lirc' '--enable-live555' '--enable-mad' '--enable-mkv' '--enable-mod' '--enable-mpc' '--enable-mtp' '--enable-mux_ogg' '--enable-ncurses' '--enable-notify' '--enable-ogg' '--enable-opus' '--enable-oss' '--enable-pulse' '--enable-qt' '--enable-realrtsp' '--enable-samplerate' '--enable-schroedinger' '--enable-sdl' '--enable-sftp' '--enable-shout' '--enable-skins2' '--enable-smbclient' '--enable-speex' '--enable-svg' '--enable-taglib' '--enable-theora' '--enable-twolame' '--enable-upnp' '--enable-vcd' '--enable-vcdx' '--enable-vorbis' '--enable-x264' '--enable-zvbi' '--with-kde-solid=/usr/share/kde4/apps/solid/actions/' '--disable-decklink' '--disable-dxva2' '--disable-fdkaac' '--disable-gnomevfs' '--disable-goom' '--disable-libvnc' '--disable-opencv' '--disable-projectm' '--disable-quicksync' '--disable-sndio' '--disable-telx' '--disable-vsxu' '--disable-wasapi' '--enable-alsa' '--enable-atmo' '--enable-dc1394' '--enable-dv1394' '--enable-linsys' '--enable-omxil' '--enable-udev' '--enable-libva' '--enable-v4l2' '--enable-crystalhd' '--enable-mmx' '--enable-sse' '--disable-neon' '--disable-altivec' 'CFLAGS=-g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Werror=format-security' 'CXXFLAGS=-g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Werror=format-security' 'build_alias=x86_64-linux-gnu'
[0xd48118] main libvlc debug: searching plug-in modules
[0xd48118] main libvlc debug: loading plugins cache file /usr/lib/vlc/plugins/plugins.dat
[0xd48118] main libvlc debug: recursively browsing `/usr/lib/vlc/plugins'
[0xd48118] main libvlc debug: saving plugins cache /usr/lib/vlc/plugins/plugins.dat
[0xd48118] main libvlc debug: plug-ins loaded: 428 modules
[0xd48118] main libvlc debug: opening config file (/home/freeman/.config/vlc/vlcrc)
[0xd48118] main libvlc debug: translation test: code is "fr"
[0xd48118] main libvlc debug: CPU has capabilities MMX MMXEXT SSE SSE2 SSE3 SSSE3 SSE4.1 SSE4.2 FPU 
[0xd73cf8] main input debug: Creating an input for 'Bibliothèque'
[0xd73cf8] main input debug: Input is a meta file: disabling unneeded options
[0xd73cf8] main input debug: using timeshift granularity of 50 MiB, in path '/tmp'
[0xd73cf8] main input debug: `file/xspf-open:///home/freeman/.local/share/vlc/ml.xspf' gives access `file' demux `xspf-open' path `/home/freeman/.local/share/vlc/ml.xspf'
[0xd73cf8] main input debug: creating demux: access='file' demux='xspf-open' location='/home/freeman/.local/share/vlc/ml.xspf' file='/home/freeman/.local/share/vlc/ml.xspf'
[0xf5f388] main demux debug: looking for access_demux module matching "file": 21 candidates
[0xf5f388] main demux debug: no access_demux modules matched
[0xd73cf8] main input debug: creating access 'file' location='/home/freeman/.local/share/vlc/ml.xspf', path='/home/freeman/.local/share/vlc/ml.xspf'
[0xd5e9e8] main access debug: looking for access module matching "file": 25 candidates
[0xd5e9e8] filesystem access debug: opening file `/home/freeman/.local/share/vlc/ml.xspf'
[0xd5e9e8] main access debug: using access module "filesystem"
[0xd5f6f8] main stream debug: Using stream method for AStream*
[0xd5f6f8] main stream debug: starting pre-buffering
[0xd5f6f8] main stream debug: received first data after 0 ms
[0xd5f6f8] main stream debug: pre-buffering done 296 bytes in 0s - 1661 KiB/s
[0xd5f958] main stream debug: looking for stream_filter module matching "any": 9 candidates
[0xd5f958] main stream debug: no stream_filter modules matched
[0xd5f958] main stream debug: looking for stream_filter module matching "record": 9 candidates
[0xd5f958] main stream debug: using stream_filter module "record"
[0xd73cf8] main input debug: creating demux: access='file' demux='xspf-open' location='/home/freeman/.local/share/vlc/ml.xspf' file='/home/freeman/.local/share/vlc/ml.xspf'
[0xd62a88] main demux debug: looking for demux module matching "xspf-open": 63 candidates
[0xd62a88] playlist demux debug: using XSPF playlist reader
[0xd62a88] main demux debug: using demux module "playlist"
[0xd62d38] main demux meta debug: looking for meta reader module matching "any": 2 candidates
[0xd62d38] lua demux meta debug: Trying Lua scripts in /home/freeman/.local/share/vlc/lua/meta/reader
[0xd62d38] lua demux meta debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/reader
[0xd62d38] lua demux meta debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/reader/filename.luac
[0xd62d38] lua demux meta debug: Trying Lua scripts in /usr/share/vlc/lua/meta/reader
[0xd62d38] main demux meta debug: no meta reader modules matched
[0xd73cf8] main input debug: `file/xspf-open:///home/freeman/.local/share/vlc/ml.xspf' successfully opened
[0xe1aa98] main xml reader debug: looking for xml reader module matching "any": 1 candidates
[0xe1aa98] main xml reader debug: using xml reader module "xml"
[0xd62a88] playlist demux debug: parsed 0 tracks successfully
[0xd73cf8] main input debug: EOF reached
[0xd62a88] main demux debug: removing module "playlist"
[0xd5f958] main stream debug: removing module "record"
[0xd5e9e8] main access debug: removing module "filesystem"
[0xf53c08] main playlist debug: creating audio output
[0xe1d808] main audio output debug: looking for audio output module matching "any": 7 candidates
[0xe1d808] pulse audio output debug: using library version 4.0.0
[0xe1d808] pulse audio output debug:  (compiled with version 4.0.0, protocol 28)
[0xe1d808] pulse audio output debug: connected locally to unix:/run/user/1000/pulse/native as client #38
[0xe1d808] pulse audio output debug: using protocol 28, server protocol 28
[0xe1d808] main audio output debug: using audio output module "pulse"
[0xf53c08] main playlist debug: keeping audio output
[0xf53c08] main playlist debug: adding item `video' ( file:///path/to/video )
[0x7ff730000958] main input debug: Creating an input for 'video'
[0xf54e78] main interface debug: looking for interface module matching "hotkeys,none": 19 candidates
[0xf54e78] main interface debug: using interface module "hotkeys"
[0xf555b8] main interface debug: looking for interface module matching "globalhotkeys,none": 19 candidates
[0xf53c08] main playlist debug: no fetch required for (null) (art currently (null))
[0xe1d808] pulse audio output debug: adding sink 0: alsa_output.pci-0000_01_00.1.hdmi-stereo (RV710/730 HDMI Audio [Radeon HD 4000 series] Stéréo numérique (HDMI))
[0xe1d808] pulse audio output debug: adding sink 1: alsa_output.pci-0000_00_1b.0.analog-stereo (Audio interne Stéréo analogique)
[0xf555b8] main interface debug: using interface module "globalhotkeys"
[0xe18ec8] main interface debug: looking for interface module matching "dbus,none": 19 candidates
[0xe18ec8] dbus interface debug: listening on dbus as: org.mpris.MediaPlayer2.vlc.instance12443
[0xe18ec8] main interface debug: using interface module "dbus"
[0xd48118] main libvlc: Lancement de vlc avec l'interface par défaut. Utilisez « cvlc » pour démarrer VLC sans interface.
[0xe13818] main interface debug: looking for interface module matching "any": 19 candidates
[0xe18ec8] dbus interface debug: Getting All properties
[0xe18ec8] dbus interface debug: Getting All properties
[0xe18ec8] dbus interface debug: Getting All properties
[0xe13818] qt4 interface debug: Boring first Run Wizard
[0x7ff730663e68] main generic debug: looking for extension module matching "any": 1 candidates
[0x7ff730663e68] lua generic debug: Opening Lua Extension module
[0x7ff730663e68] lua generic debug: Trying Lua scripts in /home/freeman/.local/share/vlc/lua/extensions
[0x7ff730663e68] lua generic debug: Trying Lua scripts in /usr/lib/vlc/lua/extensions
[0x7ff730663e68] lua generic debug: Trying Lua playlist script /usr/lib/vlc/lua/extensions/VLSub.luac
[0x7ff730663e68] lua generic debug: Scanning Lua script /usr/lib/vlc/lua/extensions/VLSub.luac
[0x7ff730663e68] lua generic debug: Script /usr/lib/vlc/lua/extensions/VLSub.luac has the following capability flags: 0x5
[0x7ff730663e68] lua generic debug: Trying Lua scripts in /usr/share/vlc/lua/extensions
[0x7ff730663e68] main generic debug: using extension module "lua"
[0xe13818] main interface debug: using interface module "qt4"
[0xf53c08] main playlist debug: processing request item: null, node: Liste de lecture, skip: 0
[0xf53c08] main playlist debug: rebuilding array of current - root Liste de lecture
[0xf53c08] main playlist debug: rebuild done - 1 items, index -1
[0xf53c08] main playlist debug: starting playback of the new playlist item
[0xf53c08] main playlist debug: resyncing on video
[0xf53c08] main playlist debug: video is at 0
[0xf53c08] main playlist debug: creating new input thread
[0x7ff7080009b8] main input debug: Creating an input for 'video'
[0x7ff7080009b8] main input debug: using timeshift granularity of 50 MiB, in path '/tmp'
[0x7ff7080009b8] main input debug: `file:///path/to/video' gives access `file' demux `' path `/path/to/video'
[0x7ff7080009b8] main input debug: creating demux: access='file' demux='' location='/path/to/video' file='/path/to/video'
[0x7ff700000e78] main demux debug: looking for access_demux module matching "file": 21 candidates
[0x7ff700000e78] main demux debug: no access_demux modules matched
[0x7ff7080009b8] main input debug: creating access 'file' location='/path/to/video', path='/path/to/video'
[0x7ff700001098] main access debug: looking for access module matching "file": 25 candidates
[0x7ff700001098] filesystem access debug: opening file `/path/to/video'
[0x7ff700001098] filesystem access error: cannot open file /path/to/video (No such file or directory)
[0x7ff700001098] main access debug: no access modules matched
[0x7ff7080009b8] main input error: open of `file:///path/to/video' failed
[0xf53c08] main playlist debug: finished input
[0xf53c08] main playlist debug: dead input
[0xf53c08] main playlist debug: changing item without a request (current 0/1)
[0xf53c08] main playlist debug: nothing to play
[0xe1d808] pulse audio output debug: changing sink 1: alsa_output.pci-0000_00_1b.0.analog-stereo (Audio interne Stéréo analogique)
[0xe1d808] pulse audio output debug: changing sink 1: alsa_output.pci-0000_00_1b.0.analog-stereo (Audio interne Stéréo analogique)
[0xe1d808] pulse audio output debug: changing sink 1: alsa_output.pci-0000_00_1b.0.analog-stereo (Audio interne Stéréo analogique)
[0xe1d808] pulse audio output debug: changing sink 1: alsa_output.pci-0000_00_1b.0.analog-stereo (Audio interne Stéréo analogique)
[0xe1d808] pulse audio output debug: changing sink 1: alsa_output.pci-0000_00_1b.0.analog-stereo (Audio interne Stéréo analogique)
[0xe1d808] pulse audio output debug: changing sink 1: alsa_output.pci-0000_00_1b.0.analog-stereo (Audio interne Stéréo analogique)
[0xe1d808] pulse audio output debug: changing sink 1: alsa_output.pci-0000_00_1b.0.analog-stereo (Audio interne Stéréo analogique)
[0xe1d808] pulse audio output debug: changing sink 1: alsa_output.pci-0000_00_1b.0.analog-stereo (Audio interne Stéréo analogique)
[0xe1d808] pulse audio output debug: changing sink 1: alsa_output.pci-0000_00_1b.0.analog-stereo (Audio interne Stéréo analogique)
[0xe1d808] pulse audio output debug: changing sink 1: alsa_output.pci-0000_00_1b.0.analog-stereo (Audio interne Stéréo analogique)
[0xe1d808] pulse audio output debug: changing sink 1: alsa_output.pci-0000_00_1b.0.analog-stereo (Audio interne Stéréo analogique)
```


.freetuxtv dev /AMD Driver dev!  Long Time Support !  LTS !  more six month OUT on My Desktop with "(Sigsev)" error ! and now Laptop fresh install....but i can watch now on my Laptop Pffuuuu ...... Safe...


Thanks for help.


HAVE A GOOD DAY ! :) (i don't watch TV !....but i'm not alone.....)

Laptop L505-13J core i5  ATI card  4.4.0-45-generic #66~14.04.1-Ubuntu SMP Wed Oct 19 15:05:38 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

---

