---
title: "Media.ts file size vs Media.mp4 file size"
date: 2020-04-04
forum: Multimedia Software
---

### Post by MoebusNet on 2020-04-04
Everything I've read leads me to believe that all things being equal, a video file saved using  .mp4 format would be smaller than the same video file saved in mpeg2.ts format. Or am I mistaken? in my case, I edited a mpeg2.ts video file using the OpenShot video editor, removing about 2 minutes worth of video & audio. I exported the edited file to .mp4 and the resulting file size *increased* by about 10%! I am puzzled. Any ideas what is going on?

---

### Post by TheFu on 2020-04-04
ts and mp4 are just containers.  ts is usually mpeg2 "transport stream", which is good for picking up mid-stream.

The video, audio codecs selected and settings for those are what control the size.  Changing video codecs is called "transcoding" and we want to avoid that since every transcode loses some quality and introduces artifacts.

Cut the mpeg2 files, leave them as mpeg2, then use handbrake to transcode to h.265/aac or h.264/aac.  The container can be mp4 or if you want more flexibility, then mkv is, by far, the most flexible container.

---

### Post by MoebusNet on 2020-04-05
Thanks for the reply. Mythtv forum was recommending mp4 for long-term storage due to file size, but you're right about transcoding - storage is relatively cheap. I'll export my edited mpeg-2 files as mpeg-2 and leave it at that.

---

### Post by TheFu on 2020-04-05
if we have a 1 hr HiDef TV recording mpeg2 that's 10G in size, removing commercials (use comskip) will make it about 7G for the remaining 42-44 minutes.
Transcode that to h.264 and it will be about 5G in size with ZERO artifacts.  i cannot tell the difference between the 5G file and the original.
However, if we transcode to h.265 instead, the file will be about 2.25G with ZERO artifacts.

h.265 is much harder to create and to decode at playback time, so if we have specific playback devices  like a Roku or raspberry-pi, then they probably cannot play h.265.

h.264 has been the standard video encoding used for almost every streaming service the last 10 yrs. it hasn't THAT hard on a CPU to make and lots of HW devices can create it in realtime.  Be aware that any encodings created in real-time will have file size as a secondary consideration.  Whenever i use a recording device that makes h.264 video in real-time, i'll always re-transcode it again to save the other 50% of the file size while still keeping h.264 encoding.  A computer doing the transcoding gives us muh more control over the setting that control size, ease of decoding at playback and quality.  We can also apply filters to rotate, crop, add or remove overlays, etc.

My equipment cannot handle h.265, but it all handles h.264 easily, including cheap phones and tablets.

No way would i leave any hidef content as mpeg2 unless it was to be watched once, then deleted.  The files are just too big.

Again, mp4 doesn't say anything about the video format.  it is just a container.  Take one of the edited files and run it through handbrake, see the results.  i think you will be impressed.  if you batch process files, it takes next to no effort or time to save 50%.

---

