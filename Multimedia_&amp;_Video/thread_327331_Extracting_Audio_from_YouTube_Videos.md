---
title: "Extracting Audio from YouTube Videos"
date: 2006-12-29
forum: Multimedia &amp; Video
---

### Post by SuperMike on 2006-12-29
I read on the web [**[COLOR="Red"]here[/COLOR]**]("http://macaudiovideo.wordpress.com/2006/12/17/how-to-extract-audio-from-youtube-videos/") and [**[COLOR="Red"]here[/COLOR]**]("http://www.linuxquestions.org/questions/showthread.php?t=508026") that you can download YouTube videos and extract their audio content in MP3 format. The technique for Ubuntu supposedly was:

1. Go to YouTube without logging in. If you're logged in already, log out. This shortens the URLs properly. Now search YouTube for the video you want and paste the URL into your favorite text editor.

2. Now go to:

[**[COLOR="Red"]http://www.youtubex.com/[/COLOR]**]("http://www.youtubex.com/")

...and paste this URL into the field they provide and click Get Video.

3. A page displays a Download hyperlink. Rightclick it and choose Save Target As. When a window appears, rename it to something like get_stream.flv. The *.flv file extension is important. Save it to your desktop.

4. Open a Terminal window and do:

cd ~/Desktop
ffmpeg -i get_stream.flv -f mp3 -vn -acodec copy audio.mp3

...and this saves 'audio.mp3' for you to play on your computer or copy to your portable MP3 player.

**[COLOR="Blue"]However, I wasn't able to get this to work.[/COLOR]** I can get the video part, but not the audio part. The file is created, and Totem can play it, but I get dead silence. Note my system can play DVD movies just fine, and MP3s just fine, so I have the proper audio and video codecs from Automatix.

Anyone got a better route?

---

### Post by SuperMike on 2006-12-29
Aha! I was **WRONG!!!**  It does work!  There was something up with the state of my session. I logged out and back in again, and then played the MP3 file. It worked just fine then.

Enjoy!

P.S. Another site that helps you get the FLV files is [[COLOR="Red"]**keepvid.com**[/COLOR]]("http://keepvid.com/").

---

### Post by SuperMike on 2006-12-29
Here's a script I've dug up that you can drop in /usr/bin as 'ytr' and then make it executable with 'sudo chmod a+x /usr/bin/ytr'. Then, you can create a launcher on your desktop for it, give it a YouTube icon, call it 'You Tube Ripper', and check off "Use Terminal".

```
#!/bin/bash
bu="http://youtube.com/get_video.php?"
mkdir -p ~/mp3
cd ~/mp3
read -p "YouTube url? " ur
read -p "Name? " nv
echo;echo;
wget ${ur} -O /tmp/y1
uf=${bu}`grep player2.swf /tmp/y1 | cut -d? -f2 | cut -d\" -f1`
wget "${uf}" -O /tmp/y.flv
ffmpeg -i /tmp/y.flv -f mp3 -vn -acodec copy "${nv}.mp3"
echo;echo;
echo "Your new MP3 file is saved in your home directory in the 'mp3' folder."
read
```

---

### Post by gilrim on 2006-12-29
regarding downloading the movies, I'd try one of these:
[https://addons.mozilla.org/search.php?q=youtube&type=A&app=firefox](https://addons.mozilla.org/search.php?q=youtube&type=A&app=firefox)

I've used Ook and UnPlug myself, they both work great

---

### Post by nphx on 2007-06-22
Do you know to save it as ogg instead of mp3?

---

### Post by david_2001 on 2007-06-22
> **nphx said:**
> Do you know to save it as ogg instead of mp3?
This works:
```
ffmpeg -i Some_YouTube_Video.flv -acodec vorbis -aq 60 -ac 2 Just_The_Audio.ogg
```

---

### Post by nphx on 2007-06-22
> **david_2001 said:**
> This works:
```
ffmpeg -i Some_YouTube_Video.flv -acodec vorbis -aq 60 -ac 2 Just_The_Audio.ogg
```

Prior to your post I played around with it and found out this works too: 

```
ffmpeg -i FlashFileName.flv -f ogg -vn -acodec vorbis AudioFileName.ogg
```

Your method works too, but the files are a larger with your method.

The same file I extracted with end result being 1.8mb, and I got 10.5mb with your method?

For some reason flash to mp3 converts a lot faster than flash to vorbis ogg.

---

### Post by david_2001 on 2007-06-22
> **nphx said:**
> Prior to your post I played around with it and found out this works too: 

```
ffmpeg -i FlashFileName.flv -f ogg -vn -acodec vorbis AudioFileName.ogg
```

Your method works too, but the files are a larger with your method.

The same file I extracted with end result being 1.8mb, and I got 10.5mb with your method?

For some reason flash to mp3 converts a lot faster than flash to vorbis ogg.
[LIST=1]
[*]All of the YouTube videos that I have downloaded contain single channel audio and ffmpeg gives the following error if I try your method to extract the audio:
> [vorbis @ 0xb04220]Current FFmpeg Vorbis encoder only supports 2 channels.
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height
(I'm using ffmpeg compiled from cvs but I'm not sure that should make any difference.)
[*]Regarding file size, I have audio quality set quite high (-aq 60).  Using a lower audio quality value will give a smaller output file.
[*]Flash to mp3 is faster because the original audio is already in mp3 format and so all ffmpeg has to do is extract it from the flv file.
[/LIST]

---

### Post by SuperMike on 2007-06-25
> **david_2001 said:**
> [LIST=1]
[*]All of the YouTube videos that I have downloaded contain single channel audio and ffmpeg gives the following error if I try your method to extract the audio:

(I'm using ffmpeg compiled from cvs but I'm not sure that should make any difference.)
[*]Regarding file size, I have audio quality set quite high (-aq 60).  Using a lower audio quality value will give a smaller output file.
[*]Flash to mp3 is faster because the original audio is already in mp3 format and so all ffmpeg has to do is extract it from the flv file.
[/LIST]

Hmm. Don't know. Here's what I did. Even though I built this on Breezy, I went and installed a fresh copy of Feisty Fawn. then, I did:

apt-get install xulrunner
apt-get install ffmpeg*
apt-get install ecasound*
apt-get install mpg123*
apt-get install lame*
# to tell you the truth, I think I only installed with asterisk (*) on ecasound, but don't fully recall at this point

...and then downloaded:

[http://code.google.com/p/yt2mp3/](http://code.google.com/p/yt2mp3/)

I made a shortcut to where I put yt2mp3 and fired it up. The GUI loaded. I put in a URL from YouTube and down it came with an MP3 file in $HOME/mp3 folder.

Note that if you get my version working either with the Bash script or with the yt2mp3 GUI version, it will give you a simulated stereo MP3 that's of pretty good quality, not a mono MP3.

---

### Post by SuperMike on 2007-06-26
Important -- Those reading this forum thread should look at this one:

[http://ubuntuforums.org/showthread.php?t=328347](http://ubuntuforums.org/showthread.php?t=328347)

---

### Post by david_2001 on 2007-06-26
I reckon that I'll stick to my way because it's simpler.  It doesn't give simulated stereo but does at least duplicate the mono input into the left and right output channels.  (I took a look at the yt2mp3 package.  It uses the ecasound fake stereo effect command line option "-etf:8".)

---

