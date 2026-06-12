---
title: "newest Wine, Alsa, newest problems..."
date: 2006-12-06
forum: Multimedia &amp; Video
---

### Post by sgx on 2006-12-06
Hi...
the following is the error message received when starting
the famed freeware Synth1 VST. Before updating wine from
ubuntu 9.9 to 9.26, this ran stable every time, but now, 
this and several other vsts are crashdiving...
(I renamed the program to s7, but the behaviour is consistant, both as user, and root, regardless of namechange.
issue command
fst s7.dll
yo... lets see...
The program 'fst' received an X Window System error.
This probably reflects a bug in the program.
The error was 'RenderBadPicture (invalid Picture parameter)'.
  (Details: serial 15077 error_code 182 request_code 155 minor_code 7)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

Now, running the same Synth1 version with vsthost, when changing to certain sounds, (the same sounds always cause a crash) I get the following error...(after this initial successful starting report

issue command
vsthost s7.dll

Returning file identifiers: BOpruQYeVBNwxJTfAg4AwML0
RemoteVSTClient: executing /usr/lib/dssi/dssi-vst/dssi-vst-server -g s7.dll,BOpruQYeVBNwxJTfAg4AwML0
DSSI VST plugin server v0.986
Copyright (c) 2004-2006 Chris Cannam - Fervent Software
Loading "s7.dll"...
dssi-vst-server[1]: not found in /home/zonger/abvst/s7.dll
dssi-vst-server[1]: not found in abvst/s7.dll
dssi-vst-server[1]: found in /home/zonger/s7.dll
done
Testing VST compatibility...
dssi-vst-server[1]: VST 2.4 entrypoint "VSTPluginMain" not found in DLL "s7.dll", looking for "main"
dssi-vst-server[1]: VST entrypoint "main" found
dssi-vst-server[1]: plugin instantiated
dssi-vst-server[1]: plugin is a VST
dssi-vst-server[1]: plugin has a GUI
dssi-vst-server[1]: plugin supports processReplacing
dssi-vst-server[1]: opening plugin
dssi-vst-server[1]: plugin is VST 2.0 or newer
dssi-vst-server[1]: plugin is a synth
dssi-vst-server[1]: plugin name is "Synth1 VSTi"
dssi-vst-server[1]: vendor string is "Daichi"
Initialising Windows subsystem...
dssi-vst-server[1]: registered Windows application class "dssi_vst"
dssi-vst-server[1]: created main window
dssi-vst-server[1]: sized window
dssi-vst-server[1]: showed window
done
dssi-vst-server[1]: created audio thread
Failed to set realtime priority for audio thread: Operation not permitted
dssi-vst-server[1]: set sample rate to 44100
dssi-vst-server[1]: set buffer size to 512
client sized shm to 4096
sized shm to 4096, 0 inputs and 2 outputs

error message begins here...

fixme:win:SetLayeredWindowAttributes (0x10028,0x00000000,204,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20028,0x00000000,204,2): stub!
fixme:win:SetLayeredWindowAttributes (0x40028,0x00000000,204,2): stub!
fixme:win:SetLayeredWindowAttributes (0x50028,0x00000000,204,2): stub!
Ignoring incoming sequencer event of type 66
fixme:win:SetLayeredWindowAttributes (0x70028,0x00000000,204,2): stub!
fixme:win:SetLayeredWindowAttributes (0x80028,0x00000000,204,2): stub!
fixme:win:SetLayeredWindowAttributes (0x90028,0x00000000,204,2): stub!
fixme:win:SetLayeredWindowAttributes (0xa0028,0x00000000,204,2): stub!
fixme:win:SetLayeredWindowAttributes (0xb0028,0x00000000,204,2): stub!
fixme:win:SetLayeredWindowAttributes (0xc0028,0x00000000,204,2): stub!
WARNING: NOTE OFF received for pitch 61 with no preceding NOTE ON, ignoring
fixme:win:SetLayeredWindowAttributes (0xd0028,0x00000000,204,2): stub!
fixme:win:SetLayeredWindowAttributes (0xe0028,0x00000000,204,2): stub!
fixme:win:SetLayeredWindowAttributes (0xf0028,0x00000000,204,2): stub!
fixme:win:SetLayeredWindowAttributes (0x110028,0x00000000,204,2): stub!
wine: Unhandled division by zero at address 0x10011318 (thread 000d), starting debugger...
ERROR: Remote VST plugin communication failure
Unhandled exception: divide by zero in 32-bit code (0x10011318).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:10011318 ESP:7e0c10bc EBP:00000000 EFLAGS:00210206(   - 00      - RIP1)
 EAX:00000100 EBX:003721e8 ECX:00000000 EDX:00000000
 ESI:003771a4 EDI:00000100
Stack dump:
0x7e0c10bc:  00000000 00000100 1001b377 00000100
0x7e0c10cc:  7e54fc00 7e54f400 7e0c1954 7e0c1140
0x7e0c10dc:  00000000 7e0c1940 00000000 00000001
0x7e0c10ec:  00000000 10013bb9 00000100 7e0c1140
0x7e0c10fc:  7e0c113c 7ffdaf10 00372158 7ef7531c
0x7e0c110c:  00000000 00000000 00000000 00000000
Backtrace:
=>1 0x10011318 in s7 (+0x11318) (0x00000000)
0x10011318: idivl       %ecx,%eax
Modules:
Module  Address                 Debug info      Name (71 modules)
PE      10000000-1007c000       Export          s7
ELF     4802c000-48047000       Deferred        ld-linux.so.2
ELF     48049000-48169000       Deferred        libc.so.6
ELF     4816b000-4816f000       Deferred        libdl.so.2
ELF     48171000-48196000       Deferred        libm.so.6
ELF     48198000-481ab000       Deferred        libpthread.so.0
ELF     481ad000-481c1000       Deferred        libz.so.1
ELF     481c3000-4828e000       Deferred        libx11.so.6
ELF     48290000-4829e000       Deferred        libxext.so.6
ELF     482a0000-4830a000       Deferred        libfreetype.so.6
ELF     48333000-48336000       Deferred        libxinerama.so.1
ELF     48338000-48358000       Deferred        libexpat.so.1
ELF     4835a000-48384000       Deferred        libfontconfig.so.1
ELF     48386000-4838f000       Deferred        libxrender.so.1
ELF     48391000-48395000       Deferred        libxrandr.so.2
ELF     483a1000-483aa000       Deferred        libxcursor.so.1
ELF     483ac000-483b7000       Deferred        libgcc_s.so.1
ELF     484a2000-484ab000       Deferred        libsm.so.6
ELF     484ad000-484c5000       Deferred        libice.so.6
ELF     4855b000-4856d000       Deferred        libresolv.so.2
ELF     4856f000-4859e000       Deferred        libcups.so.2
ELF     4943c000-49440000       Deferred        libgpg-error.so.0
ELF     497b4000-497c9000       Deferred        libnsl.so.1
ELF     497cb000-497f9000       Deferred        libcrypt.so.1
ELF     49840000-4988e000       Deferred        libgcrypt.so.11
ELF     49890000-498fe000       Deferred        libgnutls.so.13
ELF     49890000-498fe000       Deferred        libgnutls.so.13
ELF     49890000-498fe000       Deferred        libgnutls.so.13
ELF     49b33000-49b46000       Deferred        libtasn1.so.3
ELF     7b800000-7b91b000       Deferred        kernel32<elf>
  \-PE  7b820000-7b91b000       \               kernel32
ELF     7bc00000-7bc82000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc82000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7e40e000-7e440000       Deferred        uxtheme<elf>
  \-PE  7e420000-7e440000       \               uxtheme
ELF     7e440000-7e471000       Deferred        winspool<elf>
  \-PE  7e450000-7e471000       \               winspool
ELF     7e471000-7e531000       Deferred        comctl32<elf>
  \-PE  7e480000-7e531000       \               comctl32
ELF     7e554000-7e572000       Deferred        iphlpapi<elf>
  \-PE  7e560000-7e572000       \               iphlpapi
ELF     7e572000-7e5c6000       Deferred        rpcrt4<elf>
  \-PE  7e580000-7e5c6000       \               rpcrt4
ELF     7e5c6000-7e65a000       Deferred        ole32<elf>
  \-PE  7e5d0000-7e65a000       \               ole32
ELF     7e65a000-7e6b2000       Deferred        shlwapi<elf>
  \-PE  7e670000-7e6b2000       \               shlwapi
ELF     7e6b2000-7e79e000       Deferred        shell32<elf>
  \-PE  7e6c0000-7e79e000       \               shell32
ELF     7e79e000-7e83a000       Deferred        comdlg32<elf>
  \-PE  7e7b0000-7e83a000       \               comdlg32
ELF     7e845000-7e861000       Deferred        imm32<elf>
  \-PE  7e850000-7e861000       \               imm32
ELF     7e861000-7e864000       Deferred        iso8859-1.so
ELF     7e86b000-7e888000       Deferred        ximcp.so.2
ELF     7e9ef000-7e9f2000       Deferred        xlcdef.so.2
ELF     7e9ff000-7ea8d000       Deferred        winex11<elf>
  \-PE  7ea10000-7ea8d000       \               winex11
ELF     7ec1b000-7ec61000       Deferred        advapi32<elf>
  \-PE  7ec30000-7ec61000       \               advapi32
ELF     7ec61000-7ed17000       Deferred        gdi32<elf>
  \-PE  7ec80000-7ed17000       \               gdi32
ELF     7ed17000-7ee4d000       Deferred        user32<elf>
  \-PE  7ed30000-7ee4d000       \               user32
ELF     7ef50000-7ef7f000       Deferred        dssi-vst-server<elf>
  \-PE  7ef60000-7ef7f000       \               dssi-vst-server
ELF     7efab000-7efb5000       Deferred        libnss_files.so.2
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7d27000-b7d2f000       Deferred        libnss_compat.so.2
ELF     b7e78000-b7f89000       Deferred        libwine.so.1
Threads:
process  tid      prio (all id:s are in hex)
0000000a
        0000000c    0
        0000000b    0
00000008 (D) Z:\usr\lib\dssi\dssi-vst\dssi-vst-server.exe
        0000000d    0 <==
        00000009    0
vsthost: signal 17 received, exiting

I use windowmaker, kde 3.5.5 and enlightenment 16.7, the newest
available fst, dssi-vsthost, alsa jackd, qjackctl, and vkeybd, and the kernel is stock 2.6.15 from distro Mepis 3.4, and Synth1 ran fine before the newer wine 9.26 was installed, via synaptic.

Another trouble, after starting EffEm.dll (and some others) the vsti will 'steal the gui' from
qjaclctl when connection is made! leaving only the outline and
some gray boxes within that outline. If I quit EffEm, the gui returns to qjackctl, and funtions normally...the process is repeatable, regardless of root, user, or if programs are run on
separate multiple desktops. The same vsts run from vsthost, may
load fine, and function in all ways, except no sound is heard.
Immediately loading crystal.dll reveals the audio emgine is OK,
and the problem remains. 
More vsts succombed to this -after- updating to the latest alsa
software...

issue command
 fst EffEm.dll
yo... lets see...
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dsnoop.c:558:(snd_pcm_dsnoop_open) unable to open slave
err:midi:MIDI_AlsaToWindowsDeviceType Cannot determine the type (alsa type is 100000) of this midi device. Assuming FM Synth
err:midi:MIDI_AlsaToWindowsDeviceType Cannot determine the type (alsa type is 100000) of this midi device. Assuming FM Synth

(the EffEm gui is drawn, all knobs etc working, but after connecting to qjackctl,

The program 'fst' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 210 error_code 8 request_code 42 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
and the qjackctl gui is 'stolen', only returned when the vsti is
exited.

Any comments, similar experiences, tips appreciated. If you know
developers, or their bugtrackers, please pass this on.

---

