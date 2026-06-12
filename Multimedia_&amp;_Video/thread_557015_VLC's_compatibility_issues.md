---
title: "VLC's compatibility issues"
date: 2007-09-22
forum: Multimedia &amp; Video
---

### Post by Venerence on 2007-09-22
my main problem is that VLC doesn't seem to want to use the correct codec for some movies. I've mainly had this problem with blizzard's .MPQ (divx video) files, which they use for trailers and cutscenes (I play warcraft III a lot for the curious). However, this same video works in movie player relatively well.

I've been spending the last couple of hours transitioning from ubuntu's default movie player into VLC's media player, for two reasons:

[LIST]
[*]the default movie player, while highly compatible, does not buffer at all, which makes scrolling through videos to occasionally desync audio and video, and just sounds horrible while scrolling
[*]Movie player occasionally has an issue where the screen is washed out and red colors show up as blue -- it's driving me crazy, because it's hard to notice when it happens but ruins the overall quality of the video.[/list]

I do have the correct codecs installed, since the files in question work (somewhat) fine in media player, and I have optional codecs installed through easybuntu

Here's the codecs that movie player uses (according to properties), which works correctly:
> Video: Blizzard DivX
Audio: MPEG-1 layer 3


In VLC, I only get the audio and no video, and the properties info shows this:
> Video: BLZ0 (which is wrong I'm assuming)
Audio: mpga (which works correctly)

The statistics for VLC show that it does not successfully decode any video frames.

My first guess would be that VLC doesn't know where to look for codecs -- in which case, someone with knowledge of how to link VLC to easybuntu's codecs would be helpful, because I have no idea how to do that.

My second guess is that VLC is incorrectly associating the correct codec, which is also an issue because I have no idea how to manually associate the correct codecs with certain files.

In any case, any help with getting VLC to correctly recognize the codecs would be wonderful. As a side note, if anybody knows what's going on with the red-blue bug for movie player, that is bugging the heck out of me (I haven't pinned down the cause yet, for all I know it could be a quirk with the monitor).



EDIT: after a bit more looking, the red-blue issue seems to be a problem only when running ubuntu in the session that doesn't use XGL. This is still an issue because I can't use wine with XGL, which brings me back to square one.

Also, I have uploaded a side-by-side comparison of what the red-blue issue looks like for those who are interested:
[http://img.photobucket.com/albums/v321/taelrie/Screenshot.jpg](http://img.photobucket.com/albums/v321/taelrie/Screenshot.jpg) - what it should look like
[http://img.photobucket.com/albums/v321/taelrie/Screenshot2.jpg](http://img.photobucket.com/albums/v321/taelrie/Screenshot2.jpg) - running video (with the codec info on the side)

Of course, that still doesn't help me to get VLC's codecs working correctly unfortunately.

---

