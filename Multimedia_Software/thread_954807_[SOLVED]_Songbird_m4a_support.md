---
title: "[SOLVED] Songbird m4a support?"
date: 2008-10-21
forum: Multimedia Software
---

### Post by owain123 on 2008-10-21
My flatmate has iTunes (Damn him!), and a lot of the music i have got on my computer is from his. 
Im trying to use Songbird, but it wont play m4a's. Is there anyway i can get it to play them?

note: I have installed all restricted codecs, and gstreamer files on my machine.

---

### Post by cozmicharlie on 2008-10-21
this is from the Songbird web site:

"Songbird supports MP3, FLAC, and Vorbis on all platforms; WMA and WMA DRM on Windows; and AAC and Fairplay on Windows and Mac."

It does not look like you can on Linux but reading some posts on the web site gives me the impression it is supported in the recent version.  I don't see why if they can make it work on Mac and Windows they can't on Linux.  Are you sure your friends files are not protected by drm?  Also are you sure they are m4a and not in Apple Lossless?  Apple Lossless is ALAC not AAC.

There is a discussion here ([http://getsatisfaction.com/songbird/topics/problem_switching_to_gstreamer](http://getsatisfaction.com/songbird/topics/problem_switching_to_gstreamer)) that might shed some light - it looks like it will depend on what core you are using.  I am not an expert in Songbird but you should be able find some help on there web site.

---

### Post by owain123 on 2008-10-21
Cheers for the info, turns out they are apple lossless which isn't yet supported.

---

### Post by mc4man on 2008-10-21
If you have songbird 0.7 it should play all m4a files including apple lossless (alac).
see screen
If 0.7 can't play a file then it offers to play back thru a supported player (if possible

---

### Post by chiisana on 2009-09-17
Sorry to bump a year old question.  I had the same problem after a vanilla install of Ubuntu 9.04 and Songbird 1.20.  However, the same file plays fine if I use mplayer to play the file (this helped me verify that the file was not corrupted).  

As it turned out, the problem is because I lacked gstreamer0.10-ffmpeg package.  So all you'd need to do (assuming if you have a relatively recent version of Ubuntu and a relative recent version of Songbird) is use Synaptic and search for gstreamer ffmpeg and install that.

Hope this helps some other lost souls :)

---

### Post by andree_b on 2009-09-21
Had the same problem (9.04+1.2 no m4a playback). Thank you for the solution!

---

### Post by kedmond on 2010-04-12
> **andree_b said:**
> Had the same problem (9.04+1.2 no m4a playback). Thank you for the solution!

Thank you so much.  It took me so long to find this post.  Thanks.  It works!  Yay.  I'm running Ubuntu 9.10, Songbird 1.4.3 (and also 1.80a).

I had to install Gstreamer-0.10-plugins-good/bad/ugly and the multiverse versions of all of those, and FINALLY the gstreamer0.10-ffmpeg package.

All my m4a files work!

---

### Post by andree_b on 2010-05-18
btw. I have to use "SB_GST_SYSTEM=1 songbird" on 10.4 to since mixing system gstreamer plugins and songbirds local ones doesnt work any more. (at least with the binary 1.4.3 that i have installedI)

---

### Post by 1jackjack on 2010-05-23
I already had the gstreamer0.10-ffmpeg package installed, but couldnt play m4a files. It was the SB_GST_SYSTEM=1 tip that fixed it for me. Thanks andree_b!!!

I put it in a little script, which I now use to run songbird flawlessly:

#!/bin/sh
export SB_GST_SYSTEM=1
/usr/local/songbird/songbird

---

### Post by c1k2j3c4 on 2010-05-23
> **1jackjack said:**
> I already had the gstreamer0.10-ffmpeg package installed, but couldnt play m4a files. It was the SB_GST_SYSTEM=1 tip that fixed it for me. Thanks andree_b!!!

I put it in a little script, which I now use to run songbird flawlessly:

#!/bin/sh
export SB_GST_SYSTEM=1
/usr/local/songbird/songbird

Forgive me here, but I'm a linux noob. How did you do that fix.

---

### Post by c1k2j3c4 on 2010-05-23
Ok I think I get how to create the script. However I do not have a /usr/local/songbird folder. I'm using mint 9 and I installed songbird via getdeb.

---

### Post by 1jackjack on 2010-05-24
you can find where your songbird binary is by executing the following command:

whereis songbird

---

### Post by c1k2j3c4 on 2010-05-24
Thanks. I added "export SB_GST_SYSTEM=1" to the existing script and that fixed it.

---

### Post by boglode on 2010-05-27
Hi 

I had the same problem (.m4a-files played under Ubuntu 9.10 and not after upgrading to Ubuntu 10.04 LTS) However I could'nt find the scripts file to put "export SB_GST_SYSTEM=1" in :-) 

I stumbled on an old thread explaining the removal of libgst*-files in the lib-directory of Songbird (in my case /opt/Songbird/lib/) would stop a collision between Ubuntu/OtherLinux versions of Gstreamer* and Songbirds ditto --- VOILA **removing the libgst* files in the Songbirds lib-directory made the .m4a-files play again** :)

