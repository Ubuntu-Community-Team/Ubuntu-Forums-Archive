---
title: "PS3 MKV x264 how to play them ?"
date: 2007-08-01
forum: Multimedia &amp; Video
---

### Post by davidme on 2007-08-01
I simply want to play MKV video files on my PS3.

So far playing them via VLC on PS3 gives lagging since I think there is not enough ram ?

PS3 XMB cannot play MKV files.

They say that it can be as simple as chagning the container from MKV to MP4 to make the files playbale on PS3. I have searched a lot and cannot find anything useful on how to perform this magical video container change on Linux. Only windows guides I saw.

I just want to play my MKV HD video files on PS3, how do I do that ?

---

### Post by tseliot on 2007-08-02
Did you try Mplayer + w32codecs ?

---

### Post by davidme on 2007-08-02
Yes, it VLC amd Mplayer  do play the files, but there is lag. It freezes back and forth. As if there is not enough CPU or RAM to process these files.

---

### Post by tseliot on 2007-08-02
> **davidme said:**
> Yes, it VLC amd Mplayer  do play the files, but there is lag. It freezes back and forth. As if there is not enough CPU or RAM to process these files.
The problem is that the PS3 doesn't use its own (Nvidia) graphic card but only relies on the CELL processor. HD videos are quite resource intensive...

Unfortunately Sony locked the access to the GPU (on Linux).

---

### Post by davidme on 2007-08-03
Ok, can we try it the other way ?

I know that on Windows there are quiet a few programs that can change video containers from mkv to mp4. For example PS3 Video 9

Is there something like that on Linux ?

I kinds of miss having Xbox 360 which I traded for PS3. There are so many files that are HD in WMV and you can easily play them on Xbox 360.

There are no good games on PS3 and it can only play a few file types. At least any of the popular ones

---

### Post by tseliot on 2007-08-03
1) type:
```
sudo apt-get install ffmpeg mkvtoolnix
```

2) download the file convertmkv.py which I attached to this post.
[COLOR="Red"]**NOTE: I didn't write or try the script therefore you should use it at your very own risk**[/COLOR]
I took the script from this page:
[http://www.larsen-b.com/Article/261.html](http://www.larsen-b.com/Article/261.html)

3) Put the mkv file in the directory in which you put convertmkv.py 

4) Open terminal and "cd" to the directory in which you put convertmkv.py 

5) type:
```
python convertmkv.py name_of_your_mkvfile
```

---

### Post by davidme on 2007-08-03
The script you took from the site has this 

"This stuff can be repack in a AVI (xivd..) file with some open source tools. Here, a little script to do the hard stuff ;)"

This script will repack it into xvid format which PS3 does not support. I need MP4

Thanks.

---

### Post by tseliot on 2007-08-04
1) use that script to convert the file into an xvid
2) convert the xvid file into an mp4 by typing:
```
ffmpeg -f mp4 -vcodec mpeg4 -acodec aac -maxrate 5000k -bufsize 4096 -i /path/to/originalavi.avi /path/to/newmov.mov
```

NOTE: you will have to replace "/path/to/originalavi.avi" and "/path/to/newmov.mov" with the real path and names of the files

---

### Post by davidme on 2007-08-04
I really appreciate all your help tseliot.

But all this work looks like a big waste of time. That means for every video file I want to watch, I have to go through all these steps which take a lot of time as this is a video conversion.

I think I will just wait until PS3 will natively support playing these files or Tversity will somehow work on Linux.

Thank you.

---

### Post by goldenfri on 2008-07-12
I am trying to use this script and I get the following errors when combining the files with the following: ffmpeg -i temp_audio.mp3 -i temp_video.avi -vcodec copy -acodec copy output.avi

[mp3 @ 0xb7f80110]Could not find codec parameters (Audio: mp2, 48 kb/s)
temp_video.avi: could not find codec parameters

I have tried doing it not in a script and still get the same errors I can't figure out what I am doing wrong.

mkvmerge -i gives me:

File 'TBB.mkv': container: Matroska
Track ID 1: video (V_MPEG4/ISO/AVC)
Track ID 2: audio (A_AC3)

can anyone help?

EDIT: nevermind I found my answer here: [http://ubuntuforums.org/showthread.php?t=548547&page=4](http://ubuntuforums.org/showthread.php?t=548547&page=4)

---

