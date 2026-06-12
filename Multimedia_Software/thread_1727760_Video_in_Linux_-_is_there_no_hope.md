---
title: "Video in Linux - is there no hope?"
date: 2011-04-12
forum: Multimedia Software
---

### Post by kelt65 on 2011-04-12
I am simply trying to make short educational clips from DVD's in linux to upload to youtube. This is evidently impossible. I can't even seem to rip a movie these days. DVD:rip crashes if you so much as look at it, OGMrip garbles the audio, is there anything else worth looking at? Something that can deal with subtitles and burn them onto the video? (normally not something I'd want, but there's no other option with youtube). The last few ventures with DVD:rip, a program I've used for about 10 years, indicates the packagers are simply not paying attention. It fails consistently because it is trying to pass options to transcode that it (transcode) doesn't understand.

---

### Post by Chronon on 2011-04-12
> **kelt65 said:**
> I am simply trying to make short educational clips from DVD's in linux to upload to youtube. This is evidently impossible. I can't even seem to rip a movie these days. DVD:rip crashes if you so much as look at it, OGMrip garbles the audio, is there anything else worth looking at? Something that can deal with subtitles and burn them onto the video? (normally not something I'd want, but there's no other option with youtube). The last few ventures with DVD:rip, a program I've used for about 10 years, indicates the packagers are simply not paying attention. It fails consistently because it is trying to pass options to transcode that it (transcode) doesn't understand.

Is there a bug report for this?

---

### Post by K_45 on 2011-04-12
You could try WIne and DVD Shrink:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2230](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2230)

then transcode the .vob's to the settings you want.

---

### Post by inobe on 2011-04-12
[https://help.ubuntu.com/community/RestrictedFormats/RippingDVDs](https://help.ubuntu.com/community/RestrictedFormats/RippingDVDs)

---

### Post by bryanl on 2011-04-13
Several parameters I see here. One is getting videos off a DVD. Second is editing that video. Third is saving the edited video in a desired format.

For longer videos, such as DVD movies, I use avidemux. Point it at the first big file in the DVD's VIDEO_TS directory and it'll put together the whole title. Then you can edit it, select the output container and encoding you desire and save the result. 

I often just use avidemux to edit but not transcode. I normally use Handbrake to transcode the mp2 into mp4 using one of Handbrake's presets.

For YouTube sized clips OpenShot seems to be convenient. I have started playing around with it for video clips from my camera and for some youtube video concatenation efforts. It's a bit slow importing large files compared to avidemux (as are most of the video editors I have tried) but does seem to work.

---

### Post by alphacrucis2 on 2011-04-13
> **kelt65 said:**
> I am simply trying to make short educational clips from DVD's in linux to upload to youtube. This is evidently impossible. I can't even seem to rip a movie these days. DVD:rip crashes if you so much as look at it, OGMrip garbles the audio, is there anything else worth looking at? Something that can deal with subtitles and burn them onto the video? (normally not something I'd want, but there's no other option with youtube). The last few ventures with DVD:rip, a program I've used for about 10 years, indicates the packagers are simply not paying attention. It fails consistently because it is trying to pass options to transcode that it (transcode) doesn't understand.

You could try Avidemux to rip the DVD reencoded to your video and audio codecs of choice.

---

### Post by dnguyen1963 on 2011-04-13
I use K9copy to rip the movie then Kino to edit and save a portion of the movie.  BTW, K9copy works well from ArtistX distro.  In Ubuntu, K9copy crashes too often.

---

### Post by SeijiSensei on 2011-04-13
Try **Handbrake**.  It will rip DVDs to mp4 or mkv and allow you to choose audio and subtitle tracks.  [John Stebbins's ppa]("https://launchpad.net/~stebbins/+ppa-packages") has both current releases and daily builds.

If you just want to pull clips, you might find it easier to use [**mencoder**]("http://www.mplayerhq.hu/DOCS/HTML/en/encoding-guide.html") with its "-ss hh:mm:ss" and "-endpos ss" options to define a starting point and duration within a video.

---

### Post by kelt65 on 2011-04-18
> **kelt65 said:**
> I am simply trying to make short educational clips from DVD's in linux to upload to youtube. This is evidently impossible. I can't even seem to rip a movie these days. DVD:rip crashes if you so much as look at it, OGMrip garbles the audio, is there anything else worth looking at? Something that can deal with subtitles and burn them onto the video? (normally not something I'd want, but there's no other option with youtube). The last few ventures with DVD:rip, a program I've used for about 10 years, indicates the packagers are simply not paying attention. It fails consistently because it is trying to pass options to transcode that it (transcode) doesn't understand.

I've gotten dvd:rip to work as it used to, not sure why it was passing options to transcode that transcode could not understand. Seems to have been fixed by an update; still, that's messed up.

Thanks everyone for the useful responses. I do use avidemux and openshot for various things. I find Openshot would be wonderful if it just didn't choke up and crash so often when you have multiple layers in a huge video.

---

