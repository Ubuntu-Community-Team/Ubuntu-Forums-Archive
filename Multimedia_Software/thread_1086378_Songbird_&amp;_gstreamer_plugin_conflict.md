---
title: "Songbird &amp; gstreamer plugin conflict"
date: 2009-03-04
forum: Multimedia Software
---

### Post by nikoboxxx on 2009-03-04
I am on Intrepid 64-bit...

I want to use songbird.  I downloaded the x86_64 version and was having issues starting the program.  It would either hang or give me an error relating to not being able to initialize gstreamer (Could not initialize GStreamer: Error re-scanning registry , child terminated by signal).  I decided to remove some gstreamer packages in hopes of getting songbird to run and was successful.  After removing gstreamer0.10-plugins-base, songbird fired right up.

The issue is that now other programs that rely on that package have been removed.  Brasero, Rhythmbox, and Sound Recorder are all gone.  I can live without the last two, but I want Brasero back.  Of course, installing brasero meant installing gstreamer0.10-plugins-base which meant.. no songbird.

I'm stuck.  I guess what I really need is a way to run songbird without deleting the plugins-base.  If I boot from a LiveCD, 64-bit, it works just fine.  I am currently resorting to running the 32bit version on the 64-bit OS.

Help please :)

---

### Post by nikoboxxx on 2009-03-15
Doesn't seem like anyone is wanting to reply to the post.. but I will add more info anyway.  This is what I see when I run songbird from a terminal...  Anyone??

