---
title: "Convert *.MKV to *.AVI"
date: 2008-12-14
forum: Multimedia Software
---

### Post by Tasc0 on 2008-12-14
I have a .mkv video file that I'd like to convert it to .avi format. How can I do it?

Thanks in advance.

---

### Post by Tasc0 on 2008-12-14
No one?

---

### Post by jellyfisharepretty on 2008-12-14
Hi Tasc0,

Basically the strategy I would try is to dump the compressed video and audio out of the mkv file using mplayer, then mux the video and audio into an avi container using mencoder.  Mencoder for me was tough to learn, but in the end it's a great tool.  See [http://www.mplayerhq.hu/DOCS/HTML/en/encoding-guide.html]("http://www.mplayerhq.hu/DOCS/HTML/en/encoding-guide.html") for how to use it.

In particular, see [http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-dvd-mpeg4.html#menc-feat-dvd-mpeg4-muxing]("http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-dvd-mpeg4.html#menc-feat-dvd-mpeg4-muxing") for the muxing instructions.

But beware of audio synch issues, which could happen.

Unfortunately I am not sure of the exact commands you must use.  I can give it a try here but it might not work straight away.  I'm assuming here the mkv contains mpeg3 audio and h.264 video.  Just change the extensions to whatever you are using :

```
mplayer file.mkv -dumpaudio -dumpfile audio.mp3
mplayer file.mkv -dumpvideo -dumpfile video.264

mencoder -vf harddup -oac copy -ovc copy -o output_movie.avi -audiofile audio.mp3 video.264
```

You may want to try other combinations of filters.  I added harddup here because the mencoder doc strongly recommends it, but you could also try without it.  Just delete -vf harddup if you don't want to use it.

Hope it helps

---

### Post by eye208 on 2008-12-16
The first question to ask here is: Why convert from MKV to AVI?

If it is because you plan to play back the AVI on a DVD player, then just changing containers won't be sufficient. If the MKV contains streams incompatible with DVD players or even incompatible with AVI in general (e.g. H.264 video + Vorbis audio), you have to transcode them. You also have to transcode if the MKV contains high definition video exceeding 720x480 resolution, because that is the maximum supported by most DVD players. Another reason to transcode is if the MKV contains subtitles that you want to keep with the AVI etc. ... You get the idea.

First find out what you have (i.e. what's inside the MKV), then find out what you want (DVD player compatibility?). Then we can show you how to get from A to B.

---

### Post by Tasc0 on 2008-12-16
> **eye208 said:**
> The first question to ask here is: Why convert from MKV to AVI?

If it is because you plan to play back the AVI on a DVD player, then just changing containers won't be sufficient. If the MKV contains streams incompatible with DVD players or even incompatible with AVI in general (e.g. H.264 video + Vorbis audio), you have to transcode them. You also have to transcode if the MKV contains high definition video exceeding 720x480 resolution, because that is the maximum supported by most DVD players. Another reason to transcode is if the MKV contains subtitles that you want to keep with the AVI etc. ... You get the idea.

First find out what you have (i.e. what's inside the MKV), then find out what you want (DVD player compatibility?). Then we can show you how to get from A to B.
That's correct, I'm trying to watch the video file on a DVD player. The file is 720p. Not really sure about the audio.

I'll wait for your reply, thanks.

---

### Post by eye208 on 2008-12-17
This will scale the video down to 480p and encode it as Xvid/MP3 AVI:
```
mencoder -mc 0 -noskip -vf expand=:::::16/9,scale=720:480,hqdn3d,harddup -ovc xvid -oac mp3lame -xvidencopts fixed_quant=3.8:me_quality=6:noqpel:nogmc:trellis:chroma_me:chroma_opt:hq_ac:vhq=4:lumi_mask:max_key_interval=300:quant_type=mpeg:max_bframes=2:closed_gop:nopacked:profile=asp5:autoaspect:bvhq=1 -lameopts vbr=2:q=6:aq=2 -o outfile.avi infile.mkv
```

---

### Post by Tasc0 on 2008-12-17
> **eye208 said:**
> This will scale the video down to 480p and encode it as Xvid/MP3 AVI:
```
mencoder -mc 0 -noskip -vf expand=:::::16/9,scale=720:480,hqdn3d,harddup -ovc xvid -oac mp3lame -xvidencopts fixed_quant=3.8:me_quality=6:noqpel:nogmc:trellis:chroma_me:chroma_opt:hq_ac:vhq=4:lumi_mask:max_key_interval=300:quant_type=mpeg:max_bframes=2:closed_gop:nopacked:profile=asp5:autoaspect:bvhq=1 -lameopts vbr=2:q=6:aq=2 -o outfile.avi infile.mkv
```
Thanks for the help. But why 480p?

---

### Post by eye208 on 2008-12-17
> **Tasc0 said:**
> But why 480p?
Because very few DVD players support 720p.

---

### Post by diggerOS on 2008-12-22
Hello! Try WinFF.

---

### Post by Tasc0 on 2008-12-22
> **eye208 said:**
> Because very few DVD players support 720p.
Sorry for the delay. I tried this and I get the following error message:
```
xvid:[ERROR] frame rate must be <= 30 for the chosen profile
FATAL: Cannot initialize video driver.

```
Not really sure why's that.


> **diggerOS said:**
> Hello! Try WinFF.

I don't use Windows. Thanks anyways.

---

### Post by mvandemar on 2008-12-22
> **Tasc0 said:**
> [QUOTE=diggerOS;6417505]Hello! Try WinFF.

I don't use Windows. Thanks anyways.[/QUOTE]

And the reason you thought that someone was suggesting programs that were Windows only on an Ubuntu forum was...? :)

> WinFF is a GUI for the command line video converter, FFMPEG. It will convert most any video file that FFmpeg will convert. WinFF does multiple files in multiple formats at one time. You can for example convert mpeg's, flv's, and mov's, all into avi's all at once. WinFF is available for Windows 95, 98 , ME, NT, XP, VISTA, and Debian, **[COLOR="Red"]Ubuntu[/COLOR]**, Redhat based GNU/Linux distributions. WinFF is available in Brazillian Portuguese, Bulgarian, Chinese Tradditional, Danish, English, French, German, Italian, Polish, Portuguese, Spanish, and Turkish.

WinFF: [http://code.google.com/p/winff/](http://code.google.com/p/winff/)

-Michael

---

### Post by diggerOS on 2008-12-23
:) ok man, i just dont know how do you manage this WINter then.. 
Merry Christmas everyone! :-P

---

### Post by Tasc0 on 2008-12-25
> **diggerOS said:**
> :) ok man, i just dont know how do you manage this WINter then.. 
Merry Christmas everyone! :-P
Ok, I'll try this if eye208's command don't work. I'll wait for his reply.

---

### Post by SetsunaFSei on 2008-12-31
The easiest way by installing MediaCoder.  Very easy to install follow the steps below.

Step 1)
---------

