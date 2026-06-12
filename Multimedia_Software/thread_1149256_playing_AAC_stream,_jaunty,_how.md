---
title: "playing AAC stream, jaunty, how?"
date: 2009-05-05
forum: Multimedia Software
---

### Post by hardyn on 2009-05-05
i cannot seem to find a codec that will work with the AAC stream from radioparadise.com.

what does one have to do to get AACs to play?

currently i have installed the good/bad/ugly multi and not; and a few applications like songbird and amarok.

Thanks in advance.

---

### Post by mc4man on 2009-05-05
Well the 128k AAc plays fine in firefox or even a bit better in vlc.

Make sure you have libfaad0

I know very little about 'streaming', for vlc I just right clicked on the 128k link and saved it as a .m3u and then opened it in vlc (worked both in 'stream' or in 'open file'

for amarok and rhythmbox just adding the stream to the radio streams list works fine  

[http://stream-ny2.radioparadise.com:8018/](http://stream-ny2.radioparadise.com:8018/)

---

### Post by hardyn on 2009-05-06
what versions of each are you running (ubuntu, songbird, amarok, etc) still no AAC, and there is a growning thread on songbirds site confirming my errors with 904... seems there are some library conflicts.

---

### Post by mc4man on 2009-05-06
Right at this moment I'm on a jaunty livecd, added the url to rhythmbox and amarok 2 and streams fine in both
Last night was using my main install of hardy (default rhythmbox, amarok 1.4, vlc 0.9.9a (worked best in rhythmbox and amarok, vlc wouldn't show songs changes as quickly as those 2, though vlc 'recorded' the stream quite well to a .m4a

screens from jaunty live cd

---

### Post by mc4man on 2009-05-06
And back in hardy with amarok 1.4


((the info on vlc stream, definitly getting the 128k aac stream

> General

Complete name                    : /home/doug/save1.m4a

Format                           : MPEG-4

Format profile                   : Base Media

Codec ID                         : isom

File size                        : 19.8 MiB

Duration                         : 21mn 22s

Overall bit rate                 : 129 Kbps

Encoded date                     : UTC 2009-05-06 06:05:44

Tagged date                      : UTC 2009-05-06 06:05:44

Writing application              : vlc 0.9.9a stream output

Comment                          : QuickTime 6.0 or greater



Audio

ID                               : 1

Format                           : AAC

Format/Info                      : Advanced Audio Codec

Format version                   : Version 4

Format profile                   : LC

Format settings, SBR             : No

Codec ID                         : 40

Duration                         : 21mn 22s

Bit rate mode                    : Variable

Bit rate                         : 128 Kbps

Maximum bit rate                 : 216 Kbps

Channel(s)                       : 2 channels

Channel positions                : L R

Sampling rate                    : 44.1 KHz

Resolution                       : 16 bits

---

### Post by hardyn on 2009-05-07
I had the bad-multiverse codecs installed not he bad-universe; all good all fixed now.

mc4man:

how did you get amarok to run?  i installed from the repos and get errors about falling back to digital output, and seem to be missing a full configuration menu.  I have no way to configure amarok output.

---

### Post by mc4man on 2009-05-07
I was running a jaunty live cd on my little m1330 laptop, I believe with intel sound. 
It did strike me that there is no audio config in amarok2, nor anywhere else obvious, so to start you'd be at the mercy of pulseaudio, ect. to get things right.

I did install libxine1-ffmpeg and phonon-backend-xine when I installed amarok.
Also xine-ui does have a xine engine config that should translate to all xine apps (if need be use the "masters of ...." to get more complete options

Otherwise maybe install those pavu packages
[http://packages.ubuntu.com/jaunty/pavumeter](http://packages.ubuntu.com/jaunty/pavumeter)
[http://packages.ubuntu.com/jaunty/padevchooser](http://packages.ubuntu.com/jaunty/padevchooser)

I think if I installed jaunty on my desktop I'd might end up going back to amarok1.4 for the time being
(though I could get everything to work there are some simple things 'missing' and overall found amarok2 to be a bit 'unfinished'

[https://edge.launchpad.net/ubuntu/+ppas?name_filter=amarok+14](https://edge.launchpad.net/ubuntu/+ppas?name_filter=amarok+14)

---