```

*** glibc detected *** ././songbird-bin: free(): invalid pointer: 0x00007f4f73f8b1f0 ***
======= Backtrace: =========
/lib/libc.so.6[0x7f4f92f42a58]
/lib/libc.so.6(cfree+0x76)[0x7f4f92f450a6]
/usr/lib/libvisual-0.4.so.0(visual_mem_free+0xe)[0x7f4f6f44e4ce]
/usr/lib/libvisual-0.4.so.0[0x7f4f6f447646]
/usr/lib/libvisual-0.4.so.0(visual_plugin_get_list+0x48)[0x7f4f6f4477d8]
/usr/lib/libvisual-0.4.so.0(visual_init+0x243)[0x7f4f6f454703]
/usr/lib64/gstreamer-0.10/libgstlibvisual.so[0x7f4f6f675c24]
/home/niko/Desktop/Songbird64/lib/libgstreamer-0.10.so[0x7f4f819ef32a]
/home/niko/Desktop/Songbird64/lib/libgstreamer-0.10.so(gst_plugin_load_file+0x64b)[0x7f4f819efbe3]
/home/niko/Desktop/Songbird64/lib/libgstreamer-0.10.so[0x7f4f819f9f41]
/home/niko/Desktop/Songbird64/lib/libgstreamer-0.10.so(gst_registry_scan_path+0x11f)[0x7f4f819fa0c4]
/home/niko/Desktop/Songbird64/lib/libgstreamer-0.10.so[0x7f4f819aa7a5]
/home/niko/Desktop/Songbird64/lib/libgstreamer-0.10.so[0x7f4f819aac13]
/home/niko/Desktop/Songbird64/lib/libgstreamer-0.10.so[0x7f4f819ab1cf]
/home/niko/Desktop/Songbird64/lib/libgstreamer-0.10.so[0x7f4f819ab753]
/usr/lib/libglib-2.0.so.0(g_option_context_parse+0x528)[0x7f4f8f2628e8]
/home/niko/Desktop/Songbird64/lib/libgstreamer-0.10.so(gst_init_check+0xd6)[0x7f4f819a9b56]
/home/niko/Desktop/Songbird64/lib/libgstreamer-0.10.so(gst_init+0x29)[0x7f4f819a9c43]
/home/niko/Desktop/Songbird64/lib/sbGStreamerMediacore.so(_ZN18sbGStreamerService4InitEv+0xacc)[0x7f4f7f64bcb8]
/home/niko/Desktop/Songbird64/lib/sbGStreamerMediacore.so[0x7f4f7f652de9]
/home/niko/Desktop/Songbird64/xulrunner/libxul.so[0x7f4f90d99e7f]
/home/niko/Desktop/Songbird64/xulrunner/libxul.so[0x7f4f90d999c9]
/home/niko/Desktop/Songbird64/lib/sbGStreamerMediacore.so[0x7f4f7f65866b]
/home/niko/Desktop/Songbird64/lib/sbGStreamerMediacore.so[0x7f4f7f658698]
/home/niko/Desktop/Songbird64/lib/sbGStreamerMediacore.so[0x7f4f7f657e80]
/home/niko/Desktop/Songbird64/lib/sbGStreamerMediacore.so[0x7f4f7f651aaa]
/home/niko/Desktop/Songbird64/lib/sbGStreamerMediacore.so(_ZN27sbGStreamerMediacoreFactory4InitEv+0x4b)[0x7f4f7f652039]
/home/niko/Desktop/Songbird64/lib/sbGStreamerMediacore.so[0x7f4f7f652d59]
/home/niko/Desktop/Songbird64/xulrunner/libxul.so[0x7f4f90d99e7f]
/home/niko/Desktop/Songbird64/components/sbMediacoreManager.so[0x7f4f837d9a9f]
/home/niko/Desktop/Songbird64/components/sbMediacoreManager.so[0x7f4f837d9adc]
/home/niko/Desktop/Songbird64/components/sbMediacoreManager.so[0x7f4f837d93be]
/home/niko/Desktop/Songbird64/components/sbMediacoreManager.so(_ZN8nsCOMPtrI19sbIMediacoreFactoryEC1ERK15nsCOMPtr_helper+0x1c)[0x7f4f837c5a24]
/home/niko/Desktop/Songbird64/components/sbMediacoreManager.so(_ZN18sbMediacoreManager4InitEv+0x1ff)[0x7f4f837c39cb]
/home/niko/Desktop/Songbird64/components/sbMediacoreManager.so[0x7f4f837c3da0]
/home/niko/Desktop/Songbird64/xulrunner/libxul.so[0x7f4f90d7a79a]
/home/niko/Desktop/Songbird64/xulrunner/libxul.so[0x7f4f90d7ac6c]
/home/niko/Desktop/Songbird64/xulrunner/libxul.so[0x7f4f9064fc76]
/home/niko/Desktop/Songbird64/xulrunner/libxul.so(XRE_main+0x177d)[0x7f4f9064d947]
././songbird-bin[0x401417]
/lib/libc.so.6(__libc_start_main+0xe6)[0x7f4f92ee7466]
././songbird-bin[0x401009]
======= Memory map: ========
00400000-00408000 r-xp 00000000 08:05 3228394 /home/niko/Desktop/Songbird64/songbird-bin
00608000-00609000 rw-p 00008000 08:05 3228394 /home/niko/Desktop/Songbird64/songbird-bin
0166d000-0168e000 rw-p 0166d000 00:00 0 [heap]
4001b000-4001c000 ---p 4001b000 00:00 0
4001c000-4081c000 rwxp 4001c000 00:00 0
40c61000-40c62000 ---p 40c61000 00:00 0
40c62000-41462000 rwxp 40c62000 00:00 0
7f4f6da6f000-7f4f6da70000 r-xp 00000000 08:05 132360 /usr/lib/tls/libnvidia-tls.so.180.11
7f4f6da70000-7f4f6db70000 ---p 00001000 08:05 132360 /usr/lib/tls/libnvidia-tls.so.180.11
7f4f6db70000-7f4f6db71000 rw-p 00001000 08:05 132360 /usr/lib/tls/libnvidia-tls.so.180.11
7f4f6f435000-7f4f6f472000 r-xp 00000000 08:05 101854 /usr/lib/libvisual-0.4.so.0.0.0
7f4f6f472000-7f4f6f671000 ---p 0003d000 08:05 101854 /usr/lib/libvisual-0.4.so.0.0.0
7f4f6f671000-7f4f6f672000 r--p 0003c000 08:05 101854 /usr/lib/libvisual-0.4.so.0.0.0
7f4f6f672000-7f4f6f673000 rw-p 0003d000 08:05 101854 /usr/lib/libvisual-0.4.so.0.0.0
7f4f6f673000-7f4f6f679000 r-xp 00000000 08:05 115389 /usr/lib/gstreamer-0.10/libgstlibvisual.so
7f4f6f679000-7f4f6f878000 ---p 00006000 08:05 115389 /usr/lib/gstreamer-0.10/libgstlibvisual.so
7f4f6f878000-7f4f6f879000 r--p 00005000 08:05 115389 /usr/lib/gstreamer-0.10/libgstlibvisual.so
7f4f6f879000-7f4f6f87a000 rw-p 00006000 08:05 115389 /usr/lib/gstreamer-0.10/libgstlibvisual.so
7f4f6f87a000-7f4f6f880000 r-xp 00000000 08:05 115368 /usr/lib/gstreamer-0.10/libgstcdxaparse.so
7f4f6f880000-7f4f6fa7f000 ---p 00006000 08:05 115368 /usr/lib/gstreamer-0.10/libgstcdxaparse.so
7f4f6fa7f000-7f4f6fa80000 r--p 00005000 08:05 115368 /usr/lib/gstreamer-0.10/libgstcdxaparse.so
7f4f6fa80000-7f4f6fa81000 rw-p 00006000 08:05 115368 /usr/lib/gstreamer-0.10/libgstcdxaparse.so
7f4f6fa81000-7f4f6fa8d000 r-xp 00000000 08:05 115443 /usr/lib/gstreamer-0.10/libgstpango.so
7f4f6fa8d000-7f4f6fc8d000 ---p 0000c000 08:05 115443 /usr/lib/gstreamer-0.10/libgstpango.so
7f4f6fc8d000-7f4f6fc8e000 r--p 0000c000 08:05 115443 /usr/lib/gstreamer-0.10/libgstpango.so
7f4f6fc8e000-7f4f6fc8f000 rw-p 0000d000 08:05 115443 /usr/lib/gstreamer-0.10/libgstpango.so
7f4f6fc8f000-7f4f6fc97000 r-xp 00000000 08:05 115466 /usr/lib/gstreamer-0.10/libgstcairo.so
7f4f6fc97000-7f4f6fe96000 ---p 00008000 08:05 115466 /usr/lib/gstreamer-0.10/libgstcairo.so
7f4f6fe96000-7f4f6fe97000 r--p 00007000 08:05 115466 /usr/lib/gstreamer-0.10/libgstcairo.so
7f4f6fe97000-7f4f6fe98000 rw-p 00008000 08:05 115466 /usr/lib/gstreamer-0.10/libgstcairo.so
7f4f6fe98000-7f4f6fe9b000 r-xp 00000000 08:05 115432 /usr/lib/gstreamer-0.10/libgstfreeze.so
7f4f6fe9b000-7f4f7009a000 ---p 00003000 08:05 115432 /usr/lib/gstreamer-0.10/libgstfreeze.so
7f4f7009a000-7f4f7009b000 r--p 00002000 08:05 115432 /usr/lib/gstreamer-0.10/libgstfreeze.so
7f4f7009b000-7f4f7009c000 rw-p 00003000 08:05 115432 /usr/lib/gstreamer-0.10/libgstfreeze.so
7f4f7009c000-7f4f700b0000 r-xp 00000000 08:05 5570678 /usr/lib/libid3tag.so.0.3.0
7f4f700b0000-7f4f702af000 ---p 00014000 08:05 5570678 /usr/lib/libid3tag.so.0.3.0
7f4f702af000-7f4f702b2000 rw-p 00013000 08:05 5570678 /usr/lib/libid3tag.so.0.3.0
7f4f702b2000-7f4f702d0000 r-xp 00000000 08:05 5570680 /usr/lib/libmad.so.0.2.1
7f4f702d0000-7f4f704cf000 ---p 0001e000 08:05 5570680 /usr/lib/libmad.so.0.2.1
7f4f704cf000-7f4f704d0000 r--p 0001d000 08:05 5570680 /usr/lib/libmad.so.0.2.1
7f4f704d0000-7f4f704d1000 rw-p 0001e000 08:05 5570680 /usr/lib/libmad.so.0.2.1
7f4f704d1000-7f4f704e1000 r-xp 00000000 08:05 115557 /usr/lib/gstreamer-0.10/libgstmad.so
7f4f704e1000-7f4f706e0000 ---p 00010000 08:05 115557 /usr/lib/gstreamer-0.10/libgstmad.so
7f4f706e0000-7f4f706e1000 r--p 0000f000 08:05 115557 /usr/lib/gstreamer-0.10/libgstmad.so
7f4f706e1000-7f4f706e2000 rw-p 00010000 08:05 115557 /usr/lib/gstreamer-0.10/libgstmad.so
7f4f706e2000-7f4f706f1000 r-xp 00000000 08:05 2572325 /lib/libbz2.so.1.0.4
7f4f706f1000-7f4f708f1000 ---p 0000f000 08:05 2572325 /lib/libbz2.so.1.0.4
7f4f708f1000-7f4f708f2000 r--p 0000f000 08:05 2572325 /lib/libbz2.so.1.0.4
7f4f708f2000-7f4f708f3000 rw-p 00010000 08:05 2572325 /lib/libbz2.so.1.0.4
7f4f708f3000-7f4f708f8000 r-xp 00000000 08:05 115366 Could not initialize GStreamer: Error re-scanning registry , child terminated by signal
```

