---
title: "Can't Transfer Video to My Creative Zen Portable Media Player"
date: 2009-03-31
forum: Multimedia Software
---

### Post by brian_hayward on 2009-03-31
Here's the deal ladies and gentlemen, i have one last hurdle to overcome before i can totally rid myself of the huge headache that is windows and that is transferring video podcasts to my Creative Zen player.  I know how to transfer the shows to my player (Gnomad2), but they won't play.  I did a little research and i found ffmpeg which people use to manipulate video.  I've copied some examples, and ran the program a few times but i can't seem to get the parameters right to make the video playable on my Zen.  If anybody uses the Creative Zen and you watch video podcasts on it i would very much appreciate it if you could share with me how you get the video to a point that it will play on the Zen.  Thank you.  

Just to make sure we are all talking about the same device here is a pic of what i have:  

[IMG]http://images.americas.creative.com/images/products/large/17623.png[/IMG]

---

### Post by andrew.46 on 2009-03-31
Hi Brian,

I had a similar battle to get video encoded for a much less capable device: an iRiver x20. But the battle is won if you can find out exactly what video and sound your device can support, one way is to download one of the 'sample' videos usually included with such a device and examine it with FFmpeg:

```
ffmpeg -i sample_file.avi
```

and simply duplicate these settings. Good news though is that I documented my own battle with the x20 in a typically pedantic way:

Encoding Video for the iRiver X20
[http://www.andrews-corner.org/iRiverX20.html](http://www.andrews-corner.org/iRiverX20.html)

And you may be able to glean some information from this. Your device should be capable of playing back much more sophisticated encodings but I suspect that the encoding method I describe on this page (2 pass mpeg4 video + mp3 sound + avi container) will work well enough on your device as the settings are pretty generic.

The key is to find what your device supports.

All the best,

Andrew

---

