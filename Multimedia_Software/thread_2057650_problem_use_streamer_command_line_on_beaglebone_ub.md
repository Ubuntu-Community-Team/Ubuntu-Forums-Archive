---
title: "problem use streamer command line on beaglebone ubuntu 12.04"
date: 2012-09-14
forum: Multimedia Software
---

### Post by eternalhero198 on 2012-09-14
I have a beaglebone use ubuntu v12.04.I want take photo by command ```
streamer -f jpeg -o image.jpeg 
```
but when i use it, have error   
> libv4l2: error allocating conversion buffer
mmap: Cannot allocate memory
v4l2: ioctl(fildes = 4 "/dev/video0", request = VIDIOC_QBUF, struct v4l2_buffer *data = { index = 0, type = 0, bytesused = 0, flags = 0, field = V4L2_FIELD_ANY, timestamp = { 0 seconds }, timecode = { type = 0, flags = 0, frames = 0, seconds = 0, minutes = 0, hours = 0 }, sequence = 0, memory = 0, length = 0, input = 0 }) failed, Invalid argument (22, EINVAL) because the data->type argument was incorrectly specified
munmap: Invalid argument
munmap: Invalid argument
munmap: Invalid argument

help me,please!
or another command can use on beaglebone ubuntu

---