---

### Post by nikoboxxx on 2009-03-15
Found this thread: [@Getsatisfaction]("http://getsatisfaction.com/songbird/topics/glibc_2_8_detects_invalid_free_pointer")

The workaround suggested involved removing this package: libvisual-0.4-plugins

Working for now.. lets see if this interferes with anything else.  Does anyone know of any potential issues/conflicts with removing that package?

---

### Post by buehldot on 2009-04-01
Weird... I can confirm that the above fix (uninstalling libvisual-0.4-plugins) works for me.

---

### Post by JustAboutRealJAR on 2009-04-10
removing libvisual-0.4-plugins fixed the problem for me too :)

---

### Post by dennypayne on 2009-04-12
I can confirm this worked for me as well.  Has anybody found anything that removing libvisual-0.4-plugins has broken?

Denny

---

### Post by trigoman05 on 2009-04-15
I can also confirm that removing libvisual-0.4-plugins fixed the error. I have no idea if that'll break anything else but will report back if I see anything abnormal.

Thanks!

---

### Post by amr2205 on 2009-04-19
> **nikoboxxx said:**
> Found this thread: [@Getsatisfaction]("http://getsatisfaction.com/songbird/topics/glibc_2_8_detects_invalid_free_pointer")

The workaround suggested involved removing this package: libvisual-0.4-plugins

