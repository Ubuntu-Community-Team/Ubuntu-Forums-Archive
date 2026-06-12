---
title: "youtube streaming comment on an upload"
date: 2012-12-31
forum: Multimedia Software
---

### Post by sdowney717 on 2012-12-31
I am uploading this file that I encoded from DV video to h264 using flowblade.

Youtube says it is not optimized for streaming. Is there some setting I can set that will do that? I notice Handbrake has a web optimize check mark.
I did not see any thing obvious in flowblade for streaming. They do likely have a youtube profile for conversion.

youtube sends me to this link
[http://support.google.com/youtube/bin/answer.py?hl=en&answer=1297408&amp;hl=en-US](http://support.google.com/youtube/bin/answer.py?hl=en&answer=1297408&amp;hl=en-US)

---

### Post by andrew.46 on 2012-12-31
I am not familiar with flowblade but there may be elements of this page of the FFmpeg wiki that might prove useful:

How to Encode Videos for YouTube and other Video Sharing Sites
[https://ffmpeg.org/trac/ffmpeg/wiki/EncodeforYouTube](https://ffmpeg.org/trac/ffmpeg/wiki/EncodeforYouTube)

The heart of the message on this page seems to be:

> 
Since YouTube, Vimeo, and other similar sites will re-encode anything you give it the best practice is to provide the highest quality video that is practical for you to upload. Uploading the original content is the first recommendation, but this is not always a choice due to file size or bandwidth limitations, so re-encoding may be required.


So if FFmpeg is not your cup of tea I would hunt around in flowblade for the ability to export in high quality h.264 and then expect youtube to re-encode it anyway :)

---

### Post by sdowney717 on 2013-01-01
Thanks. I think so too.
Youtube likely gives out that message to help them a little on processing time for your video as they will redo the encoding to make it stream properly.

What I wonder is if you upload a massive 2.9gb file, does their encoding make the file a similar size compared to if you upload a 1.5gb file if they are the same time playing length? Or will the huge file you uploaded be a significantly different size? (assuming that both videos are the same 480p, just different bite rates). One of the vids I uploaded was 2.9gb in size and plays for an hour, and another was 1.5gb in size and plays for an hour. On my video manager page, the huge video I have no option to save as mp4, and the other one I do.

the one that is 2.9gb, also Youtube gave me a notice it contained copywrited music tracks. Part of it was filmed at a skating rink where they play music. My response was fair use. So on my management page, I have a notice saying content copy write dispute, but on the view play page there is no mention of anything. Not sure what that all means.

---

### Post by shantiq on 2013-01-01
hi sdowney


whatever you upload they will reduce in size but from personal experience usually proportionately [so 2.9 and 1.5 will produce different results]

if i upload to YT i will often download it again from the site and check the specs to see what they have done...   always lower than what i put up...    but and to their credit these days usually very decent quality [sound and image]

if you upload 720p or 1080p they also retain that...

---

### Post by FakeOutdoorsman on 2013-01-02
> **sdowney717 said:**
> What I wonder is if you upload a massive 2.9gb file, does their encoding make the file a similar size compared to if you upload a 1.5gb file if they are the same time playing length?

Both of those file sizes would be impractical (for me) to upload. File size should not be much of consideration other than your ability and/or patience to upload it (and if you care about YouTube having to archive it which I guess they do but I don't know). More important factors are the duration and the complexity of the input video. Something that is hard to encode is going to require a higher bitrate to achieve a certain quality than something that is fairly static, and *file size = bitrate * duration*.

I assume that if two more-or-less identical videos are encoded with two different encoders with similar quality but significantly different output file sizes, then the resulting videos on YouTube would probably end up a similar size...but I haven't tested this.

---

### Post by andrew.46 on 2013-01-02
> **sdowney717 said:**
>  So on my management page, I have a notice saying content copy write dispute, but on the view play page there is no mention of anything. Not sure what that all means.

Do you have a link for the curious? (=me!)

---

### Post by lisati on 2013-01-02
> **andrew.46 said:**
> Do you have a link for the curious? (=me!)

Some info on Youtube's position can be found here: [https://www.youtube.com/t/copyright_my_video](https://www.youtube.com/t/copyright_my_video)

---

### Post by sdowney717 on 2013-01-02
> **andrew.46 said:**
> Do you have a link for the curious? (=me!)

Ok, I sent you a message

---

### Post by andrew.46 on 2013-01-03
> **sdowney717 said:**
> Ok, I sent you a message

Hmmm.... the youtube guys are hypervigilant indeed, as you mentioned the music was simply playing in the background at a skate rink.

---

### Post by sdowney717 on 2013-01-03
Yes, I think that is just incidental fair use. The skating rink has to pay hundreds to the music companies to publicly play the music.
as a patron of the rink, I have to listen to what they already playing, I dont choose this.
Its sort of like you would go into a public place and hear music from some where.

---

