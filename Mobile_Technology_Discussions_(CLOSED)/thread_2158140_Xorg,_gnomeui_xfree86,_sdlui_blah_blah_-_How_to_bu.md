---
title: "Xorg, gnomeui xfree86, sdlui blah blah - How to build a lightweight solution"
date: 2013-06-28
forum: Mobile Technology Discussions (CLOSED)
---

### Post by crvella on 2013-06-28
Hi all - Little new so please bare with me.

I'm currently working on a project using a Beagleboard XM running Ubuntu 12.10.  Beagleboard obviously has limited resources.  Im trying to work out what components I need installed and which is the most lightweight option of each component.

I'm trying to compile VICE 2.4 ([http://vice-emu.sourceforge.net/](http://vice-emu.sourceforge.net/)) for the ARMv7 Cortex A8 processor, and there are ALOT of compile options;  which made me realize I have absolutely no idea about anything related to the Video / Graphical side of Linux and this is making it hard for me to choose the configuration options.  I'd take the defaults but I seem to get EXTREME lag and I can't achieve 'full screen'.  The Raspbery Pi is capable of this and is a lower spec, so I assume the Beagle should be able to achieve the same or better. This brings me to my first question;

1a) - What are the minimal 'Components' I need to be able to bring up a visual window.  i.e  X-Server, X-Client, Media Library, Media Code etc etc?  
1b) - I am using the HDMI/DVI-D video out from the same system the OS is running on, so do I need both an XServer AND an XClient?
1c) - What are the lightest weight for ubuntu 12.10 of each of these components.

2 - The compile configuration options for VICE are as follows;  