Working for now.. lets see if this interferes with anything else.  Does anyone know of any potential issues/conflicts with removing that package?

Yeap, it worked for me too, thanks! ;)

---

### Post by itisthus on 2009-07-01
I too can confirm that the removal of libvisual-0.4-plugins enabled Songbird to work.

After updating to 1.2, running Songbird from the terminal returned an error:
...
Could not initialize GStreamer: Error re-scanning registry , child terminated by signal

That is now fixed with the suggested work around, but I will update if I find any dependency issues.

Thanks.

---

### Post by vasiauvi on 2009-08-30
> **itisthus said:**
> I too can confirm that the removal of libvisual-0.4-plugins enabled Songbird to work.

After updating to 1.2, running Songbird from the terminal returned an error:
...
Could not initialize GStreamer: Error re-scanning registry , child terminated by signal

That is now fixed with the suggested work around, but I will update if I find any dependency issues.

Thanks.

Unfortunately for me didn't worked!:(

---

### Post by DGortze380 on 2009-08-31
Just an update .. nothing teribly useful, but removing libvisual-0.4-plugins also worked for me on 9.04 64-bit.

---

### Post by Rubadubdub on 2009-09-24
For me just removing libvisual-0.4-plugins was not enough.

I also had to remove all libgst*.so files from the /songbird/lib directory.

