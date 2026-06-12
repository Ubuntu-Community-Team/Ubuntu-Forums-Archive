---
title: "text editor on video"
date: 2014-08-13
forum: Multimedia Software
---

### Post by satimis on 2014-08-13
Hi all,


OS - Ubuntu 12.04 desktop

I'm a beginner in video editing.  I'm prepared adding text on the video of .mpg format taken with Sony Digital Camera.  I have no problem to convert them to other formats such as mp4 wkd etc.

gnome-subtitle is available for install.  I'm now looking for its tutorial and found;

Video subtitling for the GNOME desktopVideo subtitling for the GNOME desktop
[http://gnome-subtitles.sourceforge.net/gnome-subtitles-release-1.2](http://gnome-subtitles.sourceforge.net/gnome-subtitles-release-1.2)

GNOME Subtitles
[http://en.flossmanuals.net/video-subtitling/ch022_gnome-subtitles/](http://en.flossmanuals.net/video-subtitling/ch022_gnome-subtitles/)

Which of them will be suitable for me to follow.  Is there any other suggestion?  Thanks

Regards
satimis

---

### Post by TheFu on 2014-08-13
Do you want closed captions, subtitles or text embedded into the video that cannot easily be removed/added later?
Also - do you need to control where the text is placed always?

---

### Post by satimis on 2014-08-13
> **TheFu said:**
> Do you want closed captions, subtitles or text embedded into the video that cannot easily be removed/added later?
Also - do you need to control where the text is placed always?
Hi,

I expect having the subtitles embedded on the video permanently.

Is there any way creating a running banner with text scrolling, similar to news broadcasting?  I have searched a while on Internet but couldn't discover a link.

Thanks

satimis

---

### Post by TheFu on 2014-08-13
My google-fu is strong:
[http://askubuntu.com/questions/179109/what-tools-can-i-use-to-a-text-overlay-to-a-video](http://askubuntu.com/questions/179109/what-tools-can-i-use-to-a-text-overlay-to-a-video)
[http://askubuntu.com/questions/97975/insert-subtitles-permanently-and-convert-video](http://askubuntu.com/questions/97975/insert-subtitles-permanently-and-convert-video)
[http://tuxtweaks.com/2011/01/adding-video-captions-with-avidemux/](http://tuxtweaks.com/2011/01/adding-video-captions-with-avidemux/)
[https://www.youtube.com/watch?v=mhVopNOMl-M](https://www.youtube.com/watch?v=mhVopNOMl-M)
[http://www.makeuseof.com/tag/openshot-finally-excellent-video-editor-linux/](http://www.makeuseof.com/tag/openshot-finally-excellent-video-editor-linux/)

Tools in those links: kendlive, openshot, avidemux, mencoder.

As someone who uses srt and subs a-bunch, I would beg you NOT to force these into the video itself. Let your uses decide if they want subs or captions with their playback device instead.  Merging these into the MP4 or MKV video files is really easy.  Use handbrake or mkvmerge for that. You can force the default to be on - if you must - the users can turn it off.  OTOH, your requirements might not allow that.

---

### Post by satimis on 2014-08-13
> **TheFu said:**
> My google-fu is strong:
[http://askubuntu.com/questions/179109/what-tools-can-i-use-to-a-text-overlay-to-a-video](http://askubuntu.com/questions/179109/what-tools-can-i-use-to-a-text-overlay-to-a-video)
[http://askubuntu.com/questions/97975/insert-subtitles-permanently-and-convert-video](http://askubuntu.com/questions/97975/insert-subtitles-permanently-and-convert-video)
[http://tuxtweaks.com/2011/01/adding-video-captions-with-avidemux/](http://tuxtweaks.com/2011/01/adding-video-captions-with-avidemux/)
[https://www.youtube.com/watch?v=mhVopNOMl-M](https://www.youtube.com/watch?v=mhVopNOMl-M)
[http://www.makeuseof.com/tag/openshot-finally-excellent-video-editor-linux/](http://www.makeuseof.com/tag/openshot-finally-excellent-video-editor-linux/)

Tools in those links: kendlive, openshot, avidemux, mencoder.

As someone who uses srt and subs a-bunch, I would beg you NOT to force these into the video itself. Let your uses decide if they want subs or captions with their playback device instead.  Merging these into the MP4 or MKV video files is really easy.  Use handbrake or mkvmerge for that. You can force the default to be on - if you must - the users can turn it off.  OTOH, your requirements might not allow that.
Hi,

Lot of thanks for your assistance.

What I expect to find is the tutorial using Gnome Subtitles creating a .srt file, the technique making specific effect on text.  But I couldn't find its tutorial on Internet.

How to use mencoder to add subtitle to your video
[http://www.linuxandlife.com/2012/11/use-mencoder-add-subtitles-to-videos.html](http://www.linuxandlife.com/2012/11/use-mencoder-add-subtitles-to-videos.html)
provides me info adding a .srt file on the video

How To Create Subtitles In Openshot 1.3
[https://www.youtube.com/watch?v=mhVopNOMl-M](https://www.youtube.com/watch?v=mhVopNOMl-M)
is an interesting video.  Thanks

My serious problem is the video size.(the video are owned by me).  As you know most video files are big size.  I can upload it to the server of the hosting company subscribed by me.  But it takes prolong time loading the page (file-128MB).  I'm now trying to find a solution without uploading the videos files to Youtube, vimeo, flickr etc., if possible.

I'm running WordPress.  .mkv file having smaller size but I can't find a player on WordPress to play it.  I'm stucked here.

Anyway lot of thanks for your help.

Regards
satimis

---

### Post by TheFu on 2014-08-14
Use mp4 containers with h.264 video encoding and AAC audio encoding.  MP4 containers accept SRT files as captions too.
I think the only things you can control with SRT files, is the start/end of each line of text and the color, but I've never created one myself.  You can use HTML5 "video" tags to stream those.  I don't know/think mkv containers are universally supported for web streaming.

I did come across a tool a few weeks ago that helps create SRTs on Linux, sorry, I don't recall the name and the machine I installed it onto isn't powered on - can't remote in to look.

---

