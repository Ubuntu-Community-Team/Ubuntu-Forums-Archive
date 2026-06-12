---
title: "Cutting and/or transcoding H.264 HD recordings"
date: 2010-05-14
forum: Mythbuntu
---

### Post by Jay2k1 on 2010-05-14
Hello Community,

I recently upgraded from a DVB-T card to a DVB-C card. I did this mainly to have better image quality and Dolby Digital 5.1 AC3 sound, but now I also receive some HD channels. These are broadcasted in H.264, not MPEG2.

Now when I record a movie which I want to keep, I want to get rid of unnecessary stuff, so I fine-tune the commercial flags and add markers for pre- and post-roll (I often set them to 5 and 20 minutes respectively). Then I add a lossless transcode job so it would cut out stuff using the cutlist.
Now with recordings from HD channels, this won't work, because mythtranscode fails at H.264. I'd like to know if there is any other way to accomplish this, because especially with HD, the overhead eats up quite some space. I want to avoid having to copy the recording to another computer and use a GUI video editing software, doing it all manually. It would be nice to have a user job in mythTV that would honor the cutlist.

As I am pretty sure that I am not the only one in this situation, I wanted to ask how you guys manage to do this. What options do I have here?

Thank you in advance,

Jay

---

### Post by goffa72 on 2010-05-14
Hi Jay,

have you tried the script at [http://web.aanet.com.au/~auric/?q=node/6](http://web.aanet.com.au/~auric/?q=node/6), it has recently been revised. [Current Version: 1.60]("http://web.aanet.com.au/%7Eauric/files2/V1.60/mythnuv2mkv.sh") Fixes for latest x264. If this does not work you could try posting in the comments for advice. The script can be ran as a user job.

Hope this helps

---

### Post by Jay2k1 on 2010-05-14
> **goffa72 said:**
> Hi Jay,

have you tried the script at [http://web.aanet.com.au/~auric/?q=node/6](http://web.aanet.com.au/~auric/?q=node/6), it has recently been revised. [Current Version: 1.60]("http://web.aanet.com.au/%7Eauric/files2/V1.60/mythnuv2mkv.sh") Fixes for latest x264. If this does not work you could try posting in the comments for advice. The script can be ran as a user job.

Hope this helps

It seems this script would always transcode, not just cut (which would be lossless). 
The perfect solution would be just cutting out stuff by using the cutlist though. Maybe I found something useful [here]("http://www.mythtv.org/wiki/User:Iamlindoro"), gonna try that out and let you guys know if it worked.

---