After removing these files songbird uses the installed lib files from ubuntu not his own. And then it worked, :)

---

### Post by draconid on 2009-10-18
Confirming that I too needed to remove all the libgst* files - this on Ubuntu 9.10. (libvisual-0.4-plugins wasn't even installed for me)

---

### Post by haghdoost on 2009-10-21
I can NOT confirm that removing lib libvisual-0.4-plugins works for me, I have Installed Songbird .Deb package (from getDeb.com), so I don't know the exact path of libgst*.so in my Filesystem.
Do you where is the exact path of libgst that I should remove them ?

Note that I have Nvidia Geforece 7300 graphic card.

---

### Post by DGortze380 on 2009-10-21
> **haghdoost said:**
> I can NOT confirm that removing lib libvisual-0.4-plugins works for me, I have Installed Songbird .Deb package (from getDeb.com), so I don't know the exact path of libgst*.so in my Filesystem.
Do you where is the exact path of libgst that I should remove them ?

Note that I have Nvidia Geforece 7300 graphic card.

Remove via Synaptic Package Manager

---

### Post by MohanaRao on 2009-11-22
Not sure, it works if we install by following the below link
[http://www.getdeb.net/app/Songbird](http://www.getdeb.net/app/Songbird)

Even I faced the same issue trying to install with *.tar.gz file.

---

### Post by kalandraka on 2009-12-17
> **Rubadubdub said:**
> For me just removing libvisual-0.4-plugins was not enough.

I also had to remove all libgst*.so files from the /songbird/lib directory.

After removing these files songbird uses the installed lib files from ubuntu not his own. And then it worked, :)

I simply removed all libgst*.so from /songbird/lib... without uninstalling libvisual... and worked for me!!

:guitar::lolflag:

---

### Post by RRN on 2009-12-20
> **nikoboxxx said:**
> I am on Intrepid 64-bit...

I want to use songbird.  I downloaded the x86_64 version and was having issues starting the program.  It would either hang or give me an error relating to not being able to initialize gstreamer (Could not initialize GStreamer: Error re-scanning registry , child terminated by signal).  I decided to remove some gstreamer packages in hopes of getting songbird to run and was successful.  After removing gstreamer0.10-plugins-base, songbird fired right up.

The issue is that now other programs that rely on that package have been removed.  Brasero, Rhythmbox, and Sound Recorder are all gone.  I can live without the last two, but I want Brasero back.  Of course, installing brasero meant installing gstreamer0.10-plugins-base which meant.. no songbird.

I'm stuck.  I guess what I really need is a way to run songbird without deleting the plugins-base.  If I boot from a LiveCD, 64-bit, it works just fine.  I am currently resorting to running the 32bit version on the 64-bit OS.

Help please :)
I have tried your fix and it did not work for me. I removed the libvisual-0.4 plugins using sudo apt-get autoremove to no avail. The reason I wanted Songbird was that it will read my MP3player while Rhythmbox will not.

the errors I get are when I launch in terminal are;

robert@robert-desktop:/usr/share/Songbird$ ./songbird

(songbird-bin:2562): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstrawparse.so': /usr/lib64/gstreamer-0.10/libgstrawparse.so: undefined symbol: gst_video_format_new_caps_interlaced

(songbird-bin:2562): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstdv.so': /usr/lib64/gstreamer-0.10/libgstdv.so: undefined symbol: gst_tag_list_new_full
././songbird-bin: symbol lookup error: /usr/lib/python2.6/dist-packages/gst-0.10/gst/_gst.so: undefined symbol: gst_task_pool_get_type
Could not initialize GStreamer: Error re-scanning registry , child terminated by signal
robert@robert-desktop:/usr/share/Songbird$

