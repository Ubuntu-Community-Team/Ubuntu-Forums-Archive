---
title: "H.264"
date: 2007-11-30
forum: Multimedia &amp; Video
---

### Post by mrscript on 2007-11-30
[FONT="Arial"][SIZE="4"]I've spent days on google without any result.
The situation is that I can't play H.264 encoded videos, that includes DVB-T television in my region (it encoded with h.264, and not mpeg-2).
You could find some sample H.264 movies [/SIZE][/FONT][here]("http://www.leadcodecs.com/Download/H264-Videos.htm"). 
[FONT="Arial"][SIZE="4"]I've installed latest SVN mplayer and ffmpeg, and many others codecs, but no result - I o nly get sound and no video.
VLC result when trying play movie with h.264:[/SIZE][/FONT]
[PHP]VLC media player 0.8.6c Janus
[00000304] main decoder error: no suitable decoder module for fourcc `L264'.
VLC probably does not support this sound or video format.
[00000281] main playlist: stopping playback[/PHP].

[FONT="Arial"][SIZE="4"]Xine result when trying play:[/SIZE][/FONT]
[IMG]http://www.talpink.lt/images/images/99596Untitled-1.png[/IMG]

[FONT="Arial"][SIZE="4"]Any suggestions?[/SIZE][/FONT]

---

### Post by shirilover on 2007-11-30
It would appear that they are using an unknown codec format as seen by the following output from mplayer:
```

Cannot find codec matching selected -vo and video format 0x3436324C.

```

Also putting H.264 video into an avi container is not recommended. I could not get the video portion to play at all. Therefore, I believe that there is something wrong with the files.

I have played several H.264 files without problem even 1024x576 on my old Athlon, so I don't believe that playback is the problem, I believe Lead Tools has decided to use their own fourcc (L264, LX64) and force people to use/buy their decoders. The streaming videos even say to use IE so that they can install their codecs.

---

### Post by ron999 on 2007-11-30
I agree with you shirilover.
I've viewed H264 encoded vids with VLC etc, but the ones in the above link won't play for me (sound but no video).

---

### Post by sloggerkhan on 2007-11-30
I also have played H.264 vids back without problem frequently and get an issue with those vids. (Audio only.) I don't think they use a normal H.264 encode.

---

### Post by eye208 on 2007-11-30
I changed the AVI's FourCC tag to H264 and then AVC1 (using the cfourcc tool). In both cases I'm getting video, but it's severely broken. This is definitely not a standards-compliant H.264 video stream. It looks like another attempt to push a proprietary format onto consumers. I wonder if it's even legal to call these videos H.264 since H.264 is a registered ISO standard and maybe a trademark of the MPEG group too.

---

### Post by mrscript on 2007-12-01
[FONT="Arial"][SIZE="3"]Thankz. I discovered that there avi's are realy broken or something wrong with them, i've downloaded some H.64 movies from other sources and they played well.

BUT. I still have the main me problem - I can't watch DVB-T H.264 TV.

It founds channels, fouds codecs, but no video - only sound - [**_Kaffeine here_**]("http://talpink.lt/images/v.php?id=10197DVB.png").

I can watch TV only if i start "Instant Record" and open that Instant Record File with[**_ VLC_**]("http://limpo.lt/mrscript/wp-content/lnk.png").[/SIZE][/FONT]

---

### Post by mrscript on 2007-12-02
SOLVED.
Compiled ffmpeg, then lib-xine 1.1.8 with external ffmpeg and then compiled caffeine from svn.

---

