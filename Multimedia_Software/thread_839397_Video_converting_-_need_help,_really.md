---
title: "Video converting - need help, really"
date: 2008-06-24
forum: Multimedia Software
---

### Post by Thanh-BKK on 2008-06-24
Hello :)

I am definitely struggling here - one of the main tasks of my computer is "converting/editing videos", now i haven't done any since i switched to Ubuntu from Vista a couple of months ago, but now i have enough raw material to start doing it again.... and can't!

I have tried a LOT of things. Medibuntu repos, all sorts of codecs (there must be a ton of codecs in this system) and finally i really appear to be able to convert any format into any format - if only they would play in anything else but Totem!

Regardless what format i convert into what format, the only application able to run the resulting files is Totem.

No VLC, no RealPlayer, nothing at all under Windows.

oh, and 3gp files DO play on phones, but no sound - in Totem, needless to say, the sound works.

I found (via G-Spot on Windows) that avi files come out with a "corrupted avi header".

Please, what can i do to get files that work the way they should - on all players, as opposed to "Totem only"..??

I use WinFF/ffmpeg to do the converting, and i am still VERY much a newbie in this stuff (under Linux, that is). 

As i already got the converting process itself working (after much struggle with those $#%@ codecs!) i feel i can't be too far off the target.... but i need a guide.

Many thanks in advance for any advice......

Thanh

---

### Post by unoodles on 2008-06-24
I had the same problem: Converted Videos do not work on Windows.
The way I do it now is use ffmpeg or mencoder to convert it to an AVI, then open it in AviDemux and save it as an XviD.

---

### Post by Thanh-BKK on 2008-06-24
Hi :)

Anyone with a solution? I need primary 3gp files as end result, but also wmv and mpg, rarely avi.

it must be possible to do this in Ubuntu??

Best regards.....

Thanh

---

### Post by Thanh-BKK on 2008-06-25
Hello again.

Still no replies..... :-(

However i found out something.... while my first .avi file really didn't play in ANYthing but Totem, now, after i have installed all these 39,982,218,856 codecs (or was it more??) some of them actually DO play - in Windows, that is, but not in Ubuntu!

I tested it by converting an mpg into the following, with results:

.avi - plays in Totem and anything under Windows
.wmv - plays in Totem and anything under Windows
.3gp - plays in Totem, GOM (Windows) and on a phone (w/o sound)
.mp4 - plays in Totem and VERY CHOPPY under Windows
.mov - plays in Totem and RealPlayer (Windows)

ALL of these will NOT play in VLC or RealPlayer, under Ubuntu! Totem ONLY. 

Please note the 3gp - the codec used is h.263 for video and AAC for audio, which is what the phone (Sony Ericsson K750i) wants, but the sound doesn't work on the phone.... but it's fine on Linux and Windows.

The mp4 file plays fine in Totem but under Windows it looks like it's "stuttering" and missing frames. Sound is fine.

Also weird - 3gp and mp4 are much brighter than the origin file (which in this particular case was good as the origin file is rather dark) but the .avi was even darker (Xvid codec). 

Now how do i get VLC (Linux!) and RealPlayer (Linux!) to play these? I was used to VLC playing everything, and it still does play everything i download, but nothing that i make myself. 

I feel i'm so close, but not quite there yet..... please, to all media guru's out there, help me...... "video converting" is the reason for my computer to exist, and i want to keep that Vista DVD in it's box........ i like Ubuntu so much more!!

Best regards......

Thanh

---

### Post by eye208 on 2008-06-25
> **Thanh-BKK said:**
> I was used to VLC playing everything, and it still does play everything i download, but nothing that i make myself.
I guess you are trying to store streams in incompatible containers. Some formats just don't work in AVI. Some don't work in MP4. Not to mention that FFmpeg's stream copy mode often results in broken files.

I can walk you through the steps of producing a spec-compliant MP4 file with AVC or ASP video and AAC or MP3 audio. Or a Matroska file with arbitrary video, audio, and subtitles. However, AVI and WMV I won't touch because the former is dead and the latter is proprietary.

---

### Post by timcredible on 2008-06-25
my first thought is that you've installed too many codec packages and they're messing each other up.  the only packages i've installed are ubuntu-restricted-extras and libdvdcss2.  that allows me to convert and play mpeg1, mpeg2, mpeg4, quicktime, flash, avi, and wmv, and probably more that i don't use.  

it doesn't make much sense that totem can view a file that vlc can't since they both rely on gstreamer for decoding the file.

also, keep in mind that these formats usually have many different parts, like mpeg4 has [23 different parts]("http://en.wikipedia.org/wiki/MPEG-4#MPEG-4_parts"), so just because you converted to mpeg4 doesn't mean that the target device will understand that particular part of mpeg4.  the same holds true for mpeg2 and avi.  

not sure about realplayer format - i've never tried making a .rm or .ram file.

so, if it were me, i'd re-install hardy and only install the 2 packages above (and winff and ffmpeg and mencoder) and see what happens.

---

### Post by Thanh-BKK on 2008-06-25
Hi :)