Any suggestions would be appreciated.

---

### Post by PAStheLoD on 2009-12-21
Removing songbirds's own GStreamer .so files fixed it for me.

I am currently on 9.10. And I think the libvisual thing is misleading, because the real cause it just the system GStreamer library conflicting with the ones distributed/packaged with Songbird. And because gstreamer0.10-plugins depends on libvisual, by removing libvisual probably most of you also removed the system-wide gstreamer. And a lot of stuff (pidgin for example) that depends on libvisual.

---

### Post by DGortze380 on 2009-12-21
> **PAStheLoD said:**
>  And because gstreamer0.10-plugins depends on libvisual, by removing libvisual probably most of you also removed the system-wide gstreamer. And a lot of stuff (pidgin for example) that depends on libvisual.

Not on my machine it didn't.

---

### Post by CJay554 on 2010-01-02
confirmation: libgst*.so removal fixed same problem on 32-bit Ubuntu 9.10.
I still have libvisual-0.4-plugins installed.

---

### Post by oooh on 2010-01-20
I have no libvisual plugins to uninstall

Maybe the .SO removal works , I will try

This is the error that I get by the way ...

(songbird-bin:2421): GLib-WARNING **: g_set_prgname() called multiple times
Bus error

---

### Post by song.gao on 2010-01-28
> **Rubadubdub said:**
> For me just removing libvisual-0.4-plugins was not enough.

I also had to remove all libgst*.so files from the /songbird/lib directory.

After removing these files songbird uses the installed lib files from ubuntu not his own. And then it worked, :)

this works for me too. thanks.

i'm on a Ubuntu 9.10 amd64

---

### Post by nrayever on 2010-02-03
Hi guys:

i'm kind of having the same issue. i will check on songbird bugsite for some more information. i got to work songbird, just removing the libgstreamer-0.10.so from the ~/songbird/lib 

Hope this info helps someone else.

nrayever

---

### Post by nebcanuck on 2010-02-22
I've been experiencing a similar issue, and cannot resolve it based on the answers given above, for the same reason as haghdoost. I am using the getdeb binary through the respository, and thus have no /songbird/lib file to remove gst files from.

This is my output when I run Songbird:

