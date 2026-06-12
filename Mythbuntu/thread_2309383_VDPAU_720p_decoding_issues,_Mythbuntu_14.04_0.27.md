---
title: "VDPAU 720p decoding issues, Mythbuntu 14.04 0.27"
date: 2016-01-10
forum: Mythbuntu
---

### Post by wpcprez on 2016-01-10
Hello All,
I have a really strange issue I've never seen before. Some background, I have a one backend/frontend connected to a ceton + cable card and a second frontend just for playback. 

Just recently both machines stopped being able to play 720p without stuttering. Both are on nvidia cards that can easily handle the high profile of VDPAU. One of the machines is a GTX 950 SC so that should definitely have the horsepower to decode. Especially since there's no deinterlacing involved. 

I've tried a few things like benchmarking the disk that holds the videos to make sure it can play properly and playing the video files to a windows machine which plays them fine. I also tried changing nvidia drivers all the way up to the newest beta and still no dice. I really am not sure what else to try here. I've never had this type of issue since vdpau ever existed. 

Any help would be appreciated. Thanks

---

### Post by wpcprez on 2016-01-11
figured it out.

Seems like some sort of bug with vdpau and adjusting audio sync? I had to adjust audio sync for one video we were watching and I didn't realize it was a global setting. Once the -300ms setting was changed back to 0ms the stuttering disappeared. It's just strange that other 1080i content did not have this issue and only the 720p that was recorded from cable card has this issue.

---

