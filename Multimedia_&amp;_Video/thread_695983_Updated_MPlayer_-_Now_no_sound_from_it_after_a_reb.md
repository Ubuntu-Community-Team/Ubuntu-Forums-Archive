---
title: "Updated MPlayer - Now no sound from it after a reboot"
date: 2008-02-13
forum: Multimedia &amp; Video
---

### Post by PiggiePaul on 2008-02-13
Ok, now perhaps I did something wrong, but hopefully some kind soul can help?

Firstly this evening I installed Mplayer, and it worked fine.

Then I went to SM Players website and downloaded the latest version of that and installed it.

Whilst there I noticed they said the version of Mplayer that comes with ubuntu is really old and said the following:

[COLOR="Blue"]Suggested package:
The version of mplayer included in Ubuntu is very old (1.0rc1). SMPlayer has support for some of the new features of mplayer, so a newer version is highly recommended. You can download here MPlayer SVN r25873 (from 2008-01-27).[/COLOR]

So I installed it.


Now. after all of this............

When I went to play a video just with mplayer it did (and still does) give a small error:

[COLOR="Red"]New_Face failed. Maybe the font path is wrong. Please supply the text font file (~/.mplayer/subfont.ttf)[/COLOR]

But the video still played and I had sound.

I then tried the SM Player front end, and I think it's superb, this played files without throwing up any errors, so I was very happy.

Then, I rebooted the system, and now I have no sound when playing video's either from SM Player, or direct from Mplayer.

There's nothing wrong with the sound on my system as I can still play MP3's and Video's back with Totem just fine.

Seeing as (If I understand it correctly) SM Player uses Mplayer, I guess it's just the new Mplayer I have the problem with?

The mute is not on, and I have the volume up to 100% in Mplayer.

So, any idea's why my newly installed Mplayer has lost it's sound since I rebooted?

Thanks.

---

### Post by cor2y on 2008-02-13
for the font thing you will have to move the font files to your local folder or create a symlink, they are usually store in /usr/share/mplayer/font if you installed mplayer via synaptic.
If not then you will have to download the font files from the mplayer site and put them in the local folder mplayer is complaining about.

For the audio see what both mplayer and smplayer have setup as the default audio device.
You should be set to alsa or oss to hear audio, depending on which audio deamon you have installed in ubuntu (its alsa by default)

---

### Post by PiggiePaul on 2008-02-13
> **cor2y said:**
> for the font thing you will have to move the font files to your local folder or create a symlink, they are usually store in /usr/share/mplayer/font if you installed mplayer via synaptic.
If not then you will have to download the font files from the mplayer site and put them in the local folder mplayer is complaining about.

For the audio see what both mplayer and smplayer have setup as the default audio device.
You should be set to alsa or oss to hear audio, depending on which audio deamon you have installed in ubuntu (its alsa by default)

Thanks for the help

I've checked both SM Player and Mplayer and they both have alsa as the audio setting.

As I say, The media player i was using up to now (Totem movie player) still works fine for videos and mp3's and the sound is fine.

It's only mplayer which has no sound.

Perhaps? (wild guess) it's the other error (seemingly unconnected) that's causing the problem?

As well as the font error (in my 1st post) if I now RIGHT CLICK on a video file and tell it to open with Mplayer, Mplayer loads with a error box saying it can't find the file.

Yet, if I run mplayer 1st then browse to the file, it will play (without sound) but gives the font error.



I did download it (self installing package) from this page here:
[http://smplayer.sourceforge.net/downloads.php?tr_lang=en&PHPSESSID=a7d7f12938af8ae5eebf38cb1767d538](http://smplayer.sourceforge.net/downloads.php?tr_lang=en&PHPSESSID=a7d7f12938af8ae5eebf38cb1767d538)

About halfway down, in the middle of the page, you will see the link to the mplayer download.

That's all I've done.
I even reinstalled it a 2nd time, just in case. But I still get that font error.

I'm new to Ubuntu/Linux so would need a little hand-holding to deal with this font issue myself.

Thanks.

---

### Post by andrew.46 on 2008-02-13
Hi,

 I can see at least 1 easily fixed problem :-)

> **PiggiePaul said:**
> Ok, now perhaps I did something wrong, but hopefully some kindsoul can help?
Firstly this evening I installed Mplayer, and it worked fine.
Then I went to SM Players website and downloaded the latest version of that and installed it.
Whilst there I noticed they said the version of Mplayer that comes with ubuntu is really old and said the following:

[COLOR="Blue"]Suggested package:The version of mplayer included in Ubuntu is very old (1.0rc1). SMPlayer has support for some of the new features of mplayer, so a newer version is highly recommended. You can download here MPlayer SVN r25873 (from 2008-01-27).[/COLOR]
So I installed it.
The maker of smplayer produces a debian package of the subversion mplayer to work with his software. Mind you this dates *really* fast, the latest svn for example is 

> andrew@ilium~/source/svn_mplayer/mplayer/mplayer-r25990$ svn info
Path: .
URL: svn://svn.mplayerhq.hu/mplayer/trunk
Repository Root: svn://svn.mplayerhq.hu/mplayer
Repository UUID: b3059339-0415-0410-9bf9-f77b7e298cf2
Revision: 25990
Node Kind: directory
Schedule: normal
Last Changed Author: diego
Last Changed Rev: 25990
Last Changed Date: 2008-02-13 11:55:37 +1100 (Wed, 13 Feb 2008) 

