---
title: "FFMpeg/WinFF Video Conversion Problem"
date: 2008-11-26
forum: Multimedia Software
---

### Post by EPrips on 2008-11-26
So I'm trying to convert an .avi file into an .mp4 file so I can play it on my iPod. Using the guide at the top of the page, I installed ffmpeg and WinFF. In WinFF, I've got it set to "Convert to: Ipod" and then regardless of which other preset I select, I get an error. The error is:

Warning: The bitrate parameter is set too low. It takes bits/s as argument, not kbits/s
Unknown encoder 'h264' (or Xvid if I select that as a preset)

Any ideas?

---

### Post by kaworunagisa on 2008-11-26
.

---

### Post by kaworunagisa on 2008-11-26
Not sure if it helps, but here's the parameters I use for my ipod videos. 

for anamorphic wide screen:

-r 29.97 -croptop 58 -cropbottom 62 -vcodec h264 -s 640x272 -aspect 2.35 -flags +loop -cmp +chroma -deblockalpha 0 -deblockbeta 0 -b 1000k -maxrate 1250k -bufsize 4M -bt 256k -refs 1 -coder 0 -me umh -me_range 16 -subq 7 -partitions +parti4x4+parti8x8+partp8x8 -g 250 -keyint_min 25 -level 30 -qmin 10 -qmax 51 -qcomp 0.6 -trellis 2 -sc_threshold 40 -i_qfactor 0.71 -acodec aac -ab 64 -ar 48000 -ac 2

for regular widescreen

r 29.97 -vcodec h264 -s 640x352 -aspect 16:9 -flags +loop -cmp +chroma -deblockalpha 0 -deblockbeta 0 -b 1000k -maxrate 1250k -bufsize 4M -bt 256k -refs 1 -coder 0 -me umh -me_range 16 -subq 7 -partitions +parti4x4+parti8x8+partp8x8 -g 250 -keyint_min 25 -level 30 -qmin 10 -qmax 51 -qcomp 0.6 -trellis 2 -sc_threshold 40 -i_qfactor 0.71 -acodec aac -ab 80k -ar 48000 -ac 2

for full screen 

-r 29.97 -vcodec h264 -s 640x480 -aspect 4:3 -flags +loop -cmp +chroma -deblockalpha 0 -deblockbeta 0 -b 1000k -maxrate 1250k -bufsize 4M -bt 256k -refs 1 -coder 0 -me umh -me_range 16 -subq 7 -partitions +parti4x4+parti8x8+partp8x8 -g 250 -keyint_min 25 -level 30 -qmin 10 -qmax 51 -qcomp 0.6 -trellis 2 -sc_threshold 40 -i_qfactor 0.71 -acodec aac -ab 80k -ar 48000 -ac 2

these are in the presets.xml file, found in /home/(yourusername)/.winff

Hope this might be of use...I'm still learning Linux...

---

### Post by EPrips on 2008-11-26
So I'd go to presets.xml and past those options in?

Edit: Couldn't find presets.xml so I did a search for it and still nothing.

---

### Post by EPrips on 2008-11-26
Bump

---

### Post by paul.gevers on 2008-12-04
Depending on the version of ffmpeg you are running your presets.xml file might need to change. You can get different versions of the presets.xml files at [1]. At [2] is an explaination about how to install them (copied below as well)

[1] [http://code.google.com/p/winff/downloads/list](http://code.google.com/p/winff/downloads/list)
[2] [http://code.google.com/p/winff/wiki/InstallPresetsxml](http://code.google.com/p/winff/wiki/InstallPresetsxml)

If you just want to install for the current user, unzip/untar the downloaded file and copy the new presets.xml file to /home/user/.winff/

If you want to change the system wide presets.xml file, unzip/untar the downloaded file and copy the new presets.xml to /usr/share/winff/presets.xml. If you install to the system each user must delete /home/user/.winff/presets.xml for the new presets to take effect. This last procedure might prevent successful updates of later if you are using standard Debian/Ubuntu updates.

---

### Post by paul.gevers on 2008-12-04
> **EPrips said:**
> So I'd go to presets.xml and past those options in?


You could do that, but winff has it's build in presets editor. Just choose "edit" in the menu.

---

### Post by fewjr on 2008-12-08
Thanks to paul.gevers I have winff and ffmpeg installed properly and have converted a couple .avi videos to h264 for my Ipod. I used the presets within the program and it worked great. That help was from this thread: [http://ubuntuforums.org/showthread.php?t=999403](http://ubuntuforums.org/showthread.php?t=999403)
I used dvd::rip to get the .avi from the dvd, then converted/transcoded or whatever. I need to figure out how to convert VOB files next because I saved alot of my netflix movies from the Ubuntu desktop by right clicking and saving to image. I think you have to make it one continuous VOB though from something I read, but I haven't gotten that far.

Good luck
fewjr

---

### Post by wolfen69 on 2008-12-08
use [Handbrake]("http://handbrake.fr/") to convert videos to mp4. all it takes is just 1 click. choose the apple or psp preset on the right. it's an awesomely simple program.

---

