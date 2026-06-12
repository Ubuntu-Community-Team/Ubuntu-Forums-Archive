---
title: "Medibuntu ffmpeg aac encoding funky?"
date: 2007-05-27
forum: Multimedia &amp; Video
---

### Post by GMaq on 2007-05-27
Hi,
     I've been following some of the threads on video for the iPod and not having much success, even though my scripts were good, The mp4 files I was creating would playback fine in VLC and MPlayer and even Quicktime under Windows XP, but when added to the iPod there was no audio, this was also apparent with files created with AviDemux which shares libfaad. Anyway I traced the problem to the "unlocked" Medibuntu ffmpeg. I got a newer ffmpeg build from debian-multimedia.org and now the scripts work fine on the iPod, even with 640xXXX H.264 resolutions. I just thought I would mention this in case anyone else was having difficulties creating iPod videos. BTW there is an excellent ffmpeg GUI front-end at [www.biggmatt.com](www.biggmatt.com) called "WinFF" it is very similar to "VIVE" but more versatile. There is a .deb there for download, the latest version is 0.29. I tried 2 different source versions of VIVE but got nowhere, although it looks good as well.

---

### Post by major_rocks on 2007-05-29
GMaq - thanks for this post, 

which repository did you use from debian-multimedia.org? They have a ton of repos on they're miirrors page:o

I believe i'm having similar issues encoding movies for my ipod. The audio is out of sync with video.

---

### Post by GMaq on 2007-05-29
major_rocks,
     I went to debian-multimedia.org and added the key for the "stable" branch, I then installed it using synaptic. Something about ffmpeg and AviDemux don't get along, my system seems to not want one to install if the other is present. As for the out-of-sync issue I've had some trouble with this as well, usually due to a bad DVD rip. Sometimes there are issues if you change your frame rate from the source file to your encoded file. For the record I have completely uninstalled AviDemux for the time being and am having success with both XviD and H.264 videos on my iPod using some presets I tweaked in WinFF.

---

### Post by major_rocks on 2007-05-30
GMaq-

thanks for the reply- i will probably give debian-multimedia.org's version of ffmpeg a try tomorrow. I'm really green at ripping and encoding video, and i have been using this info here:

[https://help.ubuntu.com/community/iPodVideoEncoding](https://help.ubuntu.com/community/iPodVideoEncoding)

mostly the lower section of the how-to pertaining to ffmpeg for encoding, and mplayer for dumping the dvd to a  .vob. I've had mixed results, from the dump being in spanish (i speak english), to what i mentioned before with video not syncing with audio. I have also had some rip and encodes go smoothly, i guess i just need to keep plugging away and try different things till i find what works best for my system on a consistent basis.

thanks for the info  !!

btw- i'll probably take a look at winff as well........i just cant seem to totally shake the windows ways just yet:shock:

---

### Post by GMaq on 2007-05-30
major_rocks,
    Like you I got most of my info from the same iPodVideoEncoding Wiki, I just took some of the script ideas and some Windows ffmpeg stuff I already knew and dumped it into WinFF, I contacted the developer and he said he would put the iPod presets I did on his site. BTW another workaround is using MP4Box which is in the Feisty repos under "gpac" I've had a couple of movies that ffmpeg wouldn't sync work by doing the Video and Audio separately and putting them together with MP4Box. It is a commandline tool but the commands are pretty straightforward - If I can do it then pretty much any chimpanzee can! Best of luck!

---

