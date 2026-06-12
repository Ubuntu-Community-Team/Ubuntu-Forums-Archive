---
title: "flv flash Totem internal data stream vlc undf"
date: 2009-03-23
forum: Multimedia Software
---

### Post by meka4996 on 2009-03-23
can't play downloaded flv flash files? 
due to youtube's recent re-encoding scheme for future pay-per-view plan...
or just downloadHelper not doing a good job...
for those errors ...
Totem [with GStreamer] with sound/audio delay/lagging or leading video
Totem cannot play with internal data stream error
VLC: No suitable decoder module: VLC does not support the audio or video format "undf". 
VLC: No suitable decoder module: VLC does not support the audio or video format "mlp ". 
VLC can't recognize the input's format

Solution...
just use another way to download. 
I now can play flv flash files using VLC or Totem in Ubuntu 8.04 Hardy and 8.10 Intrepid.
Try the following... thanks for contribution from 
[http://ubuntuforums.org/showthread.php?t=1048382](http://ubuntuforums.org/showthread.php?t=1048382)

cd /path/where/you/want/the/video/stored
$ clive [http://www.youtube.com/watch?v=xb9ypkc9Uvs](http://www.youtube.com/watch?v=xb9ypkc9Uvs) ... 
no installing, sets the file name and type automatically

$ youtube-dl [http://www.youtube.com/watch?v=xE0iPY7XGBo](http://www.youtube.com/watch?v=xE0iPY7XGBo) ... 

add pwn in front of youtube...
[http://www.youtube.com/watch?v=rpOhWvOoraw](http://www.youtube.com/watch?v=rpOhWvOoraw) -> 
[http://www.pwnyoutube.com/watch?v=rpOhWvOoraw](http://www.pwnyoutube.com/watch?v=rpOhWvOoraw)

[http://www.youtube.com/watch?v=_WSGwnz7XpY](http://www.youtube.com/watch?v=_WSGwnz7XpY) ->
[http://www.kissyoutube.com/watch?v=_WSGwnz7XpY](http://www.kissyoutube.com/watch?v=_WSGwnz7XpY) 
and it will bring you to a page to prompt if you have java and hit the download button. ...

The flv file copied from /tmp while firefox is opened cannot be played, it is less in size than that via the above ways!

---

### Post by meka4996 on 2009-05-09
the problem maybe is downloading method (as mentioned above), 
but above method is too time consuming as you cannot watch video while downloading it

Solution 2: use other real time video capture tools
Replay Media Catcher 3.0 might help??[http://applian.com/download-videos](http://applian.com/download-videos)

Solution 3: use some Windows flash players
Applian FLV Player 2.0 [http://applian.com/flvplayer/index.php](http://applian.com/flvplayer/index.php) in Wine 1.1.21 in Ubuntu 8.04 Hardy successfully play[with no audio delay] flash flv files obtained via DownloadHelper or copied from firefox tmp folder at /tmp, and these files are those VLC 0.9.9a or Totem 2.22.1 in Ubuntu 8.04 cannot play.

---

### Post by Bernhard001 on 2009-05-10
> **meka4996 said:**
> the problem maybe is downloading method (as mentioned above), 
but above method is too time consuming as you cannot watch video while downloading it

No. The download ways are not responsible.

The Flash-Videos are h264 encoded (says Windows-VLC). Someone checked more and found that the encoder was used is Sorenson....

I use Ubuntu 8.04 and the Medibuntu codecs. Vlc 0.99a is installed.

My problem video on Youtube: [http://www.youtube.com/watch?v=Mm-8aIcAJKo](http://www.youtube.com/watch?v=Mm-8aIcAJKo) .

Totem and Vlc doesn't work. Stream error (totem), undf-Codec (Vlc.)

Some help?

Best regards 
Bernhard

---

### Post by mc4man on 2009-05-10
@ Bernhard001
You should be able to play that with vlc 0.9.9a in hardy if vlc was built well

What you'd probably need to do first is run the video thru a current ffmpeg.

```
ffmpeg -i [COLOR="Red"]name[/COLOR].flv -acodec copy -vcodec copy [COLOR="Red"]name[/COLOR].mp4
```

You'd need a relatively current ffmpeg for this, see here
[http://ubuntuforums.org/showpost.php?p=6963607&postcount=360](http://ubuntuforums.org/showpost.php?p=6963607&postcount=360)

(you should see a video thumbnail after ffmpeg (screen, before and after ffmpeg

Edit : Otherwise any recent mplayer should play it as is (no ffmpeg

---

### Post by meka4996 on 2009-05-23
[... Updated 24 May 09]
Solution 4, The Final Solution!!! Thanks greatly to Bernhard001...

(for Ubuntu Intrepid 8.10, Hardy 8.04 and Gutsy 7.10, check out the forum link below)

Assuming booting from a fresh Ubuntu 9.04 Jaunty Hard disk install
--Step 1.
Wait for Update Manager checking patch updates (10 minutes)
Note: you don't have to install any updates, but you do have to wait for Update Manager to show up, otherwise, when you click on the file install_flash_player_10_linux.deb (see below), it will say missing dependency libcurl3 ...

--Step 2.
for youtube viewing: download the file install_flash_player_10_linux.deb from
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
click on the .deb file, it should download all other dependencies and install itself.

you can check if installation is successful by typing in Firefox url field "about:plugins", and see...
Shockwave Flash
File name: libflashplayer.so
Shockwave Flash 10.0 r22
MIME Type Description Suffixes Enabled
application/x-shockwave-flash Shockwave Flash swf Yes
application/futuresplash FutureSplash Player spl Yes

and some other default settings ...
Firefox->Edit-> Preferences-> Applications->
  Shockwave Flash file(application/futuresplash): Use Shockwave Flash (in Firefox)
  Shockwave Flash file(application/x-shockwave-flash): Use Shockwave Flash (in Firefox)

Note: the other method [unzip install_flash_player_10_linux.tar.gz, in terminal, run the file "flashplayer-installer" ] is not recommended, due to extreme difficulty for uninstalling flash player after that method.
You only need one method. If you use both methods, you will end up that Youtube not automatically plays videos, but you have to click on the ...xyz.swf link everytime!

--
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
Enable extra repositories
System -> Administration -> Software sources -> Tab= Ubuntu software
check boxes of
Canonical-supported Open Source software (main)
Community-maintained Open Source software ( universe ) 
Proprietary drivers for devices ( restricted )
Software restrictecd by copyright or legal issue ( multiverse )

--Step 3.
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)
B. Installing the "unstripped" libraries
```
sudo apt-get install ffmpeg libavcodec-unstripped-52
```

--Step 4.
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)
C. Installing the ubuntu-restricted-extras package
```
sudo apt-get install ffmpeg ubuntu-restricted-extras
```

That's IT! EASY!
Now you can use Firefox addon "DownloadHelper" to download flv files or just copy them from the folder /tmp 
[at upper left corner: Places-> Home Folder-> Up button-> Up button-> tmp]
I now can see flv video thumbnails in folders[in Nautilus, the file manager] 
I now can play all flash flv files with Totem Movie Player 2.26.1, good audio and video synchronization, but VLC 0.9.9a has video jittering problem[quick jumpy movements]...
tested on same flv file from 
[http://www.youtube.com/watch?v=2N45paD8jw8](http://www.youtube.com/watch?v=2N45paD8jw8)

---

### Post by meka4996 on 2009-10-18
If you want to watch dvd movies or play downloaded flv video files and mp3 files in Ubuntu Linux,

It's better to install everything in 32 bit, even if you have a 64 bit machine, as there are something missing in 64 bit depository like drivers, codecs...

Google keywords...
how to watch flv videos in linux
how to play flv files in linux
play flv files in linux
Ubuntu Linux play flv dvd mp3 mp4 wmv proprietary restricted format files

---

### Post by chinnaraaju on 2009-11-15
Thanks meka4996

I have tried your solution 4 step by step..but still i am receing internal data stream error...

please let me know what should i check now...

thanks,
chinna.

---

### Post by meka4996 on 2009-11-15
chinnaraaju, follow the link above [http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)
try to compile FFmpeg, 
or try solution 1,2,3 ;) or search on this forum, or use another distro like Mint or Ultimate, or go to [https://launchpad.net/ubuntu](https://launchpad.net/ubuntu). 
Use Divide-and-Conquer method: 
check if your computer can play any .flv file at all. What's special about some .flv files?
That's all I can offer. cheers

---

### Post by badrra on 2010-01-03
This is by far the best solution if you watn to watch youtube videos using an external player rather than the crappy flash player. Just follow this link. 

[http://badrra.wordpress.com/2009/12/03/watch-youtube-using-vlc-mozilla-plugin/](http://badrra.wordpress.com/2009/12/03/watch-youtube-using-vlc-mozilla-plugin/)

Have fun.

---

