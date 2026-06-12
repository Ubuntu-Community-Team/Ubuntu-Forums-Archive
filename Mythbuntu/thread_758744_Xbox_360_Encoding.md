---
title: "Xbox 360 Encoding"
date: 2008-04-18
forum: Mythbuntu
---

### Post by SniperKIng on 2008-04-18
Hi guys

I have been searching for a way to convert shows recorded on my mythbox to a format that will play on my xbox 360.

I read about nuvexport but have yet to see any success written in a forum. So i was just wondering if anyone else does this and could share there method.  Any help will be greatly appreciated.

---

### Post by aashay on 2008-04-18
This was written before 360s started supporting divx:
[http://ubuntuforums.org/showthread.php?t=559370](http://ubuntuforums.org/showthread.php?t=559370)
You could also try to encode with the xvid codecs. I'm not sure what myth uses to encode the video files, so can't be more specific

---

### Post by SniperKIng on 2008-04-18
Thanks for the reply ill take a look at that.

I didnt realise about the xbox supporting mp4 till about an hour ago but i tried the simple mp4 transcode by myth and the xbox can see it when i put it on my memory stick but cannot play it, providing me with an error.

ps any idea on transcoding times for your method.

Thanks again.

---

### Post by tgm4883 on 2008-04-18
> **SniperKIng said:**
> Thanks for the reply ill take a look at that.

I didnt realise about the xbox supporting mp4 till about an hour ago but i tried the simple mp4 transcode by myth and the xbox can see it when i put it on my memory stick but cannot play it, providing me with an error.

ps any idea on transcoding times for your method.

Thanks again.

You can use mythexport to do that

---

### Post by aashay on 2008-04-19
I've h seen a thread teaching you to transcode vids on the fly from ubuntu (upnp) for your 360. I've used TVersity to do that on windows before. Never got around to making it work on ubuntu. Search around in theTips/Howto section. As for avidemux, transcoding is pretty so-so. About 30-50% of the actual playtime

---

### Post by bigpapapump on 2011-01-15
I am looking at mythexport to transcode the mythtv recordings for playback on the xbox360.  However, my mythtv backend is running an atom processor (a very low-power backend) and cannot transcode the videos on the fly.

Mythexport seems to require set aspect ratio and video dimensions as its parameters.  I do not want to change the recording's aspect ration or dimensions.  I simply want to transcode it into a format that the xbox 360 can play natively, and that the backend can simply stream without having to transcode anything.

Is there anyway to do this?  I'm sure there is since other projects like the ps3 media server do this on the fly.  I just want to do this ahead of time (i.e. in the middle of the night, when I don't care if the cpu is pegged on the backend).

Anyone know the command line to use to just do the codec and not mess with the aspect ratio and such?

Thanks

---