```
(songbird-bin:8606): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstsiren.so': /usr/lib64/gstreamer-0.10/libgstsiren.so: undefined symbol: gst_adapter_prev_timestamp

(songbird-bin:8606): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstfaad.so': /usr/lib64/gstreamer-0.10/libgstfaad.so: undefined symbol: gst_util_uint64_scale_round

(songbird-bin:8606): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstshout2.so': /usr/lib64/gstreamer-0.10/libgstshout2.so: undefined symbol: gst_poll_new_timer

(songbird-bin:8606): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstlibvisual.so': /usr/lib64/gstreamer-0.10/libgstlibvisual.so: undefined symbol: gst_adapter_prev_timestamp

(songbird-bin:8606): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstwavpack.so': /usr/lib64/gstreamer-0.10/libgstwavpack.so: undefined symbol: gst_util_uint64_scale_round

(songbird-bin:8606): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstmatroska.so': /usr/lib64/gstreamer-0.10/libgstmatroska.so: undefined symbol: gst_util_array_binary_search

(songbird-bin:8606): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstdv.so': /usr/lib64/gstreamer-0.10/libgstdv.so: undefined symbol: gst_tag_list_new_full

(songbird-bin:8606): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstspeex.so': /usr/lib64/gstreamer-0.10/libgstspeex.so: undefined symbol: gst_util_uint64_scale_round

(songbird-bin:8606): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstmpegdemux.so': /usr/lib64/gstreamer-0.10/libgstmpegdemux.so: undefined symbol: gst_structure_id_get

(songbird-bin:8606): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstffmpegcolorspace.so': /usr/lib64/gstreamer-0.10/libgstffmpegcolorspace.so: undefined symbol: _gst_debug_get_category

(songbird-bin:8606): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstrawparse.so': /usr/lib64/gstreamer-0.10/libgstrawparse.so: undefined symbol: gst_video_format_new_caps_interlaced

(songbird-bin:8606): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgsthdvparse.so': /usr/lib64/gstreamer-0.10/libgsthdvparse.so: undefined symbol: _gst_debug_dump_mem

(songbird-bin:8606): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstcelt.so': /usr/lib64/gstreamer-0.10/libgstcelt.so: undefined symbol: gst_util_uint64_scale_round

(songbird-bin:8606): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstapp.so': /usr/lib/libgstapp-0.10.so.0: undefined symbol: gst_buffer_list_get_type

(songbird-bin:8606): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstsubparse.so': /usr/lib64/gstreamer-0.10/libgstsubparse.so: undefined symbol: gst_util_double_to_fraction

(songbird-bin:8606): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstschro.so': /usr/lib64/gstreamer-0.10/libgstschro.so: undefined symbol: gst_adapter_masked_scan_uint32

(songbird-bin:8606): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgsth264parse.so': /usr/lib64/gstreamer-0.10/libgsth264parse.so: undefined symbol: gst_adapter_prev_timestamp

(songbird-bin:8606): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstjpeg.so': /usr/lib64/gstreamer-0.10/libgstjpeg.so: undefined symbol: _gst_debug_get_category

(songbird-bin:8606): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstavi.so': /usr/lib64/gstreamer-0.10/libgstavi.so: undefined symbol: _gst_debug_dump_mem

(songbird-bin:8606): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstvideo4linux2.so': /usr/lib64/gstreamer-0.10/libgstvideo4linux2.so: undefined symbol: _gst_debug_get_category

(songbird-bin:8606): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstdeinterlace.so': /usr/lib64/gstreamer-0.10/libgstdeinterlace.so: undefined symbol: gst_video_event_parse_still_frame

(songbird-bin:8606): GStreamer-WARNING **: invalid name template bwf_audio_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:8606): GStreamer-WARNING **: invalid name template alaw_audio_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:8606): GStreamer-WARNING **: invalid name template dv_dif_video_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:8606): GStreamer-WARNING **: invalid name template jpeg2000_video_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:8606): GStreamer-WARNING **: invalid name template mpeg_audio_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:8606): GStreamer-WARNING **: invalid name template mpeg_video_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:8606): GStreamer-WARNING **: invalid name template up_video_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:8606): GStreamer-WARNING **: invalid name template vc3_video_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:8606): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libresindvd.so': /usr/lib64/gstreamer-0.10/libresindvd.so: undefined symbol: gst_navigation_event_parse_command

(songbird-bin:8606): GStreamer-WARNING **: Failed to load plugin '/usr/lib64/gstreamer-0.10/libgstofa.so': /usr/lib64/gstreamer-0.10/libgstofa.so: undefined symbol: gst_util_uint64_scale_round

(songbird-bin:8602): Gdk-WARNING **: gdk_window_set_icon_list: icons too large

(songbird-bin:8602): Gdk-WARNING **: gdk_window_set_icon_list: icons too large

(songbird-bin:8602): Gdk-WARNING **: gdk_window_set_icon_list: icons too large

(songbird-bin:8602): Gdk-WARNING **: gdk_window_set_icon_list: icons too large
bt_audio_service_open: connect() failed: Connection refused (111)

```

Any help would be appreciated.Banshee and VLC both play my files properly, but I really prefer Songbird.

---

### Post by JoelOl75 on 2010-03-06
The "proper" workaround in my opinion:

If you installed by downloading the .tar.gz universal linux package, extract the contents and copy the Songbird directory to /opt so your binary would be located at /opt/Songbird/songbird

