---
title: "mplayer vdpau... how to enable"
date: 2014-02-17
forum: Multimedia Software
---

### Post by ionic77 on 2014-02-17
The following script does not work with Xubuntu 13.1 (Saucy)
```
#!/bin/bash
# file: atsc_play.sh
# play recorded ATSC program selected by file manager
opt=" -vo vdpau -vc ffmpeg12vdpau -quiet -msglevel all=0 "
/usr/bin/mplayer $opt $1
```

Mplayer needs to be compiled with --enable-vdpau.. what is the easy way to set that up on my Zotac ION230 which has Nvidia GPU?
The cpu is overloaded without vdpau.

---

### Post by monkeybrain20122 on 2014-02-17
Did you install libvdpau1 and vdpau-driver-va?

I use Smplayer as a gui for mplayer, just set video output to vdpau and that's it.

---

### Post by andrew.46 on 2014-02-18
It would be useful to see the full error message that MPlayer gives when it fails? As a troubleshooting tip perhaps eliminate the vdpau options (-vo vdpau -vc ffmpeg12vdpau) in the script and see if you at least get playback

**Edit: **I see after rereading your post you may have already tried this...

---

### Post by SeijiSensei on 2014-02-19
> **monkeybrain20122 said:**
> I use Smplayer as a gui for mplayer, just set video output to vdpau and that's it.

+100 for SMPlayer.  Who wants to spend all that time typing command-line parameters for every video?  On an NVIDIA machine, I just install the proprietary drivers using "sudo apt-get install nvidia-current".  The VDPAU functionality is included by default.  Then in SMPlayer, I just select vdpau from the list of video drivers, and it all works.

Here's the mplayer command that SMPlayer generated when I watched a 720p video in H.264:
```
/usr/bin/mplayer -noquiet -nofs -nomouseinput -lavdopts threads=4 -sub-fuzziness 1 -identify -slave -vo xv -ao pulse -nokeepaspect -nodr -double -input nodefault-bindings:conf=/dev/null -stop-xscreensaver -wid 39846104 -monitorpixelaspect 1 -ass -embeddedfonts -ass-line-spacing 0 -ass-font-scale 1 -ass-styles /home/seiji/.config/smplayer/styles.ass -font Arial -subfont-autoscale 0 -subfont-text-scale 20 -subcp ISO-8859-1 -subpos 100 -volume 48 -cache 10240 -osdlevel 0 -vf-add screenshot -noslices -channels 6 -af scaletempo,equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 110 /path/to/some/video.mkv

```
I'm happy to let the program do that job!  This machine has no NVIDIA card, so I'm using the standard "xv" driver.  If I were on my NVIDIA machine it would read "-vo vdpau".

---

### Post by monkeybrain20122 on 2014-02-19
> **SeijiSensei said:**
> +100 for SMPlayer.  Who wants to spend all that time typing command-line parameters for every video?  On an NVIDIA machine, I just install the proprietary drivers using "sudo apt-get install nvidia-current".  The VDPAU functionality is included by default.  Then in SMPlayer, I just select vdpau from the list of video drivers, and it all works.


That's why I am sticking to mplayer2 instead of mpv. I absolutely hate watching movies with the cli even though I can if I need it for debugging, it is so 1990's.:P 
When mplayer2 stops working I will just move back to mplayer unless mpv works with smplayer or has a comparable gui (not some minimalist crap you have to start with the terminal)

---

### Post by SeijiSensei on 2014-02-19
rvm says that the differences between mplayer2 and mpv are [sufficiently large]("http://forum.smplayer.info/viewtopic.php?f=2&t=6087") to require a rewriting of SMPlayer.

I use mplayer at the command line to grab segments from a video and write them as PNGs so I can make [animated]("http://forums.animesuki.com/album.php?albumid=115") [avatars]("http://www.takinganimeseriously.com/images/avatars/").

---

### Post by andrew.46 on 2014-02-19
> **monkeybrain20122 said:**
>  I absolutely hate watching movies with the cli even though I can if I need it for debugging, it is so 1990's.

Mind you if you spend some time setting the MPlayer config file things become a lot easier from the commandline...

---

### Post by monkeybrain20122 on 2014-02-19
> **andrew.46 said:**
> Mind you if you spend some time setting the MPlayer config file things become a lot easier from the commandline...

I did. But I still can't see how it would be 'easier' with commandline, whatever you did in the conf file you got to navigate to folder and cut and paste (or type) some usually long and weird file name (movie file) into the terminal and that alone is a major turn off even without any special parameter. :) Of course you can rename it first but again more work. I am also installing *buntu for other people and if I tell them in Linux you have to watch movies with the cli they would think that i am some crazy geek and stick to XP even after it expires. :)

---

### Post by mc4man on 2014-02-20
Any player can be opened from  the context menu & or DnD including mplayer & mpv
(for local files I prefer mpv thru a .desktop  with  Osc.

---

