---
title: "Problems encoding HD video to get smooth playback in Cinelerra with an effect added"
date: 2012-05-20
forum: Multimedia Software
---

### Post by streamsanddragonflies on 2012-05-20
Hi!  I was advised to encode my 1080p60fps HD video files with ffmpeg to the DNxHD proxy with 220M bitrate (.mov wrapper) rather then 45M so the image doesnt have too much artifacts. I reduced the framerate to 29.97 fps when I encoded the clips and the project is also 29.97 fps at 1920X1080p. 

My clips play smooth in the Compositor Window but the minute I apply an effect to my video track, playback becomes choppy and I need to evaluate the clip with effects and see the motion in real-time. My computer is 4 core AMD 3.4 GHz with 12G memory. Ubuntu LTS 10.04.4 with desktop effects OFF. Decent Sata2 drives. 

I don't want to re-encode my original clips at this point, so instead I was stuck rendering parts of the project to mpeg4 since it seems faster so I can add a couple of more effects. But some other clips that didnt need anymore effects were rendered to RGBa uncompressed to preserve quality. Now I dont know what to encode my final project to!! Its a potential mess! Anyone has an idea how to proceed? 

Some things that could be slowing it down; PulseAudio has been known for issues, but I don't see it taking up ressources.  I am rendering and using clips on "fakeraid" 0 drives (the raid was set in bios and is done by the CPU) but my / and /home are not raid.  I will test this later, but I was hoping that raid 0 (wether Ubuntu software raid or fakeraid) could speed rendering up...

And for the future, what the heck should I be encoding to next time?? (for Cinelerra-CV). I'm having a hard time finding help in IRC etc, I hope there is a happy ending!

---

