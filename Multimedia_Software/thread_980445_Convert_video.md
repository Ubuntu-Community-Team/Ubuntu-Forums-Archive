---
title: "Convert video"
date: 2008-11-12
forum: Multimedia Software
---

### Post by ipburbank on 2008-11-12
Hi all, I came across a problem today. I use VLC to convert my videos between formats and re-size them, however it appears that it only uses one core.... I got a quad core for a reason.... I was wondering if there were any favorites out there I should try?

---

### Post by Rhubarb on 2008-11-12
There are 2 good CLI based apps that can do this for you:
ffmpeg and mencoder.
You can tell them both to use multiple threads when encoding.

Another app that may work is handbrake, but unfortunately I haven't tried out this app yet (it's a nice GUI app).

Using ffmpeg / mencoder can be a bit tricky, as there can be a lot of options you can pass to it (trellis quantization, bitrate, codecs, gamma correction, resolution, all sorts of stuff).
But, once you've got the right settings, encoded videos can be really small and high quality.  And of course once you've got the right settings, you could make up a nautilus script to make it easy for you to convert videos from within nautilus.

You'd be best off doing a search for these applications, as I haven't had much recent experience with them.

Best of luck.

---

### Post by IceBadger on 2008-11-12
I have not used VLC to transcode video.

It is possible to do this in dvd::rip, available from the ubuntu repositories.  You tell dvd::rip to use more threads, and the kernel places one on each core.  In your case, make it 4 threads.

[Here is a link that explains the process.]("http://ubuntuforums.org/archive/index.php/t-560969.html")

Something similar might work in VLC, but it gives you an idea on how to get started.

---

