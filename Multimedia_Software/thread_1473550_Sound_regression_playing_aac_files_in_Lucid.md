---
title: "Sound regression playing aac files in Lucid"
date: 2010-05-05
forum: Multimedia Software
---

### Post by matthewbpt on 2010-05-05
I currently have a problem with all my Lucid installs, whereby certain aac files (.m4a extension) cannot play properly anymore. When played the songs skip constantly and play high-pitched noise every split second between the real audio. I tested the same files in Arch, in a Karmic live cd and in Windows and they plays fine in all of them. I have tested this on 3 Lucid installs, one an upgrade, the other two fresh installs, and the problem is present in all of them.

Funny thing that I just discovered, the files are unplayable in Rhythmbox, Vlc, Totem and Audacious, but play perfectly in XBMC and Aqualung. What is different about how these players play the audio files?

Here's a link to one of the offending files [http://drop.io/lwx4fgt](http://drop.io/lwx4fgt) , anyone with more expertise with sound problems care to help, it's quite an annoying bug as I have hundreds of music files with the same problem. I want to post a bug in launchpad but i dont know that to post the bug against,

Matt

EDIT: I've submitted a bug report, [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/575798](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/575798) , can anyone else confirm the bug?

---

### Post by matthewbpt on 2010-05-05
bump

---

### Post by mc4man on 2010-05-05
Not exactly sure what's up with your file(s) yet.

Of interest  - the sample plays fine in browser, but not locally as you described.

But if it's decoded with ffaac it will play fine (vs. faad or libfaad which most players will default to.

So ffplay will decode ok as will mplayer as such

 > mplayer  -ac ffaac '/home/doug/Downloads/new.m4a'


---

### Post by matthewbpt on 2010-05-05
That's interesting, so this is a bug in faad then? Should I change the affected package to faad in the bug report?

---

### Post by mc4man on 2010-05-05
edit - wrong assumption

> Complete name                    : /home/doug/Downloads/new.m4a
Format                           : MPEG-4
Format profile                   : Apple AAC audio with iTunes info
Codec ID                         : M4A 
File size                        : 161 KiB
Duration                         : 10s 7ms
Overall bit rate                 : 132 Kbps
Writing application              : Lavf52.31.0

Audio
ID                               : 1
Format                           : AAC
Format/Info                      : Advanced Audio Codec
Format version                   : Version 4
Format profile                   : Main
Codec ID                         : 40
Duration                         : 10s 7ms
Bit rate mode                    : Variable
Bit rate                         : 129 Kbps

---

### Post by matthewbpt on 2010-05-05
Hmm, well I encoded the affected files before Lucid was released, so I didn't encode them with Lucid's ffmpeg. I think I used Rhythmbox inbuilt CD ripper.

---

### Post by mc4man on 2010-05-05
> Hmm, well I encoded the affected files before Lucid was released, so I didn't encode them with Lucid's ffmpeg. I think I used Rhythmbox inbuilt CD ripper.

