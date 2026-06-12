---
title: "Whats the best video player in the Software Center?"
date: 2015-01-16
forum: Multimedia Software
---

### Post by kenny18 on 2015-01-16
I have some MP4s I'm watching and there a little laggy.. Im using VLC right now and I was wondering if theres any other player that would be better, or even play a larger range of files?
Any advice is thanked in advanced
-Kenny

---

### Post by TheFu on 2015-01-16
VLC is the best, most fully supported with codecs player that exists.
You can use smplayer if you like. The real issue is likely that the GPU isn't being used for video decoding. What GPU and which drivers are loaded on the machine?

---

### Post by Rob Sayer on 2015-01-16
I like vlc but it's not my default.  Smplayer is.

Actually I disagree that vlc has the best format/codec support.  SMplayer's is better.  It's also much faster and easier to config.  My main issue with vlc is that when v. 2 came out they dropped support for an adjustable local file cache size.  I don't think they've reintroduced it either.  That feature makes a huge performance difference.  *Stupid*.

I *do* agree that the it's probably not vlc per se that's lagging but either a video card that's not set properly in linux or just plain slow hardware.

Need hardware details obviously.

If it's slow hardware all you can do besides reinstalling a version with a lighter DE is try to do some tweaking that won't really make that much difference for video.  Or try Gnome Mplayer from the repos.  It's an mplayer front end like smplayer that's not so full featured but it's quite light and faster.  It's what's installed in lubuntu.

---

### Post by kenny18 on 2015-01-16
IS there a application that can download what drivers I need to maximize my performance

---

### Post by Bucky Ball on 2015-01-16
Please give the details of your graphics card, as requested, so we can see what drivers you need. Do an update and check 'Additional Drivers'. Do you see anything relating to graphics on offer there?

---

### Post by efflandt on 2015-01-17
In a terminal type the following and see what shows for your video which would usually have VGA or possibly 3D in its the first line of that section and show what driver is being used for it in the last line of that section:```
sudo lspci -v
```

---

### Post by monkeybrain20122 on 2015-01-18
None of them is good from the software centre because they are all out of date.Install vlc, Smplayer or mpv from a ppa or compile it from source. 

I agree with Rob Sayer than vlc is not the best player, at least on Linux, it has the most functions but I find Smplayer to be better for playing videos and more efficient in using hardware acceleration , unfortunately mplayer is not upgraded very much and mplayer2 seeems to be unmaintained. mpv is very good, but you may find the gui a bit sparse.

---

### Post by TheFu on 2015-01-18
PPA sure, but avoid installing anything from source. When you do, you've accepted to manually maintain that program forever.  Bad idea, IMHO, especially for someone with limited experience.

Have installed smplayer a few days ago.  Used mplayer for years before VLC was useful and I still use mencoder to transcode non-HiDef videos.  Don't think I'll keep smplayer - no need for a GUI over mplayer here.

---

### Post by SeijiSensei on 2015-01-18
I find it much easier to navigate and use playlists with smplayer.  Beats having to remember all those key assignments in mplayer itself.

I watch anime with smplayer in the MKV container with A** subtitles and usually the H.264 codec.  Works well with dual-audio streams, too.

---

### Post by monkeybrain20122 on 2015-01-18
> **SeijiSensei said:**
> I find it much easier to navigate and use playlists with smplayer.  Beats having to remember all those key assignments in mplayer itself.
.

Couldn't agree more, I don't mind using command lines when needed but it is ridiculous in 2015 to have to remember arcane commands and key assignments just to watch videos. For trouble shooting the players, no doubt useful, but not for using them.

---

### Post by mc4man on 2015-01-18
> **kenny18 said:**
> I have some MP4s I'm watching and there a little laggy.. Im using VLC right now and I was wondering if theres any other player that would be better, or even play a larger range of files?
Any advice is thanked in advanced
-Kenny
Without specific's of what hardware you have, what version of vlc & what type of vids,  your issues with vlc or in general are unknown. Vlc does a lot automatically now depending on version, latest auto picks the video out & hw acel if supported. It's quite possible though that it doesn't use whats best for your hw and  or video source.

