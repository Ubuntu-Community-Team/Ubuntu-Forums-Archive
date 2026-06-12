---
title: "Rhythmbox and Opus: kbps when ripping from CD"
date: 2019-05-06
forum: Multimedia Software
---

### Post by theprisoner2 on 2019-05-06
Just a general query about this. When ripping a CD with Rhythmbox, to Opus format, it gives the option on the slider of going to 600 kbps. The official Opus documentation states that the maximum quality is 510 kbps. Is this a bug in Rhythmbox, and what happens if the slider is set at 600? Does it just rip at 510?

Thanks.

---

### Post by Yellow Pasque on 2019-05-07
> The official Opus documentation states that the maximum quality is 510 kbps.

The reference 'opusenc' seems to be limited to that. The gstreamer opus encoder goes up to 650k, and it really will produce a 650k constant bitrate (CBR) file if you tell it to. I find it very strange that the gstreamer opus encoder defaults to CBR output.
I'm guessing Rhythmbox uses the gstreamer opus encoder, inherits its CBR default, and will output 600k CBR if the slider is set there. 

> what happens if the slider is set at 600?

Give it a try and run mediainfo on the resultant file. You will get your answer faster than us non-Rbox users can tell you ;)

I'm hoping this is a theoretical question and you're not trying to rip stereo tracks to such a large bitrate (use FLAC instead to preserve CD quality if you don't mind larger files).
[https://wiki.xiph.org/Opus_Recommended_Settings](https://wiki.xiph.org/Opus_Recommended_Settings)

---

### Post by theprisoner2 on 2019-05-07
Thanks for the reply. I tried mediainfo and it gives 517 kbps off a setting of 512 variable in Rhythmbox, so I guess it's doing what is says. The discrepancy is odd, but never mind!

---

