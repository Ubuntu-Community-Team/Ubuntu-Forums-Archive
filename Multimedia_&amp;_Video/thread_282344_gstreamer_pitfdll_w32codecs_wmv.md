---
title: "gstreamer pitfdll w32codecs wmv"
date: 2006-10-22
forum: Multimedia &amp; Video
---

### Post by HadroLepton on 2006-10-22
this is a short howto or troubleshooting for following problem:

> 
i have installed gstreamer and pitfdll and w32codecs but totem does not play wmv files :(


you need to rebuild your gstreamer codec registry. delete the .gstreamer directory in your home and then trigger a rebuild using gst-inspect.

```

rm -rf ~/.gstreamer-0.10
gst-inspect-0.10

```

source:
[http://gstreamer.freedesktop.org/data/doc/gstreamer/head/faq/html/chapter-troubleshooting.html#troubleshooting-gst-register](http://gstreamer.freedesktop.org/data/doc/gstreamer/head/faq/html/chapter-troubleshooting.html#troubleshooting-gst-register)

some explanations:
gstreamer maintains a registry of codecs in your home (~/.gstreamer/). apparently, if this registry already exists, gstreamer will not check for any new codecs. if you already have the registry, and then install w32codecs, gstreamer will not recognize the new codecs. when you delete this registry, gstreamer will rebuild the registry, and while doing so will find new codecs installed in the system.

disclaimer:
i am no gstreamer expert. there are many different ways gstreamer can fail and there are many fixes. i just wanted to share this because it worked for me and it has not been posted here in this forum.

---

### Post by forger on 2006-10-23
still doesn't work :)
i installed w32codecs, used your fix, but nada, then i installed mplayer and it's ok!

---

### Post by HadroLepton on 2006-10-23
do you have gstreamer0.10-pitfdll installed?
please post output of following command:
```
gst-inspect-0.10 pitfdll
```

please note that i misspelled the command in my original post. it is gst-inspect-0.10 instead of only gst-inspect.

---

### Post by forger on 2006-10-28
```

...@ubuntu:~/downloads/et$ gst-inspect-0.10 pitfdll
Plugin Details:
  Name:                 pitfdll
  Description:          DLL-loader elements
  Filename:             /usr/lib/gstreamer-0.10/libpitfdll.so
  Version:              0.9.1.1
  License:              GPL
  Source module:        pitfdll
  Binary package:       PitfDLL
  Origin URL:           http://ronald.bitfreak.net/pitfdll/

  qtadec_bin: quicktime binary audio decoder
  dmodec_wmspdmodv1: DMO wmspdmod decoder version 1
  dmodec_wmadmodv3: DMO wmadmod decoder version 3
  dmodec_wmadmodv2: DMO wmadmod decoder version 2
  dmodec_wmadmodv1: DMO wmadmod decoder version 1
  dmodec_wmvdmodv3: DMO wmvdmod decoder version 3
  dmodec_wmvdmodv2: DMO wmvdmod decoder version 2
  dmodec_wmvdmodv1: DMO wmvdmod decoder version 1
  dmodec_wmv9dmodv3: DMO wmv9dmod decoder version 3
  dshowdec_ir41_32v4: DS ir41_32 decoder version 4
  dshowdec_ir50_32v5: DS ir50_32 decoder version 5

  11 features:
  +-- 11 elements

```

---

### Post by forger on 2006-10-28
erm.. i tried it on edgy, and well.. it works :) or maybe automatix2 did the work :P

---

### Post by spejz on 2006-10-28
I've also got a problem playing wmv and even normal avi-files. The w32codecs packages seems to be nice installed. I've done everything   is told in this thread and even more. Totem always tells me "Video codec 'DivX 5' is not handled. You might need to install additional plugins to be able to play some types of movies". Can I do something else?
edit: I'm using ubuntu edgy at the moment.

---

### Post by forger on 2006-10-28
try: ```
sudo apt-get install totem-xine
```
instead of totem-gstreamer, automatix2 installed it on edgy
if you don't have any sound at all, try:
```
sudo apt-get install --reinstall alsa-base
```
then logout and press ctrl+alt+backspace to restart the desktop

---

### Post by PilotJLR on 2006-11-04
Thank you, HadroLeptop! This worked perfectly in Edgy.

---

### Post by greatidea on 2006-11-05
Your post helped me get CNN.COM videos to play! =D> 

Here are all the steps I followed to get it to work:

First I installed the w32codecs.
( [http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb ]("http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb"))

(Double click the .deb file to install the codecs.)

I then followed the instructions in your post for rebuilding the gstreamer codec registry.

Then I used Synaptic Package Manager to install "gstreamer-xine"

That worked, and now I can play videos from CNN.COM in Firefox on Edgy i386.

Thanks for your helpful post. :smile:

---

### Post by Dittie on 2006-11-13
I've done all of what you've all said here, and I'm still unable to play videos with firefox.

When I go to CNN, I get errors like this: 
Totem could not play 'mms://wmscnn.stream.aol.com.edgestreams.net/cnn/offbeat/2006/11/12/miller.wi.big.foot.sighting.wisn.wisn.ws.wmv'.

And when I try to play others, it simply says that I don't have the proper decoder installed.

I've reinstalled MPlayer, put in the latest win32 codecs, and all of the above. Any other ideas to help? :(

---

### Post by rcarricato on 2006-11-14
I couldnt figure it out for months and I right clicked the mplayer screen and  selected "gl" as video output and "alsa" and audio output clicked ok and bam!!! my video popped up.

I dont know if anyone else has experienced it but I havent seen it in any documentation, I read almost all ubuntu books

---

### Post by peteliuz on 2006-12-08
> **HadroLepton said:**
> do you have gstreamer0.10-pitfdll installed?
please post output of following command:
```
gst-inspect-0.10 pitfdll
```

please note that i misspelled the command in my original post. it is gst-inspect-0.10 instead of only gst-inspect.

I typed: ```
rm -rf ~/.gstreamer-0.10
``` in the terminal. It was ok, but when I typed: ```
gst-inspect-0.10 pitdll
``` I got an error message:

```
No such element or plugin 'pitfdll'
``` What I have to do now? Please help!

I have mplayer, wc32codecs, and all of the players (including real player) installed on my Ubuntu (edgy).

---

### Post by kapilg_it on 2006-12-09
aptitude install w32codecs
aptitude install mplayer
aptitude install vlc

now System is ready to play any multimedia files ...I tried , and mplayer played files of flash also like .flv files.

---

### Post by HadroLepton on 2006-12-15
@peteliuz
do you have gstreamer0.10-pitfdll installed?

try following command
```
dpkg-query -l gstreamer0.10-pitfdll
```

the last line of the output should look like this
```
ii  gstreamer0.10- 0.9.1.1+cvs200 GStreamer plugin for using MS Windows binary
```

note the **ii** at the beginning which means that it is installed. if it says **un** then it is not installed. if it says anything else then it might be corrupt.

if not installed then install using
```
sudo apt-get install gstreamer0.10-pitfdll
```

---

### Post by jefrat72 on 2006-12-20
do any of these instructions apply to mplayer?  I've been working on it for a while trying to get it to play CNN videos, no go.

---

### Post by dmizer on 2007-01-07
still no totem.  i get a non-responsive gray box where the video should be.

i CAN play video with totem gstreamer or xine when i use the multimedia add-on for firefox.  but this is extremely undesireable for me.  i need embedded media to play like embedded media is intended to play.

```
~$ dpkg-query -l gstreamer0.10-pitfdll
ii  gstreamer0.10- 0.9.1.1+cvs200 GStreamer plugin for using MS Windows binary
```
```
$ gst-inspect-0.10 pitfdll
Plugin Details:
  Name:                 pitfdll
  Description:          DLL-loader elements
  Filename:             /usr/lib/gstreamer-0.10/libpitfdll.so
  Version:              0.9.1.1
  License:              GPL
  Source module:        pitfdll
  Binary package:       PitfDLL
  Origin URL:           http://ronald.bitfreak.net/pitfdll/

  qtadec_bin: quicktime binary audio decoder
  dmodec_wmspdmodv1: DMO wmspdmod decoder version 1
  dmodec_wmadmodv3: DMO wmadmod decoder version 3
  dmodec_wmadmodv2: DMO wmadmod decoder version 2
  dmodec_wmadmodv1: DMO wmadmod decoder version 1
  dmodec_wmvdmodv3: DMO wmvdmod decoder version 3
  dmodec_wmvdmodv2: DMO wmvdmod decoder version 2
  dmodec_wmvdmodv1: DMO wmvdmod decoder version 1
  dmodec_wmv9dmodv3: DMO wmv9dmod decoder version 3
  dshowdec_ir41_32v4: DS ir41_32 decoder version 4
  dshowdec_ir50_32v5: DS ir50_32 decoder version 5

  11 features:
  +-- 11 elements
```
i sincerely hope that you can help me because i've had zero luck with totem, mplayer, and vlc.

**@jefrat72**
if you don't mind media popping up in a new window (i do), then you can simply install the streaming media add-on for firefox: [https://addons.mozilla.org/firefox/446/](https://addons.mozilla.org/firefox/446/)

this usually is a satisfactory solution for most users.

---

### Post by sh4d3z on 2007-02-11
thanx dmizer for that ext...
it's better than nothing
just yesturday i had a perfectly working dapper system and my ignorant lil' bro got on and fuxored erything so i figured i'd reinstall with edgy, but find it very frustrating to get things working... but this will do for now again thanx

---

### Post by SMS on 2007-03-13
i get this error message when trying to watch embedded movies
cannot find codec matching selected -vo and video format etc
lol any ideas

---

### Post by dmizer on 2007-03-13
@SMS ...

you'll probably find your answer here: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by digital_sabotage on 2007-04-05
finally  ...i can play streaming videos ...woohoo! ...did win32 codec install as instructed earlier in this thread and replaced totem-gstreamer with totem-xine ...been looking for this fix for sooo long ...couldn't play anything in firefox ...thank you all very much:-)

---

### Post by jfca283 on 2007-04-05
with vlc or totem-gstreamer i can't watch divx 5 videos
anyone of you can?
only with Mplayer i am able to see them

---

### Post by Kenetack on 2007-04-12
Thanks forger!  Your single line of code worked great for me.  I am using Totem Movie Player 2.16.2  Gstreamer 0.10.10.  I was unable to get any sound with Divx movies and now full stereo!  Great work!

---

### Post by Taemojitsu on 2008-06-19
Wow, still useful 2 years later with 8.04. Thank you for the how-to, it fixed my problems when installing 2 million extra codecs/video players didn't! :&#8203;)

---

