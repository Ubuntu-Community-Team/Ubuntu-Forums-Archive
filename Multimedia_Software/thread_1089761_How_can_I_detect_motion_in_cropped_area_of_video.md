---
title: "How can I detect motion in cropped area of video?"
date: 2009-03-07
forum: Multimedia Software
---

### Post by lavinog on 2009-03-07
I am reviewing months worth of security videos. I know I am looking for activity in a specific area.
Is there a way to only show movement in that area?

I came across a utility called motion, but it seems that it is only good for live video streams.

I am suspecting that I could use mencoder to break apart images and just compare the current image with previous images.

---

### Post by lavinog on 2009-04-08
Let me rephrase my question:
Is there a utility that can extract/re-encode parts of a video that only have motion?

I suspect one way to do this would be to extract all of the frames of a video as images(jpeg) and compare the differences between consecutive frames.
I can use mencoder to extract the frames. What would be good for comparing them?

---

### Post by demccully on 2011-07-14
Any luck with this? I have a similar problem. Thanks.

---

### Post by lavinog on 2011-07-17
I implemented a crude (and slow) way of doing this.
It did what I needed at the time, and I don't think I have the code anymore.
I converted all frames to jpeg images, converted the images 2 tone images using convert. At this point I had an image that consisted of just 1s and 0s.  I zeroed out the areas that I didn't care about, then summed all the bits.  If the sum changed: the image was tagged.  After all of the images were processed, the tagged images were reencoded into a new video.

This was all done in bash and took a very long time to process.  I was able to utilize the multicore processor by exporting the images of the next video while the current video was being processed.
I have learned python since then, and have been wanting to revisit this project when I had more time.

---

### Post by Unterseeboot_234 on 2011-07-18
Look into OpenCV, a donated, computer vision library from Intel. Check youtube for working implementations. The O'Reilly book 'Learning OpenCV' is about the only hard copy information. Basically, you have done the same thing as the OpenCV library would do for you -- high contrast to get shapes using algorithms.

For cropping and things like that, I batch with ImageMagick. You have many choices for the scripting. I prefer the terseness of Perl. Seems to me I was accomplishing 600+ Nikon photos @ 14.5 megapixals converted to a new format and resolution in 25 minutes on single-core AMD64, and about 4 minutes on a hexacore AMD64.

---

