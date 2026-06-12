---
title: "Advice On Re-encoding Animated DVD"
date: 2011-08-08
forum: Multimedia Software
---

### Post by dodle on 2011-08-08
I'm copying an animated TV series from DVD to my computer. The DVDs are encoded at 29.970fps, which I find strange because animation usually uses 23.976fps. Anyway, what I have done is de-interlaced and re-encoded it to H.264. Now it is set to 59.970fps, which I think is higher than what I want. I'm seeking advice on whether I should leave it at that or change it to one of the lower frame rates.

**----- EDIT -----**
Another question: Do you think that I should be encoding to H.263 instead? This is just to have copies of the videos on my hard drive.

**Note:** I used Avidemux with the Yadif filter using the bob method to de-interlace the film. I think the bob method preserves the actual 60 fields and converts them into complete frames. I'm guessing that the temporal spatial check would halve the frames and give me the 29.970fps.

---

### Post by dodle on 2011-08-08
D'OH!! >.< I totally overlooked Avidemux's Resample FPS video filter. Problem solved.

---

### Post by BicyclerBoy on 2011-08-09
Just my ravings..
H264 is much better than H263 DivX XVid .

H264 supports interlaced video.
Any good video card can easily de-interlace properly i.e. nVidia GT 220 or better
And de-interlace better than your bob de-interlacing.

De-interlacing moves the computation to the encode stage & makes the files bigger for the same effective temporal resolution.
But most people don't seem to know how to turn the yadifx2 filter on in (VLC).

---

### Post by dodle on 2011-08-11
I just hate dealing with interlaced video. I don't really know a lot about the benefits of either. I know that film is originally captured at 24p and many of the videos found online are in a progressive format. And I know that my life is easier when I try to encode from a progressive format. 

I agree with you, the h264 format is awesome. I'm amazed at how well it compresses. Though, I like the idea of Theora. I hope the guys over at Xiph keep working hard and make it a competitor for h264. 

I changed the deinterlace method. These DVDs were encoded terribly and once in a while interlace artifacts flash on the screen. The bob method didn't fix this so I tried the spatial checks and it cleared it up. I think I might just leave it at 60p fps. Encoded in h264 the files are still extremely small and when I try to resample FPS the picture becomes more jerky.

---

### Post by BicyclerBoy on 2011-08-11
Well the idea of continuing with making movies with 24p just because it is some analogue of the past (film) is just stupid.

Old films were made at 24p because that was the mechanical limits etc
The playback involved flashing each frame twice to reduce the perception of flicker.
This is the cinema effect..

Digital cameras do not have to run at 24p.
All broadcast material (TV DVD) is all interlaced 50 or 60Hz.

All modern TVs with 24p input modes are now frame interpolating (frame creating) to improve the temporal resolution.

So 24p has just traded temporal resolution for spatial.
So you now need to run a post decode "de-interlacing" filter to generate new intra-frames.

---