Mind you it will still get you vastly superior performance than the old repository version you were using.

> 
Now. after all of this............
When I went to play a video just with mplayer it did (and still does) give a small error:

[COLOR="Red"]New_Face failed. Maybe the font path is wrong. Please supply the text font file (~/.mplayer/subfont.ttf)[/COLOR]
But the video still played and I had sound.


Mplayer likes to have a font available for the On Screen Display and subtitles. This can easily be corrected:

```
$ sudo apt-get install ttf-bitstream-vera
$ mkdir -v ~/.mplayer
$ ln -sv /usr/share/fonts/truetype/ttf-bitstream-vera/Vera.ttf ~/.mplayer/subfont.ttf
```

You may already have this directory and this font but no matter, this is the complete method.

> 
I then tried the SM Player front end, and I think it's superb, this played files without throwing up any errors, so I was very happy.
Then, I rebooted the system, and now I have no sound when playing video's either from SM Player, or direct from Mplayer.
There's nothing wrong with the sound on my system as I can still play MP3's and Video's back with Totem just fine.
Seeing as (If I understand it correctly) SM Player uses Mplayer, I guess it's just the new Mplayer I have the problem with?
The mute is not on, and I have the volume up to 100% in Mplayer.
So, any idea's why my newly installed Mplayer has lost it's sound since I rebooted?
Thanks.

I would tend to suspect the other way: Smplayer or a system problem. The developer of Smplayer is usually quite active in these forums, can I suggest that you make another post with Smplayer in the subject line? This way he will see it and hopefully be able to make a few suggestions.

All the best,

   Andrew

---

### Post by PiggiePaul on 2008-02-13
Thanks Andrew for your help.

I followed your "code" and thanks to you, have successfully stopped the error about the missing font.

I did some google searching and it seems a common problem.

Anyway, putting that to one side, I was trying to work out what you meant near the start of your helpful advice.

Have I downloaded and installed a unsuitable version of MPlayer?

Would you have a link to a self installing version that I SHOULD be using that would (fingers crossed) over-write the version I've just got and which is causing issues on my system?

Thanks.

===== EDIT =====

Just to update, I've now uninstalled MPlayer, but I'm not convinced that if I go to install it again, what version I'm getting, the original ubuntu one of the new version thats still lurking.

So if there is a link to a proper (bug free?) ubuntu version of mplayer (self installing package) that anyone could point me to, I'd be grateful

---

### Post by andrew.46 on 2008-02-13
Hi,

 Glad the font error disappeared, although this was not really a major problem. As to versions of mplayer, that is a bigger question. I can summarise, although I welcome any corrections:

=======================

There is a wonderful media player / converter called mplayer that is put together by these people:

[http://www.mplayerhq.hu/design7/news.html](http://www.mplayerhq.hu/design7/news.html)

It is an incredible tool that, when properly setup, will play almost any media format available and will also convert between them. Primarily a command line tool it can be compiled with a fairly rudimentary GUI called Gmplayer. It is intermittently released as a "Release Candidate" the most recent of which being rc2:

[http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html)

These releases are a long way apart while the cutting edge work is done in a Subversion Repository that can be downloaded *from* by interested users and contributed *to* by developers.

Now a distro like Ubuntu takes either a release candidate or a subversion snapshot and develops it into a 'package' and releases it to say Gutsy Gibbon. It may be modified and patched a little and may come with fewer codecs than is available from the mplayer web site. Depending on the skill and political feelings of the developer (re the codecs) it will be a good package and will integrate well with the distro.

You can also install the subversion (svn)  mplayer  independent of the distro and enjoy the full codec pack and both the benefits *and* perils of really up to date software. I have written and actively support a walkthrough that promotes just that:

[http://ubuntuforums.org/showthread.php?t=558538](http://ubuntuforums.org/showthread.php?t=558538)

Now mplayer and mencode from the commandline can be a little difficult and the gui sux more than a little :-) So some people code 'frontends' for mplayer. Welcome to Smplayer, which prefers to use an svn snapshot, which aims to improve the Gui and open up many of the mplayer / mencoder options that are often hidden from the casual (or experienced!) users.

=========================

So you can see that there are many choices and it is really up to you to chose which suits you the best.

  All the best,

    Andrew

---

### Post by PiggiePaul on 2008-02-13
Thanks Andrew.

I'm hating to say this, but this mplayer problem might just be the turning point for me and Linux (ubuntu)

I'm spent every evening this week fiddling and trying to do the most basic things, which would take seconds in any version of windows.

I'm trying to remain positive (and I'm still JUST ABOUT) there, but my patience is just about starting to give.

I've not yet got the extra buttons on my mouse working.
YouTube plays back like junk in firefox.

I do 1 thing and I loose sound in mplayer.

I'm teetering, on saying sod this, what's the point and going back to windows, returning when the Linux community can get their act together, back 1 product and support it.

Which is when Msoft will start worrying.

That said, I'm still holding on to my good feelings, but it does put a strain when you see the forums full of such basic problems that people can't solve that should just no be problems in the 1st place.

Phew.......... Just had to get that of my chest!

Well, I've uninstalled Mplayer, and SMplayer fully and re-installed the original ubuntu versions and still no sound.

So something's been turned off somewhere. 

Despite this, Totem movie player still works perfect with sound.

Somethings screwy is going on.

