---
title: "Can anyone play this .mov media file?"
date: 2007-05-09
forum: Multimedia &amp; Video
---

### Post by acturneruk on 2007-05-09
I can play .mov files at [http://www.apple.com/trailers](http://www.apple.com/trailers) (e.g. [http://images.apple.com/movies/fox/fantastic_4-silver_surfer/fantastic4silversurfer-tlrj_h.480.mov)](http://images.apple.com/movies/fox/fantastic_4-silver_surfer/fantastic4silversurfer-tlrj_h.480.mov)), but this file just won't play:-

[http://wilcoworld.net/roadcase/webcast/sydney2007/wilco_webcast_apr_2007.mov](http://wilcoworld.net/roadcase/webcast/sydney2007/wilco_webcast_apr_2007.mov)

Can anyone get it to play, and if so, what is your set up?

Cheers

---

### Post by dfreer on 2007-05-09
couldn't get it to play on i386 with mplayer/vlc/totem. probably just has a weird encoding.

---

### Post by stchman on 2007-05-09
> **acturneruk said:**
> I can play .mov files at [http://www.apple.com/trailers](http://www.apple.com/trailers) (e.g. [http://images.apple.com/movies/fox/fantastic_4-silver_surfer/fantastic4silversurfer-tlrj_h.480.mov)](http://images.apple.com/movies/fox/fantastic_4-silver_surfer/fantastic4silversurfer-tlrj_h.480.mov)), but this file just won't play:-

[http://wilcoworld.net/roadcase/webcast/sydney2007/wilco_webcast_apr_2007.mov](http://wilcoworld.net/roadcase/webcast/sydney2007/wilco_webcast_apr_2007.mov)

Can anyone get it to play, and if so, what is your set up?

Cheers

I have not been able to reliably play Quicktime files on Ubuntu.  I installed the w32codec file and still the same.  I am glad that I come across them rarely.

---

### Post by acturneruk on 2007-05-09
I have tried totem-gstreamer, totem-xine and mplayer, all with no success. I have win32codecs installed, along with every other plugin I've come across.

---

### Post by acturneruk on 2007-05-09
I have emailed the owners of the website in the hope that the videos may be made available in a more friendly format. If you are also a fan of Wilco, I would recommend you do the same.

Cheers for your replies.

---

### Post by jdunn on 2007-05-09
It worked well when I used it on previous versions of Ubuntu in the past.  I'm having no luck on Feisty.  I noticed that a new version of the Windows Quicktime player came out recently and I believe the codecs need to be updated in the w32codecs package for Ubuntu.

---

### Post by mikewitt on 2007-05-09
> **acturneruk said:**
> I can play .mov files at [http://www.apple.com/trailers](http://www.apple.com/trailers) (e.g. [http://images.apple.com/movies/fox/fantastic_4-silver_surfer/fantastic4silversurfer-tlrj_h.480.mov)](http://images.apple.com/movies/fox/fantastic_4-silver_surfer/fantastic4silversurfer-tlrj_h.480.mov)), but this file just won't play:-

[http://wilcoworld.net/roadcase/webcast/sydney2007/wilco_webcast_apr_2007.mov](http://wilcoworld.net/roadcase/webcast/sydney2007/wilco_webcast_apr_2007.mov)

Can anyone get it to play, and if so, what is your set up?

Cheers

It plays just fine on my system.

I think it's because I have the AUD-codecs installed from automatix (I know, some people don't like it, but it hasn't failed me yet). But yeah, it works just fine under mplayer.

---

### Post by acturneruk on 2007-05-10
Whist I won't touch Automatix, it's good to know that it is possible to get it to play. It would still be nice to see the media made available in a more easily accessible cross-platform format.

---

### Post by acturneruk on 2007-05-10
> **jdunn said:**
> It worked well when I used it on previous versions of Ubuntu in the past.  I'm having no luck on Feisty.  I noticed that a new version of the Windows Quicktime player came out recently and I believe the codecs need to be updated in the w32codecs package for Ubuntu.

Do you mean that the Wilco media worked for you on previous versions of Ubuntu, or .mov files worked for you in the past? On Edgy, I had totem-xine which worked well with .mov normally, but on Feisty I had to switch to totem-gstreamer to get them to play. I've never been able to play the Wilco ones, however.

---

### Post by DarkN00b on 2007-05-10
I had to remove the ) from the end of the link, but it played for me. Looks awesome. :)

---

### Post by acturneruk on 2007-05-10
> **DarkN00b said:**
> I had to remove the ) from the end of the link, but it played for me. Looks awesome. :)

I can play the Silver Surfer trailer (sorry about the wayward bracket), it is the second file I cannot play:-

[http://wilcoworld.net/roadcase/webcast/sydney2007/wilco_webcast_apr_2007.mov](http://wilcoworld.net/roadcase/webcast/sydney2007/wilco_webcast_apr_2007.mov)

Can you play this one?

But yes, the Silver Surfer movie does look awesome ;)

---

### Post by DarkN00b on 2007-05-10
> **acturneruk said:**
> I can play the Silver Surfer trailer (sorry about the wayward bracket), it is the second file I cannot play:-

[http://wilcoworld.net/roadcase/webcast/sydney2007/wilco_webcast_apr_2007.mov](http://wilcoworld.net/roadcase/webcast/sydney2007/wilco_webcast_apr_2007.mov)

Can you play this one?

But yes, the Silver Surfer movie does look awesome ;)

Nope, can't play that one. It buffers for a couple of seconds and then stops. 

It does buffer to 100% though, it just plays nothing for a fraction of a second and the stops.

EDIT: I downloaded it using wget and there is something there. I played it with VLC and saw some text; I'll try to open it in Kino and see what I can see. This appears to be a problem with the file though and not your codecs.

EDIT 2: The file is 33 microseconds long and contains one frame, attached below. Prepare to be disappointed. There wasn't even any text. :(

---

### Post by acturneruk on 2007-05-10
Yep, I tried the wget method too, with the same results. But I'm guessing the little file you get is some sort of defence mechanism against being able to download the whole thing (which, according to the website, is over an hour long) - i.e. it will only let you watch it as streaming video.

Can anyone confirm this?

---

### Post by acturneruk on 2007-05-11
Okay, I just tried it on a Windows machine at work (it plays fine). It appears to be an audio webcast with a custom interface (see attached picture).

So there is something more there than the tiny file we downloaded with wget...

---

