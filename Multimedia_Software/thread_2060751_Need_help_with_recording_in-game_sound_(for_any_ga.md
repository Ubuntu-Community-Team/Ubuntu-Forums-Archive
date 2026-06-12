---
title: "Need help with recording in-game sound (for any game)"
date: 2012-09-20
forum: Multimedia Software
---

### Post by myromance123 on 2012-09-20
Hey there,
I have an issue with recording the internal audio for Ubuntu 12.04 when I record either gameplay videos or simple tutorials etc.

The software that I currently use is (gtk)RecordMyDesktop, installed from the USC.

**_[SIZE="3"]What I have tried:[/SIZE]_**
I have tried two methods thus far to record the internal audio.
First, I have and most frequently used a software called OutRec.
[http://outrec.sourceforge.net/](http://outrec.sourceforge.net/)

It produces a significantly small audio file, which is good. I've tried storing the audio in .wav(default), .ogg and .mp3. With each, the same issue reoccurs. After a good several minutes (usually after the 2 minute mark) the sound ITSELF will become unsynchronized (with the video I mean).
**It's almost as if the sound recording is skipping a beat and adding rubbish extra data.**

So, after struggling with OutRec's audio files in Kdenlive and Openshot (cutting and repositioning) I can usually get a substantially close enough approximation to sync the sound with the video file. Sometimes however its so bad, that no amount of cutting and moving the sound will fix it.

Thus, after recently being successful in getting RecordMyDesktop to record internal audio I've gone ahead and used it to record my Sauerbraten gameplay (as a simple test). 1 hour's worth of gameplay, and the end result was indeed predictable. Just as with OutRec, RecordMyDesktop messes up the sound synchronization as well!
It's so frustrating!

This leaves me with good video + audio for about 2 minutes of recording, and everything after that is either total rubbish or requires extremely tedious editing to sound right.

I have tried to get myself aquainted with GLC, but it is seriously damn hard. I produced some rather large, unplayable and uneditable files. This was going solely off GLC's documentation and one guy's website tutorial.

I have yet to try Kazam Screencaster, but I doubt it can record games. Can it? Will it or does it have the same sound/audio synchronization problem?

[B][U][SIZE="3"]
What I need:[/SIZE][/U][/B]
What I ask of you is, at the very least, to help list out some alternatives I can try for:
1. Recording video with audio (simultaneously)
2. Recording internal audio with video recording in another software (Separately)

Or, if you are more technically inclined, you may guide me in attempting to resolve or discover this internal audio recording problem.

Are there other unknown or seriouly underground software that I can test/experiment with? Outrec was pretty hard to find out about.

**_[SIZE="3"]About my Computer/System/Rig:[/SIZE]_**

I have an **ALC892 Realtek** sound device if that makes a difference.
I assumed it was a driver issue, and have already installed the HD Driver from Realtek here:
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false)

So I am currently on Linux Driver (3.0), which does support ALC892.
I have no other audio issues at all. Playing songs and movies are fine.
Heck, recording from my mic on Audacity is perfect!

When recording native apps or games, sound usually becomes unsynchronized after the 2 minute mark. With WINE apps however, recording is COMPLETELY messed up. OutRec produces GB's worth of unusable files, and RecordMyDesktop acts as if there is no sound being produced.

My recordMyDesktop settings:
FPS: 30
Encode on the Fly: NOT ticked
Zero Compression: ticked
Quick Subsampling: NOT ticked
Full shots at every frame: ticked

Channels: 1
Frequency: 22050
Device: pulse

Under Misc,
MIT-Shm extension: ticked
Include Window Decorations: ticked
Tooltips: ticked
Outline Capture Area on Screen: ticked
Reset Capture Area: ticked

On another unrelated problem to this post, I have been completely unable to record full screen games with RecordMyDesktop ( I simply get a black screen and my cursor, yet sound recording works fine here. Dammit).

My system specs:
CPU   - AMD Phenom II x4 965 3.4GHz
GPU   - AMD Asus RadeonHD 6870 (Catalyst 12.8)
Mobo  - M4A88T-V EVO/USB3
RAM   - 8GB DDR3 Corsair 1333MHz

**[FONT="Arial Black"]Ubuntu 12.04 64Bit[/FONT]**
A big thanks in advance for any form of help given.

---

### Post by myromance123 on 2012-09-21
I thought I'd give GLC another chance.
Tried glc-capture sauerbraten, the game starts up no problem.

However, upon clicking Shift+F8 (to start and stop recording) I am presented with this error:

```
[   2.16s       file error ] can't open sauer_client-32336-0.glc: Permission denied (13)
[   2.16s       main error ] can't start capturing: Permission denied (13)
[  14.81s       file error ] can't open sauer_client-32336-0.glc: Permission denied (13)
[  14.81s       main error ] can't start capturing: Permission denied (13)
```

Regardless to say, I have tried using gksudo, sudo and even sudo su. When running as root, the game plays but its as if glc-capture is not read whatsoever. I'll give it a go on Torchlight or may S.P.A.Z but I don't really have my hopes up.

I've read that Istanbul is a screen recording software that can capture games, but that it's also extremely heavy on resources which could be bad.
[B][U]
EDIT:[/U][/B] 
I've managed to get GLC to record the survival zombie game Violetland.
Problem is that it is without sound. I have NOT disabled sound, it just won't record sound from the game. I am not recording via mic when attempting this.

[IMG]http://i519.photobucket.com/albums/u360/my-_-romance/VioletlandGLC_zps062bd3df.png[/IMG]


I've attemped to run _**glc-capture with Torchlight**_ as well, but it does nothing. The game runs fine. However, no .glc file is produced. Pressing Shift+F8 seems to do nothing. The terminal shows no sign of registering that I've pressed Shift+F8.
```
glc-capture '/usr/local/games/Torchlight/Torchlight.bin.x86_64'
```

I have also tried running _0 A.D at fullscreen._
This one's really buggy. When playing back the .glc file, the first several seconds are just pure black nothingness. After that, it will show a fast-forwarded version of the recording. STILL NO SOUND recorded. No idea why, no error messages or anything from the terminal.
```
glc-capture 0ad
```

**_EDIT 2:_**

```
glc-capture -s '/usr/local/games/Torchlight/Torchlight.bin.x86_64'
```

*Note, the -s parameter makes GLC record as soon as Torchlight starts.
With this, there's no need for pressing Shift+F8 to start/stop recording.

This seems to make recording Torchlight work. _HOWEVER_, here are issues that exist when doing this:
1. No sound
2. Loading screens are NOT recorded (stuck screen of last render)
3. glc-play issues segmentation fault after watching .glc file
3. When issuing glc-play to watch the .glc file, two glc-play windows open up. One small, one large. Large is where the game is. Small one is just black and stuck. Named ctx1 and ctx2 respectively.

---

### Post by myromance123 on 2012-09-22
I have further tested GLC with Violetland.
About 10 minutes of gameplay.

```
glc-capture --force-sdl-alsa-drv violetland
```

This is the only way for me to capture game sound and video with GLC.
However, as with RecordMyDesktop and OutRec there is a serious issue with sound recording.

To summarise:
RecordMyDesktop messes up sound after about the first 2 minutes of recording.
OutRec messes up sound IF there exists moments of silence (S.P.A.Z), OR sound is continuous (Sauerbraten bgm).
GLC on the other hand, will have 1 second of sound play. Then the video will run without sound for about a 1 minute maybe longer. Then sound will come in (which is meant to be played earlier in the video). Completely unsynchronized.

Looks like there really is no way to record a game in fullscreen, where both audio and video are recorded by one app with adequate synchronization. I'm going to give Istanbul a go, then Kazam. After that, there's nothing left that I know of that I may try. Wish I knew enough about OpenGL so that I could make an app for this.

**_EDIT:_**
I have further tested GLC. This is one piece of recording software that really is not stable in any way.

```
glc-capture -s --out=RochardGameplay '/opt/rochard/Rochard.app'
```
Recorded Rochard from HiB6 at 1080p fullscreen with OutRec for sound. Sound was not a problem (OutRec seems to work properly when used in conjunction with GLC, so far at least).
The video recording was. GLC decide that it would only record the top left part of the screen for the first 15 minutes of recording. After which it switched to recording only the bottom right. WTF seriously.

I then recorded Violetland at 1080p fullscreen with OutRec for sound.
This one worked out perfectly! Sound was synchronized, gameplay recording was smooth. Yet I did nothing differently! You can see it here:
[https://www.youtube.com/watch?v=sHbqebfkfHs](https://www.youtube.com/watch?v=sHbqebfkfHs)
I'm going to take it that GLC works on a per-game basis.

I have asked another Youtuber who's recorded Guild Wars 2 on Linux, and he recommended x11grab with ffmpeg/avconv. I've never used these before, so I'm going to look for tutorials and if anything is successful I'll post back here how it went. Still haven't given Kazam a go, but its installed.

Istanbul does not work on Ubuntu 12.04. I run it, it sits idle. No errors, no nothing. Literally blank. Only way to close it via GUI is kill process in System monitor, or Ctrl+C in the terminal.

---

### Post by myromance123 on 2012-10-26
Alright, this is pretty much my last post in this.
I have tried Kazam. In Ubuntu 12.04 it has a memory leak bug. Causes Ubuntu 12.04 64Bit to hang, forcing a manual shutdown. I know this because it happens to me everytime I used Kazam. A shame, since Kazam has a great UI and for the very few seconds of video I did record, it did it well with sound (both mic and system audio).

No words for Istanbul. Can't get it to work at all.

Gave ffmpeg a go several times. It does not respect the aspect ratio of the screen or size I set it to. It ends up with a vertically squished video everytime. Fullscreen games result in a blackscreen (just like RMD/Kazam and sometimes GLC). Not good with sound either, ends up unsynchronized as well.

I discovered a new screen recording application called Gamecaster, which relies on GLC. You can read about it here:
[http://www.ubuntuvibes.com/2012/10/gamecaster-updated-for-ubuntu-1210.html]("http://www.ubuntuvibes.com/2012/10/gamecaster-updated-for-ubuntu-1210.html")
[https://launchpad.net/gamecaster]("https://launchpad.net/gamecaster")

However, for me it did not work whatsoever. Everytime I tried to run a game through it, it would not start the game. Tried manually going to the game's executable file (used Torchlight, Rochard, and Amnesia as tests) and it also did not work.

Btw, outRec does not work in Ubuntu 12.10 for anyone reading this. outRec was developed using Gambas2, whilst Ubuntu 12.10 only ships with Gambas3 so we're out of a good sound recording tool now.

Since I can't find anything, I am developing a basic sound recording tool using Python and Gtk+3. I'm thinking of going with PyAudio for sound recording, but have only managed to record microphone input. Still trying to figure out how to make it take the system's audio instead (if it is at all possible).

[IMG]http://i519.photobucket.com/albums/u360/my-_-romance/first_Ubuntu_app_2.png[/IMG]

tl;dr I have not found a solution. No way to properly record fullscreen games and/or just simply record the system's audio.

---

### Post by danielbauwens on 2012-10-26
I think for recordmydesktop you have to download jack.
Where you write "pulse" right under there is a area for jack.
If you download that, you can also record ingame sound (normally).

Daniel

---

