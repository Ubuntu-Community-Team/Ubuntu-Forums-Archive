---
title: "Mencoder"
date: 2008-10-16
forum: Multimedia Software
---

### Post by pisio on 2008-10-16
I Get information from [http://wiki.showmedo.com/index.php/Video_editing_Ubuntu](http://wiki.showmedo.com/index.php/Video_editing_Ubuntu)
How I can adding subs to  movie. (Avidemux can't adding it )
```
pisio@unix:~/Desktop/I.Spy.2002.DVDRip.XviD.AC3-WAF/test$ mencoder -oac copy -ovc raw -sub I.Spy.2002.DVDRip.XviD.AC3.CD1-WAF.sub  -sub-bg-alpha  150 -utf8 -o I.Spy.2002.DVDRip.XviD.AC3.CD1-WAF.avi test.avi
MEncoder 2:1.0~rc2-0ubuntu13 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU          6320  @ 1.86GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 0  data: 0x0 - 0x0
Win32 LoadLibrary failed to load: avisynth.dll, /usr/lib/win32/avisynth.dll, /usr/local/lib/win32/avisynth.dll
Seek failed
============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.

Exiting...
pisio@unix:~/Desktop/I.Spy.2002.DVDRip.XviD.AC3-WAF/test$ sudo apt-cache search avisynth
pisio@unix:~/Desktop/I.Spy.2002.DVDRip.XviD.AC3-WAF/test$ 


```

---

### Post by shirilover on 2008-10-16
Avidemux can add subtitles, but not if you just copy the video stream.
You need to actually re-encode the video.
Should you choose to do so, open the video file in avidemux.
On the left under Video, select MPEG-4 ASP (Xvid4) from the drop-down list.
Click the Configure button.
On the Main tab of the Xvid encoding options dialog, select Same quantizer as input for encoding type. You may want to adjust settings in the other tabs to your preferences. Click OK when finished.
Now, click the Filters button.
On the left, select the subtitles tab.
Select Subtitler from the list in the middle and click the large '+' button at the bottom.
In the subtitler dialog, place your subtitle file in the text box using the browse button. Select your font and encoding type for the subtitles.
You can also change the color, size and position using the buttons in the dialog. Click OK when finished.
Your subtitle filter should appear in the list of active filters.
Unless you want to change the audio stream, leave it as copy.
Select the container for your new video file from the drop-down list under format.
Press the save button and give your new file a name.
Depending on your hardware, it may take several minutes to a few hours to re-encode your video.

---

### Post by pisio on 2008-10-17
> **shirilover said:**
> Avidemux can add subtitles, but not if you just copy the video stream.
You need to actually re-encode the video.
Should you choose to do so, open the video file in avidemux.
On the left under Video, select MPEG-4 ASP (Xvid4) from the drop-down list.
Click the Configure button.
On the Main tab of the Xvid encoding options dialog, select Same quantizer as input for encoding type. You may want to adjust settings in the other tabs to your preferences. Click OK when finished.
Now, click the Filters button.
On the left, select the subtitles tab.
Select Subtitler from the list in the middle and click the large '+' button at the bottom.
In the subtitler dialog, place your subtitle file in the text box using the browse button. Select your font and encoding type for the subtitles.
You can also change the color, size and position using the buttons in the dialog. Click OK when finished.
Your subtitle filter should appear in the list of active filters.
Unless you want to change the audio stream, leave it as copy.
Select the container for your new video file from the drop-down list under format.
Press the save button and give your new file a name.
Depending on your hardware, it may take several minutes to a few hours to re-encode your video.

10x

---

### Post by pisio on 2008-10-17
Try about 10 times. No subtitles in movies.
Thought and drawn Naruto and put English subtitles on filma.Obache they left.
Can this be a problem and avidemux?

---

