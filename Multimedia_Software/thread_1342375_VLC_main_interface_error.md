---
title: "VLC main interface error"
date: 2009-11-30
forum: Multimedia Software
---

### Post by futureismo on 2009-11-30
I am running 64 bit Ubuntu 9.10, which was upgraded from my old 9.04 install.
Unfortunately since upgrading I have found that VLC does not work, movie player works as does mplayer when set to use X11 output. On trying to open a video file vlc crashes after playing a second of audio.
Running vlc -v
I get the results
```
VLC media player 1.0.2 Goldeneye
[0x26835d8] main demux warning: no access_demux module matching "file" could be loaded
[0x267f378] main interface error: no interface module matched "globalhotkeys,none"
[0x267f378] main interface error: no suitable interface module
[0x258a888] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x258a888] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.

``` And then when I attempt to play the video:
```
 m_el[mi_level] == NULL
 arrrrrrrrrrrrrg Up cannot escape itself
[0x395ce18] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:384000
[0x395b248] pulse audio output: No. of Audio Channels: 6
[0x463b668] scaletempo audio filter warning: bad input or output format
[0x463b668] main audio filter warning: no audio filter module matching "scaletempo" could be loaded
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[0x395b248] main audio output warning: PTS is out of range (-25679), dropping buffer
QPainter::begin: Paint device returned engine == 0, type: 1
[0x395b248] main audio output warning: output date isn't PTS date, requesting resampling (88164)
[????????] x11 video output error: X11 request 133.19 failed with error code 8:
 BadMatch (invalid parameter attributes)
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  133 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  101
  Current serial number in output stream:  102

```Launching VLC without the gui through the command cvlc does get the video to play, but obviously without any controls for it.
A quick search shows this problem has crept up before and I have used ```
apt-get purge vlc
``` and ```
vlc --reset-config --reset-plugins-cache
``` a number of times to no avail but do not want to try any suggestions on other older threads in case they do not apply in this circumstance and would just cause more problems.
Any suggestions would be very welcome.

---

### Post by mc4man on 2009-11-30
You could try setting your video output in vlc to X11 also ( tools -> preferences -> video icon, in the drop down on right.

What's interesting is you seem to be able to use Xv output, just not with the embedded video/interface

you could also just try keeping them separate, you'll still get controls in full-screen (if enabled, both settings in tools -> preferences

Whether this would have any effect on the embedded video don't know, see [here]("http://ubuntuforums.org/showthread.php?p=8414554#post8414554") about qt config and vlc

---

### Post by Z06Gal on 2009-11-30
> **mc4man said:**
> You could try setting your video output in vlc to X11 also ( tools -> preferences -> video icon, in the drop down on right.

What's interesting is you seem to be able to use Xv output, just not with the embedded video/interface

you could also just try keeping them separate, you'll still get controls in full-screen (if enabled, both settings in tools -> preferences

Whether this would have any effect on the embedded video don't know, see [here]("http://ubuntuforums.org/showthread.php?p=8414554#post8414554") about qt config and vlc


mc4man, i just gave this a shot so that the video is separate and at least i got a screen although it is all black so that somehow fixed the transparent or invisible issue.  I'm not sure what to call it so I hope this makes sense.  Maybe we are getting closer to solving it.  Thanks.

---

### Post by Z06Gal on 2009-11-30
mc4man,

I got my video back and all I did was set my video to be separate as it wasn't and I don't know how that got changed in the first place.  Anyway, I reset that and put my video output back to default settings and it went right to playing.  This stuff amazes me.  Lol.  Thanks because it was one of your posts that made me think of it.  My video has always been separate and I've never had an issue with it that way.  I changed it somehow and I have no idea when that was.   Oh well, it works which is all that matters.  Thanks again. :D

---

### Post by futureismo on 2009-12-01
Apologies for the time taken to get back, my router started playing up last night.
I've tried setting the output to x11, unfortunately that doesn't do anything and I still can't play any videos unless through the command cvlc.

---

### Post by futureismo on 2009-12-02
Bump. Any suggestions?

---

### Post by mc4man on 2009-12-02
> I've tried setting the output to x11...

Did you try separating the controls and video window? (tools -> preferences -> uncheck "Embed video in interface"

Otherwise - are you running cairo dock?

---

### Post by HappyFeet on 2009-12-02
Completely remove vlc and then do:
```
sudo apt-get clean && sudo apt-get autoremove
```
Then go [here]("https://launchpad.net/~c-korn/+archive/vlc") and install the latest vlc.

---

### Post by futureismo on 2009-12-03
> **mc4man said:**
> Did you try separating the controls and video window? (tools -> preferences -> uncheck "Embed video in interface"

Otherwise - are you running cairo dock?

Thank you very much. Don't know how I passed by that check box knowing it was an interface problem. I am running Cairo but this method has successfully got vlc working. Again, thanks very much for everyone's help. I really appreciate it.

Thread will be marked as solved.

---