---

### Post by andrew.46 on 2008-02-13
Hi,

I can sense a little frustration :-)

> **PiggiePaul said:**
> Thanks Andrew.
I'm hating to say this, but this mplayer problem might just be the turning point for me and Linux (ubuntu)
I'm spent every evening this week fiddling and trying to do the most basic things, which would take seconds in any version of windows.
I'm trying to remain positive (and I'm still JUST ABOUT) there, but my patience is just about starting to give.
I think there is a good case for keeping windows running as well as having an Ubuntu system. This can be as a dual-boot or as a second computer. That way in times of frustration you can simply walk away from the linux computer rather than wipe the disk in frustration :-)

> I've not yet got the extra buttons on my mouse working.
YouTube plays back like junk in firefox.
I do 1 thing and I loose sound in mplayer.
I'm teetering, on saying sod this, what's the point and going back to windows, returning when the Linux community can get their act together, back 1 product and support it.
Which is when Msoft will start worrying.
That said, I'm still holding on to my good feelings, but it does put a strain when you see the forums full of such basic problems that people can't solve that should just no be problems in the 1st place.
Phew.......... Just had to get that of my chest!

You may be losing sight of one of the golden rules of Linux : "Have fun". If you work at each of these problems individually they can be solved and you will have picked up a new skill. But if it ceases to be fun IMHO you should take the dog for a walk instead :-)

> Well, I've uninstalled Mplayer, and SMplayer fully and re-installed the original ubuntu versions and still no sound.
So something's been turned off somewhere. 
Despite this, Totem movie player still works perfect with sound.
Somethings screwy is going on.

Rather than wrestle with mplayer / Smplayer any more what about installing vlc? It has a nice repository version and plays DVDs and most formats quite easily:

```
$ sudo apt-get install vlc
```

Ubuntu linux can be a little chaotic at times, don't forget that there are several other distros which perhaps might work better for you. I personally dual boot Hardy Heron with Slackware 12 and there are many many other distros to try. Have a hunt around if you like and look at distros like Mandriva or try the following test:

[http://polishlinux.org/choose/quiz/](http://polishlinux.org/choose/quiz/)

which can be quite accurate :-) And whatever you do remember that linux is fun.

            Andrew

---

### Post by rvm4000 on 2008-02-14
> **PiggiePaul said:**
> Have I downloaded and installed a unsuitable version of MPlayer?

The version of mplayer in my site is not a "special" version to be used with smplayer. In fact it's not patched at all (I do patch the Windows builds).

So I think it can be used alone, no need to use it with smplayer. It's like if you've built it yourself.

I created that mplayer package because mplayer has many improvements since the old 1.0rc1 and smplayer will work better with a recent version of mplayer, although you can use 1.0rc1 if you want.

About the problem with the sound, I'm convinced it's an easy thing to resolve. First look at the output of mplayer, probably it's telling why it can't use sound.
Just guessing, maybe your system is using esd for the sound, which allows several applications to play sound at the same time. If you configure mplayer/smplayer to use alsa or oss maybe it can't use sound because the audio device is busy. Changing the audio driver in mplayer to esd too would fix the problem.
But that's just a guess.

---

### Post by PiggiePaul on 2008-02-14
> **rvm4000 said:**
> The version of mplayer in my site is not a "special" version to be used with smplayer. In fact it's not patched at all (I do patch the Windows builds).

So I think it can be used alone, no need to use it with smplayer. It's like if you've built it yourself.

I created that mplayer package because mplayer has many improvements since the old 1.0rc1 and smplayer will work better with a recent version of mplayer, although you can use 1.0rc1 if you want.

About the problem with the sound, I'm convinced it's an easy thing to resolve. First look at the output of mplayer, probably it's telling why it can't use sound.
Just guessing, maybe your system is using esd for the sound, which allows several applications to play sound at the same time. If you configure mplayer/smplayer to use alsa or oss maybe it can't use sound because the audio device is busy. Changing the audio driver in mplayer to esd too would fix the problem.
But that's just a guess.