VICE_ARG_WITH_LIST(xaw3d,         [  --with-xaw3d            use Xaw3d library instead of plain Xaw])
VICE_ARG_WITH_LIST(readline,      [  --without-readline      do not try to use the system's readline library])
VICE_ARG_WITH_LIST(midas,         [  --with-midas            use MIDAS sound system instead of Allegro for audio])
VICE_ARG_WITH_LIST(arts,          [  --with-arts             use aRts sound system])
VICE_ARG_WITH_LIST(pulse,         [  --without-pulse         do not use PulseAudio sound system])
VICE_ARG_WITH_LIST(alsa,          [  --without-alsa          do not use the ALSA sound system])
VICE_ARG_WITH_LIST(oss,           [  --without-oss           do not use the OSS sound system])
VICE_ARG_WITH_LIST(sdlsound,      [  --with-sdlsound         use SDL sound system])
VICE_ARG_WITH_LIST(resid,         [  --without-resid         do not use the reSID engine])
VICE_ARG_WITH_LIST(residfp,       [  --without-residfp       do not use the reSID-fp engine])
VICE_ARG_WITH_LIST(png,           [  --without-png           do not use the PNG screenshot system])
VICE_ARG_WITH_LIST(zlib,          [  --without-zlib          do not use the zlib support])
VICE_ARG_WITH_LIST(picasso96,     [  --with-picasso96        use Amiga P96 grafix system instead of cgx])
VICE_ARG_WITH_LIST(cocoa,         [  --with-cocoa            enables native Cocoa UI on Macs])
VICE_ARG_ENABLE_LIST(textfield,   [  --disable-textfield     disable enhanced text field widget])
VICE_ARG_ENABLE_LIST(fullscreen,  [  --disable-fullscreen    disable XFree86 fullscreen detection])
VICE_ARG_ENABLE_LIST(gnomeui,     [  --enable-gnomeui        enables GNOME UI support])
VICE_ARG_ENABLE_LIST(sdlui,       [  --enable-sdlui          enables SDL UI support])
VICE_ARG_ENABLE_LIST(gp2x,        [  --enable-gp2x           enables GP2X support])
VICE_ARG_ENABLE_LIST(wiz,         [  --enable-wiz            enables WIZ support])
VICE_ARG_ENABLE_LIST(dingoo,      [  --enable-dingoo         enables native Dingoo support])
VICE_ARG_ENABLE_LIST(dingux,      [  --enable-dingux         enables Dingux (Dingoo Linux) support])
VICE_ARG_ENABLE_LIST(nls,         [  --disable-nls           disables national language support])
VICE_ARG_ENABLE_LIST(realdevice,  [  --disable-realdevice    disables access to real peripheral devices (CBM4Linux/OpenCBM)])
VICE_ARG_ENABLE_LIST(ffmpeg,      [  --disable-ffmpeg        disable FFmpeg library support])
VICE_ARG_ENABLE_LIST(quicktime,   [  --enable-quicktime      enables Apple QuickTime support])
VICE_ARG_ENABLE_LIST(ethernet,    [  --enable-ethernet       enables The Final Ethernet emulation])
VICE_ARG_ENABLE_LIST(ipv6,        [  --disable-ipv6          disables the checking for IPv6 compatibility])
VICE_ARG_ENABLE_LIST(parsid,      [  --enable-parsid         enables ParSID support])
VICE_ARG_ENABLE_LIST(bundle,      [  --disable-bundle        do not use application bundles on Macs])
VICE_ARG_ENABLE_LIST(memmap,      [  --enable-memmap         enable the memmap feature])
VICE_ARG_ENABLE_LIST(editline,    [  --disable-editline      disable history in Cocoa UI's console])
VICE_ARG_ENABLE_LIST(lame,        [  --disable-lame          disable MP3 export with LAME])
VICE_ARG_ENABLE_LIST(static-lame, [  --enable-static-lame    enable static LAME linking])
VICE_ARG_ENABLE_LIST(rs232,       [  --disable-rs232         disable RS232 support])
VICE_ARG_ENABLE_LIST(midi,        [  --disable-midi          disable MIDI support])
VICE_ARG_ENABLE_LIST(embedded,    [  --enable-embedded       enable embedding of emulation data files])
VICE_ARG_ENABLE_LIST(hidmgr,      [  --disable-hidmgr        disable IOHIDManager joystick support on Mac])
VICE_ARG_ENABLE_LIST(hidutils,    [  --disable-hidutils      disable HID Uitlities joystick support on Mac])
VICE_ARG_ENABLE_LIST(debug,       [  --enable-debug          enable debug source options])
VICE_ARG_ENABLE_LIST(debug-code,  [  --enable-debug-code     enable debugging code])


dnl register ReSID(-fp) options here to pass arg checks
VICE_ARG_ENABLE_LIST(inline,      [  --enable-inline         enable inlining of functions [default=yes]])
VICE_ARG_ENABLE_LIST(arch,        [  --enable-arch[[=arch]]    enable architecture specific compilation [[default=yes]]], [], [enable_arch=yes])
VICE_ARG_ENABLE_LIST(sse,         [  --enable-sse            enable the use of SSE [[default=yes]]])
[COLOR=#333333][FONT=Consolas]VICE_ARG_ENABLE_LIST(no-pic,      [  --enable-no-pic         enable the use of the no-pic switch [[default=yes]]])
[/FONT][/COLOR]

2a) All I know is that i need --SDLUI and --FULLSCREEN to be able to get the resolution i want.  --FULLSCREEN makes reference to XFree86.  Is XFree86 an XServer or XClient, or is it something completely different?

2b) is GNOMEUI the same component type as SDLUI, or SDLUI the same component as XFree86?  i.e  Would I be doubling up if I used more than one of these?

3)  I am also not sure what these options are and wether they are going to speed up or slow down the system

VICE_ARG_WITH_LIST(resid,         [  --without-resid         do not use the reSID engine])
VICE_ARG_WITH_LIST(residfp,       [  --without-residfp       do not use the reSID-fp engine])

VICE_ARG_ENABLE_LIST(gnomeui,     [  --enable-gnomeui        enables GNOME UI support])
VICE_ARG_ENABLE_LIST(sdlui,       [  --enable-sdlui          enables SDL UI support])
VICE_ARG_ENABLE_LIST(gp2x,        [  --enable-gp2x           enables GP2X support])
VICE_ARG_ENABLE_LIST(wiz,         [  --enable-wiz            enables WIZ support])



Thanks in advance guys - I know these are some pretty noob questions but I really appreciate the help

---

