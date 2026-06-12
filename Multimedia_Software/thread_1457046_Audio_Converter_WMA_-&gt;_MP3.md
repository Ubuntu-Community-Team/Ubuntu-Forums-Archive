---
title: "Audio Converter WMA -&gt; MP3"
date: 2010-04-18
forum: Multimedia Software
---

### Post by _bruninha on 2010-04-18
I'm trying to convert some songs I have in the Format .WMA to .MP3 searching around I found the program soundconverter, then installed it, only when I try to convert some music gives me an error saying that lack the decoder Windows Media Audio 9 also researched how solve this problem but got no success, I installed a lot of codecs and solved nothing.
How can I solve this problem?

---

### Post by ajgreeny on 2010-04-18
Do you have ubuntu-restricted-extras installed?  If not, install the package and see if that helps.

I always add w32codecs as well, on my machine from the medibuntu repositories, which is worth doing, (w64codecs if you run a 64 bit system) and would suggest that either the commandline application ffmpeg, or winff if you want a GUI for it, is better at converting audio (and video) than soundconverter, but that's a personal opinion.

[http://www.medibuntu.org/](http://www.medibuntu.org/)

---

### Post by _bruninha on 2010-04-18
I have installed on my machine the non-free-codecs and also the ubuntu-restricted-extras. But still can not convert a WMA music to MP3 on soundconverter.

---

### Post by ron999 on 2010-04-18
Hi
Try using ffmpeg to convert one of those tracks. Then, if it works, you can use WinFF.

Try a command like this:-
```
ffmpeg -i filename.wma whatever.mp3
```

Here is WinFF:-[http://winff.org/html_new/]("http://winff.org/html_new/")

---

### Post by _bruninha on 2010-04-18
I installed WinFF only it also is not working. Shows no error when convert command. The output from the command line is:

Input #0, asf, from '/home/bruninha/Track1.wma':
  Duration: 00:00:16.62, start: 1.579000, bitrate: 73 kb/s
    Stream #0.0: Audio: 0x0162, 44100 Hz, stereo, s16, 64 kb/s
**Unknown encoder 'libmp3lame'**
Press Enter to Continue.

it's missing  this 'libmp3lame'?

---

### Post by ron999 on 2010-04-18
> **_bruninha said:**
> 

it's missing  this 'libmp3lame'?

Look for it in Synaptic Package Manager and install it.

---

### Post by _bruninha on 2010-04-18
The libmp3lame is already installed on my machine, but the error still continues.

**Unknown encoder 'libmp3lame'**

---

### Post by mc4man on 2010-04-18
If you are using Karmic (9.10) then you can add wma3(pro) support to gstreamer by adding this ppa (for both 32 and 64 bit
[https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

Then 
```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly-multiverse
```

While I don't use sounconverter on quick test it converted a wmap file no problem.

---

### Post by andrea000 on 2010-04-18
ok never mind go with mc4man idea sounds right seems to remind me
of when i installed it come to thank of it

---

### Post by _bruninha on 2010-04-19
> **mc4man said:**
> If you are using Karmic (9.10) then you can add wma3(pro) support to gstreamer by adding this ppa (for both 32 and 64 bit
[https://launchpad.net/~gstreamer-developers/+archive/ppa]("https://launchpad.net/%7Egstreamer-developers/+archive/ppa")

Then 
```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly-multiverse
```While I don't use sounconverter on quick test it converted a wmap file no problem.

I have all these packages installed already. But I still can not convert.

When I try to convert using soundconverter the following error is shown
Plug-ins are required:
decoder Windows Media Audio 9

And trying to convert WinFF.
Unknown encoder 'libmp3lame'

---

### Post by slooksterpsv on 2010-04-19
Try Audio Format Converter - it also shows as XCFA - so run 
sudo apt-get xcfa

Be sure to install lame

---

### Post by haruo on 2010-06-09
I'm using Ubuntu Lucid Lynx. What I did was to install <libavcodec-unstripped-52> because ffmpeg has it's own libraries. I saw the following web pages. 

[www.biggmatt.com/forums/index.php?topic=428.0](www.biggmatt.com/forums/index.php?topic=428.0)
[www.biggmatt.com/forums/index.php?topic=575.0](www.biggmatt.com/forums/index.php?topic=575.0)

I hope this helps. ):P

---

### Post by malty on 2010-06-09
Download MediaCoder Audio edition (its free) and install in wine, it converts almost everything, including WMA9 to almost anything, the only downside is that it phones the ranch every time it's opened, and for the settings menu. Start the programme from the wine menu, it opens, click on the screen, it phones the ranch and deposits an icon in the top panel, close the webpage, click on the icon and off you go.

---

