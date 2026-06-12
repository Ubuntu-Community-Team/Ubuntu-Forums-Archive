---
title: "PulseAudio streaming to file"
date: 2011-09-20
forum: Multimedia Software
---

### Post by Cosmologicon on 2011-09-20
Hi there! Can anyone tell me how to stream the raw audio data from PulseAudio into a file? I'd love any help, even if it's just a search term or another forum I should ask this on.

Someone told me to use GStreamer with "tcpclientsrc to read the data from the socket", but he was unable to tell me which socket, as he hadn't done it before. (tcpclientsrc requires a port number, doesn't it?) Anyway, the pipeline he suggested started with this:

[FONT="Courier New"][SIZE="2"]gst-launch tcpclientsrc ! audio/x-raw-int[/SIZE][/FONT]

When I try that I get:

[FONT="Courier New"][SIZE="2"]WARNING: erroneous pipeline: no element "audio"[/SIZE][/FONT]

So this is obviously wrong. But I've searched a whole lot and I haven't found any explanation of what I *should* be doing. Like I said, any hints at all would be great!

---

