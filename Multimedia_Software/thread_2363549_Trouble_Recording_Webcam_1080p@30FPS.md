---
title: "Trouble Recording Webcam 1080p@30FPS"
date: 2017-06-11
forum: Multimedia Software
---

### Post by schmidtbag on 2017-06-11
I'm working on this personal project involving a couple identical 1080p webcams and a I.MX6 quad-core ARMv7 platform that records from them. I want to record the 1080p 30FPS MJPEG stream (so, not the raw YUYV stream) to a file with minimal CPU utilization.  The caveat is I can't depend on GPU acceleration.

Using ffmpeg, I can access the MJPEG stream with the resolution and theoretical framerate I want, but the quality is weirdly bad and even at 720p the CPU gets maxed-out, causing frame drops.  I haven't even attempted using the 2nd camera yet.  Here's the command I've been using:
ffmpeg -f v4l2 -s 1280x720 -input_format mjpeg -i /dev/video0 -c:v mjpeg -r 30 -b:v 256k -threads 4 output.mp4
Removing things like the "-c:v" or "-threads" flags haven't really changed the outcome.  If I use the YUYV stream, I get somewhere between 2-5FPS and the CPU is still under 100% load.

Meanwhile, I also tried using gstreamer.  This seems to use very little CPU which is great - Freescale provided a gstreamer plugin so perhaps that's why.  However, the problem is it seems to be skipping frames.  The video output is 30FPS, but the recording framerate seems to be maybe 5FPS.  In other words, it looks like a fast-forward timelapse, and I can't figure out how to make it stop doing this.  This is the command I've been using:
gst-launch-1.0 v4l2src device="/dev/video0" ! image/jpeg,width=1280,height=720,framerate=30/1 ! filesink location=output.avi
I can't seem to figure out if "image/jpeg" is actually utilizing the MJPEG stream or not.  The output is pretty much the same if I use "video/x-raw", except that doesn't work if I specify the framerate.  It doesn't work if I try using "video/x-jpeg".

You might be thinking "it's probably just your crappy ARM device" but I tried the camera on my x86 gaming PC.  The ffmpeg command works smoothly, but still taxes the CPU a lot.  The gstreamer command operates exactly the same way as it does on the ARM device.  Also, both VLC and qv4l2 are perfectly capable of viewing the webcam with 1080p@60Hz with very little CPU overhead, so I know for a fact the camera is capable of doing what I want.

So what I'm wondering is only one of the following:
1. How can I get ffmpeg to utilize less than 50% CPU without depending on transcoders?
2. How can I get gstreamer to record at 1080p@30FPS?
3. Is there something else that can do what I want?

---

### Post by Autodave on 2017-06-11
I am no expert on this (video) stuff, but I can tell you that what you are attempting to do is going to really tax the CPU. I have an 8 core over-clocked to 4.0, and the one time I recorded a program in 1080 (just to see if it was possible) at 30 fps, I was running all 8 cores at 80%. After a couple minutes, my PC was functioning as a space heater.

Besides the problem of the CPU usage, you also have a bigger problem of getting your HD to be able to write all that info as fast as the program wants it to. An SSD will help, but you are still writing an awful lot of data in a very short time span.

---

### Post by schmidtbag on 2017-06-11
> **Autodave said:**
> I am no expert on this (video) stuff, but I can tell you that what you are attempting to do is going to really tax the CPU. I have an 8 core over-clocked to 4.0, and the one time I recorded a program in 1080 (just to see if it was possible) at 30 fps, I was running all 8 cores at 80%. After a couple minutes, my PC was functioning as a space heater.

Besides the problem of the CPU usage, you also have a bigger problem of getting your HD to be able to write all that info as fast as the program wants it to. An SSD will help, but you are still writing an awful lot of data in a very short time span.

That can't be right, because there are plenty of people who stream 1080p@30FPS cameras all the time, even on systems worse than mine.  The only difference is instead of writing out through a network interface, I want to save the output to a disk.

If you stream raw, uncompressed video and save it as uncompressed, then yes, CPU usage is going to be very high and so will disk consumption.  But that's not what I'm trying to do.  My desktop CPU is a 1500X @ 3.95 GHz and running the ffmpeg command I supplied (but at 1080p) uses no more than 7% of the CPU.  This is with the MJPEG output the camera supplies; you can't do 30FPS on the raw output with this camera.  As I said before, gstreamer seems to have very low CPU usage on the ARM board, but the frame rate is low and I don't know why, and I know the storage isn't a bottleneck.

---

### Post by schmidtbag on 2017-06-11
So I managed to mostly solve my problem:

Using the following command:
gst-launch-1.0 v4l2src device=/dev/video0 ! image/jpeg,framerate=30/1,width=1920,height=1080 ! videorate ! avimux ! filesink location=output.avi
This will give me the 1080p output at 30FPS with pretty good quality, roughly 18% max CPU usage total (on the ARM system), and doesn't seem to get bottlenecked by the disk.  But, there's some weird issue where either the first roughly 15 seconds is a mostly black screen, or, doesn't start the recording.  This happens on both systems.

Any idea why this is happening?

---

