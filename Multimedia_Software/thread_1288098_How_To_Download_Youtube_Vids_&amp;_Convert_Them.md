---
title: "How To Download Youtube Vids &amp; Convert Them"
date: 2009-10-10
forum: Multimedia Software
---

### Post by tokyo-joe on 2009-10-10
I hesitate to ask this question because many people must have asked the same question millions of times in the past.

How can I download youtube videos and convert them into universal video formats like avi, mpeg-4, mpeg, and so on?

There are some applications, such as xVideoServiceThief, but it does not convert flv files on my Ubuntu Jaunty 9.04. The DownloadHelper Firefox add-on does not work too when it comes to conversion.

I assume I must tweak the ffmpeg encoder, but I don't know how.

Can anyone be of assistance?

Thanks in advance.

---

### Post by TheBuzzSaw on 2009-10-10
I cannot offer much advice on converting the videos to a format of your liking, but I can tell you the best way to download YouTube (and most Flash) videos.

After the video is buffered, simply check your /tmp folder. You'll see a folder called Flashxxxx (the xxxx will be some jumbled mix of letters/numbers). Just copy that file to your home folder and rename it. It will either be a .flv or .mp4 file (depending on the meta data). It is fantastic because you need no plugin/tool of any kind. Just go to the /tmp folder and reap your rewards. :D

<3 Linux

---

### Post by FakeOutdoorsman on 2009-10-11
YouTube videos of HQ and HD quality are already using H.264 video and AAC audio.  You can simply copy and paste the video and audio from the FLV container and place it into a MP4 container with FFmpeg.  Building off of what TheBuzzSaw says, here is an example from the HQ version of the interestingly hilarious [UAF Nanook Hockey Open 07-08 "Highway to the Danger Zone"](http://www.youtube.com/watch?v=O5YjPteCPLo) movie:
```
cd /tmp
ffmpeg -i FlashYpLhof -acodec copy -vcodec copy ~/hockey.mp4
```
Maybe I only think it's funny because I went to school there.  Anyway, this will copy the audio and video into a MP4 file without re-encoding.  This preserves the quality and is fast.  The **~/** is a shortcut to your home folder.

**Edit:** Looking closer at the HQ files, they appear to already be using the MP4 container.

---

### Post by Nyken on 2009-10-15
OMG! Thank you! I've been trying all sorts of stuff to get this to work and it turns out it was THIS simple all along! 

Thank you, much kudos, much luck, much lots of what you like, much what your enemies don't like.

:grin:

---

### Post by wilee-nilee on 2009-10-15
The temp folder is a good trick, also video downloader helper a Firefox add on will download and convert if you set it up correctly. [https://addons.mozilla.org/en-US/firefox/search?q=download+helper&cat=all](https://addons.mozilla.org/en-US/firefox/search?q=download+helper&cat=all)

---

### Post by IAmNoodle on 2009-10-15
> **TheBuzzSaw said:**
> I cannot offer much advice on converting the videos to a format of your liking, but I can tell you the best way to download YouTube (and most Flash) videos.

After the video is buffered, simply check your /tmp folder. You'll see a folder called Flashxxxx (the xxxx will be some jumbled mix of letters/numbers). Just copy that file to your home folder and rename it. It will either be a .flv or .mp4 file (depending on the meta data). It is fantastic because you need no plugin/tool of any kind. Just go to the /tmp folder and reap your rewards. :D

<3 Linux

You can (or at least used to be able to) do the same thing in Windows. Mind you, last time I tried, it didn't work

---

### Post by crichard on 2010-01-06
You no need to use any specific addon or software to download utube videos.
Here is a simple tweak, try this link [http://surferzworld.com/?p=35](http://surferzworld.com/?p=35)

---

### Post by Kreuger on 2010-01-06
You can try [Utube]("http://sourceforge.net/projects/utube/")

---

### Post by Enigmapond on 2010-01-10
Personally I use that Firefox Add-on but most times I don't convert from FLV as VLC media player plays everything I throw at it. If I do convert it I'll use ffmpeg in the command-line.

---

### Post by aerobeing on 2011-07-12
I was just looking for something for that particular purpose and found a hidden gem - viget. In the Ubuntu Software Centre it only appears if you directly search by the name (could not find it by entering "youtube"). Could not rate it there, either. Best youtube downloader so far. Simple, quick, no annoying autoplaying videos like in minitube.

---

### Post by handy on 2011-07-12
I've tried a few different methods & the way I do it now which has been perfectly reliable for me is via DownloadHelper.

[https://addons.mozilla.org/en-US/firefox/addon/video-downloadhelper/](https://addons.mozilla.org/en-US/firefox/addon/video-downloadhelper/)

So I don't know why the OP is having problems?

Have you contacted the developer of DLHelper? If there is a problem he would want to know. If he knows why you are having one he may be able to offer a solution.

---

### Post by MichaelNevermore on 2013-02-14
Best solution for me:

[https://addons.mozilla.org/en-US/firefox/addon/1-click-youtube-video-download/?src=ss](https://addons.mozilla.org/en-US/firefox/addon/1-click-youtube-video-download/?src=ss)

This is a firefix add-on that puts a button underneath every youtube video. Click it, and it will give you the option to choose from various qualities and formats and you can save the video to anywhere on your hard drive. Works wonders on Ubuntu.

---

### Post by howefield on 2013-02-14
Old thread closed.

---

