---
title: "Help with older set of recording scripts"
date: 2010-11-29
forum: Multimedia Software
---

### Post by chee on 2010-11-29
So I tried out these scripts [http://ubuntuforums.org/showthread.php?t=338029]("http://ubuntuforums.org/showthread.php?t=338029")
and they seem to work but I get no audio.

I ran the script in a terminal and this is what I saw:


6-Chan16 chosen as the channel to record.
00:00:20 chosen as the record time.
new entered as the file name.
1100 chosen as the encoding quality.
now entered as the start time.
1290968869 entered as the current time.
1290968869 entered as the start time.
0 entered as time to wait before encoding starts
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
tv.c: norm_from_string(NTSC): Bogus norm parameter, setting default.
v4l2: ioctl query control failed: Invalid argument
v4l2: ioctl query control failed: Invalid argument
SwScaler: reducing / aligning filtersize 1 -> 4
    Last message repeated 1 times
SwScaler: reducing / aligning filtersize 1 -> 1
SwScaler: reducing / aligning filtersize 9 -> 8
[swscaler @ 0xa108160]BICUBIC scaler, from uyvy422 to yuv420p using MMX2
[swscaler @ 0xa108160]using 4-tap MMX scaler for horizontal luminance scaling
[swscaler @ 0xa108160]using 4-tap MMX scaler for horizontal chrominance scaling
[swscaler @ 0xa108160]using 1-tap MMX "scaler" for vertical scaling (YV12 like)
[swscaler @ 0xa108160]720x480 -> 720x480
Forcing audio preload to 0, max pts correction to 0.

and then a whole bunch of "skipping frame" or "1 duplicate frame"  lines.

There were 2 spots that alarmed me,
v4l2: ioctl query control failed: Invalid argument
v4l2: ioctl query control failed: Invalid argument
and the last line though I don't know that that is a problem.

So any help with this would be great as it seems to be the perfect program for what I need.

Thank you.

---

### Post by chee on 2010-11-29
So now I have a new problem to go along with the old one,   I thought I would try killing pulseaudio and see if it recorded audio after that,  but I can't seem to kill the process,  no matter what I try (killall pulseaudio, pulseaudio -k, pulseaudio --kill, pasuspender) nothing gets rid of it.  It just keeps respawning,  so I edited the /etc/pulse/client.conf file line "respawn=yes" and changed it to no,  still doesn't work.

Anybody know why?

---

### Post by chee on 2010-12-01
So I got this working.  It works really well to be honest and is quite simple to use.   

For anyone that is interested,  I had to add ":adevice=/dev/dsp" after "amode=0"  near the very bottom of the script.  Then it worked great,  plus it is really easy to adjust the dimensions since they are right there too.

---