(- relatively recent hardware should handle any commonly avail. vids fine with just cpu though gpu can assist, sometimes greatly, if desired.
Ex. - A 100 Mbps AVC file here with cpu only will use about 14% cpu overall, no big deal. With a vo of opengl & hwdec of vaapi then total cpu use will drop to 2% or less.  Either way it's fine.

As far as players mpv is preferred here, usually from the context menu, sometimes cli. As far as frontends currently I have 3 installed for mpv, each has it's pluses  & minuses
- smplayer, cmplayer, baka-mplayer, but generally just use mpv straight up, adjusted thru it's various .config & .conf files

---

### Post by TheFu on 2015-01-18
> **monkeybrain20122 said:**
> Couldn't agree more, I don't mind using command lines when needed but it is ridiculous in 2015 to have to remember arcane commands and key assignments just to watch videos. For trouble shooting the players, no doubt useful, but not for using them.

Guess my viewing needs are trivial ... most of the time, I use XBMC to watch videos on a projector or large monitor/TV.
It is only on travel with a netbook that using mplayer happens. Don't know what arcane key's you are using.  I use the space bar to pause/play, 'f' to toggle full-screen, and the arrow keys to skip forward and back. Seems intuitive to me. Perhaps not.

---

### Post by monkeybrain20122 on 2015-01-18
> **mc4man said:**
> 
As far as players mpv is preferred here, usually from the context menu, sometimes cli. As far as frontends currently I have 3 installed for mpv, each has it's pluses  & minuses
- smplayer, cmplayer, baka-mplayer, but generally just use mpv straight up, adjusted thru it's various .config & .conf files

I didn't know you can use smplayer with mpv.

---

### Post by mc4man on 2015-01-18
> **monkeybrain20122 said:**
> I didn't know you can use smplayer with mpv.
Yeah, it's been added to latest smplayer. It uses the binary it a way not really supported anymore in mpv but works ok.
(- cmplayer uses a built-in static ffmpeg & mpv (libmpv), baka-mplayer uses libmpv (shared) directly.

---

### Post by shantiq on 2015-01-19
again for [MPV]("https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests")    without the shadow of a doubt     i almost never use vlc now   since mpv will be SO stable

from command line     all you need is mpv + whatever you wanna play    but you do not even need that     you can right-click on your video or folder and choose mpv

Hotkeys:

f  = fullscreen
# = toggle audio channels
v = toggle subtitles
s = screenshot dumped in folder video is in

PS:

in ~/.mpv/config    add  ```
--save-position-on-quit
```   and save so your video starts off where you stopped last

---

### Post by SeijiSensei on 2015-01-19
> **TheFu said:**
> Don't know what arcane key's you are using.  I use the space bar to pause/play, 'f' to toggle full-screen, and the arrow keys to skip forward and back. Seems intuitive to me. Perhaps not.
How about choosing a subtitle track?  Changing the size of the text on screen?  Taking screenshots?  Changing the size of video window on the desktop?  All of these are easy in smplayer; otherwise I'm looking at the mplayer man page.

---

### Post by TheFu on 2015-01-19
> **SeijiSensei said:**
> How about choosing a subtitle track?  Changing the size of the text on screen?  Taking screenshots?  Changing the size of video window on the desktop?  All of these are easy in smplayer; otherwise I'm looking at the mplayer man page.

Clearly we have different uses for a video player.  Think I'll look at mpv.
Or just use vlc which isn't an issue on my systems.

---

### Post by monkeybrain20122 on 2015-01-19
The latest upgrade of Smplayer from the rvm ppa indeed works with mpv (and drops support for mplayer2) though it has only basic support since mpv is changing too rapidly. The default lua interface of mpv works well enough for me. It has all the functions I need: toggle to full screen, start, stop, seek, pause, switch subtile and audio, there is no volume button, press 0 for volume up, 9 for volume down, so not quite sure what additional feature I may get out of Smplayer support at this point. I will play with it a bit to find out when I have the time.

There seems to be some interesting development with Smplayer lately [http://blog.smplayer.info/category/mpv/](http://blog.smplayer.info/category/mpv/)

---

### Post by monkeybrain20122 on 2015-01-19
> **shantiq said:**
> again for [MPV]("https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests")    without the shadow of a doubt     i almost never use vlc now   since mpv will be SO stable

from command line     all you need is mpv + whatever you wanna play    but you do not even need that     you can right-click on your video or folder and choose mpv

Hotkeys:

f  = fullscreen
# = toggle audio channels
v = toggle subtitles
s = screenshot dumped in folder video is in

PS:

in ~/.mpv/config    add  ```
--save-position-on-quit
```   and save so your video starts off where you stopped last


A very cool feature of mpv is that you can drag and drop a subtitle file into the video to enable it.

---

### Post by mc4man on 2015-01-19
Inc. with mpv should be a pdf version of the man which is very readable in evince - 
```
evince /usr/share/doc/mpv/mpv.pdf.gz
```
screen, though fullscreen is better

---

### Post by monkeybrain20122 on 2015-01-21
Just want to update you guys that the latest svn version of Smplayer has added vaapi support. It is great news if you use mpv with Intel gpu and want to try out Smplayer as a front end. mpv supports vaapi but Smplayer didn't,---until now  (otherwise you need libvdpau-va-gl and use the vdpau option in Smplayer to get hardware acceleration)
[URL="http://forum.smplayer.info/viewtopic.php?f=2&t=7787"]
http://forum.smplayer.info/viewtopic.php?f=2&t=7787[/URL]

---

### Post by mc4man on 2015-01-21
> **monkeybrain20122 said:**
> Just want to update you guys that the latest svn version of Smplayer has added vaapi support. It is great news if you use mpv with Intel gpu and want to try out Smplayer as a front end. mpv supports vaapi but Smplayer didn't,---until now  (otherwise you need libvdpau-va-gl and use the vdpau option in Smplayer to get hardware acceleration)
[URL="http://forum.smplayer.info/viewtopic.php?f=2&t=7787"]
http://forum.smplayer.info/viewtopic.php?f=2&t=7787[/URL]
Noticed that..
For mpv & mpv in smplayer I use a vo of opengl-hq with --hwdec=vaapi  as I don't want a vo of vaapi with hwdec of vaapi  
 - that combo can produce h tearing on fullscreen with some intel video (Haswell mobile here

---

### Post by VMC on 2015-01-27
I tried using MPV, but the subtitles don't work. They work using VLC. I tried 'v', 'V', and everything else that the man pages suggest. 
Here's the info when it starts. The mkv video works perfectly using VLC.

```
$ mpv --sub-visibility /media/vmc/NTFS/MKV/Gravity.mkvPlaying: /media/vmc/NTFS/MKV/Gravity.mkv
Detected file format: Matroska
Clip info:
 ENCODER: Lavf55.12.0
[stream] Video (+) --vid=1 (h264)
[stream] Audio (+) --aid=1 --alang=eng (*) 'Stereo' (aac)
[stream] Subs      --sid=1 --slang=eng (dvd_subtitle)
[vo/vdpau] Error when calling vdp_device_create_x11: 1
[vo/opengl/x11] X11 error: BadAlloc (insufficient resources for operation)
[vo/opengl] Could not create GL3 context. Retrying with legacy context.
Selected video codec: H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10 [lavc:h264]
Selected audio codec: AAC (Advanced Audio Coding) [lavc:aac]
AO: [alsa] 48000Hz stereo 2ch floatp
VO: [opengl] 718x360 => 852x360 420p
AV: 00:02:09 / 01:30:59 (2%) A-V:  0.000
Exiting... (Quit)
```

As you can see, MPV finds subtitles per output above: "[stream] Subs      --sid=1 --slang=eng (dvd_subtitle)". It just does not display them.

---

### Post by SeijiSensei on 2015-01-28
It found them, but you didn't invoke them.  Try adding --sid=1 to the command line.

---

### Post by mc4man on 2015-01-28
A player in progress based on mpv is bomi (formerly cmplayer
ppa here for 14.04/14.10 - [https://launchpad.net/~darklin20/+archive/ubuntu/bomi](https://launchpad.net/~darklin20/+archive/ubuntu/bomi)
It differs in many ways from baka-mplayer, one significant is it's fairly self contained where as baka needs libmpv
(menus are in the window > r. click

---

### Post by VMC on 2015-01-28
> **SeijiSensei said:**
> It found them, but you didn't invoke them.  Try adding --sid=1 to the command line.
That did it. Thank you! I read the man pages (or tried too). goggling mpv helps, tutorial, etc didn't reveal that info.

One other tidbit as I recall, was that 'smplayer ' didn't render menus very well or at all. If I use VLC on a downloaded a DVD with menus, it works by opening the folder. Can MPV display or run menus?

---

### Post by shantiq on 2015-01-28
thanx mc   looks ace!

---

### Post by VMC on 2015-01-28
> **mc4man said:**
> A player in progress based on mpv is bomi (formerly cmplayer
ppa here for 14.04/14.10 - [https://launchpad.net/~darklin20/+archive/ubuntu/bomi](https://launchpad.net/~darklin20/+archive/ubuntu/bomi)
It differs in many ways from baka-mplayer, one significant is it's fairly self contained where as baka needs libmpv
(menus are in the window > r. click
Just added this. Installing now. Will see how it works. Suggested mplayer. Also youtube downloader, which  I don't use much.

BOMI doesn't use MPV. Tried Preferences but couldn't find how to tie MVP to BOMI.

Edit: OK, it works, just not with DVD download. It must be MKV or an VOB file.

---

### Post by mc4man on 2015-01-28
> **VMC said:**
> Just added this. Installing now. Will see how it works. Suggested mplayer. Also youtube downloader, which  I don't use much.

BOMI doesn't use MPV. Tried Preferences but couldn't find how to tie MVP to BOMI.

Edit: OK, it works, just not with DVD download. It must be MKV or an VOB file.
It uses mpv internally 
Don't see any suggest for mplayer here??

There is a current trend for Debian/Ubuntu mpv packages (15.04) to recommend youtube-dl. I guess these upcoming players are also doing so in package builds. In the long run it really should be a suggest as package versions of youtube-dl will never keep up with changes.

Overall I prefer mpv over the 2 mentioned players though they both should get better. Seems here that bomi is being developed by people into anime so it may be good for such stuff. (- it also seems bomi sets vo & if supported hwdec automatically vs. mpv & baka-mplayer  where it's totally under user control
Your orig. post indicated some issues beyond the lack of subs shown, what happens with that file with something like - 

mpv --no-config --vo=xv /path/to/your file

Here with mpv subs are by default shown if there.
(if inclined & possible, if you could cut a couple of min. from the gravity file, confirm it also has the sub issue & upload somewhere I'd take a look at.
This site is decent & fairly anonymous - 
[http://www.datafilehost.com/](http://www.datafilehost.com/)

---

### Post by VMC on 2015-01-28
> **mc4man said:**
> ...
Your orig. post indicated some issues beyond the lack of subs shown, what happens with that file with something like - 

mpv --no-config --vo=xv /path/to/your file

Here with mpv subs are by default shown if there.
(if inclined & possible, if you could cut a couple of min. from the gravity file, confirm it also has the sub issue & upload somewhere I'd take a look at.
This site is decent & fairly anonymous - 
[http://www.datafilehost.com/](http://www.datafilehost.com/)

No sub using the command you provided. I needed to add '--sid=1' for subs to work. As SeijiSensei pointed out, they didn't get invoked:

```
$ mpv --no-config --vo=xv /media/vmc/NTFS/MKV/Gravity.mkv
Playing: /media/vmc/NTFS/MKV/Gravity.mkv
Detected file format: Matroska
Clip info:
 ENCODER: Lavf55.12.0
[stream] Video (+) --vid=1 (h264)
[stream] Audio (+) --aid=1 --alang=eng (*) 'Stereo' (aac)
[COLOR=#00FF00][stream] Subs      --sid=1 --slang=eng (dvd_subtitle)[/COLOR]   <<<<<<<<<<<<<<<****
Selected video codec: H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10 [lavc:h264]
Selected audio codec: AAC (Advanced Audio Coding) [lavc:aac]
AO: [alsa] 48000Hz stereo 2ch floatp
VO: [xv] 718x360 => 852x360 420p
AV: 00:03:00 / 01:30:59 (3%) A-V: -0.000

$ mpv --sid=1 --no-config --vo=xv /media/vmc/NTFS/MKV/Gravity.mkv
Playing: /media/vmc/NTFS/MKV/Gravity.mkv
Detected file format: Matroska
Clip info:
 ENCODER: Lavf55.12.0
[stream] Video (+) --vid=1 (h264)
[stream] Audio (+) --aid=1 --alang=eng (*) 'Stereo' (aac)
[COLOR=#00FF00][stream] Subs  (+) --sid=1 --slang=eng (dvd_subtitle[/COLOR]) <<<<<<<<<**********
Selected video codec: H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10 [lavc:h264]
Selected audio codec: AAC (Advanced Audio Coding) [lavc:aac]
AO: [alsa] 48000Hz stereo 2ch floatp
VO: [xv] 718x360 => 852x360 420p
AV: 00:02:26 / 01:30:59 (2%) A-V:  0.000

```

I will copy a couple minutes of Gravity and post, using your command at the suggest web site.

EDIT: BTW, what to use to cut 2 minutes of the video and retain the subs? ffmeg, I think didn't work.

---

### Post by VMC on 2015-01-28
This may be the reason the subs are not invoked:
[IMG][[IMG]http://i.imgur.com/o0KeZNK.png?1[/IMG]]("http://imgur.com/o0KeZNK")[/IMG]

---

### Post by mc4man on 2015-01-28
> **VMC said:**
> This may be the reason the subs are not invoked:

Hmm, not really sure what determines that. 
I've some mkv's with subs & mpv always opens with them on. However I grabbed a version of Gravity (not quite the same as yours) & mpv opens with them off. It appears some files open with a sub track selected, some open with no sub track selected (null

Edit: 
v makes the subs visible or not
j  selects a sub or 'turns' on 

Turning on or switching via the Osc is another way. 
Subs are the number below the audio stream(s), maybe you can see in screen, -/3 means off, 3 available. Clicking on the little icon turns on, then switches if more than one with subsequent clicks

---

