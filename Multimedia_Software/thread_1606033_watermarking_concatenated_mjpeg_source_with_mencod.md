---
title: "watermarking concatenated mjpeg source with mencoder"
date: 2010-10-26
forum: Multimedia Software
---

### Post by x2305andy2305x on 2010-10-26
Hi,

I've created an mjpeg video by concatenating (cat command) several others with same frame size and pixelformat. I would like to add a watermark to the entire video with mencoder.

Commands used: 

mkfifo myfifo
convert logo.png logo.rgba
(echo "RGBA32 640 360 -4 -4 1 1" ; cat logo.rgba ) >myfifo &
## logo.png is indeed sized 640x360 and i do need to shift it by 4 pixels upwards and to the left
mencoder -oac pcm -ovc lavc -lavcopts vcodec=mjpeg -vf bmovl=0:0:myfifo -o out.mp4 tmp.mjpeg

Everything seems to work fine, problem is that outputted mp4 container with mjpeg video codec ONLY has watermark until the first concatenated mjpeg ends (i.e. if first mjpeg used in concatenation was 5 seconds long, final content will only have 5 seconds watermarked, instead of all of the video)

How can i get by this?

Right now i need to convert to mpeg mp4 first and watermark the mpeg mp4, while converting back to mjpeg, and this implies a lot of unnecessary overhead.

I tried to reprocess the concatenated mjpeg both with ffmpeg AND mencoder by stream copying (i don't want to reencode the stream at all, but now i'm forced to do so twice), but when trying to watermark output again, still only the first mjpeg of the concatenation ends up watermarked. Can't understand how mencoder still can tell that something in the frames stream changes since both size and pixelformat is the same...

Any ideas would be greatly appreciated.

Regards,
DAV

---

### Post by x2305andy2305x on 2010-10-26
Update:

Found that it's not necessarily for concatenated mjpegs that it doesn't work, that's pure coincidence, even for a longer mjpeg obtained by transcoding an mpeg mp4, watermarking will stop early and always throw this: 
*** glibc detected *** /usr/bin/mencoder: free(): invalid next size (normal): 0x000000001af77500 ***
======= Backtrace: =========
/lib64/libc.so.6[0x32e287230f]
/lib64/libc.so.6(cfree+0x4b)[0x32e287276b]
/usr/bin/mencoder(av_destruct_packet+0xd)[0x6395ad]
/usr/bin/mencoder(av_free_packet+0x14)[0x6394f4]
/usr/bin/mencoder[0x583ce0]
/usr/bin/mencoder(ds_fill_buffer+0x9d)[0x4c317d]
/usr/bin/mencoder(ds_get_packet+0x45)[0x4c3835]
/usr/bin/mencoder(video_read_frame+0xa3b)[0x5060eb]
/usr/bin/mencoder(main+0x1754)[0x441234]
/lib64/libc.so.6(__libc_start_main+0xf4)[0x32e281d994]
/usr/bin/mencoder(cos+0x1a9)[0x43f3a9]

I might just not be on the right forum here...

---

