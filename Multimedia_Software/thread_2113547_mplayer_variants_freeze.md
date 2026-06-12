---
title: "mplayer variants freeze"
date: 2013-02-07
forum: Multimedia Software
---

### Post by imagiz on 2013-02-07
both umplayer and smplayer freeze more and more often. I'll watch video and then listen to music or surf the web and then come back to watch more vid. 

Both mplayer based players will open, size themselves and stop. sometimes they play a frame or two of the vid and then stop. they do not show time data for the video. VLC will play the video but is not a permanent solution as it cannot resume from last played position. 

it's fine once the thing is restarted but i am having to do that more and more often which makes me think maybe the system is becoming unstable.

Anyone else had this, anyone know why it is happening....and what can be done to stop it happening?

thanks.

---

### Post by GnuKian on 2013-02-07
you may want to try smplayer2: [http://www.webupd8.org/2012/01/install-mplayer2-and-smplayer2-in.html](http://www.webupd8.org/2012/01/install-mplayer2-and-smplayer2-in.html)

---

### Post by SeijiSensei on 2013-02-07
Play a video that freezes from the command line with mplayer ("mplayer /path/to/videofile") and post the results here inside [noparse]```

```[/noparse] tags.  If you start to see a neverending repetition of errors, just give us the first few.

Do you have this problem with all videos or just certain ones?  H.264-encoded videos are pretty much the norm these days, but they impose substantial demands on the processor to decode them in real time.  Newer encodings with "10-bit" color have additional issues.  If you have anything older files encoded with XviD in the AVI container (usually filename.avi), do you see the same problems with those?

What video card do you have?  Use the command "lspci" if you don't know.  Also include the results of "cat /proc/cpuinfo | grep 'model name'".

Mplayer2 might help, but lets see what you have in the way of hardware first.

---

### Post by imagiz on 2013-02-08
thanks for that. just installed mplayer2. let's see how it goes.

---

### Post by imagiz on 2013-02-08
i'll try mplayer2 before going deeper. it's great that you've shared your knowledge and hope i may draw on it again should mplayer2 not solve my problem. many thanks.

---

### Post by imagiz on 2013-02-08
> **SeijiSensei said:**
> Play a video that freezes from the command line with mplayer ("mplayer /path/to/videofile") and post the results here inside [noparse]```

```[/noparse] tags.  If you start to see a neverending repetition of errors, just give us the first few.

Do you have this problem with all videos or just certain ones?  H.264-encoded videos are pretty much the norm these days, but they impose substantial demands on the processor to decode them in real time.  Newer encodings with "10-bit" color have additional issues.  If you have anything older files encoded with XviD in the AVI container (usually filename.avi), do you see the same problems with those?

What video card do you have?  Use the command "lspci" if you don't know.  Also include the results of "cat /proc/cpuinfo | grep 'model name'".

Mplayer2 might help, but lets see what you have in the way of hardware first.

i'll try mplayer2 before going deeper. it's great that you've shared your knowledge and hope i may draw on it again should mplayer2 not solve my problem. many thanks.

---

### Post by imagiz on 2013-02-08
> **GnuKian said:**
> you may want to try smplayer2: [http://www.webupd8.org/2012/01/install-mplayer2-and-smplayer2-in.html](http://www.webupd8.org/2012/01/install-mplayer2-and-smplayer2-in.html)

thanks for that. just installed mplayer2. let's see how it goes.

---

### Post by furything on 2013-02-08
You can resume video in VLC
[http://askubuntu.com/questions/164233/how-do-i-resume-video-play-from-the-point-it-was-stopped-with-vlc](http://askubuntu.com/questions/164233/how-do-i-resume-video-play-from-the-point-it-was-stopped-with-vlc)
But if something is not set up correctly working it may be worth taking up SeijiSensei offer to assist

---

### Post by andrew.46 on 2013-02-09
Perhaps consider building your own copy of MPlayer:

[https://help.ubuntu.com/community/Compiling%20MPlayer](https://help.ubuntu.com/community/Compiling%20MPlayer)

---

### Post by imagiz on 2013-02-14
> **andrew.46 said:**
> Perhaps consider building your own copy of MPlayer:

[https://help.ubuntu.com/community/Compiling%20MPlayer](https://help.ubuntu.com/community/Compiling%20MPlayer)

wow!!

---

### Post by imagiz on 2013-02-14
.

---

### Post by imagiz on 2013-02-14
I seem to have solved the problem. 

I think alsa being used for both video and audio players caused a conflict. 

Now I have set alsa for video and pulse for audio.

Mplayer now works fine.

---