Now add in a launcher for it in your main menu (System > Preferences > Amin Menu) Add a new entry in your Sound & Video Subcategory for songbird, also set the songbird icon to /opt/Songbird/songbird-512.png

For the command add this verbatim:

sh -c "export SB_GST_NO_SYSTEM=1 ; exec /opt/Songbird/songbird"

If you used an actual .deb package most of this work should've been done for you, just edit the main menu entry and select the proper path for the executable (My guess would be /usr/bin/songbird? so it would look like:

sh -c "export SB_GST_NO_SYSTEM=1 ; exec /usr/bin/songbird"

Just make sure the path is right...

No packages to remove or rename which can cause problems with other packages and with updating, ect.... No kludges.  An explanation is that setting the environmental variable for songbird only tells it to ONLY use the plugins that come with it and not attempt to use the Systems GStreamer plugins which is causing the problems on x86_64 bit systems it seems.

Hope this helps, and you can re-install your libvisual-0.4-plugins package if you wish.

---

### Post by oooh on 2010-03-07
That does not work for me, I still get the error:

(songbird-bin:2824): GLib-WARNING **: g_set_prgname() called multiple times
Bus error

When I do:

$ sh -c "export SB_GST_NO_SYSTEM=1 ; exec /usr/bin/songbird"

In a terminal

---

### Post by dalesd on 2010-03-12
I had the same problem with Songbird.  The SB_GST_NO_SYSTEM=1 environment variable fixes it for me.  It seems the problem is related to gstreamer-ugly plugins.

If SB_GST_NO_SYSTEM=1 fixes this for you, please vote for this bug to get fixed:
[http://bugzilla.songbirdnest.com/show_bug.cgi?id=20314](http://bugzilla.songbirdnest.com/show_bug.cgi?id=20314)

---

### Post by Yellow Pasque on 2010-03-12
You could always try the latest gstreamer release: [https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

---

### Post by redraven on 2010-04-21
For me it seems like songbird comes with it's own set of gstream libraries located in the lib folder. I renamed this foler to bac_lib and songbird started. 

I assume the problem were that the libraries in this directory was conflicting with the ubuntu 9.01 gstream libraries, ie. old versions or something. 

Right now I still need to test songbrid a bit to check if it's stable.:!:

---

### Post by lidex on 2010-04-21
FYI: Songbird developers dropped major support for Linux recently. Looks like a new fork called Nightingale (for Linux) has begun but it may be awhile before their first release.

[http://getnightingale.org/]("http://getnightingale.org/")

---

### Post by James78 on 2010-05-01
> **lidex said:**
> FYI: Songbird developers dropped major support for Linux recently. Looks like a new fork called Nightingale (for Linux) has begun but it may be awhile before their first release.

[http://getnightingale.org/]("http://getnightingale.org/")

Really? I didn't know that. Thx for the info.

I installed the latest from getdeb.net, tried everything, nothing worked.

Went into the /Songbird/lib and moved all libgst*.so, and bam works like a charm!

I'm on Ubuntu 10.04 lucid (using KDE atm)

---

### Post by lidex on 2010-05-01
> **James78 said:**
> Really? I didn't know that. Thx for the info.

I installed the latest from getdeb.net, tried everything, nothing worked.

Went into the /Songbird/lib and moved all libgst*.so, and bam works like a charm!

I'm on Ubuntu 10.04 lucid (using KDE atm)

Yeah. I didn't really like it when I tried it, but it's been awhile. Couldn't believe it when I heard about the dropping of linux support though. Seems like a good fit for a lot of folks and, you know, it just kinda sucks to see software developers abandoning linux users like that.

---

### Post by itsjustarumour on 2011-11-10
Just downloaded the Songbird 1.10.1 .deb from the GetDeb website, and can confirm it installs fine on both Natty 11.04 and Oneiric 11.10  once all the libgst* files have been removed from the /usr/share/Songbird/lib directory...

:-)

---

### Post by nothingspecial on 2011-11-10
This thread is so old that it has gone moldy.

Closed.

---

