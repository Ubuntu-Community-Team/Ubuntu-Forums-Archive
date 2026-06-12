---
title: "how to grab video and audio"
date: 2012-08-31
forum: Multimedia Software
---

### Post by Smiletastic on 2012-08-31
Hello,
I've been trying to record desktop but failed. What are exact command line(s) to do screencasting?
I tried : avconv -f oss -ar 8000 -ac 1 -i /dev/dsp1 -acodec mp2 -f rtp rtp://172.17.2.2:9090

but terminal read "r@r-P4M800-M7:~$ avconv -f oss -ar 8000 -ac 1 -i /dev/dsp1 -acodec mp2 -f rtp rtp://172.17.2.2:9090
avconv version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jun 12 2012 16:37:58 with gcc 4.6.3
[oss @ 0x9a34340] /dev/dsp1: No such file or directory
/dev/dsp1: Input/output error"
Is there any solution?

---

### Post by ajgreeny on 2012-08-31
I have never used avconv, but I have in the past used ffmpeg to record my desktop with some success, marred only by my slow machine's lack of ability to do it all fast enough.
```
**ffmpeg** -f x11grab -s 1280x1024 -r 15 -i :0.0 -s 1280x1024 -r 15 -sameq video.avi
```Change the resolution to fit yours
I don't now if the same command and syntax will work with **avconv** but it is worth a try.

---

### Post by Smiletastic on 2012-08-31
Thank you for the answer but I can't use "ffmpeg"  because my terminal reads "This program is deprecated." 
Is there any way to work around the problem?

---

### Post by RodGer GR on 2012-08-31
You can now use avconv instead of ffmpeg.
Give the command
```
man avconv
```to see the manual.
Just in case the program is not already installed (if ffmpeg is installed, avconv is probably also installed), give:
```
sudo apt-get install libav-tools
```Hope this helps...

[COLOR=Red]EDIT[/COLOR]:
I suggest to try first with the same syntax as ajgreeny said, using avconv:
```
avconv -f x11grab -s 1280x1024 -r 15 -i :0.0 -s 1280x1024 -r 15 -sameq video.avi
```

---

### Post by micahpage on 2012-08-31
> Thank you for the answer but I can't use "ffmpeg" because my terminal reads "This program is deprecated." 
Is there any way to work around the problem?
Mine also says the same, but it still records if you continue the process. I still use ffmpeg as it works.

---

### Post by RodGer GR on 2012-08-31
Update:
This should work (I tested it) :
```
avconv -f x11grab -show_region 1 -video_size hd720 -framerate 24 \ -i :0.0 -threads 2 -q 1 ./test.mkv 
```

source: [http://my.opera.com/patkoscsaba/blog/2012/08/17/desktop-recording-with-avconv-formerly-know-as-ffmpeg](http://my.opera.com/patkoscsaba/blog/2012/08/17/desktop-recording-with-avconv-formerly-know-as-ffmpeg)

---

### Post by Paddy Landau on 2012-08-31
What about using a GUI? You can install Record My Desktop. I'm not at my computer, but I think it is called gtk-recordmydesktop. It works well.

Yes, it is called [gtk-recordmydesktop]("apt:gtk-recordmydesktop").

---

### Post by shantiq on 2012-09-01
[**with ffmpeg**]("http://ubuntuforums.org/showpost.php?p=10579930&postcount=1")

---

### Post by Smiletastic on 2012-09-01
Paddy Landau, thank u for mentioning gtk-recordmydesktop but the worst thing about it is that when using this application soud NEVER coincide with video.

RodGerGR, thank u really much for your answers but both commands didn't work with me.

1)       	 	 	 	 	 	   r@r-P4M800-M7:~$ avconv -f x11grab -s 1280x1024 -r 15 -i :0.0 -s 1280x1024 -r 15 -sameq video.avi 
 avconv version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers 
   built on Jun 12 2012 16:37:58 with gcc 4.6.3 
 [x11grab @ 0x97f03c0] device: :0.0 -> display: :0.0 x: 0 y: 0 width: 1280 height: 1024 
 [x11grab @ 0x97f03c0] shared memory extension  found 
 [COLOR=#800000]*_**X Error of failed request:  BadMatch (invalid parameter attributes) **_*[/COLOR]
   Major opcode of failed request:  143 (MIT-SHM) 
   Minor opcode of failed request:  4 (X_ShmGetImage) 
   Serial number of failed request:  11 
   Current serial number in output stream:  11 



What does the underlined part mean? How can I solve the problem?


2)     	 	 	 	 	 	   
r@r-P4M800-M7:~$ avconv -f x11grab -show_region 1 -video_size hd720 -framerate 24 \ -i :0.0 -threads 2 -q 1 ./test.mkv 
 avconv version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers 
   built on Jun 12 2012 16:37:58 with gcc 4.6.3 
 [COLOR=#800000]_**Requested output format 'x11grab' is not a suitable output format **_[/COLOR]
 

  [COLOR=#000000]How can I correct the underlined part?[/COLOR]
  

  [COLOR=#000000]I wish the developers gave more ready commands to choose from.[/COLOR]


[COLOR=#000000]Can anyone help to work around the problem?
[/COLOR]

---

### Post by Paddy Landau on 2012-09-01
> **Smiletastic said:**
> gtk-recordmydesktop …. soud NEVER coincide with video.
That can happen when the hardware does not keep up with the recording settings. You can adjust the settings to see what happens. Press Advanced > Performance. Play around, especially with reducing the Frames Per Second, disabling Encode On the Fly, and enabling Zero Compression and Quick Subsampling.

---

### Post by gordintoronto on 2012-09-01
What are the specs for your computer? Recording a desktop takes a pretty quick CPU.

---

### Post by Smiletastic on 2012-09-01
Paddy Landau, thanks a lot for your information. Finally've I managed to grab desktop.
I wish you all the best!

---

### Post by Smiletastic on 2012-09-01
Paddy Landau, thanks a lot for your help! Finally I've managed to grab desktop.
I wish you all the best!

---

### Post by Paddy Landau on 2012-09-02
> **Smiletastic said:**
> … Finally I've managed to grab desktop.
Excellent. Which program did you use?

Please [mark this thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

### Post by Smiletastic on 2012-09-05
Paddy Landau, thanks a lot. It worked for me!
Good luck!

---

### Post by Smiletastic on 2012-09-05
I used the program you mentioned, namely gtk-recordmydesktop.
Thanks a lot!

---