Well playing your sample with pretty much the same mplayer builds in karmic and lucid - it decodes properly in karmic, not in lucid. ( mplayer doesn't use the system libfaadX

Your best bet long term is not to use gstreamer apps to encode to m4a ( or at least if the gstreamer profile is using Main  instead of LC. 


Edit : what the difference is on lucid don't know - but changing the gstreamer profile to encode to Main, the resultant .m4a shows the decoding problem  in lucid with all players except ffplay inc. mplayer. (unless mplayer uses ffaac.
So don't think the issue is libfaad2, just something about lucid

---

### Post by andrew.46 on 2010-05-06
Hi,

I will admit that I am not testing this file on Lucid but the svn MPlayer can play it with either faad or ffaac:

```

andrew@skamandros~/Desktop$ **[COLOR="Red"]mplayer -ac faad new.m4a [/COLOR]**
MPlayer SVN-r31137-4.3.3 (C) 2000-2010 MPlayer Team

Playing new.m4a.
libavformat file format detected.
[lavf] stream 0: audio (aac), -aid 0, -alang und
Clip info:
 major_brand: M4A 
 minor_version: 512
 compatible_brands: isomiso2
 encoder: Lavf52.31.0
==========================================================================
Forced audio codec: faad
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
AUDIO: 44100 Hz, 2 ch, s16le, 128.6 kbit/9.11% (ratio: 16070->176400)
**[COLOR="Red"]Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))[/COLOR]**
==========================================================================
AO: [oss] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   9.7 (09.6) of 10.0 (10.0)  6.9% 

Exiting... (End of file)

```

```

andrew@skamandros~/Desktop$ **[COLOR="Red"]mplayer -ac ffaac new.m4a [/COLOR]**
MPlayer SVN-r31137-4.3.3 (C) 2000-2010 MPlayer Team

Playing new.m4a.
libavformat file format detected.
[lavf] stream 0: audio (aac), -aid 0, -alang und
Clip info:
 major_brand: M4A 
 minor_version: 512
 compatible_brands: isomiso2
 encoder: Lavf52.31.0
==========================================================================
Forced audio codec: ffaac
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 128.6 kbit/9.11% (ratio: 16070->176400)
**[COLOR="Red"]Selected audio codec: [ffaac] afm: ffmpeg (FFmpeg AAC (MPEG-2/MPEG-4 Audio))[/COLOR]**
==========================================================================
AO: [oss] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   9.7 (09.6) of 10.0 (10.0)  1.1% 

Exiting... (End of file)

```

I would be interested to see what the Lucid problem is...

Andrew

---

### Post by mc4man on 2010-05-06
> I would be interested to see what the Lucid problem is...

It's a weird one for sure - the bug report is in the first post

On lucid, mplayer will only play with ffaac, yet the same mplayer build will play Main profile aac on anything but lucid.

Redid a vlc 1.0.6 build on lucid that was statically linked to the karmic libfaad (libfaad0), same thing - plays LC aac fine, Main profile is not decoded properly, exact same build on karmic is fine.

And it's not something in matthewbpt file(s) - I set rhythmbox to encode to Main, same thing.

The issue then is people who trusted gstreamer to encode aac in the past (when it used Main), are now left with unplayable files in lucid (well they play - so un-listenable  - if that's even a word...

---

### Post by matthewbpt on 2010-05-06
I wasn't aware of the existence of these different profiles within the aac codec, what exactly is the difference between them?

Edit: This bug is getting more and more annoying, I didn't realise how many files I encoded using this "Main" profile, this needs a fix!

---

### Post by matthewbpt on 2010-05-08
Is there a script I can run which will search for files encoded with the Main profile and transcode them to another profile automatically? I know that's not ideal as transcoding files will produce loss in quality, but at least I'll be able to listen to them.

---

### Post by mc4man on 2010-05-08
The whole thing is too bad.
Not great at scripts here, but thought I'd post a command that would return the profile - maybe it can be used in a script to transcode or produce a list of files affected 
(assuming you may have Main and LC mixed together..?

needs the cli mediainfo installed

```
mediainfo "--Inform=Audio;%Format_Profile%"
```

Ex. on your sample
> doug@doug-laptop:~$ mediainfo "--Inform=Audio;%Format_Profile%" '/home/doug/Desktop/new.m4a' 
Main


(tried to give the bug report a bit of a 'push', we'll see

Edit:
best I could figure out was a script and a command to call it that would create a list of all the .m4a tracks in a parent dir. and subdir.'s, if any, in a 'profile, trackname, location' format  

not what you want so won't bother  posting, but if i could do that then certainly seems possible to do what you do want (main profile tracks sent to an encoder, ect.

---

### Post by mc4man on 2010-05-10
matthewbpt
I'm not sure if we're getting anywhere on that bug - I guess time will tell.

It's possible that the implementation of faad2 in lucid is the issue and a patch of faad2 will resolve. (though maybe something in lucid needs patching instead - if even possible.

There also is a possibility we're going in a bit of a circle - reminds me of when I was trying to get faad decoding restored to xinelibs in lucid - eventually we got on same page.
[https://bugs.launchpad.net/baltix/+bug/496010](https://bugs.launchpad.net/baltix/+bug/496010)

Mr. Tartler  knows more than in 10 secs than I'll ever, so in this case where it's not so clear cut probably best to leave be for the moment and see what shakes out...
(though I'm fairly sure I'm correct as far as mplayer - and while the logic is good concerning mplayer and vlc the  conclusion i may of had (issue in lucid, not faad2),  may be flawed so to speak (or still lead back to faad2 for a fix if one's possible

---

### Post by matthewbpt on 2010-05-11
Thanx for all your help mc4man, hopefully it'll be resolved.

> best I could figure out was a script and a command to call it that would create a list of all the .m4a tracks in a parent dir. and subdir.'s, if any, in a 'profile, trackname, location' format 
Could you post this script if possible, if I grep all the Main profile entries and pipe the location to an encoder maybe I can transcode all of them.

---

### Post by mc4man on 2010-05-11
Ok - though trust me in saying I only know commands and T&E - I'm sure someone could do better (and maybe give you the 'whole ball of wax'

Anyway I changed this up a bit from what I needed to do, will  output this - 
profile <space>  'full path to trackname'

(I just wanted to check all my files in Music and music that I've accumulated since gutsy - turns out i never used gstreamer or had edited the profile.

Not knowing if you have spaces in the path and or tracknames tried to account for that - if you don't - doesn't matter - the 1st rename will be ignored

 

Commented the rename back out - after I was done I wanted the tracknames returned (I do use spaces and other things. ex. (1963) in my tracknames.

If you can figure a way to use this list then leave commented out till done if you have spaces (just rerun command) or if you don't have spaces, it should stay commented out.

```
#!/bin/bash
if [ -d "${1}" ] ; then
  cd "${1}" && rename 's/ /_/g' *.m4a
fi
for f in *.m4a; do mediainfo "--Inform=Audio;%Format_Profile% '$PWD/"$f"' " "$f" | tee -a  ~/[COLOR="Blue"]Documents/format.txt[/COLOR]; done
 #rename 's/_/ /g' *.m4a
```

Blue can be adjusted to suit

I use a ~/bin which makes calling a script or exec easy, command below reflects that.

If you don't have one and want to use just - in terminal
```
mkdir bin
```
Then restart ( should be auto added to your PATH) and then create the script - put in ~/bin and make executable (I named it format2

Or from terminal
```
 gedit ~/bin/format2
```
after pasting, saving then
```
chmod u+x ~/bin/format2
```

For command (adjust blue to reflect the dir. where music files are - don't use just ~/ - trust me on that.

 It will list all sub. dir.'s if any so just use the parent if that's the case - run from your normal terminal

```
find [COLOR="Blue"]~/Music [/COLOR]-type d -exec [COLOR="RoyalBlue"]~/bin/format2[/COLOR] "{}" \;
```

again adjust light blue as needed (/path/to/scriptname if different than suggested

snippet from list
> LC '/home/doug/Music/Jerry Garcia and David Grisman (1991) Jerry Garcia and David Grisman/09_-_Arabia.m4a' 
LC '/home/doug/Music/The Band (2000) Greatest Hits/01_-_The_Weight.m4a' 



Edit: just in case a ppa for mediainfo (need 'mediainfo' pkg. for cli, 
[https://launchpad.net/~shiki/+archive/mediainfo](https://launchpad.net/~shiki/+archive/mediainfo)

---