You need to install wine. First things first go into your menu under Applications->Accessories->Terminal

In the terminal command use these commands 1 at a time

Code:
sudo wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list](http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/winehq.list


This will install the wine sources for you
next in the command line prompt you need to use these commands

Code:
sudo aptitude install wine


for those who use apt-get use

Quote:
Sudo apt-get install wine -> Both produce the same results



---------
Step 2)
---------

Next we need to download mediacoder. Pretty sure all you know the location of MediaCoder but for those that don't it's [http://mediacoder.sourceforge.net/dlfull.htm](http://mediacoder.sourceforge.net/dlfull.htm)

once downloaded you need to be sure exe files are associated with wine so right click on the installer and go to the properties section of the menu.
After thats done you need to Goto the Open With tab and make sure it's associated with wine. if it is then your all set.
Now just double click on the installer and it will run just fine. It is recommend that you leave all settings as they are because this way you can be sure you will be able to find MediaCode.
After you are done you can find MeidaCoder either in Applications -> Wine -> MediaCoder (Ubuntu) or in your userfolder in the .wine directory
(you might have to select "show hidden files).
It might take some time for MediaCoder to start (on my machine approximately 20 seconds because the usual firefox popup is missing).


---------
Step 3)
---------

Download Firefox as it is a requirement for MediaCoder. It doesn't matter if you already installed it unless it is the Windows version which is installed through wine. You can download it here: [http://www.getfirefox.com](http://www.getfirefox.com) Be sure you choose to download the version for Windows. To install it just do the same you did in the step above.


--------
Step 4)
--------

