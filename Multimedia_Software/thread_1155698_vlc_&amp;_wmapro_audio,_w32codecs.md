---
title: "vlc &amp; wmapro audio, w32codecs"
date: 2009-05-11
forum: Multimedia Software
---

### Post by mc4man on 2009-05-11
I was rebuilding vlc on hardy this evening and noticed an interesting option.
So i'm interested to know if any repo or ppa versions of vlc that people have installed can play wma3 audio

Typically shown as wma3, wmap, wmapro, 0x0162, either as audio files only or in a wmv3 video

Samples are available here if needed and if anyone wants to test, right click on sample -> 'save link as'

[http://samples.mplayerhq.hu/A-codecs/WMA9/wmapro/](http://samples.mplayerhq.hu/A-codecs/WMA9/wmapro/)

all the repo and ppa versions I've seen don't and it appears to be a simple fix to allow vlc to access w32codecs for decoding (32 bit install only

You would just add this to your configure
```

--enable-loader
```

From what I see it then allows vlc to use w32codecs and play wma3 audio and video with it.

I'm somewhat disappointed that wmal (lossless) still doesn't work, but many hd video's use wma3pro audio so it seems worthwhile to enable

Playing wma3 now show this in terminal

> main playlist debug: adding item `New Stories (Highway Blues)-1.wma' ( /home/doug/Desktop/audio samples/New Stories (Highway Blues)-1.wma )

[00000790] asf demux debug: added new audio stream(codec:0x162,ID:1
dmo decoder debug: DMO codec for wmap may work with dll=wma9dmod.dll
[00000792] main decoder debug: using decoder module "dmo"


And removing w32codecs shows this
> [00000792] dmo decoder error: DecOpen failed
Win32 LoadLibrary failed to load: wma9dmod.dll, /wma9dmod.dll, /usr/lib/win32/wma9dmod.dll, /usr/local/lib/win32/wma9dmod.dll, /usr/lib/codecs/wma9dmod.dll, /usr/local/lib/codecs/wma9dmod.dll


So well worth adding to your build or requesting if your pps doesn't use

I still think wmal is possible, vlc just needs to be 'enticed' to try the proper .dll (.so)

---

### Post by andrew.46 on 2009-05-12
Hi mc4man,

Very interesting. I confess that my copy of vlc is a slackware one that actually comes *with* that option [in the script]("http://www.slackware.com/~alien/slackbuilds/vlc/build/vlc.SlackBuild"). But can I ask a vlc n00b question: how did you get the 'debug' info? I would be interested in duplicating your find :-).

Andrew

---

### Post by mc4man on 2009-05-12
Andrew

The debug comes from running a cli vlc with -vv or -vvv. I tend to use -vv, though even then the amount of info is excessively large and mostly non verbose, certainly to myself.

Vlc from the cli usually  shows the configure, I've never seen an ubuntu repo or ppa with it. (--enable-loader), it's disabled by default, 
 vlc is about 80% default enabled, with numerous --tree options. (it employs a form of auotdetect ( which can lead to a passing configure w/build failure

Running thru the Index of /A-codecs on mplayerhu, all play now  (edit: all that i've tried that seemed related), sole exception of 0x0163 (wmal

Though I find this of some hope (purely logical, not technical

> [00000790] asf demux debug: added new audio stream(codec:0x162,ID:1
dmo decoder debug: DMO codec for wmap may work with dll=wma9dmod.dll

Seems to indicate an action prior to attempting to use dmo


( i had been looking for some time for an option like --enable-dmo which doesn't exist, keep bypassing the --enable-loader
seemingly could resolve some persistent playback issues codec wise


Can vlc on slackware play 0x0163 ..?

---

### Post by andrew.46 on 2009-05-12
Hi mc4man,

> **mc4man said:**
> 
The debug comes from running a cli vlc with -vv or -vvv. I tend to use -vv, though even then the amount of info is excessively large and mostly non verbose, certainly to myself.

Thanks for that, I was looking for something more complicated :-). So with [the same file]("http://samples.mplayerhq.hu/A-codecs/WMA9/wmapro/New Stories (Highway Blues)-1.wma") I see:

```

[00000431] main decoder debug: looking for decoder module: 33 candidates
[00000431] dmo decoder debug: DMO codec for wmap may work with dll=wma9dmod.dll
[00000431] main decoder debug: using decoder module "dmo"

```

and with the codecs removed:

```

[00000431] dmo decoder debug: failed loading 'wma9dmod.dll'
[00000431] dmo decoder error: DecOpen failed
Win32 LoadLibrary failed to load: wma9dmod.dll, /wma9dmod.dll, /usr/lib/win32/wma9dmod.dll, /usr/local/lib/win32/wma9dmod.dll, /usr/lib/codecs/wma9dmod.dll, /usr/local/lib/codecs/wma9dmod.dll

```

So you have certainly hit the nail on the head there :-).

> Can vlc on slackware play 0x0163 ..?

Well I downloaded [this file]("http://samples.mplayerhq.hu/A-codecs/lossless/luckynight.wma") and sadly vlc choked:

```

[00000431] main decoder error: no suitable decoder module for fourcc `wmal'.
VLC probably does not support this sound or video format.

```

MPlayer had no such trouble:

```

andrew@skamandros~/Desktop$ mplayer luckynight.wma 
MPlayer SVN-r29286-4.2.4 (C) 2000-2009 MPlayer Team

Playing luckynight.wma.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
Clip info:
 name: Lucky Night
 author: Jody Marie Gnant
 copyright: 1995 Sirius Publishing
 comments: 1-minute song sample demonstrating Windows Media lossless audio compression
==========================================================================
Opening audio decoder: [dmo] Win32/DMO decoders
AUDIO: 44100 Hz, 2 ch, s16le, 868.7 kbit/61.55% (ratio: 108583->176400)
Selected audio codec: [wma9dmo] afm: dmo (Windows Media Audio 9 DMO)
==========================================================================
AO: [oss] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:  63.1 (01:03.0) of 63.0 (01:03.0)  5.6% 

Exiting... (End of file)

```

Nice voice BTW...

Andrew

---

### Post by mc4man on 2009-05-12
> MPlayer had no such trouble:.........
Opening audio decoder: [dmo] Win32/DMO decoders
elected audio codec: [COLOR="Blue"][wma9dmo][/COLOR]



That's the part that seems 'odd', it appears the same dmo is used for both wmap and wmal (0x0162, 0x0163

If so, then vlc is rejecting wmal 'out of hand', not because it couldn't work.

(( to any of those who use a ppa vlc with it not enabled, and want the advantages of w32 or win32 codecs, then suggest to them that they include the option in their builds

Extends vlc to some other formats, including the wmas (speech) that was the 'issue' [here]("http://ubuntuforums.org/showthread.php?t=1153780")and elsewhere

Edit:
As far as vlc-vv or -vvv you can output to a file, makes searching thru a bit easier ( the only output comm. I could figure out sometimes caused an overwrite if the output paused and then restarted

---

### Post by andrew.46 on 2009-05-13
Hi mc4man,

So based on your idea there is a clumsy work-around that fools vlc:

```
ffmpeg -i luckynight.wma -acodec copy -atag 0x0162 test.wma
```

and vlc plays this perfectly. This is a little similar to changing the mpeg4 fourcc that FFmpeg generates 'FMP4' to 'XVID' to fool some players :-). So it should be a relatively easy matter to add this into the vlc source code?

Andrew

---

### Post by mc4man on 2009-05-13
Well that certainly confirms vlc can play the format and is actually a viable workaround if the orig. tags aren't wanted

(unless atag could be told to just change the codec id

> So it should be a relatively easy matter to add this into the vlc source code

I would think so, though myself have no coding know how at all except for the obvious  or things that can be 'adjusted' by observing 'cause and effect'

As it happened yesterday I decided to see why wmal is rejected 'out of hand' and what would happen if it wasn't.

What's interesting is wmal is defined (in /include/vlc_codecs.h ) and is rejected because there are no VLC_FOURCC entries fot it

Adding 2 allowed vlc to proceed fairly normally till the last step "set DMO input type", where it fails and segfaults (I see the segfault as a positive, something is just missing.

I would have to think someone knowledgeable and familiar with vlc code could enable wmal (at least in 0.9.9a

At the end of the day I still prefer mplayer, though if one has app it's nice to have it as capable as possible.

A a risk of wasting space, different ex., using a wmal with full tags (noting the 'warning's are the same for wmap
<[B]
Removed because of simple typing mistake I made will editing vlc source[/B]>

---

### Post by mc4man on 2009-05-15
As it turns out it was very simple to add wmal to vlc0.9.9a

I had made a stupid typing mistake while editing in some fourcc entries - used a v instead of an a in the guid
Now plays wmal perfectly

To enable wmap and wmal in 0.9.9a

Add this to the configure
--enable-loader

In vlc-0.9.9a/modules/codec/dmo/dmo.c add the 2 bottom limes as shown

```
/* WMA 3 */
    { VLC_FOURCC('W','M','A','3'), "wma9dmod.dll", &guid_wma9 },
    { VLC_FOURCC('w','m','a','3'), "wma9dmod.dll", &guid_wma9 },
    { VLC_FOURCC('W','M','A','P'), "wma9dmod.dll", &guid_wma9 },
    { VLC_FOURCC('w','m','a','p'), "wma9dmod.dll", &guid_wma9 },
    { VLC_FOURCC('W','M','A','L'), "wma9dmod.dll", &guid_wma9 },
    { VLC_FOURCC('w','m','a','l'), "wma9dmod.dll", &guid_wma9 },
```

Then configure and make ect.
As long as w32codecs or win32codecs is installed vlc will now play wmap and wmal audio (haven't tested a wmv3 with wmal audio

(only for a 32bit install

edit : even allows for some hq wma - screen

---

### Post by andrew.46 on 2009-05-15
Hi mc4man,

Great work! I do not run pre-release versions of vlc 1.0 but you may be interested to see the [changes in the source code]("http://git.videolan.org/?p=vlc.git;a=blob;f=modules/codec/dmo/dmo.c;h=3875791fee4ef84b9b57ec54e914d52eaee24326;hb=HEAD") for the upcoming version. Lines 186 and onward seem to promise decoding 'out of the box'. Alhough I am a card carrying MPlayer fanatic I look forward to vlc 1.0 :-).

Andrew

---

### Post by mc4man on 2009-05-15
Just did todays 1.0-git, at first it didn't work at all for any wma, then it started up fine and is now.

(I may not have started the new build with vlc --reset-config, otherwise I don't know.
(the 'problem turns out to a line(s) in .config/vlc/vlc-qt4-interface.conf. that get written when you exit vlc - geometry=@ByteArray.../../
removing that line(s) restores dmo for a bit, hopefully that's the 'fix' mentioned

Error message first encountered with 1.0-git here (it may be added to 0.9.9a and 1.0 so maybe at some point no need to edit, not sure

Edit : from jb
> Applied for VLC 0.9.10 and VLC 1.0.0

And dmo should be fixed this night for 1.0 and 1.1

[http://forum.videolan.org/viewtopic.php?f=13&t=59355&p=198205#p198205](http://forum.videolan.org/viewtopic.php?f=13&t=59355&p=198205#p198205)


for 1.1-git the edit is even simpler, same file, just one line (and --enable-loader in configure

For 1.1-git (as of today, add last line

```
{ VLC_FOURCC('m','s','s','1'), "wmsdmod.dll", &guid_wms },
    /* Windows Media Video Adv */
    { VLC_CODEC_WMVA,   "wmvadvd.dll", &guid_wmva },

    /* WMA 3 */
    { VLC_CODEC_WMAP,   "wma9dmod.dll", &guid_wma9 },
    { VLC_CODEC_WMAL,   "wma9dmod.dll", &guid_wma9 },

```

I must of wasted 3 hrs. grepping all over the source for some relevant code, gave up and when posing a query over at videolan saw the mistake

> &guid_wm[COLOR="Red"]v[/COLOR]9 },

Andrew - I know you like different audio samples - here are some interesting ones (mplayer passes with flying colors, vlc can't do one

[http://www.linnrecords.com/linn-downloads-testfiles.aspx](http://www.linnrecords.com/linn-downloads-testfiles.aspx)

---

### Post by andrew.46 on 2009-05-16
Hi mc4man,

> **mc4man said:**
> Andrew - I know you like different audio samples - here are some interesting ones (mplayer passes with flying colors, vlc can't do one

[http://www.linnrecords.com/linn-downloads-testfiles.aspx](http://www.linnrecords.com/linn-downloads-testfiles.aspx)

MPlayer wins again :-).

Andrew

**Edit:** alienbob has updated his slackbuild script for rc1 so even as we speak I am compiling this one :-)

---

### Post by mc4man on 2009-05-16
It definitely appears the 1.1-git has an overall issue with the dmo loader. (as of yesterdays source

At some point playback of any files needing any dmo will fail, whether it's been fixed yet remains to be seen. ( a few opening and closing of vlc using more than 1 file requiring dmo should cause the failure
(guessing some relationship between libxcb-xx, the qt interface and dmo loader

0.9.9a works flawlessly with the loader.

(would be curious if slackware or other behaves better

---

### Post by andrew.46 on 2009-05-31
Hi mc4man,

> **mc4man said:**
> It definitely appears the 1.1-git has an overall issue with the dmo loader. (as of yesterdays source

At some point playback of any files needing any dmo will fail, whether it's been fixed yet remains to be seen. 

Well I admit I am a little hooked so I compiled vlc 1.0 rc2 today, again courtesy of alien bob's script :-). Oddly enough the gui produced no sound for [the wma lossless file]("http://samples.mplayerhq.hu/A-codecs/lossless/luckynight.wma") but the cli played it flawlessly:

```

[0x8126c60] main decoder debug: looking for decoder module: 33 candidates
**[COLOR="Purple"][0x8126c60] dmo decoder debug: DMO codec for wmal may work with dll=wma9dmod.dll[/COLOR]**
[0x8126c60] dmo decoder debug: DMO input type set
[0x8126c60] dmo decoder debug: DMO output type set
[0x8126c60] dmo decoder debug: GetOutputSizeInfo(): bytes 16384, align 1
[0x8126c60] main decoder debug: using decoder module "dmo"
[0x8126c60] main decoder debug: TIMER module_need() : 31.171 ms - Total 31.171 ms / 1 intvls (Avg 31.171 ms)
[0x8126c60] main decoder debug: thread started
[0x8126c60] main decoder debug: thread (decoder) created at priority 5 (input/decoder.c:315)
[0x8116588] main input debug: `luckynight.wma' successfully opened

```

I don't understand why the gui will not play this file, the slider moves across but no sound. Mind you slackware 12.2 uses a version of gcc that vlc claims is too old so perhaps this is the problem... Do you have the same issue or can gui and cli play this for you?

**Edit:** There must be a gui setting to allow the use of the external codecs which I cannot work out. I note the wmapro file WMVHDsplash.wmv now plays as well, but cli only!

Andrew

---

### Post by mc4man on 2009-05-31
I haven't tried a 1.x since last post, will try later today. The 'problem' then seemed to associated with the qt interface, the **very** short-term solution was to delete the vlc-qt-interface.conf. (in ~/.config/vlc, noting that "solution" is far from an apt description

It had been mentioned to me by JB at videolan that something in 1.x needed fixing concerning the dmo loader so it's possible the issue has migrated elsewhere in the last few weeks.


((wmal (0x163) was to be added to the source, removing the need to edit in as previously described, curious to see if it has been.

What version of gcc does slackware use?, though I doubt it's an issue here.

Edit:
Well it's been added to the source so the issue would be with the loader itself (or it and the qt interface), will see shortly
 > /* WMA 3 */
    { VLC_CODEC_WMAP,   "wma9dmod.dll", &guid_wma9 },
    { VLC_CODEC_WMAL,   "wma9dmod.dll", &guid_wma9 },



---

### Post by mc4man on 2009-05-31
There appears to be no change in the behavior.

Stating vlc from the cli with a target file (ie. vlc ~/luckynight.wma ) is the basically the same internally as starting the gui **without** an existing vlc-qt-interface.conf.

What will happen is you can only play 1 file that requires the loader successfully, then any add. files will play with no audio. (unless you close vlc and reopen from cli with a new target or delete the qt-..... file before re-opening vlc.

As a small test to compare here with slackware.

Create a folder and put a couple of wma files inside and then make an .m3u file  either with absolute paths or just list the tracks and put the <whatever>.m3u inside the folder.

Then either open vlc from cli with a target of the .m3u or delete the qt...file and open the gui and load the .m3u.

What happens here is only the first track listed will playback with sound, the others will play, but no sound.

I guess the good news is that this is a qt/dmo loader issue, not specially  wmal, so I'd anticipate more interest in it being resolved. (unlike having wmal in the first place, which wasn't addressed till I brought up that there was no reason for it not to be included and was simple to do so

The possible bad news is specific qt issues were abandoned unresolved in 0.9.x, hopefully that's not the case here.


(( noting that the loader, wmal, ect. work perfectly in 0.9.9a



Edit; (under the heading of 1 step above worthless

I guess a temp. workaround for single files would be to make a script that deleted the qt-....file and then opened vlc on the target file. 
It could be set as a r. click 'open with' option or d. left click file association
It  would also need to close vlc after playback and unfortunately you'd lose the geometry settings
noting that vlc has a cli option "--play-and-exit"


re-edit - noting that I only know commands so 'scripts' I make reflect that
A script named test in my home/bin, then set a right click option 'open with test' and a double l.click ***.

```
#!/bin/bash
gnome-terminal -e "rm /home/doug/.config/vlc/vlc-qt-interface.conf"
vlc --play-and-exit "$1"
```

Actually all that's needed is this - keeps the geometry
```
#!/bin/bash
vlc --play-and-exit "$1"
```

---

### Post by andrew.46 on 2009-05-31
Hi mc4man,

> **mc4man said:**
> The possible bad news is specific qt issues were abandoned unresolved in 0.9.x, hopefully that's not the case here.

That would be a great pity, particularly for a milestone release like 1.0. I saw on the videolan forums you [single-handedly pushed the wmal issue]("http://forum.videolan.org/viewtopic.php?f=13&t=59355&p=198244"), are you going to keep trying with this one?

**Edit:** Slackware 'shortfall' to the vlc installer is glibc, vlc wants 2.8 or newer slackware 12.2 runs 2.7. Newer version in the upcoming slackware 13 but alien bob includes a patch to remove the check in configure.ac.

Andrew

---

### Post by mc4man on 2009-05-31
I'll probably wait a bit and see what develops, though now that you've provided an alternate way, maybe I'll start a new thread.
In other words, while I knew the vlc-qt.....file itself wasn't the problem. though it's removal does allow playback, posting just that was somewhat sketchy. (I think I did anyway 

Combine that now with leaving the vlc-qt.... file and starting a new instance of vlc with a specific target also allowing playback, should, I'd think, help to narrow the problem down. (though they may know the 'problem' but not the solution.

Overall there are some continuing issues with the qt interface that seem to morph from working to almost working to not at all to almost working, .....
Certainly problems opening directories either from vlc or vlc from the dir. continue to exist in some form, though vlc from a dir. seems to be the best bet. (at least in 0.9.9a

I've yet to see a VIDEO_TS folder open properly (stop parsing at VIDEO_TS.ifo) and dir.'s containing tracks may or may not load into the playlist properly, and when they do, may or may not start on the first track, ect. ect.

The day I see that the "Allow only one instance" and the "Enqueue files when in one instance mode" working together properly will be a revision I hold on to. (though I have created a .desktop solution to that for the moment

---

### Post by andrew.46 on 2009-05-31
Hi mc4man,

> **mc4man said:**
> Overall there are some continuing issues with the qt interface that seem to morph from working to almost working to not at all to almost working, .....

Well my existing copy of vlc 1.0 rc2 is compiled *statically* against qt 4.4.3 so I shall recompile against 4.5.1 as a *dynamic* library (this is the installed library I use for VirtualBox and SMPlayer) and see if the new vlc and new qt will work any better together. Trouble is on my poor old machine this takes a good 2-3 hours as all the other libraries are compiled at the same time and statically linked.

Andrew

---

### Post by mc4man on 2009-05-31
> I shall recompile against 4.5.1 as a dynamic library
that may prove interesting
> poor old machine this takes a good 2-3 hours
my main desktops were high end  p4's, now just outdated. I'm amazed at how fast things go on my little core2duo laptop, I can actually watch mplayer be built.

For the very few, if any, who want a single play solution for dmo and 1.x vlc, nautilus actions also works quite well ala the script/command above. Suits me fine as i tend to run a lot off of the r,click.
(Probably the 3rd best thing I love about linux is the depth of the r. click

(2nd screen is an action for proper queuing, can also be made into a userapp.desktop via the r click -> open with -> open with custom command, then edit or directly to distinguish (display name, icon, ect.

> [Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=Vlc Enqueue
Type=Application
Exec=vlc  --playlist-enqueue %f
Comment=Custom definition for vlc
NoDisplay=true
Icon=/home/doug/vlc11/vlc-0.9.9a/share/vlc48x48.png

---

### Post by andrew.46 on 2009-06-01
Hi mc4man,

New qt made no difference so I have made an account on vlc forums and see if I can get any joy there.

Andrew

---

### Post by mc4man on 2009-06-05
> see if I can get any joy there.

Atm apparently not. I'm somewhat taking no response to mean there's no answer to give other than to confirm it's broken (though even just that would be useful.

I may post a bit more 'far ranging' post tonight to see if it gathers some response (ie. that the initiating the loader is broken for all dmo codecs

The only exception seems to be wma2, which while defined as a dmo for decoding, is actually done by  avcodec instead and consequentially works.

The difference between 0.9.x and 1.x is much greater than would be typically expected, that's probably  a significant factor.

---

### Post by andrew.46 on 2009-06-05
Hi mc4man,

> **mc4man said:**
> Atm apparently not. I'm somewhat taking no response to mean there's no answer to give other than to confirm it's broken (though even just that would be useful.

I may post a bit more 'far ranging' post tonight to see if it gathers some response (ie. that the initiating the loader is broken for all dmo codecs

One big difference between your successful post and my own post is that your post isolated a problem *and* suggested a fix whereas my post only mentioned a problem. But this is one is a bit beyond my skills...

I shall watch the vlc forums with interest :-).

Andrew

---

### Post by mc4man on 2009-06-06
perhaps manana, though...

I was thinking that while wma2 could be decoded by the dmo loader and is defined in dmo.c, vlc gives it to avcodec instead. Now in the case of wma3 (pro) it doesn't, and to some extent rightly so, ffmpeg by default can't decode wmap.

But we know it can with the wmapro patch, so I thought let's have vlc ask avcodec to decode wmap instead of using the loader.

To some extent this is worthless on 0.9.9a, the loader works fine, but i know 0.9.9a fairly well so that's what i used to test the theory. (I've no doubt 1.x can also be adjusted, maybe not by me, will test this weekend to see....?

Anyway, as a worst case, if the loader remains borked, then there would be 2 alternatives for wmv3 with wmap audio, and just the one for wmal audio (I haven't seen any video with wmal.

The first for both would be to leave vlc alone and use the single instance, single play right click script I mentioned. That's worked fine as far as I've tried.

The other for wmv3 and wmap would be to patch vlc to use avcodec instead. (and obviously have a wmapro patched ffmpeg

Ex. with wma3(pro) audio

> 
[00000409] asf stream debug: read "codec list object" reserved_guid:0x86d15241-0x311d-0x11d0-0xa3a400a0c90348f6 codec_entries_count:1
[00000409] asf stream debug:   - codec[0] audio name:"Windows Media Audio 9.1 Professional" description:"384 kbps, 48 kHz, 2 channel 24 bit 2-pass VBR" information_length:2
....................
[00000410] asf demux debug: found 1 streams
[00000402] main input debug: selecting program id=0
[00000410] asf demux debug:[COLOR="Blue"] added new audio stream(codec:0x162,ID:1)[/COLOR]
[00000410] main demux debug: using demux module "asf"
[00000410] main demux debug: TIMER module_Need() : 36.926 ms - Total 36.926 ms / 1 intvls (Avg 36.926 ms)
[00000402] main input debug: looking for a subtitle file in /home/doug/
[00000412] main decoder debug: looking for decoder module: 32 candidates
[00000412] avcodec decoder debug: [COLOR="Blue"]libavcodec initialized [/COLOR](interface 3415296 )
[00000412] avcodec decoder debug: ffmpeg codec (Windows Media Audio 3) started
[00000412] main decoder debug: [COLOR="Blue"]using decoder module "avcodec"[/COLOR]
[00000412] main decoder debug: TIMER module_Need() : 51.839 ms - Total 51.839 ms / 1 intvls (Avg 51.839 ms)
[00000412] main decoder debug: thread started
[00000412] main decoder debug: thread 2929707920 (decoder) created at priority 5 (input/decoder.c:217)
[00000402] main input debug: `/home/doug/wpro.wma' successfully opened




The other possibility is that at some ...? point  wma3 will be added to ffmpeg, in which case vlc would have no reason not to switch from dmo  to avcodec. (or may do so if asked


Edit; though it just dawned on me that in any case this could prove useful for those using 64 bit where w32codecs isn't available, but a patched ffmpeg is...

Re-edit 
Actually even simpler on 1.1 git, works fine, and for 64 bit would fit into the build process anyway.
 0.9.9x - 1.1 on 64 bit would require one to build x264 and ffmpeg with fPIC, so adding wmapro to ffmpeg would be a trivial addition to build process


Note - for 1.x on hardy libc6 fails ck., disabling mozilla and nls allows build to proceed, - Andrew - do you have link to the script (readable) that disables libc6 ck.? (glib

---

### Post by mc4man on 2009-06-13
i also get no joy either over at videolan , (did gut my post for certain reasons.

anyway have tested on a 64 bit install and moving decoding for wma3 (pro) to avcodec will allow playback of wma3 audio amd wmv3 with such audio on a 64 bit vlc install.

(and does for the moment 'fix' wma3 and wmv3 on a 32 bit for the rc3 and git versions on 32 bit

---

