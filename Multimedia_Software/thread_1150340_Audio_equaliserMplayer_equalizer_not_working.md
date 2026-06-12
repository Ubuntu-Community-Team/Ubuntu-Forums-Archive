---
title: "Audio equaliser/Mplayer equalizer not working"
date: 2009-05-06
forum: Multimedia Software
---

### Post by dE_logics on 2009-05-06
The m-player equalizer is frozen...any solutions?...no it never worked, so this is not a problem that popped up one day.

If not do we have a general equalizer?...like what comes with with the sigmatel drivers (mostly on intel based chipsets)?

---

### Post by andrew.46 on 2009-05-06
Hi dE_logics,

You might want to have a look at the equalisers provided by SMPlayer, the best frontend for MPlayer. I attach a screenshot of these in action. Works quite nicely...

All the best,

Andrew

---

### Post by mc4man on 2009-05-06
I'd also go with smplayer and forget gmplayer.

If you wish to unfreeze the equalizer in gmplayer try in preferences -> audio, enabling the equalizer and then close mplayer.
Then reopen and start playing a track, *then* r. click -> equalizer. You need to see some entries in white box. (screen


Edit : the other "oddity" of gmplayer is that while with a 5.1 setup it's pretty much the only player to not upmix 2 > 6 ch from a stereo source.  The oddity is to get only 2 speaker output from a stereo source the audio driver device needs to be configured to plug=surround51, default produces upmixing to 6 ch.

---

### Post by dE_logics on 2009-05-06
Yeah...I enabled the equalizer...how stupid of me!!

---

### Post by dE_logics on 2009-05-06
But the settings are getting lost once I close Mplayer!

---

### Post by dE_logics on 2009-05-06
Where's the equalizer for SMplayer?...I see it for the video, but no audio.

---

### Post by mc4man on 2009-05-06
I'm on a  jaunty live cd atm but as i recall under the audio tab (may be greyed out if not playing something
Make your setting's changes, and then you can set 'as default' (will remain persistent

---

### Post by dE_logics on 2009-05-06
Ok...thanks!...I got the latest SMplayer, and it has the equalizer.

SMplayer has a dependency with Mplayer...so I gotta have both.

---

### Post by dE_logics on 2009-05-06
Nope...there's no such option as set as default (in Mplayer).

---

### Post by mc4man on 2009-05-06
> Nope...there's no such option as set as default (in Mplayer)

The "set as default" is in smplayer, if your referring to gmplayer then nothing will have changed though *one* of the points of installing smplayer is to not use mplayers gui (gmplayer

If your referring to mplayer from the command line then you need to specify in the command or add using an equalizer and it's settings in ~/.mplayer/config
(and probably other ways to achieve the same thing

I do sometimes use the cli mplayer for certain hq audio tracks that many other players can't handle and happened to have the line in my conf for reasons other than actually using it. (set at flatline

> # Write your default config options here!

af=equalizer=0:0:0:0:0:0:0:0:0:0


So for this route you can retrieve your smplayer setting's values by going Ctrl+m with focus on smplayer 

Ex. from mplayer log
> /usr/bin/mplayer -noquiet -nofs -nomouseinput -sub-fuzziness 1 -identify -slave -vo xv -ao alsa -nokeepaspect -framedrop -nodr -double -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 71303180 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/doug/.config/smplayer/styles.*** -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp ISO-8859-1 -aid 0 -subpos 100 -volume 100 -cache 2000 -ss 110 -osdlevel 0 -vf-add screenshot -slices -channels 6 -af scaletempo,[COLOR="Red"]equalizer=0:0:0:0:0:0:0:0:0:0[/COLOR] -channels 6 -sid 1

---

### Post by dE_logics on 2009-05-06
> af=equalizer=0:0:0:0:0:0:0:0:0:0

This is not working for Mplayer.

Yeah I got those SMplayer settings.


I use different equalizer presets for movies and songs...so I wondering about about making SMplayer for the movies, and Mplayer for the songs.

---

### Post by mc4man on 2009-05-07
I think maybe your confusing mplayer (cli) with it's gui - gmplayer.
There seems to be no persistent equalizer for gmplayer

> so I wondering about about making SMplayer for the movies, and Mplayer for the songs. 

How about smplayer for movies and a music player for songs that either has preset(s) you like or holds the settings

I use amarok 1.4 and while I don't use the equalizer it has presets and lets you create new ones. I'm sure some other players do the same.

While you can play music from the commad line mplayer, I can't imagine that many people would simply to use an equalizer, I think you'd find it somewhat inconvenient.

You could though create any number of mplayer 'presets' as scripts and launch mplayer with the appropriate one, but I don't believe this is what you had in mind in practice

Ex. (a script in /home/bin named rb (preset for rhythm & blues
This would be your 'music player' (controls limited to available keyboard bindings
> 
doug@doug-desktop:~/music/m4a/Various-Standing In The Shadows Of Motown$ rb
MPlayer SVN-r29188-4.3.2 (C) 2000-2009 MPlayer Team

Playing 01.Joan Osborne-(Love Is Like A) Heat Wave.m4a.
libavformat file format detected.
[lavf] Audio stream found, -aid 0
Clip info:
 name: (Love Is Like A) Heat Wave
 author: Joan Osborne
 album: Standing In The Shadows Of Motown
 genre: 14
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
FAAD: compressed input bitrate missing, assuming 128kbit/s!
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [alsa] 44100Hz 2ch floatle (4 bytes per sample)
Video: no video
Starting playback...
A:  70.1 (01:10.1) of 181.5 (03:01.5)  1.7% 
.....ect. thru all the tracks


---

### Post by dE_logics on 2009-05-07
I don't have gmplayer installed...

> How about smplayer for movies and a music player for songs that either has preset(s) you like or holds the settings

Yeah but I was talking about using mplayer for review purposes (for songs), I use Amarok for proper listening purposes from a playlist (which consist of all songs arranged by track names), so if I use it for reviewing purposes, the information about the last playing song will be lost, furthermore I'll have to reload the plalist.

> I'm sure some other players do the same.

:D I think we have none.

> You could though create any number of mplayer 'presets' as scripts and launch mplayer with the appropriate one, but I don't believe this is what you had in mind in practice

no no...I'm not used to an 'invisible' music player :D :D

Thanks for the advice though.

---

### Post by mc4man on 2009-05-08
> I think we have none.

While it doesn't seem too intuitive audacious will let you create presets, save them and then load.

I only spent a few min. trying so this isn't  all inclusive by any means

What seemed to work was adjust the equalizer, then click on preset -> save -> to WinAmp EQF file and pick or create a folder and then name your save. Then to load  -  preset -> from WinAmp EQF file, ... 

Saving to file option doesn't seem to work ...?

From post 1
> The m-player equalizer is frozen.

That is gmplayer
.....................

As far as Amarok, I'm on the opposite end from you, there's nothing in my collection
Basically run from some right click actions on files, folders  such as "load in amarok" (loads and plays, removes playlist if any
"append in amarok" ( appends to end of current playlist ) ,ect.
For whatever my reasoning I also  use absolute path .m3u's for custom playlists, mixes, quick access from desktop, ect.

---

### Post by dE_logics on 2009-05-08
Thanks for telling me about audacious...really appresheate it.

I gotta think upon what software to use for what purpose.

Nope the save presets are not working :cry:

To bad we don't have jetaudio for linux...else it was the master of all media players.

> That is gmplayer

That's simple mplayer.

Yeah I too save my playlist to m3u files.


Anyway...thanks a lot!

---

### Post by mc4man on 2009-05-08
> Nope the save presets are not working

If you mean in audacious pick this option, not "save" > save -> to WinAmp EQF file


There also appears to be a way to then import them back, but didn't seem to practical (in this case they're imported without distinguishing name, (didn't spend much time on to understand

The whole  "save and load process' seems a bit unwieldy, click on 'preset', click on either save -> "to WinAmp EQF file" or to load ->  "from WinAmp EQF file", browse to save folder and choose preset you previously created (or save there

A time saver if you do figure out and use would be to create a folder in home named "A presets"
That way it will become the first folder listed in audacious's browse box and be picked (highlighted) by default ( both for loading from and saving to

I get the feeling if you download real WinAmp EQF files you can import them and they'll be more readily available

---

### Post by dE_logics on 2009-05-09
> If you mean in audacious pick this option, not "save" 

It worked.

Thanks!:)

> There also appears to be a way to then import them back, but didn't seem to practical (in this case they're imported without distinguishing name, (didn't spend much time on to understand

:lol: then what's the use of exporting?...ofcourse we can import.

Ok...thanks for all the help!

---

### Post by dE_logics on 2009-05-10
Just wait a sec...audacious is having problems playing wav...its skipping wave audio.

---

### Post by brunosemedo on 2010-01-31
Thanks !!! SMPlayer saves the equalizer settings perfectly!

Long live LINUX!

---