/Bo.

---

### Post by hazardcell on 2010-06-01
> **1jackjack said:**
> I already had the gstreamer0.10-ffmpeg package installed, but couldnt play m4a files. It was the SB_GST_SYSTEM=1 tip that fixed it for me. Thanks andree_b!!!

I put it in a little script, which I now use to run songbird flawlessly:

#!/bin/sh
export SB_GST_SYSTEM=1
/usr/local/songbird/songbird

OK noob question...which file do you put this in? I'm running 10.04 if that makes a difference. The songbird directory is /etc/songbird/

---

### Post by 1jackjack on 2010-06-04
i put it in my home bin directory: /home/jack/bin/songbird-fix

then as long as that directory is in your $PATH, which i think it is by default (check by executing: echo $PATH), you should now be able to run the fixed version of songbird by executing: songbird-fix

---

### Post by polzleitner on 2010-07-14
> **c1k2j3c4 said:**
> Forgive me here, but I'm a linux noob. How did you do that fix.

Use any editor (e.g., gedit) in a console window to create a file songbird.sh, maybe on your bin directory: (don't type the $)

$ gedit /home/<your username>/bin/songbird.sh

Type in this one line into the file:
SB_GST_SYSTEM=1 songbird

Save it.

Then change the permissions on this file to make it runnable
$ chmod 755 /home/<your username>/bin/songbird.sh


Right-click the songbird icon on your panel to open the properties window.

In the "Command" field type /home/<your username>/bin/songbird.sh and the properties window.

From now on clicking on the songbird icon will run your script, which sets the value for the variable and starts songbird.

If anything is unclear, please post.

Good luck,
wp

---

### Post by jtsc on 2011-06-09
hi,

I tried what was suggested in this thread (created the script, redirected my songbird shortcut to it). The problem is that the script *doesn't* start Songbird, and when I try to use the other shortcut under "application" it says "no such file or directory."

I can manually run songbird by going into /opt/songbird/songbird, but sadly the M4A's still don't work.

---

### Post by jtsc on 2011-06-09
I also installed faac, as per this thread: [http://ubuntuforums.org/showthread.php?t=1454577](http://ubuntuforums.org/showthread.php?t=1454577)

But it still doesn't work. When I open songbird in terminal, I get this error messages... don't know if this is standard or not:

> (songbird-bin:6395): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstmpegdemux.so': /usr/lib/gstreamer-0.10/libgstmpegdemux.so: undefined symbol: gst_structure_id_get

(songbird-bin:6395): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstfaac.so': /usr/lib/gstreamer-0.10/libgstfaac.so: undefined symbol: gst_util_uint64_scale_round

(songbird-bin:6395): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstwavpack.so': /usr/lib/gstreamer-0.10/libgstwavpack.so: undefined symbol: gst_util_uint64_scale_round

(songbird-bin:6395): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstjpeg.so': /usr/lib/gstreamer-0.10/libgstjpeg.so: undefined symbol: _gst_debug_get_category

(songbird-bin:6395): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstdvdspu.so': /usr/lib/gstreamer-0.10/libgstdvdspu.so: undefined symbol: gst_video_event_parse_still_frame

(songbird-bin:6395): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstshout2.so': /usr/lib/gstreamer-0.10/libgstshout2.so: undefined symbol: gst_poll_new_timer

(songbird-bin:6395): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstaudioparsersbad.so': /usr/lib/gstreamer-0.10/libgstaudioparsersbad.so: undefined symbol: gst_byte_reader_masked_scan_uint32

(songbird-bin:6395): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstvideo4linux2.so': /usr/lib/gstreamer-0.10/libgstvideo4linux2.so: undefined symbol: _gst_debug_get_category

(songbird-bin:6395): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstapp.so': /usr/lib/libgstapp-0.10.so.0: undefined symbol: gst_buffer_list_get_type

(songbird-bin:6395): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstaiff.so': /usr/lib/gstreamer-0.10/libgstaiff.so: undefined symbol: gst_byte_writer_put_uint32_be

(songbird-bin:6395): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstavi.so': /usr/lib/gstreamer-0.10/libgstavi.so: undefined symbol: _gst_debug_dump_mem

(songbird-bin:6395): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstjpegformat.so': /usr/lib/gstreamer-0.10/libgstjpegformat.so: undefined symbol: gst_byte_writer_put_uint8

(songbird-bin:6395): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstdeinterlace.so': /usr/lib/gstreamer-0.10/libgstdeinterlace.so: undefined symbol: gst_video_event_parse_still_frame

(songbird-bin:6395): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstrawparse.so': /usr/lib/gstreamer-0.10/libgstrawparse.so: undefined symbol: gst_video_format_new_caps_interlaced

(songbird-bin:6395): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstlibvisual.so': /usr/lib/gstreamer-0.10/libgstlibvisual.so: undefined symbol: gst_adapter_prev_timestamp

(songbird-bin:6395): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstffmpeg.so': /usr/lib/gstreamer-0.10/libgstffmpeg.so: undefined symbol: gst_adapter_prev_timestamp

(songbird-bin:6395): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstcelt.so': /usr/lib/gstreamer-0.10/libgstcelt.so: undefined symbol: gst_util_uint64_scale_round

(songbird-bin:6395): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstsubparse.so': /usr/lib/gstreamer-0.10/libgstsubparse.so: undefined symbol: gst_util_double_to_fraction

(songbird-bin:6395): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstfaad.so': /usr/lib/gstreamer-0.10/libgstfaad.so: undefined symbol: gst_util_uint64_scale_round

(songbird-bin:6395): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstffmpegcolorspace.so': /usr/lib/gstreamer-0.10/libgstffmpegcolorspace.so: undefined symbol: _gst_debug_get_category

(songbird-bin:6395): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libresindvd.so': /usr/lib/gstreamer-0.10/libresindvd.so: undefined symbol: gst_navigation_event_parse_command

(songbird-bin:6395): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstsiren.so': /usr/lib/gstreamer-0.10/libgstsiren.so: undefined symbol: gst_adapter_prev_timestamp

(songbird-bin:6395): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgsth264parse.so': /usr/lib/gstreamer-0.10/libgsth264parse.so: undefined symbol: gst_adapter_prev_timestamp

(songbird-bin:6395): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstschro.so': /usr/lib/gstreamer-0.10/libgstschro.so: undefined symbol: gst_adapter_masked_scan_uint32

(songbird-bin:6395): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstmatroska.so': /usr/lib/gstreamer-0.10/libgstmatroska.so: undefined symbol: gst_util_array_binary_search

(songbird-bin:6395): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstofa.so': /usr/lib/gstreamer-0.10/libgstofa.so: undefined symbol: gst_util_uint64_scale_round

(songbird-bin:6395): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstqtmux.so': /usr/lib/gstreamer-0.10/libgstqtmux.so: undefined symbol: gst_byte_writer_put_uint32_be

(songbird-bin:6395): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstspeex.so': /usr/lib/gstreamer-0.10/libgstspeex.so: undefined symbol: gst_util_uint64_scale_round

(songbird-bin:6395): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstdv.so': /usr/lib/gstreamer-0.10/libgstdv.so: undefined symbol: gst_tag_list_new_full

(songbird-bin:6395): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgsthdvparse.so': /usr/lib/gstreamer-0.10/libgsthdvparse.so: undefined symbol: _gst_debug_dump_mem

(songbird-bin:6395): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstx264.so': /usr/lib/gstreamer-0.10/libgstx264.so: undefined symbol: _gst_debug_dump_mem

(songbird-bin:6391): Gdk-WARNING **: gdk_window_set_icon_list: icons too large

(songbird-bin:6391): Gdk-WARNING **: gdk_window_set_icon_list: icons too large

(songbird-bin:6391): Gdk-WARNING **: gdk_window_set_icon_list: icons too large

(songbird-bin:6391): Gdk-WARNING **: gdk_window_set_icon_list: icons too large



---

### Post by boglode on 2012-05-31
Just an update: **Ubuntu 12.04 LTS and Songbird 2.1.0a Build 2300 **

Creating a file called songbird.sh
[I]#!/bin/sh
export SB_GST_SYSTEM=1
/opt/Songbird/songbird

[/I]And setting properties to execute (sudo chmod 755 songbird.sh)

Songbird still plays .m4a-files (SB_GST_SYSTEM=1 means that Songbird will use the system plugins instead of its own...)

/Bo.

---

