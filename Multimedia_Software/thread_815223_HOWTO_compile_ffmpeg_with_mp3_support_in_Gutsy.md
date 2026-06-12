---
title: "HOWTO: compile ffmpeg with mp3 support in Gutsy"
date: 2008-06-01
forum: Multimedia Software
---

### Post by doncristobal on 2008-06-01
**The task:** I want to download funny movies from youtube etc. to my mobile music/video player (Cowon iAudio7, and also a friend's Cowon D2). The players need avi video files with mp3 audio in it. 

**The problem:** The program ffmpeg from the Ubuntu repositories is compiled without mp3 support. Therefore
```
sudo apt-get install ffmpeg
```
or something similar (like installing ffmpeg from Synaptic) does *not* help. 
I know, there are very good reasons for Ubuntu not to contain certain types of software like the mp3 codecs, but personally, i'm rather able to make Ubuntu encode mp3 than to make my Cowon play movies with free audio codecs...

**The solution:** We'll have to compile our own ffmpeg with mp3 support (based on [http://symbiotix.net/articles/compiling-ffmpeg-mp3-ubuntu-revised-ubuntu-gutsy-server#comment-543](http://symbiotix.net/articles/compiling-ffmpeg-mp3-ubuntu-revised-ubuntu-gutsy-server#comment-543) which worked for me, except for some points)

0. Make sure that ffmpeg is not installed (not sure if that's necessary)
```
sudo apt-get remove ffmpeg
```

1. enable universe and multiverse repositories
[https://help.ubuntu.com/8.04/add-applications/C/extra-repositories.html](https://help.ubuntu.com/8.04/add-applications/C/extra-repositories.html)

2. get your tools

```
sudo apt-get install checkinstall build-essential subversion
```

3. get the latest ffmpeg sources

```
cd /usr/local/src

```
```
sudo svn checkout svn://svn.mplayerhq.hu/ffmpeg/trunk ffmpeg
```

4. get the necessary dependencies

```
sudo apt-get install liblame-dev libfaad-dev libfaac-dev libxvidcore4-dev liba52-0.7.4 liba52-0.7.4-dev libx264-dev
``` 

5. configure

```
cd ffmpeg

```
```
sudo ./configure --enable-gpl --enable-liba52 --disable-debug --enable-libmp3lame --enable-libfaad --enable-libfaac --enable-pthreads --disable-vhook
```

6. compile

```
sudo make
```
This will take a lot of time.

7. create the .deb package

```
sudo checkinstall
```

note: just press [return] each time when asked for a configuration option. 
In my case, this directly installed the newly generated deb package, so i could skip step 8. If that's not the case for you, do step 8.

8. install the .deb package

```
sudo dpkg -i [ffmpeg_your_version.deb]
```

9. Refresh the path environment variables in order for your system to find the new ffmpeg
```
sudo rehash
```

---

Now your ffmpeg should be able to convert videos with mp3 audio, e.g. 
```
ffmpeg -i input_youtube_video.flv -vcodec mpeg4 -s 160x128 -vb 256k -r 15 -acodec libmp3lame output.avi
```

What's just sad: My Cowon iAudio7 still does not like the movie. So if anyone can tell me the right ffmpeg parameters for that Cowon model...

---

### Post by kostkon on 2008-06-02
Another easier solution is to install the version of *FFMpeg* that the [*Medibuntu* repository]("http://medibuntu.org/") offers that has the support for MP3 and other restricted formats enabled ;)

---

### Post by doncristobal on 2008-06-02
@kostkon: Don't tell me all this fuss was completely unnecessary... No, of course, tell me so, thank you very much. I'll try this as soon as I'm back home.

---