Thank you both for the replies. Now, to be honest, i know *nothing* about containers etc... what i always did (granted, under Windows) was i took the origin file (regardless what format) and converted it to mpg, using things like "Super" or "MagicVideoConverter" or "Canopus ProCoder". 

The resulting mpg i ran thru Tmpgenc to create clips from it, resulting in multiple smaller mpg files. These i then joined again to get a target mpg file.

And THAT i then converted to the final format, be it avi, rmvb, flv, 3gp or whichever was required, again using the above mentioned applications.

Now, regarding the codecs, i did not in fact install "multiple packages" but indeed only the "restricted extras" and a few extra "lib...." files which WinFF complained about to be missing (i.e. when i troed to convert, it told me precisely what i needed - such as "unknown codec - libav2" (just as an example!), i then grabbed that file from the repo and installed it. 

I now have a folder /usr/lib/codecs where they all sit - 133 items to be precise, and WinFF no longer complains about something missing, and converting appears to work fine (even relatively fast, compared to some of the Windows apps - particularly "Super" is a slow snail).

here is the precise error message VLC generates when i try to play one of the home-made videos:

Unable to open 'file:///home/thanh/Alexander%20+%20Bagoas%20WORKING%20FILE.avi'

AAARGH!! 

You know what??? When i go the routine "File -> Open File -> Browse" etc IT FRIGGIN' WORKS!!!!!!!!!!!!

ALL OF THEM !!!!!!!

But right-clicking file and "Open with -> VLC" still doesn't!

Now what sort of problem is this, actually?? 

*scratch head*
*head bleeding from all that scratchin'*

-.-

i think i have to go to sleep right now. 

Maybe i'll reinstall VLC tomorrow and let's see. By the way is there a way to simply open all video files in Totem by default? Because some (like mp4) start RealPlayer which won't play them either, but Totem does. 

RealPlayer does play the 3gp however!

*weird Linux*

Best regards......

Thanh

---

### Post by Ian0426 on 2008-10-20
You aren't alone. I finally have put a memory card in my phone (S.E. 580i), and the video files (.3GP) will only play well in Totem. There, they play perfectly. In VLC, the sound is either scratchy or non-existant, and in GNOME Movie Player, the same problem exists. Very weird.

---

### Post by /////// on 2008-10-20
To start all videos of the same file type with one application, choose a video of that file type, right click, go to properties, click open with and then the application in which you want to open it. I don't know why your conversion is screwed up or why VLC won't play files if you just right click and go to open with however

---

### Post by dalmeida on 2009-02-14
Here's a tutorial and step by step install:
[http://goinggnu.wordpress.com/2007/02/13/convert-avi-to-3gp-using-ffmpeg/](http://goinggnu.wordpress.com/2007/02/13/convert-avi-to-3gp-using-ffmpeg/)

I'm running ubuntu 8.10:

svn co -r 14946 svn://svn.mplayerhq.hu/ffmpeg/trunk ffmpeg

cd ffmpeg

./configure &#8211;enable-liba52 &#8211;disable-debug &#8211;enable-libfaad &#8211;enable-libfaac &#8211;enable-gpl &#8211;enable-nonfree &#8211;enable-libmp3lame &#8211;enable-libdc1394 &#8211;enable-libx264 &#8211;enable-libxvid &#8211;enable-pthreads &#8211;enable-libvorbis &#8211;enable-libtheora &#8211;enable-libgsm &#8211;disable-debug &#8211;enable-shared &#8211;disable-protocol=udp &#8211;prefix=/usr

sudo mkdir /usr/local/lib/pkgconfig
sudo mkdir /usr/include/libavdevice
sudo mkdir /usr/include/libavformat
sudo mkdir /usr/include/libavcodec
sudo mkdir /usr/include/libavutil
sudo mkdir /usr/lib/vhook

sudo apt-get install libx264-dev checkinstall

make

sudo make install

After ffmpeg is installed, you can convert the file like so (please see ffmpeg site for more options or just google it):

ffmpeg -i SEexample.avi -ac 1 -ab 12 -map 0.0 -map 1.0 movie.3gp

---

### Post by FakeOutdoorsman on 2009-02-14
Here's a better tutorial in my biased opinion:
[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---

