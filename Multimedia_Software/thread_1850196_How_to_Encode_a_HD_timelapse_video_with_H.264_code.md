---
title: "How to: Encode a HD timelapse video with H.264 codec and MP4 format"
date: 2011-09-26
forum: Multimedia Software
---

### Post by nahuel_89p on 2011-09-26
Ok. You have taken a few thousands of photos, and now you expect to turn them into a cool time lapse video. You also would like to upload it to, for example, Vimeo, as an HD video. Of course, you want all of this without using Windows or any of it's apps.

That's exactly what i did here: [http://vimeo.com/29459342](http://vimeo.com/29459342) (This video hasn't the full res of HD cos i wrote the resize settings wrong. However, it works as you input resize settings above 1280*720px. For vimeo specifications, read the [Vimeo FAQ]("http://vimeo.com/help/faq"))

Vimeo tells you that:
> 
A codec is the format in which your video will be encoded. Different codecs have different features and varying quality. For best results, we recommend using H.264 (sometimes referred to as MP4).

How to? 
I managed to do it using MEncoder and FFMPEG: Both are in synaptic. However a special install is needed. Without it, the commands for encoding the video won't work properly (THANKS FakeOutdoorsman):


> **FakeOutdoorsman said:**
> **FFmpeg** is a versatile tool to encode and decode a multitude of video and audio formats.  **x264** encodes high-quality H.264 video.

[SIZE="4"][color=#663300]Choose your Ubuntu[/color][/SIZE]
[SIZE="4"]0.[/SIZE]The instructions on the page are for [size="3"][color=#FF6600]**Ubuntu Natty Narwhal 11.04**[/color][/size] and [size="3"][color=#3333FF]**Ubuntu Maverick Meerkat 10.10**[/color][/size]. Separate instructions are also available for older, supported releases:
[list]
[*][Install FFmpeg and x264 on Ubuntu Lucid Lynx 10.04 LTS](http://ubuntuforums.org/showpost.php?p=9868359&postcount=1289)
[*][Install FFmpeg and x264 on Ubuntu Hardy Heron 8.04 LTS](http://ubuntuforums.org/showpost.php?p=6963607&postcount=360)
[*] Retired Guides: [Ubuntu Karmic Koala 9.10](http://ubuntuforums.org/showpost.php?p=9114176&postcount=967) [Ubuntu Jaunty Jackalope 9.04](http://ubuntuforums.org/showpost.php?p=8345112&postcount=636), [Ubuntu Intrepid Ibex 8.10](http://ubuntuforums.org/showpost.php?p=8345112&postcount=636), [Ubuntu Dapper Drake 6.06 LTS](http://ubuntuforums.org/showpost.php?p=6566863&postcount=287)
[/list]


[SIZE="4"][color=#663300]Install the Dependencies[/color][/SIZE]
[SIZE="4"]1.[/SIZE] Uninstall x264, libx264-dev, and ffmpeg if they are already installed. Open a terminal and run the following (you can usually paste into a terminal with *shift+ctrl+v*). [color=#FF6600]Copy and paste the whole code box for each step[/color].
```
sudo apt-get remove ffmpeg x264 libx264-dev
```
[SIZE="4"]2.[/SIZE] Get all of the packages you will need to install FFmpeg and x264 (you may need to [enable the Universe and Multiverse repositories]("https://help.ubuntu.com/community/Repositories/Ubuntu")):
```
sudo apt-get update
sudo apt-get install build-essential checkinstall git libfaac-dev libjack-jackd2-dev \
  libmp3lame-dev libopencore-amrnb-dev libopencore-amrwb-dev libsdl1.2-dev libtheora-dev \
  libva-dev libvdpau-dev libvorbis-dev libx11-dev libxfixes-dev libxvidcore-dev texi2html \
  yasm zlib1g-dev
```


[SIZE="4"][color=#663300]Install x264[/color][/SIZE]
[SIZE="4"]3.[/SIZE]  Get the current source files, compile, and install **x264**.
```

cd
git clone git://git.videolan.org/x264
cd x264
./configure --enable-static
make
sudo checkinstall --pkgname=x264 --pkgversion="3:$(./version.sh | \
    awk -F'[" ]' '/POINT/{print $4"+git"$5}')" --backup=no --deldoc=yes \
    --fstrans=no --default

```



Now that everything is properly installed, we're ready to encode the video:
3 commands here, each one is separated by a ";" from another, so you can run it by copy paste. This must be run in the same folder your photos are in.

```
mencoder mf://*.jpg -mf fps=30 -vf scale=1280:-1 -ovc x264 -x264encopts pass=1:bitrate=6000:crf=20:preset=veryslow -nosound -ofps 30 -noskip -of rawvideo -o rawoutput.264 ; ffmpeg -f h264 -i rawoutput.264 -r 30 -vcodec copy muxed.mp4 ; rm rawoutput.264

```
Aclaration: You can replace "30" by your desired frames per second. And in ```
preset=veryslow 
```you can change to "veryfast" if you want just a sample video. Encoding time will shorten greately, and quality will suffer a little bit.

It took me few days until i get this. But of course, the point is that with ubuntu is more than possible to achieve a high quality timelapse video created from photos. It's really cool.


Expanation: 1)Mencoder creates a RAW video output using H.264 codec, b-frames, and a set of preseted parameters that goes for high quality. Now, since MEncoder's MP4 muxer doesn't get on well with b-frames videos, we will have to mux it into a MP4 container with FFMEG. That's what the second command do. 3) The third command deletes the RAW H.264 video, leaving alone the mp4 video.

Finally, you can add an audio track to make it more interesting:

```
ffmpeg -i video-without-audio.mp4 -i audio.mp3 -vcodec copy -acodec copy video-with-audio.mp4
```



The truth is that FFMPEG can do this all, but the H.264 encoding with FFMPEG was terrible in my case, the dynamic range happened to be from 14,14,14 to 235,235,235, ergo, darkest pixels weren't black (0,0,0) and whitest pixels weren't white (255,255,255). Greyish and awful image, but i couldn't solve it.


Hope somebody finds this useful when googling.

---