Many MANY thanks for the advice.
I must admit I was pulling my hair out last night (and I don't have a lot left to pull !!!)

What was so frustrating was I'd just about got Ubuntu setup how I like it, with "most" things working (few more issues to resolve) but I felt I was well on my way.

I downloaded the "suggested" mplayer from the SMPlayer web site, and mplayer and smplayer looked superb. I loved the front end, and the video quality was excellent.

Just by coincidence, just after that, I have a Ubuntu popup about some (I think 4) security updates to the system. Downloaded and insalled those too.

At this point, eveything was working perfect.

I had the "missing font issue" with mplayer if I used that directly, but when using SMPlayer it did not occur, so no big deal.

Then I rebooted the system, and since then, mplayer has no sound output.

It's set to the ALSA sound setting as it was before the reboot.

I will however try your suggestion later tonight when back home.

I'm sure (as you say) it's just something small that's causing the problem.

I even totally uninstalled both THAT VERSION of mplayer and smplayer and installed the old? versions from Ubuntu's built in software library thing (not sure the correct term) but even then, just with mplayer alone, there is no sound.

And yet there was before that dreaded reboot last night.

Again, thanks for your advice.

One small thing. When you run from the command line (not sure what it's called now) the alasmixer (or something like that) it does "look" laid out a buit different than it did eariler last night.

But as I said Totem still works and plays fine. as it's always done.

---

### Post by cor2y on 2008-02-14
Sorry to hear about your problems PiggiePaul.
But if you wish to give it the old college try again.
Would it be possible for you to post the results of a movie file played by mplayer via the terminal.
So we or I can see if there is an error with the audio decoder being used.
To play a movie via the terminal, just make sure you are in the directory of the movie file in question if you aren't too good at remembering directory structures. For example if its in a folder called movies, cd to that folder via the terminal and then
```
mplayer movie.avi
``` and it will play.

---

### Post by PiggiePaul on 2008-02-14
> **cor2y said:**
> Sorry to hear about your problems PiggiePaul.
But if you wish to give it the old college try again.
Would it be possible for you to post the results of a movie file played by mplayer via the terminal.
So we or I can see if there is an error with the audio decoder being used.
To play a movie via the terminal, just make sure you are in the directory of the movie file in question if you aren't too good at remembering directory structures. For example if its in a folder called movies, cd to that folder via the terminal and then
```
mplayer movie.avi
``` and it will play.

Thanks for the advice "cor2y"

As a (admitted newbie) to Ubuntu and linux, I feel very much out of my depth at the moment, so I really appreciate your help here.

Before I go any further, just an update:

Last thing last night, I fully uninstalled (I'm pretty sure!) mplayer and smplayer from my system.

I have just this evening re-installed the updated mplayer from this site here (about half way down in the middle of the page)

Oddly enough, now, Now it does not even run from the Icon under Applications/Sound and Video. If I click the icon........... Nothing!  Very odd ?

Anyway, it is installed and I have done as you asked from the Terminal and here is the output: (Note, I have made no adjustments since downloading and this is the 1st video file it has played since being installed)

[COLOR="Blue"]
mplayer mentals.avi
MPlayer dev-SVN-r25873-4.1.2 (C) 2000-2008 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3200+ (Family: 15, Model: 4, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing mentals.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [DX50]  480x320  24bpp  25.000 fps  224.1 kbps (27.4 kbyte/s)
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 11025 Hz, 2 ch, s16le, 352.8 kbit/100.00% (ratio: 44100->44100)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
AO: [alsa] 11025Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 480 x 320 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.50:1 - prescaling to correct movie aspect.
VO: [xv] 480x320 => 480x320 Planar YV12 [/COLOR]

---

### Post by cor2y on 2008-02-14
The mplayer not launching from the icon could be because there is no mplayer frontend/gui/skin installed, if as you say you completely removed mplayer from before.
In the terminal try 
```
 gmplayer movie.avi
``` thats to launch the gui version of mplayer if you get an error then no mplayer skin is installed, to get one go to synaptic and search for mplayer-skins and install that.

Now back to the audio it looks like your system has everything to playback audio but can't you still can't hear , you have the alsa deamon installed since you can playback files and hear audio in totem.
Its even selected in the playback option.
So lets see what happens when you force alsa to be used.
```
mplayer -ao alsa movie.avi
``` see if you hear audio now
Using the mplayer gui Right click go to preferences Audio Tab make sure alsa and no other output is selected then go to the codec/demuxer tab and under Audio codec Family try switching from libmad if its selected to ffmpeg/libavcodec audio decoders.
If libmad was NOT selected and if it is there switch to that.
That SHOULD give you back audio, remember to restart mplayer after these selections.
If not then we will see what else can be done.

---

### Post by PiggiePaul on 2008-02-14
Thanks for the follow up help.

Right, as you correctly guessed, my mass! uninstall must have taken the skins away.

The gmplayer movie.avi did not open up any front end, so I did as you suggested and went to the Synaptic installer and selected mplayer skins, and now the mplayer icon under Applications/Sound & Video runs Mplayer, and I get the familiar front end.

Next, I followed your instructions re: [COLOR="Blue"]mplayer -ao alsa movie.avi[/COLOR]

But still have no sound (same as before) but oddly (unless I'm looking at it wrong) dosen't it still look like it's using PCM ?




[COLOR="Blue"]mplayer -ao alsa mentals.avi
MPlayer dev-SVN-r25873-4.1.2 (C) 2000-2008 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3200+ (Family: 15, Model: 4, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing mentals.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [DX50]  480x320  24bpp  25.000 fps  224.1 kbps (27.4 kbyte/s)
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 11025 Hz, 2 ch, s16le, 352.8 kbit/100.00% (ratio: 44100->44100)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
AO: [alsa] 11025Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 480 x 320 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.50:1 - prescaling to correct movie aspect.
VO: [xv] 480x320 => 480x320 Planar YV12 
A:  22.1 V:  22.1 A-V:  0.000 ct:  0.000 553/553  1%  0%  0.0% 26 0 
Exiting... (Quit)[/COLOR]



After doing this, I again just loaded up mplayer gui and (as you said) went to the Audio Tab under Preferences. It was set to [COLOR="Blue"]esd[/COLOR]

So, as you said, I reset it back to [COLOR="Blue"]alsa[/COLOR]
I then also went to the codec/demuxer tab and selected [COLOR="Blue"]libmad mpeg audio decoder[/COLOR]

I shut down and restarted mplayer and checked the preferences had stuck, and they had.

So, I closed it down again, went back to the terminal and run the same command again, and here are the results with those changed settings:

Oh, and still no sound by the way :(



[COLOR="Blue"]mplayer mentals.avi
MPlayer dev-SVN-r25873-4.1.2 (C) 2000-2008 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3200+ (Family: 15, Model: 4, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing mentals.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [DX50]  480x320  24bpp  25.000 fps  224.1 kbps (27.4 kbyte/s)
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 11025 Hz, 2 ch, s16le, 352.8 kbit/100.00% (ratio: 44100->44100)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
AO: [alsa] 11025Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 480 x 320 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.50:1 - prescaling to correct movie aspect.
VO: [xv] 480x320 => 480x320 Planar YV12 
A:  18.0 V:  18.0 A-V: -0.000 ct: -0.000 450/450  1%  0%  0.0% 0 0 
Exiting... (Quit)[/COLOR]

---

### Post by cor2y on 2008-02-14
did you try gmplayer to see if there was a difference?
We can also try looking at the conf files in your hidden .mplayer folder (note the ".") to view this enable view hidden folders which is ctrl+h go to the .mplayer folder and look at config and gui.conf
here are the details of my config (this is what mplayer from the terminal uses)
```
# Write your default config options here!

##################
# audio settings #
##################

# Specify default audio driver (see -ao help for a list).
ao=alsa,
prefer-ipv4 = yes
```
And gui.conf (this is what the mplayer frontend uses)
```
enable_audio_equ = "no"
vo_driver = "xv"
vo_panscan = "0.000000"
vo_doublebuffering = "yes"
vo_direct_render = "no"
v_framedrop = "0"
v_flip = "-1"
v_ni = "yes"
v_idx = "1"
v_vfm = "ffmpeg"
a_afm = "libmad"
vf_pp = "no"
vf_autoq = "0"
vf_lavc = "no"
ao_driver = "alsa"
ao_volnorm = "no"
softvol = "no"
ao_surround = "no"
ao_extra_stereo = "no"
ao_extra_stereo_coefficient = "1.000000"
dvd_device = "/dev/dvd"
cdrom_device = "/dev/cdrom"
osd_level = "2"
sub_auto_load = "yes"
sub_unicode = "no"
***_enabled = "no"
***_use_margins = "no"
***_top_margin = "0"
***_bottom_margin = "0"
sub_pos = "100"
sub_overlap = "no"
font_factor = "0.750000"
font_text_scale = "5.000000"
font_osd_scale = "6.000000"
font_blur = "2.000000"
font_outline = "2.000000"
font_autoscale = "1"
cache = "no"
cache_size = "2048"
playbar = "no"
load_fullscreen = "no"
show_videowin = "yes"
stopxscreensaver = "yes"
autosync = "yes"
autosync_size = "0"
gui_skin = "clearplayer"
gui_save_pos = "yes"
gui_main_pos_x = "422"
gui_main_pos_y = "732"
gui_video_out_pos_x = "267"
gui_video_out_pos_y = "179"
equ_band_00 = "0.000000"
equ_band_01 = "0.000000"
equ_band_02 = "0.000000"
equ_band_03 = "0.000000"
equ_band_04 = "0.000000"
equ_band_05 = "0.000000"
equ_band_06 = "0.000000"
equ_band_07 = "0.000000"
equ_band_08 = "0.000000"
equ_band_09 = "0.000000"
equ_band_10 = "0.000000"
equ_band_11 = "0.000000"
equ_band_12 = "0.000000"
equ_band_13 = "0.000000"
equ_band_14 = "0.000000"
equ_band_15 = "0.000000"
equ_band_16 = "0.000000"
equ_band_17 = "0.000000"
equ_band_18 = "0.000000"
equ_band_19 = "0.000000"
equ_band_20 = "0.000000"
equ_band_21 = "0.000000"
equ_band_22 = "0.000000"
equ_band_23 = "0.000000"
equ_band_24 = "0.000000"
equ_band_25 = "0.000000"
equ_band_26 = "0.000000"
equ_band_27 = "0.000000"
equ_band_28 = "0.000000"
equ_band_29 = "0.000000"
equ_band_30 = "0.000000"
equ_band_31 = "0.000000"
equ_band_32 = "0.000000"
equ_band_33 = "0.000000"
equ_band_34 = "0.000000"
equ_band_35 = "0.000000"
equ_band_36 = "0.000000"
equ_band_37 = "0.000000"
equ_band_38 = "0.000000"
equ_band_39 = "0.000000"
equ_band_40 = "0.000000"
equ_band_41 = "0.000000"
equ_band_42 = "0.000000"
equ_band_43 = "0.000000"
equ_band_44 = "0.000000"
equ_band_45 = "0.000000"
equ_band_46 = "0.000000"
equ_band_47 = "0.000000"
equ_band_48 = "0.000000"
equ_band_49 = "0.000000"
equ_band_50 = "0.000000"
equ_band_51 = "0.000000"
equ_band_52 = "0.000000"
equ_band_53 = "0.000000"
equ_band_54 = "0.000000"
equ_band_55 = "0.000000"
equ_band_56 = "0.000000"
equ_band_57 = "0.000000"
equ_band_58 = "0.000000"
equ_band_59 = "0.000000"
```
What you are concerned with in gui.conf is 
**a_afm = "libmad"** and **ao_driver = "alsa"** a_afm is what decoder mplayer will use in this case libmad and ao_driver is what sound daemon in this case alsa.
You can always check via synaptic to see if libmad is installed although if it is listed then it is.

---

### Post by PiggiePaul on 2008-02-14
Hi again. Cheers for sticking with me on this.
Even though there are problems, I feel we're ruling stuff out, which is good.
also I'm getting a tiny bit more comfortable with the Terminal which is a good thing :)

Ok, following from your last posting:

Yes, I tried gmplayer and exactly the same. Works fine but no sound.

I then (with a bit of hunting around) managed to find the .mplayer directory and the config files you mentioned.

The 1st one [COLOR="Blue"]config[/COLOR] was totally empty.

I tried pasting in and saving the same as your's, but it made no difference. (still no sound)

I then checked the [COLOR="Blue"]gui.conf[/COLOR] file and here it is:

[COLOR="Blue"]enable_audio_equ = "no"
vo_driver = "xv"
vo_panscan = "0.000000"
vo_doublebuffering = "yes"
vo_direct_render = "no"
vo_dxr3_device = "/dev/em8300-0"
v_framedrop = "0"
v_flip = "0"
v_ni = "no"
v_idx = "-1"
a_afm = "libmad"
vf_pp = "no"
vf_autoq = "0"
vf_lavc = "no"
ao_driver = "alsa"
ao_volnorm = "no"
softvol = "no"
ao_surround = "no"
ao_extra_stereo = "no"
ao_extra_stereo_coefficient = "1.000000"
dvd_device = "/dev/dvd"
cdrom_device = "/dev/cdrom"
osd_level = "1"
sub_auto_load = "yes"
sub_unicode = "no"
***_enabled = "no"
***_use_margins = "no"
***_top_margin = "0"
***_bottom_margin = "0"
sub_pos = "100"
sub_overlap = "no"
font_factor = "0.750000"
font_text_scale = "5.000000"
font_osd_scale = "6.000000"
font_blur = "2.000000"
font_outline = "2.000000"
font_autoscale = "3"
cache = "no"
cache_size = "2048"
playbar = "no"
load_fullscreen = "no"
show_videowin = "yes"
stopxscreensaver = "yes"
autosync = "no"
autosync_size = "0"
gui_skin = "default"
gui_save_pos = "yes"
gui_main_pos_x = "560"
gui_main_pos_y = "854"
gui_video_out_pos_x = "542"
gui_video_out_pos_y = "467"
equ_channel_1 = "Front Right"
equ_channel_2 = "Front Left"
equ_channel_3 = "Rear Right"
equ_channel_4 = "Rear Left"
equ_channel_5 = "Center"
equ_channel_6 = "Bass"
equ_band_00 = "0.000000"
equ_band_01 = "0.000000"
equ_band_02 = "0.000000"
equ_band_03 = "0.000000"
equ_band_04 = "0.000000"
equ_band_05 = "0.000000"
equ_band_06 = "0.000000"
equ_band_07 = "0.000000"
equ_band_08 = "0.000000"
equ_band_09 = "0.000000"
equ_band_10 = "0.000000"
equ_band_11 = "0.000000"
equ_band_12 = "0.000000"
equ_band_13 = "0.000000"
equ_band_14 = "0.000000"
equ_band_15 = "0.000000"
equ_band_16 = "0.000000"
equ_band_17 = "0.000000"
equ_band_18 = "0.000000"
equ_band_19 = "0.000000"
equ_band_20 = "0.000000"
equ_band_21 = "0.000000"
equ_band_22 = "0.000000"
equ_band_23 = "0.000000"
equ_band_24 = "0.000000"
equ_band_25 = "0.000000"
equ_band_26 = "0.000000"
equ_band_27 = "0.000000"
equ_band_28 = "0.000000"
equ_band_29 = "0.000000"
equ_band_30 = "0.000000"
equ_band_31 = "0.000000"
equ_band_32 = "0.000000"
equ_band_33 = "0.000000"
equ_band_34 = "0.000000"
equ_band_35 = "0.000000"
equ_band_36 = "0.000000"
equ_band_37 = "0.000000"
equ_band_38 = "0.000000"
equ_band_39 = "0.000000"
equ_band_40 = "0.000000"
equ_band_41 = "0.000000"
equ_band_42 = "0.000000"
equ_band_43 = "0.000000"
equ_band_44 = "0.000000"
equ_band_45 = "0.000000"
equ_band_46 = "0.000000"
equ_band_47 = "0.000000"
equ_band_48 = "0.000000"
equ_band_49 = "0.000000"
equ_band_50 = "0.000000"
equ_band_51 = "0.000000"
equ_band_52 = "0.000000"
equ_band_53 = "0.000000"
equ_band_54 = "0.000000"
equ_band_55 = "0.000000"
equ_band_56 = "0.000000"
equ_band_57 = "0.000000"
equ_band_58 = "0.000000"
equ_band_59 = "0.000000"[/COLOR]

As far as my novice eye's can tell me, those two items you pointed out to look at are all there correctly.

what is puzzling me is:

When I play a .avi file from the terminal (as I have posted my terminal output in recent postings) it always LOOKS like the sound is PCM, even though all the settings of mplayer are set to (and reporting back as) alsa.

If you play a avi file from your terminal, do you get something like this:

[COLOR="Blue"]================================================== ========================
Forced audio codec: mad
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 11025 Hz, 2 ch, s16le, 352.8 kbit/100.00% (ratio: 44100->44100)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
================================================== ========================[/COLOR]

As (as you can see) I seem to get this come up, no matter what everthing else is set to, and I'm wondering is this is the root of the problem?

---

### Post by cor2y on 2008-02-14
well while pcm audio in an avi is possible most of the avi files i have contain mp3 or aac audio tracks.
I assume this file can be played in totem with audio playback.
Try switching the audio library from libmad to ffmpeg/libavcodec

---

### Post by PiggiePaul on 2008-02-14
> **cor2y said:**
> well while pcm audio in an avi is possible most of the avi files i have contain mp3 or aac audio tracks.
I assume this file can be played in totem with audio playback.
Try switching the audio library from libmad to ffmpeg/libavcodec

Hi, last question answered 1st :)

Yes, I did try setting the audio library from libmad to ffmpeg/libavcode a whole ago when you suggested it in an earlier post.

I'm just running through a few other files, and will copy and paste the sound part of mplayers terminal output here:

I will alternate in Red and Blue to show the different movies I've played back (Silently !!!)

[COLOR="Blue"]==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 22050 Hz, 2 ch, s16le, 64.0 kbit/9.07% (ratio: 8000->88200)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [alsa] 22050Hz 2ch s16le (2 bytes per sample)
Starting playback...
[/COLOR]


[COLOR="Red"]==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 44100 Hz, 2 ch, s16le, 96.0 kbit/6.80% (ratio: 12000->176400)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [alsa] 44100Hz 2ch s16le (2 bytes per sample)
Starting playback...
[/COLOR]



[COLOR="Blue"]==========================================================================
Forced audio codec: mad
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 22050 Hz, 2 ch, s16le, 20.0 kbit/2.84% (ratio: 2501->88200)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
AO: [alsa] 22050Hz 2ch s16le (2 bytes per sample)
Starting playback...[/COLOR]


[COLOR="Red"]==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 44100 Hz, 2 ch, s16le, 256.0 kbit/18.14% (ratio: 32000->176400)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [alsa] 44100Hz 2ch s16le (2 bytes per sample)
Starting playback...
[/COLOR]


Ok, that was 4 other video files, Two AVI's an MPG and a WMV file.

From all the great help, and working through all the checking you have told me.
It's looking like everything is set right (apparently) and it's working as it should.

It's almost as if it's just muted, or the volume is right down.

But According to all settings, the volume is on and full volume.

---

### Post by cor2y on 2008-02-14
what does the alsa volume panel show?
its right there next to the date and time calender on the desktop, mplayer uses the PCM setting for volume control (at least on my system and not the master setting) is that at an audible level?
Other than that i cannot think of a reason why there should not be any audio.
I guess as a last resort you could try compiling and installing mplayer yourself heres the tutorial [link](http://ubuntuforums.org/showthread.php?t=558538) or going back to the default synaptic install , to remove any custom settings you may have done simply uninstall mplayer and all the addons, mplayer-skins etc (right click and select completely remove), then delete your .mplayer folder then reinstall via synaptic again that SHOULD set you up as being a fresh install of mplayer.
You lose all settings etc you previously had.

---

### Post by PiggiePaul on 2008-02-14
> **cor2y said:**
> what does the alsa volume panel show?
its right there next to the date and time calender on the desktop, mplayer uses the PCM setting for volume control (at least on my system and not the master setting) is that at an audible level?
Other than that i cannot think of a reason why there should not be any audio.
I guess as a last resort you could try compiling and installing mplayer yourself heres the tutorial [link](http://ubuntuforums.org/showthread.php?t=558538) or going back to the default synaptic install , to remove any custom settings you may have done simply uninstall mplayer and all the addons, mplayer-skins etc (right click and select completely remove), then delete your .mplayer folder then reinstall via synaptic again that SHOULD set you up as being a fresh install of mplayer.
You lose all settings etc you previously had.

Right then.......

You are not going to believe this.........................

I checked the volume control, that was ok, the PCM levels were at 100%, and I fiddled with other sliders etc, all made no difference.

I then loaded up the mixer panel from the terminal and did some screen grabs to show you:


[IMG]http://i26.photobucket.com/albums/c145/Paul-rs/mixer-1.jpg[/IMG]

and as the alsa mixer is so wide, here is the rest of it:

[IMG]http://i26.photobucket.com/albums/c145/Paul-rs/mixer-2.jpg[/IMG]

Whilst doing this, Firefox (it must have been) Caused Ubuntu to lock up. Just stuck solid. So had to hit the power button on my PC to kill Linux off without shutting down.

You know where this is going.......................... ;)

Ubuntu started back up and I tried mplayer and guess what.........

I HAVE SOUND AGAIN !!!!!!!!!!!!!!!!!!!!!!!!

The only thing I (we) have actually changed is the config file in the .mplayer directory (to the same as yours) the othe config (for the gui version was fine)

But .....................

I HAVE SOUND AGAIN !!!!!!!!!!!!!!!!!!!!!!!!!

Although I've no idea what fixed it, how it was fixed, (as everything seemed to be ok as it was)

I've got to give you a BIG THANKYOU for sticking with me, and offering excellent and understandable advice, talking me thru this.

Perhaps that's the answer, if you have a problem get Firefox to crash your system and kill the live running Ubuntu by using the PC's power button ;)

---

### Post by cor2y on 2008-02-14
I am glad you got audio back.

---

### Post by PiggiePaul on 2008-02-15
Ok, (are you ready) ;)

Bit of an update here.
I do still have a problem here (sigh) but I may kinda know WHEN the problem is happening, if not how and why.

With the sound working fine last night I powered my machine down.

Today, powered it back up and no sound in Mplayer again.

Rebooted the machine and then I did have sound in Mplayer.

(This is not just Mplayer by the way, as the music playing software "Amarok" is also affected the same way.

But (and here is the interesting part)

When Ubuntu is getting to the end of loading. You know you hear the log-on music of some drums and some African? humming.

Well, I quite often don't get this log-on music.

If I Do hear the log-on music, then Mplayer works fine with sound.

If I Don't hear this log-on music then Mplayer does not give any sound either.

So, I'm guessing it's some kinda small glitch re starting up/setting up/initializing (in some way) the sound card during Ubuntu's bootup.

As a side note, For some Bizarre reason Totem always has sound, so I can only assume it accesses the sound in some other way?

So, it's not Mplayer that's at fault after all. It's something that's not starting my sound up right during bootup.

I'd say I only hear the log-on music about 25% of the time.

Wondering if there's anything that can be done?

---

### Post by PiggiePaul on 2008-02-15
Reading on another thread about no sound the aplay command was used to show info, which I have done (in case it means something to someone!)

[COLOR="Blue"]aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audigy2 [Audigy 2 ZS [SB0350]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 1: Audigy2 [Audigy 2 ZS [SB0350]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: Audigy2 [Audigy 2 ZS [SB0350]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audigy2 [Audigy 2 ZS [SB0350]], device 4: p16v [p16v]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[/COLOR]

---

### Post by PiggiePaul on 2008-02-15
Another little update which may shed a little more light on this strange sound issue.

I'm 90% sure of the following.
It's looking like it's something that's being saved? incorrectly whilst Ubuntu shuts down.

If I shut Ubuntu down as you should do, then upon reboot, I get lo login sound and mplayer has no sound)

If however, I'm nasty and just hold the power button on my PC to make it turn off instantly (which I know in windows is not good, but dunno how bad it is in Linux)

Then upon reboot, I do get my login sound and mplayer has sound too.

So, (logically) It's not whilst it's booting up, but perhaps? something it being set incorrectly at shutdown when you shutdown the proper way.

Don't suppose anyone will have a clue about this, but wanted to update as I'm finding out things as I go.

If you have any idea, I'd love to hear from you.

---

### Post by rvm4000 on 2008-02-16
You said that Totem did have sound. I think the gnome apps use esd for sound.
Have you tried to use esd too in mplayer?

```

mplayer -ao esd ...

```

---

### Post by PiggiePaul on 2008-02-16
> **rvm4000 said:**
> You said that Totem did have sound. I think the gnome apps use esd for sound.
Have you tried to use esd too in mplayer?

```

mplayer -ao esd ...

```

Thank you for your suggestion.

I just tried mplayer using the "esd" option, but I'm afraid it had to effect :(

Just for the record, last night I forced a shutdown (held the power button in on the PC) and this morning rebooted and no log-in music, (and mplayer./Amarok) neither have sound.

So it's not quite a simple as I thought last night. (I will have to do a few more startup/shutdowns today and see if the log-in sound does appear with a normal reboot)

Though of course, Totem still always has sound

Also Rhythmbox has sound as well.

Yet the card game AisleRiot Solitaire (which apparently has sound effects) has no sound.

So, No Log-in music, no sound from Mplayer, or Amarok or a card game.

Yet, Totem and Rhythmbox both have sound.

And yet SOMETIMES (for as yet, no understandable reason) when I do boot up my system and I get the log-in music, Everything works.

Odd huh?

I think I may pop outside and bang my head against a tree later !!!

---

### Post by PiggiePaul on 2008-02-17
Problem is now solved...... Yayyyyyyy :D

And in the end it was nothing to do with Mplayer, it was nothing to do with Sound settings.

It was to do with the inbuilt soundcard/system on my motheboard nicking 1st place (randomly) at bootup.

Which apparently does "Randomly" happen.

I did wonder about this, and even went into my BIOS twice to check the on-board sound was disabled, and it was. but it seems Linux still finds it.

Thanks to someone elses problem, I searched the system for sound devices, added the item to a list to force the onboard sound to always take 2nd place behind my Creative Labs card.

And now, since then every reboot I have sound :)

It was the fact that it was (and it) Random, unless you tell it otherwise, which was throwing me.

This is the note I have made about what I did:
(Note this refers to MY internal sound card, Your's may have a different name)


[COLOR="Blue"]Stopping internal sound card from taking 1st place (random event) during bootup

Add this line in alsa-base


options snd-via82xx index=-2


By doing the following command (run in Terminal)

sudo gedit /etc/modprobe.d/alsa-base
[/COLOR]


It's so simple when you know huh?

Thanks to everyone who tried to help me with this.
Hopefully me posting the solution here will help someone else with the same problem.

---

### Post by andrew.46 on 2008-02-17
Hi again!

 So where does this leave you with mplayer / smplayer vlc? Hopefully a happy camper :-)

             Andrew

---

### Post by PiggiePaul on 2008-02-17
> **andrew.46 said:**
> Hi again!

 So where does this leave you with mplayer / smplayer vlc? Hopefully a happy camper :-)

             Andrew

Yes, a VERY Happy Camper.

I think the mplayer and smplayer front end is an excellent combination and something I'd recommend to anyone. :)

---

