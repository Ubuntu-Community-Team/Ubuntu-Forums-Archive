---
title: "VLC Crashes"
date: 2009-12-08
forum: Multimedia Software
---

### Post by babthooka on 2009-12-08
Running Ubuntu 9.10. A couple of weeks old installation. I've not installed stuff that's not in the repositories. I did also follow the sticky comprehensive multimedia thread and installed *all of it* (of course only the stuff that applies for my gnome desktop).

My computer should be powerful enough, with core 2 quad, and nVidia GTS250 + lots of RAM and HD.

VLC crashes as soon as it starts up. I've tried with 1080p mkv video file, and I've also tried with a normal DVD. It crashes as soon as it starts playing back. I can start it from the Applications menu, though, if I don't start playing anything, but as soon as I load a video file, it crashes :s

Mplayer works more or less, but (I've only tried HD mkv movie here) it starts playing back badly after a few minutes of playing. Starts fine, but then the frame rate starts deteriorating, and ends up sucking a lot... Completely unwatchable. Maybe this is related?

Can any1 help?

Thx!
Bab

---

### Post by babthooka on 2009-12-08
Updating? Hmm... I keep Ubuntu updated. I imagine it updates VLC along. I keep the latest version available in the repositories. Surely, this can not be the problem?

---

### Post by alexfish on 2009-12-08
Hi 

from VLC  Set the preferences to Default

Or from the terminal

''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''

Code:


[I]vlc --reset-config --reset-plugins-cache 

'''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
 [/I]

---

### Post by babthooka on 2009-12-08
Your suggestion showed the path to salvation, Alexfish. Though it didn't work, running VLC from a terminal (and reading the errors) allowed me to keep digging, leading me to:

[http://ubuntuforums.org/archive/index.php/t-1232781.html](http://ubuntuforums.org/archive/index.php/t-1232781.html)

So, video must not be embedded, or crap happens.. Nags me though that it doesn't work out of the box, since I install from Ubuntu. Am I the only one??

And why does Mplayer mess up the playback after a few minutes? Is it just a crappy player?

Anyways, thx for helping me resolve this issue! :D

Bab

---

### Post by alexfish on 2009-12-08
> **babthooka said:**
> Your suggestion showed the path to salvation, Alexfish. Though it didn't work, running VLC from a terminal (and reading the errors) allowed me to keep digging, leading me to:

[http://ubuntuforums.org/archive/index.php/t-1232781.html](http://ubuntuforums.org/archive/index.php/t-1232781.html)

So, video must not be embedded, or crap happens.. Nags me though that it doesn't work out of the box, since I install from Ubuntu. Am I the only one??

And why does Mplayer mess up the playback after a few minutes? Is it just a crappy player?

Anyways, thx for helping me resolve this issue! :D

Bab

Hi 
No your not the only one

depends if it's up grade or Clean install

If its Clean  and are Using Pulse audio then Permisions Have to be set ect
  

 And  VLC Pulse audio plugins have to be installed
   + a few other bits

    same as for movie player

   test out VLC and open up the tools Messages and increase the Verbosity level
  to   2
 Play the DVD  until the menu starts  / then save the file

  and post it here

 I will also check what in movie player / Ref: Plugins etc

---

### Post by babthooka on 2009-12-08
The output of VLC is pasted at the bottom of this post. I am unsure whether VLC has been upgraded during one of the system updates, there's been a couple of those.
I'm not sure I understand the part of Movieplayer you mention in the end of your post, though..

Thx again, m8! :)





 p, li { white-space: pre-wrap; }  [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]adding item `dvd:///dev/sr0' ( dvd:///dev/sr0 )[/COLOR]
 [COLOR=#00008b]*qt4*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]Adding a new MRL to recent ones: dvd:///dev/sr0[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]rebuilding array of current - root Playlist[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]rebuild done - 2 items, index 0[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]processing request item dvd:///dev/sr0 node null skip 0[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]resyncing on dvd:///dev/sr0[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]dvd:///dev/sr0 is at 1[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]starting new item[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]creating new input thread[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]Creating an input for 'dvd:///dev/sr0'[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]thread (input) created at priority 10 (input/input.c:230)[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]thread started[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]using timeshift granularity of 50 MBytes[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]using timeshift path '/tmp'[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]`dvd:///dev/sr0' gives access `dvd' demux `' path `/dev/sr0'[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]creating demux: access='dvd' demux='' path='/dev/sr0'[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]looking for access_demux module: 2 candidates[/COLOR]
 [COLOR=#00008b]*qt4*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]IM: Setting an input[/COLOR]
 [COLOR=#00008b]*qt4*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]Updating the geometry[/COLOR]
 [COLOR=#00008b]*qt4*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]Updating the geometry[/COLOR]
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]trying to go to dvd menu[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]using access_demux module "dvdnav"[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]TIMER module_need() : 300,165 ms - Total 300,165 ms / 1 intvls (Avg 300,165 ms)[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]`dvd:///dev/sr0' successfully opened[/COLOR]
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]DVDNAV_HOP_CHANNEL[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#ff0000]* error: *[/COLOR][COLOR=#000000]ES_OUT_RESET_PCR called[/COLOR]
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]DVDNAV_VTS_CHANGE[/COLOR]
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]     - vtsN=1[/COLOR]
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]     - domain=4[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#ff0000]* error: *[/COLOR][COLOR=#000000]ES_OUT_RESET_PCR called[/COLOR]
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]DVDNAV_CELL_CHANGE[/COLOR]
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]     - cellN=1[/COLOR]
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]     - pgN=1[/COLOR]
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]     - cell_length=43200[/COLOR]
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]     - pg_length=43200[/COLOR]
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]     - pgc_length=43200[/COLOR]
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]     - cell_start=0[/COLOR]
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]     - pg_start=0[/COLOR]
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]DVDNAV_SPU_CLUT_CHANGE[/COLOR]
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]DVDNAV_SPU_STREAM_CHANGE[/COLOR]
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]     - physical_wide=0[/COLOR]
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]     - physical_letterbox=0[/COLOR]
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]     - physical_pan_scan=1[/COLOR]
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]buttonUpdate not done b=1 t=0[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]selecting program id=0[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]looking for decoder module: 31 candidates[/COLOR]
 [COLOR=#00008b]*avcodec*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]libavcodec already initialized[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]using decoder module "spudec"[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]TIMER module_need() : 0,933 ms - Total 0,933 ms / 1 intvls (Avg 0,933 ms)[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]looking for packetizer module: 21 candidates[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]using packetizer module "spudec"[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]TIMER module_need() : 0,220 ms - Total 0,220 ms / 1 intvls (Avg 0,220 ms)[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]thread (decoder) created at priority 0 (input/decoder.c:315)[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]thread started[/COLOR]
 [COLOR=#00008b]*spudec*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]invalid starting packet (size < 4 or pts <=0)[/COLOR]
 [COLOR=#00008b]*spudec*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]spu size: 0, i_pts: 0 i_buffer: 128[/COLOR]
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]DVDNAV_AUDIO_STREAM_CHANGE[/COLOR]
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]     - physical=0[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]Buffering 0%[/COLOR]
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]buttonUpdate 1[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]Buffering 0%[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]looking for decoder module: 31 candidates[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]using decoder module "libmpeg2"[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]TIMER module_need() : 0,486 ms - Total 0,486 ms / 1 intvls (Avg 0,486 ms)[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]thread (decoder) created at priority 0 (input/decoder.c:315)[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]thread started[/COLOR]
 [COLOR=#00008b][/COLOR][COLOR=#00008b]*vdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]buttonUpdate 1[/COLOR]
 [COLOR=#00008b]*libmpeg2*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]720x576 (display 540,576), aspect 768000, sar 0:0, 25.000 fps[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]no usable vout present, spawning one[/COLOR]
 [COLOR=#00008b][/COLOR][COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]idx1=-1(??) idx2=-1(??)[/COLOR]
 [COLOR=#00008b][/COLOR][COLOR=#00008b][/COLOR][COLOR=#00008b][/COLOR][COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]looking for text renderer module: 2 candidates[/COLOR]
 [COLOR=#00008b][/COLOR][COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]DVDNAV_NOP[/COLOR]
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]DVDNAV_WAIT[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]Stream buffering done (112 ms in 18 ms)[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]thread started[/COLOR]
 [COLOR=#00008b]*freetype*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]Building font database...[/COLOR]
 [COLOR=#00008b]*freetype*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]Finished building font database.[/COLOR]
 [COLOR=#00008b]*freetype*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]Took 513 microseconds[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]thread (fontlist builder) created at priority 0 (freetype.c:475)[/COLOR]
 [COLOR=#00008b]*freetype*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]using fontsize: 2[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]using text renderer module "freetype"[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]TIMER module_need() : 4,757 ms - Total 4,757 ms / 1 intvls (Avg 4,757 ms)[/COLOR]
 [COLOR=#00008b]*qt4*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]Updating the geometry[/COLOR]
 [COLOR=#00008b]*qt4*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]Updating the geometry[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]looking for video filter2 module: 20 candidates[/COLOR]
 [COLOR=#00008b]*swscale*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]32x32 chroma: YUVA -> 16x16 chroma: YUVA with scaling using Bicubic (good quality)[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]using video filter2 module "swscale"[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]TIMER module_need() : 0,696 ms - Total 0,696 ms / 1 intvls (Avg 0,696 ms)[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]looking for video filter2 module: 20 candidates[/COLOR]
 [COLOR=#00008b]*yuvp*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]YUVP to YUVA converter[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]using video filter2 module "yuvp"[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]TIMER module_need() : 0,122 ms - Total 0,122 ms / 1 intvls (Avg 0,122 ms)[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]crop: 142,205,97,40, palette forced: 1[/COLOR]
 [COLOR=#00008b][/COLOR][COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]window size: 1024x576[/COLOR]
 [COLOR=#00008b][/COLOR][COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]looking for video output module: 8 candidates[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]thread ended[/COLOR]
 [COLOR=#00008b][/COLOR][COLOR=#00008b]*xvideo*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]adaptor 0, port 280, format 0x32315659 (YV12) planar[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]looking for xwindow module: 3 candidates[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]TIMER module_need() : 0,199 ms - Total 0,199 ms / 1 intvls (Avg 0,199 ms)[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]no "xwindow" window provider available[/COLOR]
 [COLOR=#00008b]*xvideo*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]XShm video extension v1.1 (without pixmaps, opcode: 142)[/COLOR]
 [COLOR=#00008b]*xvideo*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]Window manager supports NetWM[/COLOR]
 [COLOR=#00008b]*xvideo*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]Window manager supports _NET_WM_STATE_FULLSCREEN[/COLOR]
 [COLOR=#00008b]*xvideo*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]Window manager supports _NET_WM_STATE_ABOVE[/COLOR]
 [COLOR=#00008b]*xvideo*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]Window manager supports _NET_WM_STATE_BELOW[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]using video output module "xvideo"[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]TIMER module_need() : 33,023 ms - Total 33,023 ms / 1 intvls (Avg 33,023 ms)[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]Deinterlacing available[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]got 16 direct buffer(s)[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]pic render sz 720x576, of (0,0), vsz 720x576, 4cc I420, ar 16:9, sar 64:45, msk r0x0 g0x0 b0x0[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]pic in sz 720x576, of (0,0), vsz 720x576, 4cc I420, ar 16:9, sar 64:45, msk r0x0 g0x0 b0x0[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]pic out sz 720x576, of (0,0), vsz 720x576, 4cc I420, ar 16:9, sar 64:45, msk r0x0 g0x0 b0x0[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]direct render, mapping render pictures 0-14 to system pictures 1-15[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#008000]* warning: *[/COLOR][COLOR=#000000]dts != current_pts (-247265)[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]End of video preroll[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]Received first picture[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]Decoder buffering done in 112 ms[/COLOR]
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]DVDNAV_STILL_FRAME[/COLOR]
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]     - length=0xff[/COLOR]
 [COLOR=#00008b]*qt4*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]Qt: Entering Fullscreen[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]looking for video blending module: 1 candidate[/COLOR]
 [COLOR=#00008b]*blend*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]chroma: YUVA -> I420[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]using video blending module "blend"[/COLOR]
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]TIMER module_need() : 0,236 ms - Total 0,236 ms / 1 intvls (Avg 0,236 ms)[/COLOR]
 [COLOR=#00008b]*freetype*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]using fontsize: 36[/COLOR]

---

### Post by alexfish on 2009-12-09
Hi

I have added a screen shot of the Ubuntu SoftWare Center Above

   This is a LOT EASIER THAN SEARCHING AROUND SYNAPTIC

SEE HOW GOOD Ubuntu 9.10 is Now

    Search around with Key Words  It's Fun

---

