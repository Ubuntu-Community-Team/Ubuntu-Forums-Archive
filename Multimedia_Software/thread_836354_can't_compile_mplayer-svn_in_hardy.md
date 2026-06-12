---
title: "can't compile mplayer-svn in hardy"
date: 2008-06-21
forum: Multimedia Software
---

### Post by ptero on 2008-06-21
i made a minimal ("shell-only") installation of hardy, then installed xorg, fluxbox and everything else... mplayer didn't want to work, so i tried to compile mplayer-svn. but i get following error message (build-essential is installed):

```
help/help_create.sh help/help_mp-en.h UTF-8
make: execvp: help/help_create.sh: Permission denied
./version.sh `cc -dumpversion`
/bin/sh: ./version.sh: Permission denied
awk -f vidix/pci_db2c.awk vidix/pci.db 1
cc -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -DHAVE_CONFIG_H -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT -I/usr/include/kde/artsc -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  -D_REENTRANT    -I/usr/include/freetype2 -I/usr/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1     -c -o mplayer.o mplayer.c
mplayer.c:39:21: error: version.h: No such file or directory
mplayer.c:44:21: error: help_mp.h: No such file or directory
mplayer.c: In function 'mpctx_get_audio_out':
mplayer.c:380: warning: return discards qualifiers from pointer target type
mplayer.c: In function 'exit_player_with_rc':
mplayer.c:726: error: 'MSGTR_ExitingHow' undeclared (first use in this function)
mplayer.c:726: error: (Each undeclared identifier is reported only once
mplayer.c:726: error: for each function it appears in.)
mplayer.c: In function 'exit_sighandler':
mplayer.c:771: error: expected ')' before 'MSGTR_IntBySignal'
mplayer.c:787: error: 'MSGTR_Exit_SIGILL' undeclared (first use in this function)
mplayer.c:791: error: 'MSGTR_Exit_SIGSEGV_SIGFPE' undeclared (first use in this function)
mplayer.c:793: error: 'MSGTR_Exit_SIGCRASH' undeclared (first use in this function)
In file included from mplayer.c:821:
cfg-mplayer.h: At top level:
cfg-mplayer.h:352: warning: initialization discards qualifiers from pointer target type
In file included from cfg-mplayer.h:357,
                 from mplayer.c:821:
cfg-common-opts.h:11: warning: initialization discards qualifiers from pointer target type
cfg-common-opts.h:21: warning: initialization discards qualifiers from pointer target type
cfg-common-opts.h:148: warning: initialization discards qualifiers from pointer target type
cfg-common-opts.h:155: warning: initialization discards qualifiers from pointer target type
cfg-common-opts.h:160: warning: initialization discards qualifiers from pointer target type
cfg-common-opts.h:164: warning: initialization discards qualifiers from pointer target type
cfg-common-opts.h:166: warning: initialization discards qualifiers from pointer target type
cfg-common-opts.h:208: warning: initialization discards qualifiers from pointer target type
cfg-common-opts.h:232: warning: initialization discards qualifiers from pointer target type
cfg-common-opts.h:255: warning: initialization discards qualifiers from pointer target type
cfg-common-opts.h:258: warning: initialization discards qualifiers from pointer target type
cfg-common-opts.h:261: warning: initialization discards qualifiers from pointer target type
In file included from mplayer.c:821:
cfg-mplayer.h:361: error: 'help_text' undeclared here (not in a function)
cfg-mplayer.h:365: warning: initialization discards qualifiers from pointer target type
mplayer.c: In function 'parse_cfgfiles':
mplayer.c:831: error: 'MSGTR_NoHomeDir' undeclared (first use in this function)
mplayer.c:831: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c:840: error: 'MSGTR_GetpathProblem' undeclared (first use in this function)
mplayer.c:840: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c:843: error: 'MSGTR_CreatingCfgFile' undeclared (first use in this function)
mplayer.c:843: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c: In function 'load_per_protocol_config':
mplayer.c:873: error: 'MSGTR_LoadingProtocolProfile' undeclared (first use in this function)
mplayer.c:873: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c: In function 'load_per_extension_config':
mplayer.c:896: error: 'MSGTR_LoadingExtensionProfile' undeclared (first use in this function)
mplayer.c:896: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c: In function 'load_per_output_config':
mplayer.c:913: error: 'MSGTR_LoadingExtensionProfile' undeclared (first use in this function)
mplayer.c:913: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c: In function 'load_per_file_config':
mplayer.c:929: error: 'MSGTR_LoadingConfig' undeclared (first use in this function)
mplayer.c:929: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c:943: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c: In function 'libmpdemux_was_interrupted':
mplayer.c:960: error: 'MSGTR_Exit_quit' undeclared (first use in this function)
mplayer.c:960: warning: passing argument 1 of 'exit_player_with_rc' from incompatible pointer type
mplayer.c: In function 'add_subtitles':
mplayer.c:1042: error: 'MSGTR_CantLoadSub' undeclared (first use in this function)
mplayer.c:1043: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c:1056: error: 'MSGTR_AddedSubtitleFile' undeclared (first use in this function)
mplayer.c:1057: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c: In function 'reinit_audio_chain':
mplayer.c:1606: error: 'MSGTR_AudioFilterChainPreinitError' undeclared (first use in this function)
mplayer.c:1606: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c:1607: error: 'MSGTR_Exit_error' undeclared (first use in this function)
mplayer.c:1607: warning: passing argument 1 of 'exit_player' from incompatible pointer type
mplayer.c:1617: error: 'MSGTR_CannotInitAO' undeclared (first use in this function)
mplayer.c:1617: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c:1638: error: 'MSGTR_NoMatchingFilter' undeclared (first use in this function)
mplayer.c:1638: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c: In function 'timing_sleep':
mplayer.c:1790: error: 'MSGTR_LinuxRTCReadError' undeclared (first use in this function)
mplayer.c:1790: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c:1807: error: 'MSGTR_SoftsleepUnderflow' undeclared (first use in this function)
mplayer.c:1807: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c: In function 'adjust_sync_and_print_status':
mplayer.c:1975: error: 'MSGTR_SystemTooSlow' undeclared (first use in this function)
mplayer.c:1975: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c: In function 'reinit_video_chain':
mplayer.c:2152: error: 'MSGTR_ErrorInitializingVODevice' undeclared (first use in this function)
mplayer.c:2152: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c: In function 'pause_loop':
mplayer.c:2336: error: 'MSGTR_Paused' undeclared (first use in this function)
mplayer.c:2336: error: invalid initializer
mplayer.c:2342: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c: In function 'print_version':
mplayer.c:2399: error: 'MP_TITLE' undeclared (first use in this function)
mplayer.c:2399: warning: format '%s' expects type 'char *', but argument 4 has type 'const struct m_option_t *'
mplayer.c:2411: error: 'MSGTR_CompiledWithCPUExtensions' undeclared (first use in this function)
mplayer.c:2411: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c: In function 'edl_update':
mplayer.c:2462: error: 'MSGTR_EdlNOsh_video' undeclared (first use in this function)
mplayer.c:2462: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c: In function 'main':
mplayer.c:2657: error: 'MSGTR_GuiNeedsX' undeclared (first use in this function)
mplayer.c:2657: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c:2695: error: 'MSGTR_BuiltinCodecsConf' undeclared (first use in this function)
mplayer.c:2695: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c:2710: error: 'MSGTR_AvailableAudioCodecs' undeclared (first use in this function)
mplayer.c:2710: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c:2717: error: 'MSGTR_AvailableVideoCodecs' undeclared (first use in this function)
mplayer.c:2717: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c:2761: error: 'MSGTR_NoIdleAndGui' undeclared (first use in this function)
mplayer.c:2761: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c:2768: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c:2778: error: 'MSGTR_CommandLine' undeclared (first use in this function)
mplayer.c:2778: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c:2796: error: 'MSGTR_CantLoadFont' undeclared (first use in this function)
mplayer.c:2797: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c:2825: error: 'MSGTR_RTCDeviceNotOpenable' undeclared (first use in this function)
mplayer.c:2826: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c:2831: error: 'MSGTR_LinuxRTCInitErrorIrqpSet' undeclared (first use in this function)
mplayer.c:2831: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c:2832: error: 'MSGTR_IncreaseRTCMaxUserFreq' undeclared (first use in this function)
mplayer.c:2832: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c:2837: error: 'MSGTR_LinuxRTCInitErrorPieOn' undeclared (first use in this function)
mplayer.c:2837: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c:2841: error: 'MSGTR_UsingRTCTiming' undeclared (first use in this function)
mplayer.c:2841: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c:2927: warning: passing argument 2 of 'guiGetEvent' from incompatible pointer type
mplayer.c:2956: error: 'MSGTR_Getch2InitializedTwice' undeclared (first use in this function)
mplayer.c:2956: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c:3022: error: 'MSGTR_Exit_quit' undeclared (first use in this function)
mplayer.c:3022: warning: passing argument 1 of 'exit_player_with_rc' from incompatible pointer type
mplayer.c:3059: error: 'MSGTR_Playing' undeclared (first use in this function)
mplayer.c:3060: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c:3070: error: 'MSGTR_EdlCantOpenForWrite' undeclared (first use in this function)
mplayer.c:3071: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c:3081: error: 'MSGTR_CantLoadSub' undeclared (first use in this function)
mplayer.c:3082: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c:3168: error: 'MSGTR_DumpstreamFdUnavailable' undeclared (first use in this function)
mplayer.c:3168: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c:3169: error: 'MSGTR_Exit_error' undeclared (first use in this function)
mplayer.c:3169: warning: passing argument 1 of 'exit_player' from incompatible pointer type
mplayer.c:3175: error: 'MSGTR_CantOpenDumpfile' undeclared (first use in this function)
mplayer.c:3175: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c:3176: warning: passing argument 1 of 'exit_player' from incompatible pointer type
mplayer.c:3186: error: 'MSGTR_ErrorWritingFile' undeclared (first use in this function)
mplayer.c:3186: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c:3187: warning: passing argument 1 of 'exit_player' from incompatible pointer type
mplayer.c:3192: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c:3193: warning: passing argument 1 of 'exit_player' from incompatible pointer type
mplayer.c:3195: error: 'MSGTR_CoreDumped' undeclared (first use in this function)
mplayer.c:3195: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c:3196: error: 'MSGTR_Exit_eof' undeclared (first use in this function)
mplayer.c:3196: warning: passing argument 1 of 'exit_player_with_rc' from incompatible pointer type
mplayer.c:3357: error: 'MSGTR_DumpSelectedStreamMissing' undeclared (first use in this function)
mplayer.c:3357: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c:3358: warning: passing argument 1 of 'exit_player' from incompatible pointer type
mplayer.c:3367: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c:3368: warning: passing argument 1 of 'exit_player' from incompatible pointer type
mplayer.c:3378: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c:3379: warning: passing argument 1 of 'exit_player_with_rc' from incompatible pointer type
mplayer.c:3389: error: 'MSGTR_CannotReadVideoProperties' undeclared (first use in this function)
mplayer.c:3389: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c:3392: error: 'MSGTR_FilefmtFourccSizeFpsFtime' undeclared (first use in this function)
mplayer.c:3395: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c:3405: error: 'MSGTR_FPSnotspecified' undeclared (first use in this function)
mplayer.c:3405: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c:3413: error: 'MSGTR_NoStreamFound' undeclared (first use in this function)
mplayer.c:3413: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c:3602: error: 'MSGTR_NoSound' undeclared (first use in this function)
mplayer.c:3602: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c:3609: error: 'MSGTR_Video_NoVideo' undeclared (first use in this function)
mplayer.c:3609: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c:3623: error: 'MSGTR_FPSforced' undeclared (first use in this function)
mplayer.c:3623: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c:3646: error: 'MSGTR_StartPlaying' undeclared (first use in this function)
mplayer.c:3646: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c:3663: error: 'MSGTR_MPEndposNoSizeBased' undeclared (first use in this function)
mplayer.c:3663: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c:3725: error: 'MSGTR_NotInitializeVOPorVO' undeclared (first use in this function)
mplayer.c:3725: warning: passing argument 3 of 'mp_msg' from incompatible pointer type
mplayer.c:4040: warning: passing argument 1 of 'exit_player_with_rc' from incompatible pointer type
make: *** [mplayer.o] Error 1
 
```

---

### Post by ptero on 2008-06-21
oh, well... nevermind, it was really a permissions problem (my download folder is a symlink to my user folder from an older installation on my other hdd. it looks, like chowning it (the download folder) didn't help).
well, i installed mplayer-svn and smplayer-0.6.1 and mplayer works now. however, it plays videos extremely slow, no matter if through xv or x11...

EDIT: ok, apparently the problem is pulseaudio. i changed the audio output to sdl and everything works just fine.
however, if anybody could tell me how to set pulseaudio up to work fine with mplayer (or how to set mplayer up to work with pulseaudio...), i would be very thankful. i set pulseadio up by [this guide]("http://ubuntuforums.org/showthread.php?t=789578&highlight=mplayer+pulseaudio&page=2").

---

