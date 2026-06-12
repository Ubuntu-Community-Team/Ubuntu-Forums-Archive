---
title: "avcodec_decode_audio4() segmentation fault"
date: 2015-06-17
forum: Multimedia Software
---

### Post by glennra12 on 2015-06-17
On one of two machines I have running 14.04, the vlc media player and avconv program frequently crash with a segmentation fault in avcodec_decode_audio4().  I've tried uninstalling and reinstalling all of the packages associated with the ubuntu_restricted_extras metapackage, and it has not fixed the problem.  Anyone have any idea how to go about debugging this?  

Some time ago I attempted to install the old ffmpeg program.  I've since removed it and its related third party repository, and attempted to revert everything back to the preexisting configuration, but maybe something's still messed up.  Is there a way to verify I have the right packages installed and correctly configured (especially since I have another machine that doesn't have this problem)?

On one occasion when I was lucky enough to have the system throw up an error dialog, I was able to obtain a stack trace:

#0  0x00007fd3d92b4f06 in frame_configure_elements (avctx=0x7fd3dcc2cd80)
    at /build/buildd/libav-9.18/libavcodec/aacdec.c:194
#1  aac_decode_frame_int (avctx=avctx@entry=0x7fd3dcc2cd80,
    data=data@entry=0x7fd3dcc36b20,
    got_frame_ptr=got_frame_ptr@entry=0x7fd3f9b4e3dc,
    gb=gb@entry=0x7fd3f9b4e330)
    at /build/buildd/libav-9.18/libavcodec/aacdec.c:2491
#2  0x00007fd3d92b749d in aac_decode_frame (avctx=0x7fd3dcc2cd80,
    data=0x7fd3dcc36b20, got_frame_ptr=0x7fd3f9b4e3dc, avpkt=<optimized out>)
    at /build/buildd/libav-9.18/libavcodec/aacdec.c:2645
#3  0x00007fd3d95a0282 in avcodec_decode_audio4 (avctx=0x7fd3dcc2cd80,
    frame=0x7fd3dcc36b20, got_frame_ptr=got_frame_ptr@entry=0x7fd3f9b4e3dc,
    avpkt=avpkt@entry=0x7fd3f9b4e3f0)
    at /build/buildd/libav-9.18/libavcodec/utils.c:1384
#4  0x00007fd3da060128 in try_decode_frame (st=st@entry=0x7fd3dcc2ad60,
    avpkt=avpkt@entry=0x7fd3dcc36a60, options=<optimized out>)
    at /build/buildd/libav-9.18/libavformat/utils.c:2097
#5  0x00007fd3da065a5b in avformat_find_stream_info (ic=0x7fd3dcc2a420,
    options=options@entry=0x7fd3f9b4e7e0)
    at /build/buildd/libav-9.18/libavformat/utils.c:2477
#6  0x00007fd3da2c3ed0 in OpenDemux (p_this=0x7fd3dcc04b78)
    at avformat/demux.c:253#7  0x00007fd3fa827178 in module_load (obj=obj@entry=0x7fd3dcc04b78,
    m=m@entry=0x14e1ef0, init=init@entry=0x7fd3fa8270d0 <generic_start>,
    args=args@entry=0x7fd3f9b4eb10) at modules/modules.c:185
#8  0x00007fd3fa82772e in vlc_module_load (obj=obj@entry=0x7fd3dcc04b78,
    capability=capability@entry=0x7fd3fa85e059 "demux",
    name=0x7fd3fa85e3bb "", name@entry=0x7fd3dcc04c30 "",
    strict=<optimized out>, probe=probe@entry=0x7fd3fa8270d0 <generic_start>)
    at modules/modules.c:277
#9  0x00007fd3fa827c04 in module_need (obj=obj@entry=0x7fd3dcc04b78,
    cap=cap@entry=0x7fd3fa85e059 "demux", name=name@entry=0x7fd3dcc04c30 "",
    strict=<optimized out>) at modules/modules.c:366
#10 0x00007fd3fa7e6fbe in demux_New (p_obj=p_obj@entry=0x7fd3dc000958,
    p_parent_input=p_parent_input@entry=0x7fd3dc000958,
    psz_access=<optimized out>, psz_demux=0x7fd3fa873ca5 "",
    psz_location=<optimized out>, s=<optimized out>, out=0x7fd3dc003fe0,
    b_quick=true) at input/demux.c:188
#11 0x00007fd3fa7f3d5d in InputSourceInit (
    p_input=p_input@entry=0x7fd3dc000958, in=<optimized out>,
    psz_mrl=<optimized out>, psz_forced_demux=psz_forced_demux@entry=0x0,
    b_in_can_fail=b_in_can_fail@entry=false) at input/input.c:2535
#12 0x00007fd3fa7f4b6b in Init (p_input=p_input@entry=0x7fd3dc000958)
    at input/input.c:1225
#13 0x00007fd3fa7f6260 in input_Preparse (p_parent=p_parent@entry=0x1403288,
    p_item=p_item@entry=0x1358350) at input/input.c:200
#14 0x00007fd3fa7d7100 in Preparse (p_item=0x1358350, obj=<optimized out>)
    at playlist/preparser.c:137
#15 Thread (data=0x157fc40) at playlist/preparser.c:217
#16 0x00007fd3fb070182 in start_thread (arg=0x7fd3f9b4f700)
    at pthread_create.c:312
#17 0x00007fd3fab9247d in clone ()
    at ../sysdeps/unix/sysv/linux/x86_64/clone.S:111

Thanks!

---

### Post by Yellow Pasque on 2015-06-17
You may want to check that there are no hidden copies of the ffmpeg libs. I think this command could help:
```
sudo ldconfig -p | grep -i libav
```

---

### Post by glennra12 on 2015-06-18
A binary compare of all shared objects pulled in by avconv, between the two machines, turned up 3 that were not being restored by the package management tools.  Manually forcing the versions using apt-get, fixed the problem and eliminated the crash.  Argh!

---

