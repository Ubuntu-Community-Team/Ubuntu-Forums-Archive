---
title: "How to enable hardware mpeg accelaration on a Via Epia?"
date: 2006-03-06
forum: Multimedia &amp; Video
---

### Post by Bazon on 2006-03-06
Hello everyone!

I'm a Linux/Ubuntu (5.10) Newbee running a [Via Epia M 6000 Mainboard](http://www.via.com.tw/en/products/mainboards/mini_itx/epia_m/index.jsp).

I noticed watching videos on this board in Ubuntu is really worse than on Windows (where it makes no problem).

Probably that's because the hardware mpeg accelaration of the CLE266 Chip isn't enabled in the standard Ubuntu installation.

And in fact, I found severall sources about modding this, and I'm really confused which is the right method:

1. [Patching the Kernel](https://wiki.ubuntu.com/ViaEpiaDriHowto) or [getting another Kernel](http://ubuntuforums.org/showthread.php?t=80248).

2. Getting another graphic driver.
(a) [Open Chrome Project](http://openchrome.org/) ([here prepacked for Ubuntu](http://www.openchrome.org/snapshots/ubuntu/)) or 
(b) [Unichrome Project](http://unichrome.sourceforge.net/).

3. Building a videoplayer espacially for my hardware (can't find the links now, maybe add them later...) 


So does anybody have an idea which is the right option???

Thanks,
Bazon

---

### Post by Beej on 2006-03-10
Firstly if you're running the default ubuntu install its likely that you don't have dri enabled. 
As an emergency interim to help prevent you getting disheartend, check out [GeexBox]("http://www.geexbox.org") this is an excellent live disc that boots a basic media player. It is based around a heavily patched version of mplayer under the sun including the chipset on your (and my) board. I found the video image far surpasses anything I achieved on windows where I would always get an slight judder in my picture from time to time. Anyway Its worth a look. Only drawback is it doesn't have DVD menu support.

Now onto the difficult stuff.

Dri (Direct rendering infrastructure? I can't remember) basically allows your CLE266 chip to do the drawing of your graphics etc. You need this enabled before you will be able to look at hardware acceleration for your board.

To see if you have Dri enabled open a terminal and type: glxinfo. Scroll to the top of the output. There should be a line that says "direct rendering: yes" or "direct rendering: no"

If it says no there are a few things you can do

1 Search for a thread by a guy called Tomy. I think He created a script for Hoary, that enables dri. You have to modify it for your kernel.

2. I got dri (and frequenc scaling etc) working on breezy by following a how to on ompiling your own kernel. Think it had for newbies or similar in the title. You need to apply the ck1 patch before comp-iling. I think the howto gave advice on how to do this.

3. Install dapper. Dapper has a new Via driver. To enable I did this. 

Installed the 686 kernel from synaptic.
edited my xorg.conf (sudo gdit /etc/X11/xorg.conf) making my device section look like this.

Section "Device"
	Identifier	"VIA Technologies, Inc. VT8623 [Apollo CLE266] integrated CastleRock graphics"
	Driver		"via"
	BusID		"PCI:1:0:0"
	Option 		"DisableIRQ"
	Option 		"EnableAGPDMA"
EndSection

save and restart x with cntrl+backspace.

You can check whether these have worked by running glxinfo again and checking the output. If you get a yes try installing planet peguin racer from the repos and playing that. Playback should be smooth, but you wont get an astounding FPS.

Your video playback will still be crappy. In windows you probably had to use power dvd or similar to get your hardware acceleration. In linux you will have to patch mpalyer to get the hardware acceleration. This is the bit I have not achieved yet. Partly because I do not use my MII120000 for video playback much. 

The dapper version of mplayer seems to have the xvmc extension( the bit that gives you hardware acceleration)  but mplayer is refusing to work for me at the moment so I have not had chance to see if I can get it working properly, maybe this will be fixed nearer dapper release?!.

 On my board I at the mo I can play some dvds without hardware acceleration but with about 80 - 95% CPU usage. I doubt your CPU would cope.

If you give Geexbox a go you will see that it must be possible. I hope some of this helps. Feel free to message me again. My msn if you need is benjfearnley at hotmail dot com.

Oh, disclaimer if any of this breaks your installation, I will be happy to help you sort it out but please don't be cross with me, I'm not the ost experienced LInux user i've only been at it nearly a year now.

Good luck.

Beej

---

### Post by Bazon on 2006-03-13
Hi Beej, thanks for your answer! :D

[QUOTE=Beej]Firstly if you're running the default ubuntu install its likely that you don't have dri enabled. [/quote]
Oh, meanwhile I patched the kernel, so:

[QUOTE=Beej]Dri (Direct rendering infrastructure? I can't remember) basically allows your CLE266 chip to do the drawing of your graphics etc. You need this enabled before you will be able to look at hardware acceleration for your board.

To see if you have Dri enabled open a terminal and type: glxinfo. Scroll to the top of the output. There should be a line that says "direct rendering: yes" or "direct rendering: no"[/quote]
It says yes! :)
```
$ glxinfo
name of display: :0.0
__driCreateNewScreen_20050727 - succeeded
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method,
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control,
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_swap_control,
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_video_sync,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: VIA Technology
OpenGL renderer string: Mesa DRI CastleRock (CLE266) 20050526
OpenGL version string: 1.2 Mesa 6.3.2
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture,
    GL_ARB_point_parameters, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_mirrored_repeat,
    GL_ARB_transpose_matrix, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_clip_volume_hint, GL_EXT_compiled_vertex_array, GL_EXT_convolution,
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord,
    GL_EXT_histogram, GL_EXT_packed_pixels, GL_EXT_point_parameters,
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture,
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine,
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array,
    GL_APPLE_packed_pixels, GL_IBM_rasterpos_clip,
    GL_IBM_texture_mirrored_repeat, GL_MESA_window_pos, GL_NV_blend_square,
    GL_NV_light_max_exponent, GL_NV_texgen_reflection, GL_OES_read_format,
    GL_SGI_color_matrix, GL_SGI_color_table, GL_SGIS_texture_edge_clamp,
    GL_SGIS_texture_lod
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x22 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x23 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0x2b 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
```


[QUOTE=Beej]If it says no there are a few things you can do[/quote]So i think I can skip these...  ..but on question left:

I don't run Dapper, but my xorg.conf is much simpler:
[QUOTE=Beej3]. Install dapper. Dapper has a new Via driver. To enable I did this. 

Installed the 686 kernel from synaptic.
edited my xorg.conf (sudo gdit /etc/X11/xorg.conf) making my device section look like this.

Section "Device"
	Identifier	"VIA Technologies, Inc. VT8623 [Apollo CLE266] integrated CastleRock graphics"
	Driver		"via"
	BusID		"PCI:1:0:0"
	Option 		"DisableIRQ"
	Option 		"EnableAGPDMA"
EndSection[/quote]
mine is only:
```
Section "Device"
	Identifier	"VIA Technologies, Inc. VT8623 [Apollo CLE266] integrated CastleRock graphics"
	Driver		"via"
	BusID		"PCI:1:0:0"
EndSection
```should I also add these options?

[QUOTE=Beej3]
You can check whether these have worked by running glxinfo again and checking the output. If you get a yes try installing planet peguin racer from the repos and playing that. Playback should be smooth, but you wont get an astounding FPS.[/quote]
It works, but it is not really smooth....  ...but thaat's not so bad for me as long as it has not effect on video playback, I don't play on this hardware.

[QUOTE=Beej3]Your video playback will still be crappy. In windows you probably had to use power dvd or similar to get your hardware acceleration. In linux you will have to patch mpalyer to get the hardware acceleration. This is the bit I have not achieved yet. Partly because I do not use my MII120000 for video playback much. 
[/quote]
Yes, it is crappy. In windows it's no problem at all: I can use viplay, BSPayer, winamp, whatever i want, I got good video playback!
Too bad you don't know about that, but I'll see whether I find this patch version of mplayer...



[QUOTE=Beej3]If you give Geexbox a go you will see that it must be possible. I hope some of this helps.[/quote]
Yes, GeexBox is really amazing, even on my other Via board, the V5000, DivX runs absolutly smooth! 

Thanks for you help.
If anyone alese knows how to get a DivX / Xvid running smooth on my Epia M 6000 and Ubuntu I would be lucky.
(It has to be possible, on windows and in GeexBox it works, too!)

greetings,
Bazon

---

### Post by Beej on 2006-03-13
If Dri is showing yes when running glxinfo I don't think you need to add those 2 lines to your xorg.conf. 

To see whether you have xvmc support for your version of mplayer go to the console and type

"mplayer -vo help"

This should give you a list of all output drivers. If you see it listed you can try

"mplayer -vo -xvmc /locatioinoffile"

If you have any pointers or have any other news/success give me a shout, I'd love to have silky DVD playback within Ubuntu!

I belive you can get xvmc support in xine, and via do there own player based on xine. Something to google?

Any way good to see another Mini-ITX user here on the forums.

Beej

---

### Post by Beej on 2006-03-13
[http://www.epios.net/](http://www.epios.net/)

Don't know whether you've seen this yet. Its a gentoo based distro aming to provde a full working system for epia users. I tried it earlier on in its development. But I don't think Gentoo is for me!

---

### Post by Bazon on 2006-03-13
[QUOTE=Beej][http://www.epios.net/](http://www.epios.net/)

Don't know whether you've seen this yet. Its a gentoo based distro aming to provde a full working system for epia users. I tried it earlier on in its development. But I don't think Gentoo is for me![/QUOTE]
Unfortunatly only for C3 II and not for C3 Samuel 2 which I run.

I got a bit further:

For smooth video playback, it seems neccesary to install the VIA unichrome Pro driver ([page](http://www.viaarena.com/default.aspx?PageID=420&OSID=25&CatID=2580&SubCatID=101) [direct download](http://www.viaarena.com/Driver/p4m800ce-p4m800pro-cn-clexf40063-kernel-src_20051215.zip)). But that will be a hard thing as you need to build it from source!
And the build instructions are only for Fedora Core, including some directories I can't find here in Ubuntu... :(
When I try this, I'll start a new thread which I'll linkt to from here...

And when you have the Via Unichrome Driver installed *(it really doesn't work without, I tried...)*, you can use two specially Epia patched VideoPlayers:

[Via enhanced Xine (VeXP)](https://sourceforge.net/projects/viaexp/) and
[Via patched mplayer (vemp).](http://sourceforge.net/projects/vemp/)

[Here are some interesting informations in a zipped pdf](http://www.viaarena.com/Driver/VIA%20FC3-4%20P4M800CE-Pro-CN400-CLE266%20Kernel%20Source%20IG%20V0.8A.gz) about this, e.g. this performance list which shows improvement by the driver:

```
 Chipset       CLE266               CN400                P4M800 CE
  Video
          -x11   -xv  -vmix11  -x11   -xv -vmix11  -x11      -xv   -vmix11
 Output
   VCD   49.1%  41.3%  31.2%  37.3% 37.2%  34.4%  26.2%     28.0%   26.2%
  DVD    100%   82.4%  17.2%  88.1% 76.1%  14.9%  59.4%     67.7%   15.1%
 MPEG4    N/S    N/S    N/S   100%   100%  89.2%  74.1%*   83.9%*  73.3%*
HD MPEG2  N/S    N/S    N/S   100%   100%  57.3%   N/S       N/S     N/S
```



So if anyone else makes progress with this, please let me know! :)

greetings,
Bazon

---

### Post by Bazon on 2006-03-17
**Finally I also got smooth DivX playback!**

But I'm not sure it is reproduceable... :wink:

But let me tell what I did:

First of all, I installed Fedora Core 4.
Why?

As I said in my last post, [Via enhanced Xine Player](https://sourceforge.net/projects/viaexp/) needs the Unichrome Pro driver from via.

But [via doesn't support Ubuntu or Debain, but Fedora is supported very good.](http://www.viaarena.com/default.aspx?PageID=2&Type=3)

So I gave Fedora core 4 a try.
But even there I didn'd suceed in running VeXP.

So I tried VeMP.
Which worked. :)

The default configuration of MPlayer is without GUI.
That bothered me a bit, so I configured it again to compile gmplayer (mplayer with GUI), too.

But suprise suprise:
The DivX running smooth with mplayer without graphic interface isn't with gmplayer (with graphic interface...)!

Next step:
Tried to do the same in Ubuntu.
Compilation of Via enhanced patched mplayer worked, butI could start it. (It complained about an error in -vo.)

**next and most important step:**
But as I prefer Ubuntu to Fedora *(looks crappy compared to Ubuntu and yum sucks...:wink:)* I tried to make the mplayer working in Ubuntu anyway.

So I copied the compiled version of Fedora in my /usr/local/bin Directory *(it gets installed there by make install and not in /usr/bin, which I don't understand yet, but is a big advantage as I saw later...)* in Ubuntu and it worked! :D

You can try that, too, as I uploaded the [mplayer binary](http://home.arcor.de/bazonbloch/files/linux/mplayer) (which is for me in /usr/local/bin)

[color=#993300][edit][/color]Additionally, you should download some codecs from [here](http://www1.mplayerhq.hu/homepage/design7/codecs.html) and put them in /usr/local/lib/codecs.[color=#993300][/edit][/color]

You can start it by 
```
$ mplayer filename.avi
```or, even better on slow machines, 
```
$ mplayer -framedrop filename.avi
```

[color=#993300][edit][/color]Or of course you can open it with Nautilus by Doubleclick:
Right Click on a movie File, select properties, go to "opene with" and add as custom action *mplayer* or *mplayer -framedrop* and enable it as default action. 

As it is without GUI you may be interested in some [keyboard shortcuts](http://www.mplayerhq.hu/DOCS/man/en/mplayer.1.html#INTERACTIVE%20CONTROL).
(Most important: f: Fullscreen, Cursor:move in Movie...) [color=#993300][/edit][/color]


And here is the story why it is better that the mplayer binary is stored in /usr/local/bin and not in /usr/bin:

Because of this different path, it was possible to install mplayer from Synaptik again!
(Why: Because the binaries *mplayer* and *gmplayer* are stored in /usr/bin and not in /usr/local/bin as the self-made *mplayer*...)
And I really need that so my mozilla-plugin still works!
(For internet clips the normal mplayer was always good enough...)


greetings,
Bazon

---

### Post by Bazon on 2006-03-18
edited my post above:
removed questions (solved now...),
added URL to codecs, and short explaination how to open it with nautilus and link to keyboard shortcuts.

---

### Post by Bazon on 2006-03-27
Meanwhile I found out some other things:

1. The method described ebove definitly doesn't enable mpeg accelaration. DVD is still problematic. :(
2. If you use the posted bin, it's even better to rename it and start it with the other name:
If you use it with the name "mplayer", the mozilla-mplayer looses it's progressbar.
3. I found another Trick to increase video quality on my Epia M 6000 dramaticly:
Turn off the system-monitor! I added that to the panel (because I was used to something similar in windows...) but that seems to use a lot of CPU itself!
*[I accidently found that out as I tried Xubuntu: Video playback better until I added a System-monitor panel to Xubuntu, too...]*
Without the System monitor I'm able to watch nearly all DivX with a videoplayer with GUI, and DVD is also nearly fine (until I switch on subtitles, that makes it dramendosly slower [although subtitles work on the smae machine in windows...:x])

greetings,
Bazon

---

### Post by cjtinant on 2008-03-27
Here is a link to enable DRI as mentioned above
[https://help.ubuntu.com/community/ViaEpiaDriHowto](https://help.ubuntu.com/community/ViaEpiaDriHowto)

---

### Post by steefjeqv on 2008-03-28
Hi Bazon, 

Just noticed you're living in Germany.
Sometimes the best solutions can be found close to home.

Just three letters will give you a great solution : VDR
I've been a happy user of this great piece of software for about a year now.
It basically turns your PC into a settopbox for watching digital TV.

It has a huge (mostly German) userbase and a great forum.

This is a  direct howto link for the epia :

[http://www.vdr-portal.de/board/thread.php?threadid=71591&hilight=via+epia]("http://www.vdr-portal.de/board/thread.php?threadid=71591&hilight=via+epia")

Forum home page :

[http://www.vdr-portal.de/board/portal.php]("http://www.vdr-portal.de/board/portal.php")

Greetings,
Steven

---