If you still can't start MediaCoder (R6034 error), download the modified manifest file
[http://www.4shared.com/file/19830555/a8edfda4/MicrosoftVC80CRT.html](http://www.4shared.com/file/19830555/a8edfda4/MicrosoftVC80CRT.html)
(you have to extract this into the MediaCoder folder).




This guide was brought to you by thibeaz and expanded by SirAuron (using the workarounds in the thread "MediaCoder on Linux/WINE"
[http://mediacoder.sourceforge.net/forum/viewtopic.php?t=1072](http://mediacoder.sourceforge.net/forum/viewtopic.php?t=1072)
It was tested on Ubuntu 7.04 by several users but it should also work on other linux distributions if wine can run on them.

---

### Post by roblloyd on 2009-01-02
Hi, Personally I find MKV files too big to store for any real purpose at the moment. I found this [Guide and Shell Script]("http://www.howforge.com/how-to-convert-mkv-to-avi-using-mencoder") very useful.

[http://www.howforge.com/how-to-convert-mkv-to-avi-using-mencoder]("http://www.howforge.com/how-to-convert-mkv-to-avi-using-mencoder")

```

#!/bin/sh
 
INPUT=$1
OUTPUT=$2
 
mplayer "$INPUT" -ao pcm:fast:file=audio.wav -vc null -vo null
mencoder "$INPUT" \
    -ffourcc divx \
    -ovc lavc -lavcopts vcodec=mpeg4:vhq:vbitrate=400 \
    -audiofile audio.wav \
    -oac mp3lame -lameopts vbr=3 \
    -slang eng \
    -sws 2 -vf scale=352:-3 \
    -o "$OUTPUT"
 
rm -f audio.wav
```

In order to convert input.mkv to output.avi, run below command.

```

mkv2avi input.mkv output.avi
```

NB: The above command assumes you have saved the script as mkv2avi.sh. You may also need to perform the following to make the file executable ```
sudo chmod a+x *yourfilename.sh*
```

On another note, If you want to use windows programs to do something isn't it much easier to use a virtual machine... However in reality, there are very few things that you need WINE for! Most, if not all, functionalities of a windows machine can be reproduced on a linux box, as long as you're not afraid of the command line and google!

---

### Post by ljoslin on 2009-11-28
I use Handbrake, takes care of most of my file converting needs!

[http://www.google.com/url?sa=t&source=web&ct=res&cd=1&ved=0CAcQFjAA&url=http%3A%2F%2Fhandbrake.fr%2F&ei=z78RS9ycMIz9nQfImdDMAw&usg=AFQjCNEQmk6QunfXQq6wFpNE5G32Fjcw3g&sig2=yaAGHSBbYHkpX4gxyQo13A](http://www.google.com/url?sa=t&source=web&ct=res&cd=1&ved=0CAcQFjAA&url=http%3A%2F%2Fhandbrake.fr%2F&ei=z78RS9ycMIz9nQfImdDMAw&usg=AFQjCNEQmk6QunfXQq6wFpNE5G32Fjcw3g&sig2=yaAGHSBbYHkpX4gxyQo13A)

enjoy
-=ljoslin=-

---

### Post by ikacer on 2009-11-28
> **ljoslin said:**
> I use Handbrake, takes care of most of my file converting needs!

[http://www.google.com/url?sa=t&source=web&ct=res&cd=1&ved=0CAcQFjAA&url=http%3A%2F%2Fhandbrake.fr%2F&ei=z78RS9ycMIz9nQfImdDMAw&usg=AFQjCNEQmk6QunfXQq6wFpNE5G32Fjcw3g&sig2=yaAGHSBbYHkpX4gxyQo13A](http://www.google.com/url?sa=t&source=web&ct=res&cd=1&ved=0CAcQFjAA&url=http%3A%2F%2Fhandbrake.fr%2F&ei=z78RS9ycMIz9nQfImdDMAw&usg=AFQjCNEQmk6QunfXQq6wFpNE5G32Fjcw3g&sig2=yaAGHSBbYHkpX4gxyQo13A)

enjoy
-=ljoslin=-

You're beating a dead horse here.

---

### Post by paddy100 on 2010-04-15
Hi Guys...... Hope you can help

```
mencoder -mc 0 -noskip -vf expand=:::::16/9,scale=720:480,hqdn3d,harddup -ovc xvid -oac mp3lame -xvidencopts fixed_quant=3.8:me_quality=6:noqpel:nogmc:trellis:chroma_me:chroma_opt:hq_ac:vhq=4:lumi_mask:max_key_interval=300:quant_type=mpeg:max_bframes=2:closed_gop:nopacked:profile=asp5:autoaspect:bvhq=1 -lameopts vbr=2:q=6:aq=2 -o outfile.avi infile.mkv
``` from EYE208 (thank you) works perfect for what I need it for, however I have quite a few mkvs in one folder that I need to convert.

As a newly converted Linux user I was wondering if there was a way of useing FOR IN DO (or the Ubuntu equivilant) to convert all the mkvs in one folder to avis, useing the VARIABLE of the name of the mkv file to name the avi from one command in the terminal. Ive tried a few, just cant seem to make it work.

---

### Post by grj23 on 2010-09-30
Apologies for the thread necromancy.  I have exactly the same situation.  Wanting to watch a mkv on a dvd player.

The video is 640 x 352, Codec H264, 25 frames per second
The audio is MPEG-4-AAC audio, 48000Hz.

There is a subtitle, but I don't need it.

Would the same code apply?  I'm guessing it needs to be tweaked somehow?

---

### Post by SeijiSensei on 2010-09-30
> **grj23 said:**
> Apologies for the thread necromancy.  I have exactly the same situation.  Wanting to watch a mkv on a dvd player.

The video is 640 x 352, Codec H264, 25 frames per second
The audio is MPEG-4-AAC audio, 48000Hz.

There is a subtitle, but I don't need it.

Would the same code apply?  I'm guessing it needs to be tweaked somehow?

Paddy's code seem a bit of overkill to me.  I've used

```
mencoder -o output.avi -oac mp3lame -ovc xvid -xvidencopts=pass=1 -sid 0 input.mkv
```

-sid 0 creates a "hard" subtitle that will be written into the AVI file.  You can omit that if you'd like.  You can see which language tracks and which subtitle tracks are available by playing the video from the command line using mplayer like this "mplayer /path/to/video".  It will report the structure of the file in the terminal window.

This does "one-pass" XviD encoding.  You can improve the quality of the result by using two-pass encoding.  See the excellent [Gentoo How-To for mencoder]("http://en.gentoo-wiki.com/wiki/Mencoder#XviD") for details.  Often I find one-pass is enough, especially if I'm watching the video on a small screen like a phone or portable media player.

---

### Post by grj23 on 2010-10-01
> **SeijiSensei said:**
> Paddy's code seem a bit of overkill to me.  I've used

```
mencoder -o output.avi -oac mp3lame -ovc xvid -xvidencopts=pass=1 -sid 0 input.mkv
```

...

Fantastic.  Thanks very much.  That works perfectly.  I had to change the command slightly:  "-xvidencopts pass=1".

I also wrote a python script to do all the files in a directory, which is currently running on my machine.  Save as a .py file in the directory where you want the conversion to occur, and run:

```
import os

for fname in os.listdir("."): #mypath):
    if fname[-3:]!="mkv": continue
    cmd="mencoder -o '"
    cmd+=fname[:-3]+"avi'"
    cmd+=" -oac mp3lame -ovc xvid -xvidencopts pass=1 '"
    cmd+=fname[:-3]+"mkv'"
    print cmd
    failure=os.system(cmd)
    if failure:
        print "FAILED: "+cmd

```

---

### Post by Terry of Astoria on 2011-08-14
> **eye208 said:**
> This will scale the video down to 480p and encode it as Xvid/MP3 AVI:
```
mencoder -mc 0 -noskip -vf expand=:::::16/9,scale=720:480,hqdn3d,harddup -ovc xvid -oac mp3lame -xvidencopts fixed_quant=3.8:me_quality=6:noqpel:nogmc:trellis:chroma_me:chroma_opt:hq_ac:vhq=4:lumi_mask:max_key_interval=300:quant_type=mpeg:max_bframes=2:closed_gop:nopacked:profile=asp5:autoaspect:bvhq=1 -lameopts vbr=2:q=6:aq=2 -o outfile.avi infile.mkv
```

I did this and I got just an AWESOME quality Xvid.mp3.avi at an amazingly small size. 384 Megabytes from a 1.7 Gig mkv file (1 hr.). But super-good quality picture on my 720 p tv.
Thanks so much for the great tip.

---

### Post by Prescilla on 2011-11-25
> **eye208 said:**
> This will scale the video down to 480p and encode it as Xvid/MP3 AVI:
```
mencoder -mc 0 -noskip -vf expand=:::::16/9,scale=720:480,hqdn3d,harddup -ovc xvid -oac mp3lame -xvidencopts fixed_quant=3.8:me_quality=6:noqpel:nogmc:trellis:chroma_me:chroma_opt:hq_ac:vhq=4:lumi_mask:max_key_interval=300:quant_type=mpeg:max_bframes=2:closed_gop:nopacked:profile=asp5:autoaspect:bvhq=1 -lameopts vbr=2:q=6:aq=2 -o outfile.avi infile.mkv
```

Hello, thanks for this. It worked but the scaling zoomed in too much that some parts are not seen on the screen. How do i modify that code so that the scale ratio is preserved?

I am converting a 1280 x 528 H.264 mkv to mpeg4(xvid) avi. I tried to remove the -mc 0 -noskip -vf expand=:::::16/9,scale=720:480, but it didn't work. Please help.

---

### Post by SeijiSensei on 2011-11-25
First, if the source is really 1280x528, rescaling it to 720x480 will substantially distort the picture since the output will not have the same aspect ratio as the original.  (Personally I've never seen content in 1280x528; everything I've worked with has been in the 4:3 or 16:9 aspect ratio. 1280x528, or 2.42:1 is close to the 2.33:1 used in some "widescreen" films.)

If you want to reduce the 1280 width to 720, just use scale=720 and let mencoder calculate the vertical size.

Once you do that your problem might disappear.  If, however, you still have content being cropped on top/bottom or right/left, you'll need to read the manual on how to use the expand option.  I've only used that when trying to [resize]("http://forums.animesuki.com/showthread.php?p=937709") a 640x480 video with "hard" subtitles so it would play correctly on a traditional SD television.  

The [mencoder wiki]("http://en.gentoo-wiki.com/wiki/Mencoder") at Gentoo is a good place to start for help.  If that's not sufficient, you can find everything you could possibly need to know about mencoder in the [manual]("http://www.mplayerhq.hu/DOCS/HTML/en/mencoder.html") and man pages.

---

### Post by Prescilla on 2011-11-26
> **SeijiSensei said:**
> First, if the source is really 1280x528, rescaling it to 720x480 will substantially distort the picture since the output will not have the same aspect ratio as the original.  (Personally I've never seen content in 1280x528; everything I've worked with has been in the 4:3 or 16:9 aspect ratio. 1280x528, or 2.42:1 is close to the 2.33:1 used in some "widescreen" films.)

If you want to reduce the 1280 width to 720, just use scale=720 and let mencoder calculate the vertical size.

Once you do that your problem might disappear.  If, however, you still have content being cropped on top/bottom or right/left, you'll need to read the manual on how to use the expand option.  I've only used that when trying to [resize]("http://forums.animesuki.com/showthread.php?p=937709") a 640x480 video with "hard" subtitles so it would play correctly on a traditional SD television.  

The [mencoder wiki]("http://en.gentoo-wiki.com/wiki/Mencoder") at Gentoo is a good place to start for help.  If that's not sufficient, you can find everything you could possibly need to know about mencoder in the [manual]("http://www.mplayerhq.hu/DOCS/HTML/en/mencoder.html") and man pages.

Thanks for the response. Can someone please tell me what are the -mc -noskip, -vf options for?

---

### Post by SeijiSensei on 2011-11-26
mc allows you to adjust the timing of the audio and video tracks; noskip forces mencoder to handle every frame.  Used together you can fix problems with A/V synchronization.  I've generally not encountered this problem with the material I've encoded.

vf lets you add "video filters" to the output stream.  There are quite a few filters including both the expand and scale filters I mentioned above.

Every mencoder option is documented in the program's [man page]("http://www.mplayerhq.hu/DOCS/man/en/mplayer.1.html#VIDEO%20FILTERS") ("man mencoder" at a command prompt).

---

### Post by viktor03 on 2013-02-25
take a look at arista transcoder, it's downloadable via software center. small gui and you can easly make custom presets for converting

---

