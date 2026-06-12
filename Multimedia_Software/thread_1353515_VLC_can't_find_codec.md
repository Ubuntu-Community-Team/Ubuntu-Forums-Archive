---
title: "VLC can't find codec?"
date: 2009-12-12
forum: Multimedia Software
---

### Post by crisco552 on 2009-12-12
I try to record my dazzle and I get this:

 p, li { white-space: pre-wrap; }  [COLOR=#ff0000]Streaming / Transcoding failed:[/COLOR]
 [COLOR=#000000]It seems your FFMPEG (libavcodec) installation lacks the following encoder:[/COLOR]
 [COLOR=#000000]MPEG-4 Video.[/COLOR]
 [COLOR=#000000]If you don't know how to fix this, ask for support from your distribution.[/COLOR]
 
 [COLOR=#000000]This is not an error inside VLC media player.[/COLOR]
 [COLOR=#000000]Do not contact the VideoLAN project about this issue.[/COLOR]


[COLOR=#000000]whenever I choose MP4 how do I reinstall it?
[/COLOR]

---

### Post by hansdown on 2009-12-12
Hi crisco552.

MPEG4 should work in VLC.

Try re-installing VLC.

---

### Post by crisco552 on 2009-12-12
I tried that and again it came up with the error...

---

### Post by hansdown on 2009-12-12
Perhaps try reinstalling  FFMPEG in synaptic.

---

### Post by alexfish on 2009-12-12
> **crisco552 said:**
> I try to record my dazzle and I get this:

 p, li { white-space: pre-wrap; }  [COLOR=#ff0000]Streaming / Transcoding failed:[/COLOR]
 [COLOR=#000000]It seems your FFMPEG (libavcodec) installation lacks the following encoder:[/COLOR]
 [COLOR=#000000]MPEG-4 Video.[/COLOR]
 [COLOR=#000000]If you don't know how to fix this, ask for support from your distribution.[/COLOR]
 
 [COLOR=#000000]This is not an error inside VLC media player.[/COLOR]
 [COLOR=#000000]Do not contact the VideoLAN project about this issue.[/COLOR]


[COLOR=#000000]whenever I choose MP4 how do I reinstall it?
[/COLOR]

Hi

 can I ask which version of Ubuntu are you using ,  upgraded or clean install

     also  which version  VLC do you have

thanks in advance

alexfish

---

### Post by crisco552 on 2009-12-12
I am using Ubuntu 9.04 and vlc version is... 0.9.9a

---

### Post by mc4man on 2009-12-12
never used intrepid but maybe search ffmpeg in synaptic and if not installed then install the 'unstripped' ffmpeg libs (libavcodec-unstripped-51, libavformat-unstripped-52, ect.

If so, then don't remove the current ones, just mark the unstripped ones for install and apply.

---

### Post by alexfish on 2009-12-13
> **crisco552 said:**
> I try to record my dazzle and I get this:

 p, li { white-space: pre-wrap; }  [COLOR=#ff0000]Streaming / Transcoding failed:[/COLOR]
 [COLOR=#000000]It seems your FFMPEG (libavcodec) installation lacks the following encoder:[/COLOR]
 [COLOR=#000000]MPEG-4 Video.[/COLOR]
 [COLOR=#000000]If you don't know how to fix this, ask for support from your distribution.[/COLOR]
 
 [COLOR=#000000]This is not an error inside VLC media player.[/COLOR]
 [COLOR=#000000]Do not contact the VideoLAN project about this issue.[/COLOR]


[COLOR=#000000]whenever I choose MP4 how do I reinstall it?
[/COLOR]

                                 check these in synaptic


 vlc-plugin-pulse
 libsdl1.2debian-all
 
also
 Does The Ubuntu Software Centre Look like this

---

### Post by crisco552 on 2009-12-13
No my package manager does not look like that, should it?

---

### Post by alexfish on 2009-12-14
Mine does

Run the update manager see what happens

also check the software sources

  failing that

 have a look in synaptic

---

### Post by mc4man on 2009-12-14
There is no software center in Jaunty (9.04)

---

### Post by fancypiper on 2009-12-14
Have you followed this guide?

[Comprehensive Multimedia & Video Howto](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by crisco552 on 2009-12-14
I have done everything it says and I still come up with the error. I really have no Idea what to do now I want to be able to record audio and video from my dazzle in a very usable format. Ogg/Vorbis doesn't seem to work mpeg-2 doesn't work, all the Mpeg4's don't work

---

### Post by hansdown on 2009-12-14
I did a search for 

```
It seems your FFMPEG (libavcodec) installation lacks the following encoder:
MPEG-4 Video
```.

It seems to be a bug/regression.

[http://www.google.ca/search?q=It+seems+your+FFMPEG+(libavcodec)+installation+lacks+the+following+encoder%3A+MPEG-4+Video&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=It+seems+your+FFMPEG+(libavcodec)+installation+lacks+the+following+encoder%3A+MPEG-4+Video&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

I've been having VLC throw errors in 9.10 64-bit install.

---

### Post by crisco552 on 2009-12-14
Oh wow, I installed the unstriped and It worked perfectly, Now only to fix my sound...

---

