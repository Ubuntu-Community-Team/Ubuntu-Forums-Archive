---
title: "Best Audio File Conversion Software?"
date: 2014-09-01
forum: Multimedia Software
---

### Post by skyesharica on 2014-09-01
Hi Friends.  What is the best and easiest (beginner) sound file conversion software?  I've read a bit about "Sound Converter" in these blogs but I'm not sure.  I simply want to change an .aiff to a .wav and put it on my smartphone.  I'm on Ubuntu 14.04 LTS.
[ATTACH=CONFIG]256048[/ATTACH]

---

### Post by Lars Noodén on 2014-09-01
Audacity is pretty easy to use and in the repository.  It also does editing.

---

### Post by skyesharica on 2014-09-02
Thankyou.  I'll have a look.  And a friend - shantiq - has also suggested Sound Converter.  Have a great Tuesday morning if you are in the USA.  iT'S WAY PAST MY BED TIME.

---

### Post by Vladlenin5000 on 2014-09-02
If you need a system with almost all tools you'll ever need for A/V editing, then look for the official Ubuntu Studio or for the unoffcial Ubuntu based Dream Studio.

---

### Post by Bucky Ball on 2014-09-02
Sound Converter. Standard tool. Flexible, use it, or at least try it. There aren't many better for that job in Ubuntu (I can't actually think of others). Audacity is great, but not suitable for converting whole CDs, say, at a time. Sound Converter can do a bunch at once without issue (and you can change the metadata for a heap of tracks at once, too ... batch style). :)

---

### Post by Yellow Pasque on 2014-09-02
Bucky, since sound converter still uses gstreamer0.10, I would also recommend the gstreamer0.10-ffmpeg package: [https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media) as well as making sure the gstreamer0.10 bad and ugly plugins are installed as needed for mp3 and such.

---

### Post by ThatBum on 2014-09-02
Seconded on soundconverter. Though, I thought it used libav/ffmpeg as a backend.

---

### Post by skyesharica on 2014-09-03
Thankyou but I'm just too stupid.  Got Sound Converter now.

Thanks - I just wanted a simple .wav on my smartphone to cheer me up.

Thankyou great folks.  Simply done.

---

### Post by shantiq on 2014-09-04
Hi Skye;   just entering all the info in case it is of use to others ..:)


1. amazing free Windows software [Super]("http://www.erightsoft.com/SUPER.html")
works a treat under Wine and deals with ALL formats and easy to use
video and AUDIO
[http://www.erightsoft.com/SUPER.html](http://www.erightsoft.com/SUPER.html)
DIRECT LINK IS HERE [http://www.erightsoft.biz/GetFile3.php?SUPERsetup.exe](http://www.erightsoft.biz/GetFile3.php?SUPERsetup.exe)

download right click on file/properties/permissions/execute/set on all
right-click again install with Wine and all good EASY

2. **Linux has 2 great converters** too:

[soundconverter]("https://www.google.co.uk/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=0CCEQFjAA&url=http%3A%2F%2Fsoundconverter.org%2F&ei=wx8IVMXEHoLWaM3-gKAL&usg=AFQjCNFzwn2ES-JVC7LvK-kPNGtgHyrOuA&sig2=7HW3iRHspEPP3QJiCDu-mw") and also
[URL="http://kde-apps.org/content/show.php?content=29024"]soundkonverter
[/URL]
```
sudo apt-get install soundconverter soundkonverter

```try them then remove the one[s] you do not want


or what I do these days MORE INVOLVED BUT FUN


3. Use command line ffmpeg INSTALL THIS VERSION
[https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu](https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu)

then play with code: for BULK example all flac to 320k mp3

cd to folder where files are >>

```
for f in *.flac; do ffmpeg -i "$f" -b:a 320k -c:a  libmp3lame "${f%.*.flac}.mp3"; done
```

with compiled ffmpeg it probably with look thus

```
for f in *.flac; do **~/bin/ffmpeg** -i "$f" -b:a 320k -c:a  libmp3lame "${f%.*.flac}.mp3"; done
```



goes like this:

```
for f in *.INPUTCODEC; do ffmpeg -i "$f" BITRATEANDCODECIFNEEDBE "${f%.*.INPUTCODEC}.OUTPUTCODEC"; done
```

in example above i put -c:a  libmp3lame  and in the case of mp3 there is no need but say you want alac then you need -c:a  alac etc ...
all codecs can be seen with ```
ffmpeg -codecs
``` look for letter E for encoders

---

### Post by Y^2om&amp;#7sgP on 2014-09-04
I've used SoundConverter for a while now, also remember to install Lame, allows for output to MP3 ;)

---

### Post by Bucky Ball on 2014-09-04
> **Temüjin said:**
> Bucky, since sound converter still uses gstreamer0.10, I would also recommend the gstreamer0.10-ffmpeg package: [https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media) as well as making sure the gstreamer0.10 bad and ugly plugins are installed as needed for mp3 and such.

Good points, all of 'em.

I might also throw in that Audacity is great, but only for one track or a couple (unless someone knows a batch thing that Audacity is capable of). You CAN save them to just about anything, including FLAC, my flavour of choice, and editing audio is what it does. For fade ins, fade outs, and just about anything else, Audacity is everyone's friend ... ;)

(ps: you can vinyl crackles and pops if you like!)

---

