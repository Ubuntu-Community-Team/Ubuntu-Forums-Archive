---
title: "Encrypted DVD crash w/ libdvdcss2 installed (Natty, 11.04)"
date: 2011-10-07
forum: Multimedia Software
---

### Post by guardsman85 on 2011-10-07
I was using Movie Player to play an episode of a favorite TV show I bought on DVD.  I accessed the main menu and episode menu without trouble.  The first episode played until 12:45 and then stopped with this error:
***Could not read DVD. This may be because the DVD is encrypted and a DVD decryption library is not installed.***

I also tried viewing the episode in VLC, but consistently got crashes at 12:09.  I uninstalled and reinstalled libdvdcss2 (from medibuntu repository) and VLC and still experienced the same problem.  I ran VLC from the terminal using *vlc -vvv* and this was the output (starting at the time of the crash):
```
[0xaf5025d4] main input error: ES_OUT_SET_(GROUP_)PCR  is called too late (pts_delay increased to 300 ms)
[0xaf5025d4] main input debug: ES_OUT_RESET_PCR called
libdvdread: Can't seek to block 244541
[0x902120c] dvdnav demux warning: cannot get next block (Error reading from DVD.)
[0x8e5b574] main playlist debug: finished input
[0xaf5025d4] main input debug: control type=0
[0xaf5025d4] main input debug: control: stopping input
[0x8e5b574] main playlist debug: dying input
[0x933ef44] avcodec decoder debug: ffmpeg codec (MPEG-1/2 Video) stopped
[0x933ef44] main decoder debug: removing module "avcodec"
[0x933ef44] main decoder debug: killing decoder fourcc `mpgv', 1 PES in FIFO
[0x93a9044] main video output debug: [0] 2 0
[0x93a9044] main video output debug: [1] 2 0
[0x93a9044] main video output debug: [2] 2 0
[0x93a9044] main video output debug: [3] 2 0
[0x93a9044] main video output debug: [4] 2 0
[0x93a9044] main video output debug: [5] 4 0
[0x93a9044] main video output debug: [6] 2 0
[0x93a9044] main video output debug: [7] 2 0
[0x93a9044] main video output debug: [8] 2 0
[0x93a9044] main video output debug: [9] 2 0
[0x93a9044] main video output debug: [10] 2 0
[0x93a9044] main video output debug: [11] 2 0
[0x93a9044] main video output debug: [12] 4 0
[0x93a9044] main video output debug: [13] 2 0
[0x93a9044] main video output debug: [14] 4 0
[0x93a9044] main video output debug: [15] 2 0
[0x93a9044] main video output debug: [16] 2 0
[0x93a9044] main video output debug: [17] 2 0
[0x93a9044] main video output debug: [18] 2 0
[0x93a9044] main video output debug: [19] 2 0
[0x93a9044] main video output debug: [20] 2 0
[0x93a9044] main video output debug: [21] 2 0
[0x93a9044] main video output debug: [22] 2 0
[0x93a9044] main video output debug: [23] 2 0
[0xaf5025d4] main input debug: saving a free vout
[0x92f26dc] main packetizer debug: removing module "packetizer_mpegvideo"
[0x92f91bc] main decoder debug: removing module "a52"
[0x92f91bc] main decoder debug: killing decoder fourcc `a52 ', 0 PES in FIFO
[0x9368324] main audio filter debug: removing module "a52tofloat32"
[0x9367bdc] main audio filter debug: removing module "scaletempo"
[0x9370cd4] main audio filter debug: removing module "ugly_resampler"
[0x92f2a3c] main audio output debug: removing module "pulse"
[0x92f327c] main generic debug: removing module "float32_mixer"
[0xaf5025d4] main input debug: releasing aout
[0xaf5025d4] main input debug: Program doesn't contain anymore ES
[0x902120c] main demux debug: removing module "dvdnav"
[0xaf5025d4] main input debug: thread ended
[0x8e5b574] main playlist debug: dead input
[0x8e5b574] main playlist debug: changing item without a request (current 0/1)
[0x8e5b574] main playlist debug: nothing to play
[0x93a9044] main video output debug: destroying useless vout
[0x8e6420c] qt4 interface debug: IM: Deleting the input
[0x93366fc] xdg_screensaver inhibit debug: started xdg-screensaver (PID = 2159)
[0x8e660f4] signals interface error: signal 17 overriden (0x49074c0)
[0x8e660f4] signals interface error:  /usr/lib/libQtCore.so.4(?)[(nil)]
[0x93366fc] main inhibit debug: removing module "xdg_screensaver"
[0x944d64c] qt4 window debug: releasing video...
[0x8e6420c] qt4 interface debug: Video is not needed anymore
[0x944d64c] main window debug: removing module "qt4"
[0x944ba8c] main generic debug: removing module "xcb_xv"
[0x93a9044] main video output debug: removing module "vout_wrapper"
[0x933ec14] main blend debug: removing module "blend"
[0x92f2c5c] main spu text debug: removing module "freetype"
[0x93ba42c] main scale debug: removing module "yuvp"
[0x93adf24] main scale debug: removing module "swscale"

```Please note, I have a already used *regionset* to set the region on my DVD drive to "1" and the discs were purchased in the US.

Suggestions for getting this DVD working, please and thank you.

---

